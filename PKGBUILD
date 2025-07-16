# Maintainer: Joe User <joe.user@example.com>
pkgname=sway-westmere
pkgver=1.11
pkgrel=1
pkgdesc="sway with westmere patchez"
arch=('x86_64')
url="https://swaywm.org/"
license=('MIT')
depends=('glibc' 'wlroots0.19')
makedepends=('wlroots0.19' 'wayland-protocols' 'scdoc' )
optdepends=('swaync: simple sway notification demon')
source=("https://github.com/swaywm/sway/releases/download/1.11/sway-1.11.tar.gz")
sha256sums=('0e37a55b7c3379230e97e1ad982542b75016a0c7d6676198604e557f9b373dae')
provides=("sway")
replaces=("sway")

build() {
        export CFLAGS="-march=westmere -mtune=nehalem -O2 -pipe -fstack-protector-strong -fno-plt -fPIC -frecord-gcc-switches"
        export CXXFLAGS="${CFLAGS}"
        tar -xvf "sway-1.11.tar.gz" -C "$srcdir"
        cd "$srcdir/sway-1.11"
        mkdir build
        arch-meson build --prefix=/usr -Dc_args="$CFLAGS" -Dcpp_args="$CFLAGS" -Dsd-bus-provider=libsystemd -Dxwayland=disabled
        ninja -C build -j $(nproc)
}
package() {
        cd "$srcdir/sway-1.11"
        DESTDIR="$pkgdir/" ninja -C build install -j2
}
