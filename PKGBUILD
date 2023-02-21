# Maintainer: Name <email>

# shellcheck disable=SC2034,2154
# shellcheck shell=bash

pkgname=package_name
pkgver=0
pkgrel=1
pkgdesc="package description"
arch=('any')
url="https://github.com/..."
license=()
depends=()
source=("$pkgname::git+https://github.com/...")
sha512sums=('SKIP')
options=(debug)
pkgver() {
        cd "$pkgname" || exit
        git describe --long --tags | sed 's/\([^-]*-g\)/r\1/;s/-/./g;s/v\(.*\)/\1/'
}

build() {
        cd "$pkgname" || exit
        cmake -B. \
                -DCMAKE_BUILD_TYPE=RelWithDebInfo \
                -DCMAKE_INSTALL_PREFIX=/usr \
                -DCMAKE_INSTALL_SYSCONFDIR=/etc \
                -DCMAKE_INSTALL_LIBEXECDIR=/usr/lib
        cmake --build .
}

package() {
        cd "$pkgname" || exit
        DESTDIR="$pkgdir" cmake --install .
}
