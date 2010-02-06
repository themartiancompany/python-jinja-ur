# Maintainer: Evangelos Foutras <foutrelis@gmail.com>
# Contributor: Peter Baldwin <bald_pete@hotmail.com>

pkgname=python-jinja
pkgver=2.2.1
pkgrel=1
pkgdesc="A simple pythonic template language written in Python"
arch=('i686' 'x86_64')
url="http://jinja.pocoo.org/2/"
license=('BSD')
depends=('setuptools')
source=(http://pypi.python.org/packages/source/J/Jinja2/Jinja2-$pkgver.tar.gz)
md5sums=('fea849d68891218eb0b21c170f1c32d5')

build() {
  cd "$srcdir/Jinja2-$pkgver"

  python setup.py --with-speedups install --root="$pkgdir" --optimize=1 || return 1

  install -D -m644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}

# vim:set ts=2 sw=2 et:
