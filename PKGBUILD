# Maintainer: Felix Yan <felixonmars@archlinux.org>

pkgbase=python-idna
pkgname=('python-idna' 'python2-idna')
pkgver=2.6
pkgrel=1
pkgdesc="Internationalized Domain Names in Applications (IDNA)"
arch=('any')
license=('BSD')
url="https://github.com/kjd/idna"
makedepends=('python-setuptools' 'python2-setuptools')
source=("https://pypi.io/packages/source/i/idna/idna-$pkgver.tar.gz")
sha512sums=('cb5dbfab44c4d11521c67f9d29391f184d1267a3da6dc89f4ed12c60a7a909d5c7474c3ea2bddd0af7063f4f620e87a8dd586bb07e8b961b30b1dd7c969704c2')

prepare() {
   cp -a idna-$pkgver{,-py2}
}

build() {
   cd "$srcdir"/idna-$pkgver
   python setup.py build
 
   cd "$srcdir"/idna-$pkgver-py2
   python2 setup.py build
}

check() {
   cd "$srcdir"/idna-$pkgver
   python setup.py test

   cd "$srcdir"/idna-$pkgver-py2
   python2 setup.py test
}
 
package_python-idna() {
   depends=('python')
 
   cd idna-$pkgver
   python setup.py install --root="$pkgdir" --optimize=1 --skip-build
   install -Dm644 LICENSE.rst "$pkgdir"/usr/share/licenses/$pkgname/LICENSE.rst
}
 
package_python2-idna() {
   depends=('python2')
 
   cd idna-$pkgver-py2
   python2 setup.py install --root="$pkgdir" --optimize=1 --skip-build
   install -Dm644 LICENSE.rst "$pkgdir"/usr/share/licenses/$pkgname/LICENSE.rst
}
