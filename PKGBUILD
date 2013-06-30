# Maintainer: Evangelos Foutras <evangelos@foutrelis.com>
# Contributor: Peter Baldwin <bald_pete@hotmail.com>

pkgname=('python-jinja' 'python2-jinja')
pkgver=2.7
pkgrel=2
pkgdesc="A simple pythonic template language written in Python"
arch=('any')
url="http://jinja.pocoo.org/"
license=('BSD')
makedepends=('python-distribute' 'python2-distribute' 'python-markupsafe'
             'python2-markupsafe')
source=(http://pypi.python.org/packages/source/J/Jinja2/Jinja2-$pkgver.tar.gz
        Fix-PrefixLoader-does-not-pass-globals-to-load.patch)
sha256sums=('474f1518d189ae7e318b139fecc1d30b943f124448cfa0f09582ca23e069fa4d'
            '939f61f022a61661bb65e36eb53dd3482cbdb08ea8098c439f7c1aa7f2810b8f')

prepare() {
  cd "$srcdir/Jinja2-$pkgver"

  # https://github.com/mitsuhiko/jinja2/issues/225
  patch -Np1 -i "$srcdir/Fix-PrefixLoader-does-not-pass-globals-to-load.patch"
}

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
