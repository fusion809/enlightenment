# Maintainer: Ronald van Haren <ronald@archlinux.org>
# Contributor: Enlightenment Developers <enlightenment-devel@enlightenment.org>>

pkgname=enlightenment
pkgver=0.21.1
pkgrel=1
pkgdesc="Enlightenment window manager"
arch=('i686' 'x86_64')
url="http://www.enlightenment.org"
license=('BSD')
depends=('elementary' 'xcb-util-keysyms' 'hicolor-icon-theme' 'pixman' 'mesa'
         'desktop-file-utils' 'udisks2' 'ttf-font' 'bluez-libs')
optdepends=('connman: network module'
            'acpid: power events on laptop lid close'
	    'geoip-database: geolocation module')
provides=('notification-daemon')
backup=('etc/enlightenment/sysactions.conf'
        'etc/xdg/menus/e-applications.menu')
source=(http://download.enlightenment.org/rel/apps/${pkgname}/$pkgname-$pkgver.tar.xz)
install=enlightenment.install
sha1sums=('c022d2838ec89b483326585d5307f8b9c21864bd')

build() {
  cd "${srcdir}/${pkgname}-${pkgver}"

  export CFLAGS="$CFLAGS -fvisibility=hidden"

  ./configure --prefix=/usr --sysconfdir=/etc \
    --enable-xwayland --enable-wayland \
    --disable-wl-weekeyboard

  make
}

package() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  make -j1 DESTDIR="$pkgdir" install

  # install LICENSE
  install -Dm644 COPYING "$pkgdir/usr/share/licenses/$pkgname/COPYING"
}
