# Maintainer: Jingbei Li <i@jingbei.li>
# Contributor: Eric Cheng <ericcheng@hey.com>
# Contributor: Akhil Wali <akhil.wali.10@gmail.com>

pkgname=jellyfin-bin
pkgver=10.9.6
pkgrel=1
pkgdesc='Jellyfin server backend'
arch=('x86_64' 'aarch64' 'armv7h')
url='https://jellyfin.org/'
license=('GPL2')
provides=('jellyfin-server')
conflicts=('jellyfin-server' 'jellyfin-server-git')
depends=('bash' 'sqlite' 'fontconfig' 'jellyfin-ffmpeg')
optdepends=('jellyfin-web: to run web-app on the same machine')
source=('jellyfin.conf'
        'jellyfin.service'
        'jellyfin.sysusers'
        'jellyfin.tmpfiles')
source_x86_64=("https://repo.jellyfin.org/files/server/linux/latest-stable/amd64/jellyfin_${pkgver}-amd64.tar.gz")
source_aarch64=("https://repo.jellyfin.org/files/server/linux/latest-stable/arm64/jellyfin_${pkgver}-arm64.tar.gz")
source_armv7h=("https://repo.jellyfin.org/files/server/linux/latest-stable/armhf/jellyfin_${pkgver}-armhf.tar.gz")
sha256sums=('9f8dafb06676f972fca88cc1cedf5936518b5a7556628482aeea2c7f2f485678'
            'bb1b6e79eca51910be0898a7cbe8c53565a0e6fd64356a3d5fb1bf777c312313'
            '9bc1ddb77c73d46cc4078356b5773e5a776ebf8b47a1c820ad5fb17591ad5228'
            'b7faa4b0c756cdb361ef5b04fddfdc416b00f1246bb3a19a34bf4d185a6a7e5a')
sha256sums_x86_64=('be13ab2dab329febb5ff3aa683c6f8f190c86d14e614c5ae4f84560f3504e8b5')
sha256sums_aarch64=('9395eac0ac96f1878dcbd29e9f6a27a0338547b8a52622aa3be2e32920775942')
sha256sums_armv7h=('fad4963580ae9cdc9cf11b3a05e6b2544e2e5765fec4d7c83d81f65285385171')
backup=('etc/conf.d/jellyfin')
options=('staticlibs')

package() {
    tar xvf jellyfin_"$pkgver"-arm64.tar.gz

    mkdir -p "$pkgdir"/usr/lib
    cp -R "$srcdir"/jellyfin "$pkgdir"/usr/lib

    # install -Dm 644 "$srcdir"/jellyfin -t "$pkgdir"/usr/lib/jellyfin
    install -Dm 644 jellyfin.service -t "$pkgdir"/usr/lib/systemd/system/
    install -Dm 644 jellyfin.sysusers "$pkgdir"/usr/lib/sysusers.d/jellyfin.conf
    install -Dm 644 jellyfin.tmpfiles "$pkgdir"/usr/lib/tmpfiles.d/jellyfin.conf
    install -Dm 644 jellyfin.conf "$pkgdir"/etc/conf.d/jellyfin
}
