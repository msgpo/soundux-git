# Maintainer: D3SOX <d3sox@420blaze.it>
pkgname=soundboard-git
pkgver=r
pkgrel=1
pkgdesc="A universal soundboard in Qt for linux using pulseaudio modules"
arch=('any')
url="https://github.com/D3S0X/Soundboard"
license=('GPL3')
depends=('qt5-base' 'qt5-svg')
makedepends=('qt5-tools' 'git' 'ninja' 'cmake')
optdepends=('mpg123: mp3 support')
source=("git+https://github.com/D3S0X/Soundboard.git")
sha256sums=('SKIP')

pkgver() {
  cd "${srcdir}/Soundboard"

  # Get the version number.
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
  cd "${srcdir}/Soundboard"
  mkdir -p build
  cd build
  cmake ..
  make
}

package() {
  install -Dm 664 "${srcdir}/Soundboard/icon.jpg" "${pkgdir}/usr/share/pixmaps/soundboard-icon.jpg"
  install -Dm 644 "../soundboard.desktop" "${pkgdir}/usr/share/applications/soundboard.desktop"
  install -Dm 755 "${srcdir}/Soundboard/build/Soundboard" "${pkgdir}/usr/bin/Soundboard"
}
