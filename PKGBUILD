# Maintainer:  cuihao <cuihao dot leo at gmail dot com>
# Contributor: Xavier Devlamynck <magicrhesus@ouranos.be>
# Contributor: twa022 <twa022@gmail.com>

# Original PKGBUILD (extra/gtk-xfce-engine):
# $Id: PKGBUILD 149817 2012-02-11 08:22:29Z foutrelis $
# Maintainer: Evangelos Foutras <evangelos@foutrelis.com>
# Contributor: tobias <tobias funnychar archlinux.org>

pkgbase=gtk-xfce-engine-devel
_pkgbase=gtk-xfce-engine
pkgname=gtk-xfce-engine-devel
true && pkgname=('gtk2-xfce-engine-devel' 'gtk3-xfce-engine-devel')
pkgver=3.0.0
pkgrel=1
arch=('i686' 'x86_64')
pkgdesc="Xfce Gtk+ engine (Development Version)"
url="http://www.xfce.org/"
license=('GPL2')
makedepends=('gtk2' 'gtk3')
depends=('gtk2' 'gtk3')
options=('!libtool')
source=(http://archive.xfce.org/src/xfce/$_pkgbase/3.0/$_pkgbase-$pkgver.tar.bz2)
sha1sums=('bc35a26fc3723908e264234f12e384175779d18c')

build() {
  cd "$srcdir/$_pkgbase-$pkgver"

  ./configure \
    --prefix=/usr \
    --sysconfdir=/etc \
    --libexecdir=/usr/lib \
    --localstatedir=/var \
    --disable-static \
    --disable-debug
  make
}

package_gtk2-xfce-engine-devel() {
  _pkgname=gtk2-xfce-engine
  true && pkgdesc="Xfce Gtk+-2.0 engine (Development Version)"
  true && depends=('gtk2')
  replaces=('gtk-xfce-engine')

  groups=('xfce4-devel')
  provides=("gtk-xfce-engine=$pkgver-$pkgrel" "$_pkgname=$pkgver")
  conflicts=("$_pkgname" "$_pkgname-git" "$_pkgbase" "$_pkgbase-devel" "$_pkgbase-git")


  cd "$srcdir/$_pkgbase-$pkgver"
  make DESTDIR="$pkgdir" install

  # Remove gtk3 engine and themes
  find "$pkgdir" -name gtk-3.0 -exec rm -r {} +
}

package_gtk3-xfce-engine-devel() {
  _pkgname=gtk3-xfce-engine
  true && pkgdesc="Xfce Gtk+-3.0 engine (Development Version)"
  true && depends=('gtk3')

  groups=('xfce4-devel')
  provides=("$_pkgname=$pkgver")
  conflicts=("$_pkgname" "$_pkgname-git")

  cd "$srcdir/$_pkgbase-$pkgver"
  make DESTDIR="$pkgdir" install

  # Remove gtk2 engine and themes
  find "$pkgdir" -name gtk-2.0 -exec rm -r {} +
}

# vim:set ts=2 sw=2 et: