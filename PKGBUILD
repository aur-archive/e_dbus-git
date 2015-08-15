# Maintainer: Doug Newgard <scimmia22 at outlook dot com>
# Contributor: Ronald van Haren <ronald.archlinux.org>

pkgname=e_dbus-git
_pkgname=e_dbus
pkgver=1.7.6.568.3415409
pkgrel=1
pkgdesc="EFL's (deprecated) DBus wrapping and glue layer library - Development version"
arch=('i686' 'x86_64')
url="http://www.enlightenment.org"
license=('BSD')
depends=('efl-git')
makedepends=('git')
provides=("e_dbus=$pkgver" 'e_dbus-svn')
conflicts=('e_dbus' 'e_dbus-svn')
options=('!libtool' 'debug')
source=("git://git.enlightenment.org/legacy/$_pkgname.git")
md5sums=('SKIP')

pkgver() {
  cd "$srcdir/$_pkgname"

  for i in v_maj v_min v_mic; do
    local _$i=$(grep -m 1 $i configure.ac | sed 's/m4//' | grep -o "[[:digit:]]*")
  done

  echo $_v_maj.$_v_min.$_v_mic.$(git rev-list --count HEAD).$(git rev-parse --short HEAD)
}

build() {
  cd "$srcdir/$_pkgname"
  
  ./autogen.sh --prefix=/usr

  make
}

package(){
  cd "$srcdir/$_pkgname"

  make DESTDIR="$pkgdir" install

# install license files
  install -Dm644 COPYING "$pkgdir/usr/share/licenses/$pkgname/COPYING"
  install -Dm644 AUTHORS "$pkgdir/usr/share/licenses/$pkgname/AUTHORS"
}
