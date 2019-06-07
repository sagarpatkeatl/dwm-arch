# $Id$
# Maintainer: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Contributor: Dag Odenhall <dag.odenhall@gmail.com>
# Contributor: Grigorios Bouzakis <grbzks@gmail.com>

pkgname=dwm
pkgver=6.2
pkgrel=1
pkgdesc="A dynamic window manager for X"
url="http://dwm.suckless.org"
arch=('i686' 'x86_64')
license=('MIT')
options=(zipman)
depends=('libx11' 'libxinerama' 'libxft' 'freetype2' 'st' 'dmenu')
install=dwm.install
source=(dwm-$pkgver.tar.gz
        dwm-wrapper
	config.h
	dwm.desktop)
sha256sums=('418eaf008c5de6a827885479e6cb96d7725f87ca5480a245fec3249f47e1e729'
            '110954d0fab705f91700d97e790643b5d4294cd091c8178f582a44b43788cf3d'
            'f26e00fef844c84c4e4d56070fe0ae1acb17e4bcec177b1b1c6db73ba7aebf49'
            'c12a22f0a42497c6d436c2c029f43acca5306cb7c909ac5fd431590da861f3cb')

prepare() {
  cd "$srcdir/$pkgname"
  cp "$srcdir/config.h" config.h
}

build() {
  cd "$srcdir/$pkgname"
  make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11 FREETYPEINC=/usr/include/freetype2
}

package() {
  cd "$srcdir/$pkgname"
  make PREFIX=/usr DESTDIR="$pkgdir" install
  install -m644 -D LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
  install -m644 -D README "$pkgdir/usr/share/doc/$pkgname/README"
  install -m755 -D "$srcdir/dwm-wrapper" "$pkgdir/usr/bin/dwm-wrapper"
  install -m644 -D "$srcdir/dwm.desktop" "$pkgdir/usr/share/xsessions/dwm.desktop"
}
