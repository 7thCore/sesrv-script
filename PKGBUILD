# Maintainer: 7thCore

pkgname=sesrv-script
pkgver=1.6
pkgrel=3
pkgdesc='Space Engineers server script for running the server on linux with wine compatibility layer.'
arch=('x86_64')
license=('GPL3')
depends=('bash'
         'coreutils'
         'sudo'
         'grep'
         'sed'
         'awk'
         'curl'
         'rsync'
         'wget'
         'findutils'
         'tmux'
         'zip'
         'unzip'
         'p7zip'
         'postfix'
         'cabextract'
         'xorg-server-xvfb'
         'wine'
         'wine-mono'
         'wine_gecko'
         'winetricks'
         'lcms2'
         'mpg123'
         'giflib'
         'gnutls'
         'gst-plugins-base'
         'gst-plugins-good'
         'libpng'
         'libpulse'
         'libxml2'
         'lib32-libpulse'
         'lib32-libxml2'
         'lib32-mpg123'
         'lib32-lcms2'
         'lib32-giflib'
         'lib32-libpng'
         'lib32-gnutls'
         'lib32-gst-plugins-base'
         'lib32-gst-plugins-good'
         'steamcmd')
install=sesrv-script.install
source=('bash_profile'
        'sesrv-script.bash'
        'sesrv-send-notification@.service'
        'sesrv@.service'
        'sesrv-sync-tmpfs.service'
        'sesrv-timer-1.service'
        'sesrv-timer-1.timer'
        'sesrv-timer-2.service'
        'sesrv-timer-2.timer'
        'sesrv-tmpfs@.service')
sha256sums=('f1e2f643b81b27d16fe79e0563e39c597ce42621ae7c2433fd5b70f1eeab5d63'
            '28dd8f16531ec646154e138bdc33d987bbc0fbf929969aa1ac110905805b9c2c'
            'df35121cf2fd1f6aaa79f344746f48ca5c5fbbffdc2a2b39415305342e72dddd'
            'bc5033c190018ce4b630d8a334f3116132b11baf90075dfaf07e5a8da3e64f80'
            '1b470cd54241d4c6f5563ff2dd2533629ac1adbf53d3ca6f111474326d55bc6a'
            'a079bbe8c972f6654d9c091f2968960c9a992b189af8aadca706cd12f3c05db9'
            '017efdf5547402d13b73d3d206387ac689b6aa9b07f82a5fa5bb68e7042d46fb'
            '05676f16c87f9bfff4d998a46d640d69156d634be370b2592dd769686cab37fa'
            '537ad490a1e5241048e2b3f8beeb2dec1770024adddc5d46b2ed73c08d6ee3f6'
            'fe80d1e225bfaeca47e9804e359a497df398535ceec34b23587bd71bc238ad7e')

package() {
  install -d -m0755 "${pkgdir}/usr/bin"
  install -d -m0755 "${pkgdir}/srv/sesrv"
  install -d -m0755 "${pkgdir}/srv/sesrv/server"
  install -d -m0755 "${pkgdir}/srv/sesrv/config"
  install -d -m0755 "${pkgdir}/srv/sesrv/updates"
  install -d -m0755 "${pkgdir}/srv/sesrv/backups"
  install -d -m0755 "${pkgdir}/srv/sesrv/logs"
  install -d -m0755 "${pkgdir}/srv/sesrv/tmpfs"
  install -d -m0755 "${pkgdir}/srv/sesrv/.config"
  install -d -m0755 "${pkgdir}/srv/sesrv/.config/systemd"
  install -d -m0755 "${pkgdir}/srv/sesrv/.config/systemd/user"
  install -D -Dm755 "${srcdir}/sesrv-script.bash" "${pkgdir}/usr/bin/sesrv-script"
  install -D -Dm755 "${srcdir}/sesrv-timer-1.timer" "${pkgdir}/srv/sesrv/.config/systemd/user/sesrv-timer-1.timer"
  install -D -Dm755 "${srcdir}/sesrv-timer-1.service" "${pkgdir}/srv/sesrv/.config/systemd/user/sesrv-timer-1.service"
  install -D -Dm755 "${srcdir}/sesrv-timer-2.timer" "${pkgdir}/srv/sesrv/.config/systemd/user/sesrv-timer-2.timer"
  install -D -Dm755 "${srcdir}/sesrv-timer-2.service" "${pkgdir}/srv/sesrv/.config/systemd/user/sesrv-timer-2.service"
  install -D -Dm755 "${srcdir}/sesrv-send-notification@.service" "${pkgdir}/srv/sesrv/.config/systemd/user/sesrv-send-notification@.service"
  install -D -Dm755 "${srcdir}/sesrv@.service" "${pkgdir}/srv/sesrv/.config/systemd/user/sesrv@.service"
  install -D -Dm755 "${srcdir}/sesrv-sync-tmpfs.service" "${pkgdir}/srv/sesrv/.config/systemd/user/sesrv-sync-tmpfs.service"
  install -D -Dm755 "${srcdir}/sesrv-tmpfs@.service" "${pkgdir}/srv/sesrv/.config/systemd/user/sesrv-tmpfs@.service"
  install -D -Dm755 "${srcdir}/bash_profile" "${pkgdir}/srv/sesrv/.bash_profile"
}
