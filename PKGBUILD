# This is an example PKGBUILD file. Use this as a start to creating your own,
# and remove these comments. For more information, see 'man PKGBUILD'.
# NOTE: Please fill out the license field for your package! If it is unknown,
# then please put 'unknown'.

# Maintainer: Guillaume Chanel <guillaume.chanel@unige.ch>
pkgname=nexus-client-git
pkgver=1.6.6
pkgrel=1
epoch=
pkgdesc="Client for the virtual desktop infrastructure"
arch=('x86_64' 'aarch64')
url="https://gitedu.hesge.ch/flg_projects/nexus_vdi/nexus-client"
license=('unknown')
groups=()
depends=()
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
source=("$pkgname"::git+ssh://git@ssh.hesge.ch:10572/flg_projects/nexus_vdi/nexus-client.git)  # TODO: to change with public repo
noextract=()
md5sums=('SKIP')
validpgpkeys=()

#prepare() {
#}

build() {
    NEXUSARCH=${CARCH/x86_64/amd64}
    NEXUSARCH=${NEXUSARCH/aarch64/arm64}
    echo "The following arachitecture has been detected: '$NEXUSARCH'"
    make -C "$pkgname/src/nexus-cli" build OS=linux ARCH=$NEXUSARCH
    make -C "$pkgname/src/nexush" build OS=linux ARCH=$NEXUSARCH
}

#check() {
#}

package() {
    #TODO: how to avoid repeating the two lines below ?
    NEXUSARCH=${CARCH/x86_64/amd64}
    NEXUSARCH=${NEXUSARCH/aarch64/arm64}
    mkdir -p "$pkgdir/usr/bin"
    cp "$pkgname/src/nexus-cli/build/${NEXUSARCH}/linux/nexus-cli" "$pkgdir/usr/bin"
    cp "$pkgname/src/nexush/build/${NEXUSARCH}/linux/nexush" "$pkgdir/usr/bin"
}
