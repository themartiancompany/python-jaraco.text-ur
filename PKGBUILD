# Maintainer: Chih-Hsuan Yen <yan12125@archlinux.org>
# Contributor: Kyle Keen <keenerd@gmail.com>

_py="python"
_pyver="$( \
  "${_py}" \
    -V | \
    awk \
      '{print $2}')"
_pymajver="${_pyver%.*}"
_proj="jaraco"
_pkg="${_proj}.text"
pkgname="${_py}-${_pkg}"
# https://github.com/jaraco/jaraco.text/blob/main/NEWS.rst
pkgver=3.12.0
pkgrel=1
pkgdesc='Module for text manipulation'
_http="https://github.com"
_ns="${_proj}"
arch=(
  'any'
)
url="${_http}/${_ns}/${_pkg}"
license=('MIT')
depends=(
  "${_py}>=${_pymajver}"
  "${_py}-${_proj}.functools"
  "${_py}-${_proj}.context"
  "${_py}-autocommand"
  "${_py}-inflect"
  "${_py}-more-itertools"
)
makedepends=(
  'python-build'
  'python-installer'
  'python-setuptools-scm'
  'python-wheel'
)
checkdepends=(
  'python-pytest'
)
conflicts=(
  'python-jaraco'
)
replaces=(
  'python-jaraco'
)
source=(
  "https://files.pythonhosted.org/packages/source/j/jaraco.text/jaraco.text-$pkgver.tar.gz"
)
sha512sums=(
  '75068006c96dae3b8d21228f2ae21820939c68b1fb7e5db35bd0c1126a20399eb4d99c6bea15e88076599956c4b41104558cd32d860d8f4fd4e96aeeb22711c9'
)

build() {
  cd \
    "${srcdir}/${_pkg}-${pkgver}"
  "${_py}" \
    -m build \
    --wheel \
    --no-isolation
}

check() {
  cd \
    "${srcdir}/${_pkg}-${pkgver}"
  PYTHONPATH="$PWD" \
  pytest
}

package() {
  cd \
    "${srcdir}/${_pkg}-${pkgver}"
  "${_py}" \
    -m installer \
    --destdir="${pkgdir}" \
    dist/*.whl
  install \
    -Dm644 \
    LICENSE \
    "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}

# vim:set ts=2 sw=2 et:
