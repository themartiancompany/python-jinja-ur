# Maintainer: Evangelos Foutras <foutrelis@gmail.com>
# Contributor: Peter Baldwin <bald_pete@hotmail.com>

pkgname=python-jinja
pkgver=2.1.1
pkgrel=4
pkgdesc="A simple pythonic template language written in Python"
arch=('i686' 'x86_64')
url="http://jinja.pocoo.org/2/"
license=('BSD')
depends=('setuptools')
source=(http://pypi.python.org/packages/source/J/Jinja2/Jinja2-$pkgver.tar.gz)
md5sums=('b37fc262e4f613eec57c3defe6aea97c')

build() {
  cd "$srcdir/Jinja2-$pkgver"

  # Put documentation in the correct directory (usr/share/doc)
  sed -i "s|'docs'|'share/doc/$pkgname'|" setup.py || return 1

  python setup.py install --root="$pkgdir" --optimize=1 || return 1

  install -D -m644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}

# vim:set ts=2 sw=2 et:
