# Maintainer: Evangelos Foutras <evangelos@foutrelis.com>
# Contributor: David Runge <dave@sleepmap.de>
# Contributor: Peter Baldwin <bald_pete@hotmail.com>

pkgname=python-jinja
pkgver=3.1.3
pkgrel=1
epoch=1
pkgdesc="A simple pythonic template language written in Python"
arch=('any')
url="https://palletsprojects.com/p/jinja/"
license=('BSD')
depends=('python-markupsafe')
makedepends=('python-setuptools')
optdepends=('python-babel: for i18n support')
checkdepends=('python-pytest')
source=(https://files.pythonhosted.org/packages/source/J/Jinja2/Jinja2-$pkgver.tar.gz)
sha256sums=('ac8bd6544d4bb2c9792bf3a159e80bba8fda7f07e81bc3aed565432d5925ba90')

prepare() {
  cd Jinja2-$pkgver
}

build() {
  cd Jinja2-$pkgver
  python3 setup.py build
}

check() {
  cd Jinja2-$pkgver
  # https://github.com/pypa/setuptools/issues/2466
  PYTHONDONTWRITEBYTECODE=1 PYTHONPATH=build/lib pytest \
    --deselect tests/test_loader.py::test_package_dir_list \
    --deselect tests/test_loader.py::test_package_dir_source \
    --deselect tests/test_loader.py::test_package_file_list \
    --deselect tests/test_loader.py::test_package_file_source \
    --deselect tests/test_loader.py::test_package_zip_list \
    --deselect tests/test_loader.py::test_package_zip_omit_curdir \
    --deselect tests/test_loader.py::test_package_zip_source
}

package() {
  cd Jinja2-$pkgver
  python3 setup.py install --root="$pkgdir" --optimize=1 --skip-build
  install -Dm644 LICENSE.rst -t "$pkgdir/usr/share/licenses/$pkgname"
}

# vim:set ts=2 sw=2 et:
