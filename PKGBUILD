# Maintainer: Chih-Hsuan Yen <yan12125@archlinux.org>
# Contributor: Kyle Keen <keenerd@gmail.com>

pkgname=python-jaraco.text
# https://github.com/jaraco/jaraco.text/blob/main/NEWS.rst
pkgver=3.12.0
pkgrel=1
pkgdesc='Module for text manipulation'
arch=('any')
url='https://github.com/jaraco/jaraco.text'
license=('MIT')
depends=('python' 'python-jaraco.functools' 'python-jaraco.context' 'python-autocommand' 'python-inflect' 'python-more-itertools')
makedepends=('python-build' 'python-installer' 'python-setuptools-scm' 'python-wheel')
checkdepends=('python-pytest')
conflicts=('python-jaraco')
replaces=('python-jaraco')
source=("https://files.pythonhosted.org/packages/source/j/jaraco.text/jaraco.text-$pkgver.tar.gz")
sha512sums=('75068006c96dae3b8d21228f2ae21820939c68b1fb7e5db35bd0c1126a20399eb4d99c6bea15e88076599956c4b41104558cd32d860d8f4fd4e96aeeb22711c9')

build() {
  cd "$srcdir/jaraco.text-$pkgver"
  python -m build --wheel --no-isolation
}

check() {
  cd "$srcdir/jaraco.text-$pkgver"
  PYTHONPATH="$PWD" pytest
}

package() {
  cd "$srcdir/jaraco.text-$pkgver"
  python -m installer --destdir="$pkgdir" dist/*.whl
  install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}

# vim:set ts=2 sw=2 et:
