# Maintainer: Linxuan Chen <me@black-desk.cn>

# shellcheck disable=SC2034,2154
# shellcheck shell=bash

pkgname=linglong-git
provides=('linglong')
pkgver=1.3.5.1.r61.gb8750a3
pkgrel=1
pkgdesc="a container based package manager"
arch=('any')
url="https://github.com/linuxdeepin/linglong"
license=('LGPL-3.0')
depends=('linglong-box')
source=("linglong-git::git+https://github.com/linuxdeepin/linglong")
sha512sums=('SKIP')
options=(debug)

pkgver() {
        cd "$pkgname" || exit
        git describe --long --tags | sed 's/\([^-]*-g\)/r\1/;s/-/./g;s/v\(.*\)/\1/'
}

build() {
        cd "$pkgname" || exit
        cmake -B build \
                -DCMAKE_BUILD_TYPE=RelWithDebInfo \
                -DCMAKE_INSTALL_PREFIX=/usr \
                -DCMAKE_INSTALL_SYSCONFDIR=/etc \
                -DCMAKE_INSTALL_LIBEXECDIR=/usr/lib
        cmake --build build
}

package() {
        cd "$pkgname" || exit
        DESTDIR="$pkgdir" cmake --install build
}
