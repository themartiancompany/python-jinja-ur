# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>
# Maintainer: Evangelos Foutras <foutrelis@archlinux.org>
# Contributor: David Runge <dave@sleepmap.de>
# Contributor: Peter Baldwin <bald_pete@hotmail.com>
_py="python"
_pyver="$( \
  "${_py}" \
    -V | \
    awk \
      '{print $2}')"
_pymajver="${_pyver%.*}"
_pyminver="${_pymajver#*.}"
_pynextver="${_pymajver%.*}.$(( \
  ${_pyminver} + 1))"
_pkg=jinja
pkgname="${_py}-${_pkg}"
# _name="${pkgname#python-}"
pkgver=3.1.4
pkgrel=1
epoch=1
pkgdesc="A simple pythonic template language written in Python"
arch=('any')
url="https://palletsprojects.com/p/${_pkg}"
license=('BSD-3-Clause')
depends=(
  'python'
  'python-markupsafe'
)
makedepends=(
  "${_py}-build"
  "${_py}-installer"
  "${_py}-setuptools"
  "${_py}-wheel"
  "${_py}-flit-core"
)
optdepends=(
  'python-babel: for i18n support'
)
checkdepends=(
  'python-pytest'
)
_http="https://github.com"
_ns="pallets"
_url="${_http}/${_ns}/${_pkg}"
source=(
  "${_pkg}-${pkgver}.tar.gz::${_url}/archive/refs/tags/${pkgver}.tar.gz"
)
sha256sums=(
  'ed06f67abd2c8b7697dfb714f80715903ab0507e3c5acc11e92477e4ea51033b'
)

prepare() {
  echo \
    "nope"
}

build() {
  cd \
    "${_pkg}-${pkgver}"
  "${_py}" \
    -m \
      build \
    --wheel \
    --no-isolation
}

check() {
  cd \
    "${_pkg}-${pkgver}"
  PYTHONPATH=src \
  pytest
}

package() {
  cd \
    "${_pkg}-${pkgver}"
  "${_py}" \
    -m installer \
    --destdir="${pkgdir}" \
    dist/*.whl
  install \
    -Dm644 \
    LICENSE.txt \
    -t \
    "${pkgdir}/usr/share/licenses/${pkgname}"
}

# vim:set ts=2 sw=2 et:
