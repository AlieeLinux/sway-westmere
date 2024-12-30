# Maintainer: Your Name <your.email@example.com>
pkgname=sway-optimized-git
pkgver=1.0.0
pkgrel=1
pkgdesc="A simple example package"
arch=('x86_64')
url="https://example.com"
license=('GPL')
depends=('bash')  # Dependencies
makedepends=()
source=("https://example.com/mypackage-${pkgver}.tar.gz")
sha256sums=('SKIP')  # Replace with actual checksum

build() {
    cd "${srcdir}/${pkgname}-${pkgver}"
    make
}

package() {
    cd "${srcdir}/${pkgname}-${pkgver}"
    make DESTDIR="${pkgdir}" install
}

