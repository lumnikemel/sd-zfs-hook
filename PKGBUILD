pkgname="sd-zfs-hook"
pkgver=1.0
pkgrel=1
pkgdesc='A standalone systemd ZFS hook for mkinitcpio, extracted from the archlinuxcn repository.'
arch=("any")
url="https://github.com/lumnikemel/sd-zfs-hook"
license=("CDDL-1.0")
makedepends=()   # Empty since we don't need any build dependencies
depends=('zfs')

source=(
    "sd-zfs.initcpio.install::https://raw.githubusercontent.com/archlinuxcn/repo/master/archlinuxcn/zfs-linux-lts-poscat/sd-zfs.initcpio.install"
    "parse-cmdline::https://raw.githubusercontent.com/archlinuxcn/repo/master/archlinuxcn/zfs-linux-lts-poscat/parse-cmdline"
    "zfs-set-env::https://raw.githubusercontent.com/archlinuxcn/repo/master/archlinuxcn/zfs-linux-lts-poscat/zfs-set-env"
    "zfs-root-generator::https://raw.githubusercontent.com/archlinuxcn/repo/master/archlinuxcn/zfs-linux-lts-poscat/zfs-root-generator"
)
sha256sums=('SKIP' 'SKIP' 'SKIP' 'SKIP')

package() {
    depends=('zfs')  # Runtime dependency on ZFS moved here

    # Install the sd-zfs hook
    install -Dvm644 "${srcdir}"/sd-zfs.initcpio.install "${pkgdir}"/usr/lib/initcpio/install/sd-zfs

    # Install helper scripts
    install -Dvm755 -t "${pkgdir}"/usr/lib/zfs/initcpio/ "${srcdir}"/{parse-cmdline,zfs-set-env,zfs-root-generator}
}