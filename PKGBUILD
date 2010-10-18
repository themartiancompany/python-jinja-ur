# Maintainer: Evangelos Foutras <foutrelis@gmail.com>
# Contributor: Peter Baldwin <bald_pete@hotmail.com>

pkgname=python-jinja
pkgver=2.5.4
pkgrel=2
pkgdesc="A simple pythonic template language written in Python"
arch=('any')
url="http://jinja.pocoo.org/2/"
license=('BSD')
depends=('python-markupsafe' 'setuptools')
source=(http://pypi.python.org/packages/source/J/Jinja2/Jinja2-$pkgver.tar.gz)
md5sums=('4553d5aef15d550bfebbc1903014067e')

build() {
  cd "$srcdir/Jinja2-$pkgver"

  python2 setup.py install --root="$pkgdir" -O1

  install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}

# vim:set ts=2 sw=2 et:
