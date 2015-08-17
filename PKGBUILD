# Maintainer: Doug Newgard <scimmia22 at outlook dot com>
# Contributor: Fabio Falcinelli <fabio.falcinelli@gmail.com>

pkgname=rage-svn
_pkgname=rage
pkgver=83451
pkgrel=2
pkgdesc="An Enlightened multimedia library browser based on EFL"
arch=('i686' 'x86_64')
license=('BSD')
url="http://www.enlightenment.org"
makedepends=('subversion')
depends=('emotion')
source=("svn+http://svn.enlightenment.org/svn/e/trunk/$_pkgname"
        'rage.desktop')
md5sums=('SKIP'
         '7e56125cc786187267a33cb3ef7a9465')

pkgver() {
  cd "$SRCDEST/$_pkgname"

  LC_ALL=C svn info | awk '/Last Changed Rev/ {print $4}'
}

build() {
  cd "$srcdir/$_pkgname"

  ./autogen.sh --prefix=/usr

  make
}

package() {
  cd "$srcdir/$_pkgname"

  make DESTDIR="$pkgdir" install

# install desktop file
  install -Dm644 "$srcdir/rage.desktop" "$pkgdir/usr/share/applications/rage.desktop"

# install license files
  install -Dm644 AUTHORS "$pkgdir/usr/share/licenses/$pkgname/AUTHORS"
  install -Dm644 COPYING "$pkgdir/usr/share/licenses/$pkgname/COPYING"
}

