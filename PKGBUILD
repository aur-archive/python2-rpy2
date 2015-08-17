# Maintainer: Oliver Sherouse <oliver DOT sherouse AT gmail DOT com>
# Contributor: David Scholl <djscholl@gmail.com> 
# Contributor: David Pretty <david.pretty@gmail.com> 
pkgname=python2-rpy2
pkgver=2.4.3
pkgrel=1
pkgdesc="A very simple, yet robust, Python interface to the R Programming Language."
arch=('any')
url="http://rpy.sourceforge.net/"
license=('MPL' 'GPL' 'LGPL')
depends=('python2-numpy' 'r')
source=("http://pypi.python.org/packages/source/r/rpy2/rpy2-$pkgver.tar.gz")
md5sums=('57e3fda409226dffb543c913c8553cdc')

package() {
  cd $srcdir/rpy2-$pkgver
  sed -i "s:Rlapack:lapack:" setup.py
  sed -i "s:'python':'python2':" rpy/rinterface/tests/test_EmbeddedR.py
  sed -i "s:os.path.join(RHOME.strip(), 'include'):'/usr/include/R':" setup.py
  sed -i "s:os.path.join(RHOME.strip(), 'include'):'/usr/include/R':" setup.py
  python2 setup.py install --prefix=/usr --root=$pkgdir || return 1
  mkdir -p $pkgdir/etc/ld.so.conf.d
  echo /usr/lib/R/lib > $pkgdir/etc/ld.so.conf.d/rpy_$CARCH.conf
}
