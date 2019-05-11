# Maintainer: Bilal ELmoussaoui <bil.elmoussaoui@gmail.com>

pkgname=lyricfier
pkgrel=1
pkgver=0.3.0
_pkgver="v${pkgver}"
pkgdesc="a Spotify Lyrics alternative app"
url="https://github.com/jakub-tucek/lyricfier"
provides=('lyricfier')
arch=('x86_64')
license=('MIT')
makedepends=('unzip')
source=(
  "${pkgname}.desktop"
  "${pkgname}.png"
)

source_x86_64+=("${url}/releases/download/${_pkgver}/${pkgname}-linux-x64.zip")

sha256sums_x86_64=('341f1a13860b25957361a89342bb23de43270b2c3af0f846f5348f9e24bfb70c')
sha256sums=(
  '2d5d757e286dbf32d75740ffe48e221ffdc2dc10f4fd3f1c5718d7f02fe127a5'
  '73393cdb03f498e5b43126323a6cf64bd529bd37182280f80bff25abc3a04297'
)

package() {
  # Installing the desktop file and the icon
  install -D -m644 "./${pkgname}.desktop" "${pkgdir}/usr/share/applications/${pkgname}.desktop"
  install -D -m644 "./${pkgname}.png" "${pkgdir}/usr/share/pixmaps/${pkgname}.png"
  # Installing the application files
  install -d "${pkgdir}/opt/"
  cp -R "${srcdir}/" "${pkgdir}/opt/${pkgname}"
  # Copying the binary file
  install -d "${pkgdir}/usr/bin"
  ln -sf "../../opt/${pkgname}/${pkgname}" "${pkgdir}/usr/bin/${pkgname}"
  # Clean the build
  rm -f "${pkgdir}/opt/${pkgname}/${pkgname}.png"
  rm -f "${pkgdir}/opt/${pkgname}/${pkgname}.desktop"
  case "$CARCH" in
    i686)
      rm -f "${pkgdir}/opt/${pkgname}/lyricfier-linux-ia32.zip"
      ;;
    x86_64)
      rm -f "${pkgdir}/opt/${pkgname}/lyricfier-linux-x64.zip"
      ;;
  esac
}
