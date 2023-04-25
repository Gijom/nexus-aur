# This is an example PKGBUILD file. Use this as a start to creating your own,
# and remove these comments. For more information, see 'man PKGBUILD'.
# NOTE: Please fill out the license field for your package! If it is unknown,
# then please put 'unknown'.

# Maintainer: Guillaume Chanel <guillaume.chanel@unige.ch>
pkgname=nexus-client-git
pkgver=0.0.0
pkgrel=1
epoch=
pkgdesc="Client for the virtual desktop infrastructure"
arch=('x86_64' 'aarch64')
url="https://gitedu.hesge.ch/flg_projects/nexus_vdi/nexus-client"
license=('unknown')
groups=()
depends=()  # depends on go but is it a dependency or just for build ? -> makedepends, others are needed ?
makedepends=('git' 'go' 'upx')
checkdepends=()
optdepends=()
provides=()
conflicts=()
replaces=()
backup=()  # check if there are any configuration files in /etc that need to be placed here (relative path see doc)
options=()
install=
changelog=
source=('$pkgname::git+$url')
noextract=()
md5sums=('SKIP')
validpgpkeys=()

prepare() {
}

build() {
    cd "$pkgname/src/nexus-cli"
    if [ "$CARCH" == "x86_64" ]; then
        make build OS=linux ARCH=amd64
    else
        if [ "$CARCH" == "aarch64" ]; then
            make build OS=linux ARCH=arm64
        else
            echo "$CARCH not supported"  # should not happen
        fi
    fi
}

check() {
}

package() {
    #TODO
    if [ "$CARCH" == "x86_64" ]; then
        cp "$pkgname/src/nexus-cli/build/amd64/linux/nexus-cli" "$pkgdir/usr/bin"
    else
        if [ "$CARCH" == "aarch64" ]; then
            cp "$pkgname/src/nexus-cli/build/arm64/linux/nexus-cli" "$pkgdir/usr/bin"
        else
            echo "$CARCH not supported"  # should not happen
        fi
    fi
    # TODO: copy file damn it !
}
