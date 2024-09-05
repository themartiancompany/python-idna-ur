# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>
# Maintainer: Felix Yan <felixonmars@archlinux.org>

_py='python'
_pkg=idna
pkgname="${_py}-${_pkg}"
pkgver=3.6
pkgrel=1
_pkgdesc=(
  "Internationalized Domain Names"
  "in Applications (IDNA)"
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  'any'
)
license=(
  'BSD'
)
_http="https://github.com"
_ns="kjd"
url="${_http}/${_ns}/${_pkg}"
depends=(
  "${_py}"
)
makedepends=(
  "${_py}-build"
  "${_py}-installer"
  "${_py}-flit-core"
)
checkdepends=(
  "${_py}-pytest"
)
source=(
  "${url}/archive/v${pkgver}/${pkgname}-${pkgver}.tar.gz"
)
sha512sums=(
  '4ffadae74aa69529cd37a6d361564b2a11450af6aa15f6691ba668139f4efe2893361c0fe7bf8e0d8ebcba1dc8937d50a3dfb3782905f1e1983d01455dced1ff'
)

build() {
  cd \
    "${_pkg}-${pkgver}"
  "${_py}" \
    -m build \
    --no-isolation \
    --wheel
}

check() {
  cd \
    "${_pkg}-${pkgver}"
  pytest
}

package() {
  cd \
    "${_pkg}-${pkgver}"
  "${_py}" \
    -m \
      installer \
    --destdir="${pkgdir}" \
    dist/*.whl
  install \
    -Dm644 \
    LICENSE.md \
    -t \
    "${pkgdir}"/usr/share/licenses/${pkgname}/
}

