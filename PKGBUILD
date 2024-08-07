# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>
# Maintainer: Felix Yan <felixonmars@archlinux.org>

pkgname=python-idna
pkgver=3.6
pkgrel=1
pkgdesc="Internationalized Domain Names in Applications (IDNA)"
arch=(
  'any'
)
license=(
  'BSD'
)
url="https://github.com/kjd/idna"
depends=(
  'python'
)
makedepends=('
  python-build'
  'python-installer'
  'python-flit-core'
)
checkdepends=(
  'python-pytest'
)
source=(
  "https://github.com/kjd/idna/archive/v$pkgver/$pkgname-$pkgver.tar.gz"
)
sha512sums=(
  '4ffadae74aa69529cd37a6d361564b2a11450af6aa15f6691ba668139f4efe2893361c0fe7bf8e0d8ebcba1dc8937d50a3dfb3782905f1e1983d01455dced1ff'
)

build() {
  cd \
    idna-$pkgver
  python \
    -m build \
    --no-isolation \
    --wheel
}

check() {
  cd \
    idna-$pkgver
  pytest
}

package() {
  cd \
    idna-$pkgver
  python \
    -m installer \
    --destdir="${pkgdir}" \
    dist/*.whl
  install \
    -Dm644 \
    LICENSE.md \
    -t \
    "$pkgdir"/usr/share/licenses/$pkgname/
}

