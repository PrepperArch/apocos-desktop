pkgbase=apocos
pkgver=0.0.3
pkgrel=2
pkgname='apocos-desktop'
pkgdesc="Graphical desktop system configuration for Apocalypse OS"
arch=('any')
url="https://github.com/PrepperArch/apocos-desktop"
license=('MIT')
source=(
    'lightdm.conf'
    'lightdm-slick-greeter.conf'
    'xinit-apocos.sh'
    'xresource-colors'
    'xresource-xterm'
)
sha256sums=(
    'a53767c6791541a5e3af927ad323151e1968ccae475ca9708e130a30cf47650d'
    '0c64985be8fa73bd41dda7f493311b89f0e3695bcec25ddba75e9fce5be1d249'
    '42c4520ef5a906fe4f7a75cc5e1f572dd2c05abd194b44eb13464e2c910d4733'
    '397137596ebb4dbafbe1a259e6df13bcbdc3205a7fb98dc1674e19aa0105162d'
    '808bd9c4d8c9391652e7602c61614048ef03c372802058c67e9174e7dc0d9d24'
)
depends=(
    'apocos-base'

    # Xorg
    'xorg-server' 'xorg-setxkbmap' 'xorg-xset' 'xorg-xev' 'xorg-xrdb'
    'intel-ucode' 'xorg-xrandr' 'vulkan-intel' 'libvdpau-va-gl'
    'xf86-input-evdev' 'xf86-video-fbdev' 'xf86-video-vesa'
    'ttf-liberation'

    # Desktop Environment
    'lightdm' 'lightdm-slick-greeter' 'dex'
    'light-locker' 'awesome' 'accountsservice'

    # Tools
    'xterm' 'autorandr'
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

    # Setup X resources
    install -Dm0755 xinit-apocos.sh $pkgdir/etc/X11/xinit/xinitrc.d/10-apocos.sh
    install -Dm0644 xresource-colors  $pkgdir/usr/share/apocos/desktop/xresource-colors
    install -Dm0644 xresource-xterm  $pkgdir/usr/share/apocos/desktop/xresource-xterm
}
