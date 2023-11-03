pkgbase=apocos
pkgver=0.0.2
pkgrel=1
pkgname='apocos-desktop'
pkgdesc="Graphical desktop system configuration for Apocalypse OS"
arch=('any')
url="https://github.com/PrepperArch/apocos-desktop"
license=('MIT')
source=(
    'lightdm.conf'
    'lightdm-slick-greeter.conf'
)
sha256sums=(
    'a53767c6791541a5e3af927ad323151e1968ccae475ca9708e130a30cf47650d'
    '0c64985be8fa73bd41dda7f493311b89f0e3695bcec25ddba75e9fce5be1d249'
)
depends=(
    'apocos-base'

    # Xorg
    'xorg-server' 'xorg-setxkbmap' 'xorg-xset' 'xorg-xev'
    'intel-ucode' 'xorg-xrandr' 'vulkan-intel' 'libvdpau-va-gl'
    'xf86-input-evdev' 'xf86-video-fbdev' 'xf86-video-vesa'

    # Desktop Environment
    'lightdm' 'lightdm-slick-greeter' 'dex'
    'light-locker' 'awesome' 'accountsservice'

    # Tools
    'autorandr'
)
install="$pkgname.install"

package(){
    # Enable lightdm as displaymanager and override system
    # configuration
    mkdir -p $pkgdir/etc/systemd/system
    chmod 0755 -R $pkgdir/etc/systemd
    ln -sf /usr/lib/systemd/system/lightdm.service $pkgdir/etc/systemd/system/display-manager.service

    mkdir -p $pkgdir/etc/lightdm/lightdm.conf.d
    chmod 0755 -R $pkgdir/etc/lightdm/lightdm.conf.d
    install -Dm0644 lightdm.conf $pkgdir/etc/lightdm/lightdm.conf.d/apocos-lightdm.conf
    install -Dm0644 lightdm-slick-greeter.conf $pkgdir/etc/lightdm/slick-greeter.conf
}
