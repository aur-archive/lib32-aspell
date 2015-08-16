# Contributor: Jochem Kossen <j.kossen@home.nl>
# Contributor: dorphell <dorphell@archlinux.org>
# Contributor: Thayer Williams <thayer@archlinux.org>
# Contributor: Daniel J Griffiths <ghost1227@archlinux.us>
# Maintainer : Andy McMillan <awmcmillan@gmail.com

pkgname=lib32-aspell
_pkgbasename=aspell
pkgver=0.60.6.1
_pkgmajorver=0.60
pkgrel=2
pkgdesc="A spell checker designed to eventually replace Ispell (32-bit libraries)"
arch=('x86_64')
url="http://aspell.net/"
license=('LGPL')
depends=('gcc-libs-multilib' 'lib32-ncurses' 'aspell')
makedepends=('gcc-multilib')
optdepends=('perl: to import old dictionaries')
options=('!libtool')
source=(ftp://ftp.gnu.org/gnu/${_pkgbasename}/${_pkgbasename}-${pkgver}.tar.gz)
sha1sums=('ff1190db8de279f950c242c6f4c5d5cdc2cbdc49')

build() {
  export CC="gcc -m32"
  export CXX="g++ -m32"
  export PKG_CONFIG_PATH="/usr/lib32/pkgconfig"

  cd "${srcdir}/${_pkgbasename}-${pkgver}"
  ./configure --prefix=/usr --sysconfdir=/etc --libdir=/usr/lib32 --enable-dict-dir=/usr/lib/aspell-"${_pkgmajorver}"
  make
}

package() {
  cd "${_pkgbasename}-${pkgver}"
  make DESTDIR="${pkgdir}" install
  rm -rf "${pkgdir}"/usr/{include,share,bin,lib} #remove files that are being provided by original aspell
}
