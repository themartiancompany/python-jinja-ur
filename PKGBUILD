# Maintainer: Evangelos Foutras <evangelos@foutrelis.com>
# Contributor: Peter Baldwin <bald_pete@hotmail.com>

pkgname=('python-jinja' 'python2-jinja')
pkgver=2.6
pkgrel=3
pkgdesc='Simple pythonic template language written in Python'
arch=('any')
url="http://jinja.pocoo.org/"
license=('BSD')
makedepends=('python-distribute' 'python2-distribute' 'python-markupsafe' 'python2-markupsafe')
source=(http://pypi.python.org/packages/source/J/Jinja2/Jinja2-$pkgver.tar.gz)
sha256sums=('a85e185375db75c109f99ecde3d55415f035e7068a82252cf4f16c667ac38f49')

build() {
  cd "$srcdir"

  rm -rf python{2,3}-build
  for builddir in python{2,3}-build; do
    cp -r Jinja2-$pkgver $builddir
    pushd $builddir
    ${builddir%-build} setup.py build
    popd
  done
}

package_python-jinja() {
  depends=('python-distribute' 'python-markupsafe')

  cd "$srcdir/python3-build"

  python3 setup.py install --root="$pkgdir" -O1

  install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}

package_python2-jinja() {
  depends=('python2-distribute' 'python2-markupsafe')

  cd "$srcdir/python2-build"

  python2 setup.py install --root="$pkgdir" -O1

  install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}

# vim:set ts=2 sw=2 et:
