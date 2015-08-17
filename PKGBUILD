#  Maintainer: Archadept
# Contributor: Andrea Tarocchi <valdar@email.it>
#    Revision: 2011-08-08

 _PKGNAMENX=wesnoth-devel

 pkgname=${_PKGNAMENX}-x
 pkgver=1.10
 pkgrel=1
 pkgdesc="Turn-based strategy game on a fantasy world. This package is only for those who can't wait for stable!"
 arch=('i686' 'x86_64')
 url="http://www.wesnoth.org/"
 license=('GPL')
 depends=('pango' 'sdl_ttf' 'sdl_net' 'sdl_mixer' 'sdl_image' 'boost' 'fribidi' 'ruby' 'dbus-core')
 makedepends=('scons')
 conflicts=('wesnoth-devel' 'wesnoth')
 install=${_PKGNAMENX}.install
 source=(http://sourceforge.net/projects/wesnoth/files/wesnoth-$pkgver/wesnoth-$pkgver/wesnoth-$pkgver.tar.bz2 \
 ${_PKGNAMENX}.desktop \
 wesnoth_editor-devel.desktop \
 wesnoth-devel-icon.xpm \
 wesnoth-devel_editor-icon.xpm)
 md5sums=('707daa13e2f5b3976d9b169aab62dc29'
 'ac79ad95324d0e6bbd21352e39a25e36'
 '428eea0f8b0d1fd5cc49c448ef9bbe33'
 'b73f4fdefd3e7daa158cce278f11be64'
 '931e7443fe37b2862ca59f65ded74a0b')
 
 build() {
 
 # CONFIGURATION - scons
 _SCONSFLAGS="destdir=$pkgdir build=release wesnoth wesnothd campaignd test prefix=/usr prefsdir=.config/wesnoth-devel program_suffix=-devel datadirname=wesnoth-devel fifodir=/var/run/wesnothd-devel docdir=/usr/share/doc/wesnoth-devel mandir=/usr/share/man/wesnoth-devel"

 cd "${srcdir}/wesnoth-$pkgver"
 
 scons install $_SCONSFLAGS
 
 # INSTALLING of menu entry and icons:
 install -D -m644 ../../wesnoth-devel.desktop ${pkgdir}/usr/share/applications/wesnoth-devel.desktop
 install -D -m644 ../../wesnoth-devel-icon.xpm ${pkgdir}/usr/share/pixmaps/wesnoth-devel-icon.xpm
 install -D -m644 ../../wesnoth-devel-icon.xpm ${pkgdir}/usr/share/icons/wesnoth-devel-icon.xpm
 
 install -D -m644 ../../wesnoth_editor-devel.desktop ${pkgdir}/usr/share/applications/wesnoth_editor-devel.desktop
 install -D -m644 ../../wesnoth-devel_editor-icon.xpm ${pkgdir}/usr/share/pixmaps/wesnoth-devel_editor-icon.xpm
 install -D -m644 ../../wesnoth-devel_editor-icon.xpm ${pkgdir}/usr/share/icons/wesnoth-devel_editor-icon.xpm
 
 chmod +x ${pkgdir}/var/run/wesnothd-devel
 chmod o+r ${pkgdir}/var/run/wesnothd-devel
 
 rm -f ${pkgdir}/usr/share/applications/wesnoth.desktop
 rm -f ${pkgdir}/usr/share/applications/wesnoth_editor.desktop
 rm -f ${pkgdir}/usr/share/icons/wesnoth-icon.png
 rm -f ${pkgdir}/usr/share/icons/wesnoth_editor-icon.png
 }
