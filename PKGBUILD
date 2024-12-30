# Maintainer: Lumnikemel <lumnikemel@github.com>
pkgname="sd-zfs-hook"
pkgver=1.0
pkgrel=1
pkgdesc='A standalone systemd ZFS hook for mkinitcpio, extracted from the archlinuxcn repository.'
arch=("any")
url="https://github.com/lumnikemel/sd-zfs-hook"
license=("CDDL-1.0")
makedepends=()   

options=(zipman !strip)
PKGEXT='.pkg.tar.zst'
COMPRESSZST=(zstd -c -T0 -10 -)

# Change the source to use local files from src directory
source=(
    "sd-zfs.initcpio.install"
    "parse-cmdline"
    "zfs-set-env"
    "zfs-root-generator"
)
sha256sums=('SKIP' 'SKIP' 'SKIP' 'SKIP')

package() {
    depends=('zfs')

    # Install the sd-zfs hook
    install -Dvm644 "${srcdir}"/sd-zfs.initcpio.install "${pkgdir}"/usr/lib/initcpio/install/sd-zfs

    # Install helper scripts
    install -Dvm755 -t "${pkgdir}"/usr/lib/zfs/initcpio/ "${srcdir}"/{parse-cmdline,zfs-set-env,zfs-root-generator}
}
