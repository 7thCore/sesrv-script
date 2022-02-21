#    Copyright (C) 2022 7thCore
#    This file is part of IsRSrv-Script.
#
#    IsRSrv-Script is free software: you can redistribute it and/or modify
#    it under the terms of the GNU General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    IsRSrv-Script is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU General Public License for more details.
#
#    You should have received a copy of the GNU General Public License
#    along with this program.  If not, see <http://www.gnu.org/licenses/>.

pkgname=sesrv-script
pkgver=1.7
pkgrel=1
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
         's-nail'
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
            '708c3877df75ea814fcca7f9efca48dd8e15225a1a9165285951ead93ac597e3'
            'df35121cf2fd1f6aaa79f344746f48ca5c5fbbffdc2a2b39415305342e72dddd'
            '64f6e963e4891e32ae42467efb4399377766f6908f84a138f836fcedae02f083'
            '225fd6b39d58152e7897a54b1ef6d71fe71e822c51d228f441151912ce60f692'
            'a079bbe8c972f6654d9c091f2968960c9a992b189af8aadca706cd12f3c05db9'
            '017efdf5547402d13b73d3d206387ac689b6aa9b07f82a5fa5bb68e7042d46fb'
            '05676f16c87f9bfff4d998a46d640d69156d634be370b2592dd769686cab37fa'
            '537ad490a1e5241048e2b3f8beeb2dec1770024adddc5d46b2ed73c08d6ee3f6'
            '7f9d1a3aa4e430aa4fd05270696e56a2281d1f1eadcce6d7b2836443b6bc91d6')

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
