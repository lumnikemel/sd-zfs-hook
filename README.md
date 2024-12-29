# sd-zfs-hook

[![Build Status](https://github.com/lumnikemel/sd-zfs-hook/actions/workflows/update.yml/badge.svg)](https://github.com/lumnikemel/sd-zfs-hook/actions/workflows/update.yml)
[![GitHub release (latest by date)](https://img.shields.io/github/v/release/lumnikemel/sd-zfs-hook)](https://github.com/lumnikemel/sd-zfs-hook/releases)
[![GitHub stars](https://img.shields.io/github/stars/lumnikemel/sd-zfs-hook)](https://github.com/lumnikemel/sd-zfs-hook/stargazers)
[![GitHub issues](https://img.shields.io/github/issues/lumnikemel/sd-zfs-hook)](https://github.com/lumnikemel/sd-zfs-hook/issues)
[![Arch Linux](https://img.shields.io/badge/arch-linux-1793D1?logo=arch-linux&logoColor=white)](https://aur.archlinux.org/packages/sd-zfs-hook)
A standalone systemd ZFS hook for mkinitcpio, built from the archlinuxcn repository.

The `archlinuxcn` repo is the only org maintaining a `sd-zfs` module. However, their project is based on `linux-lts` and the module should be made available for all to use. Therefore, I created this repo to simplify the creation of just the module for others to use.

## Installation

### Option 1: Install from release
1. Go to the [Releases](../../releases) page
2. Download the latest `.zst` file
3. Install with pacman:
```bash
sudo pacman -U sd-zfs-hook-*.pkg.tar.zst
```

### Option 2: Build from source
```bash
git clone https://github.com/lumnikemel/sd-zfs-hook.git
cd sd-zfs-hook
makepkg -si
```

## Usage
Add `sd-zfs` to your HOOKS array in `/etc/mkinitcpio.conf`:
```bash
HOOKS=(systemd sd-zfs ...)
```

Then rebuild your initramfs:
```bash
sudo mkinitcpio -P
```

## Command Line Options
The following boot parameters are supported:
* `root=zfs` - imports all pools, searches for bootfs property
* `root=zfs:poolname` - imports specified pool, uses its bootfs
* `root=zfs:poolname/dataset` - imports pool, mounts specified dataset
