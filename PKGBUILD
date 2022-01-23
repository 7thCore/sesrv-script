# Maintainer: 7thCore

pkgname=sesrv-script
pkgver=1.5
pkgrel=5
pkgdesc='Space Engineers server script for running the server on linux with wine compatibility layer.'
arch=('x86_64')
depends=('bash'
         'coreutils'
         'sudo'
         'grep'
         'sed'
         'awk'
         'curl'
         'rsync'
         'findutils'
         'cabextract'
         'unzip'
         'p7zip'
         'wget'
         'tmux'
         'postfix'
         'zip'
         'jq'
         'samba'
         'xorg-server-xvfb'
         'wine'
         'wine-mono'
         'wine_gecko'
         'winetricks'
         'libpulse'
         'libxml2'
         'mpg123'
         'lcms2'
         'giflib'
         'libpng'
         'gnutls'
         'gst-plugins-base'
         'gst-plugins-good'
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
backup=('')
install=sesrv-script.install
source=('sesrv-script.bash'
        'sesrv-timer-1.timer'
        'sesrv-timer-1.service'
        'sesrv-timer-2.timer'
        'sesrv-timer-2.service'
        'sesrv-send-notification@.service'
        'sesrv@.service'
        'sesrv-sync-tmpfs.service'
        'sesrv-tmpfs@.service'
        'bash_profile')
noextract=('')
sha256sums=('2edd2fe90df540ab4420e0952f8e968f2005a525e6a339cb074aa9c6af1767a2'
            '88848b4fad449dd01d1fb478ae0e1d39908ea4a31053cde47be7dcda38548e53'
            'c06df25e6ec278317e00bcca562baaead02475db90cb139732c21dabe7d3324f'
            'b614436c5cbdeea4b9ea8170d909c5f8a1cbe82505b716d07e2dfa45f52112d1'
            'a9b2b6f1bb3fb3c75677eba13ea2f0b12b7ddfe969d5d659a66a7695250187a9'
            '9a0d4b378bf7f3987ba7194caf88633f80bfee313bbced49f9ee42fc5e450f88'
            '1ab932e692763b5c69abee43faff42201e71a1dc39af6cfb001deca1d6011567'
            'e942bc76f7a7c1b5ae1a70012a0d55c3a01f1c321de5a8b0315cf50b30152b14'
            '54fcb9cbbf5e2c26d3e54442ace1022b3afa0bcfd282206cdb0cd1336c967787'
            'f1e2f643b81b27d16fe79e0563e39c597ce42621ae7c2433fd5b70f1eeab5d63')

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
