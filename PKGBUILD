# Maintainer: Joe User <joe.user@example.com>
pkgname=wlroots0.17-westmere
pkgver=0.17.4
pkgrel=13
pkgdesc="wlroots with westmere patches"
arch=('x86_64')
url="https://swaywm.org/"
license=('MIT')
makedepends=('wayland-protocols' 'wayland' 'vulkan-headers' 'xorg-xwayland')
optdepends=('swaync: simple sway notification demon')
source=("https://github.com/AlieeLinux/wlroots0.19-westmere/releases/download/wl/wlroots-0.17.4.tar.gz")
sha256sums=('d3190d19d03446955e68a92c77d4c74af78384b0db39a85a0b1582adc80f36d1')
provides=("wlroots0.17" "libwlroots.so=12-64" )
replaces=("wlroots0.17")
conflicts=('wlroots0.17')

build() {
        export CFLAGS="-march=westmere -mtune=nehalem -O2 -pipe -fstack-protector-strong -fno-plt -fPIC"
        export CXXFLAGS="${CFLAGS}"
        tar -xvf "wlroots-0.17.4.tar.gz" -C "$srcdir"
        cd "$srcdir/wlroots-0.17.4"
        mkdir build
        arch-meson build --prefix=/usr -Dc_args="$CFLAGS" -Dcpp_args="$CFLAGS"  Dxwayland=disabled
        ninja -C build -j $(nproc)
}
package() {
        cd "$srcdir/wlroots-0.17.4"
        DESTDIR="$pkgdir/" ninja -C build install -j $(nproc)
}
