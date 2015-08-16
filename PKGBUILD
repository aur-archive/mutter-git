# Contributor: Hinrich Harms <arch@hinrich.de>
# Contributor: Flamelab <panosfilip@gmail.com>
# Maintainer: Yosef Or Boczko <yoseforb@gnome.org>

_pkgname=mutter
pkgname=$_pkgname-git
pkgver=3.17.2.16.g64cf87c
pkgrel=1
_realver=3.17.2
pkgdesc="The next-gen WM for gnome, with compositing by clutter"
arch=('i686' 'x86_64')
url="http://www.gnome.org"
license=('GPL')
depends=("gtk3" "cogl>=1.17.1" "clutter>=1.21.3" 'dconf' 'gobject-introspection' "gsettings-desktop-schemas"
         'libcanberra' 'startup-notification' 'zenity' 'libsm' "upower>=0.99.0" "wayland>=1.4.93" "libxkbcommon-x11")
makedepends=('git' 'intltool' 'gnome-doc-utils' 'gtk-doc')
provides=("mutter=${_realver}" "mutter-wayland=${_realver}")
conflicts=('mutter' 'mutter-wayland')
groups=('gnome')
options=('!libtool' '!emptydirs')
install=$_pkgname.install
source=('git://git.gnome.org/mutter')
sha256sums=('SKIP')

prepare() {
  cd "$srcdir/$_pkgname"
}

pkgver() {
  cd "$srcdir/$_pkgname"
  git describe --always | sed 's|-|.|g'
}

build() {
  cd "$srcdir/$_pkgname"
  ./autogen.sh --prefix=/usr --sysconfdir=/etc \
      --libexecdir=/usr/lib/mutter \
      --localstatedir=/var --disable-static \
      --disable-schemas-compile --enable-compile-warnings=minimum \
      --enable-gtk-doc

  make

}

package()  {
  cd "$srcdir/$_pkgname"
  make DESTDIR="$pkgdir/" install
}
