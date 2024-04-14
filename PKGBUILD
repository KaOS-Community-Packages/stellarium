pkgname=stellarium
pkgver=24.1
pkgrel=1
pkgdesc="Stellarium is a free open source planetarium for your computer. It shows a realistic sky in 3D."
arch=('x86_64')
url="https://stellarium.org/"
license=('GPL2')
depends=('libpng' 'libglvnd' 'freetype2' 'openssl' 'gpsd' 'qt6-charts' 'qt6-serialport'
         'boost-libs' 'qt6-multimedia' 'qt6-positioning' 'qt6-webengine' 'libindi')
makedepends=('cmake' 'ninja' 'boost' 'mesa' 'qt6-tools')
source=("${pkgname}-${pkgver}.tar.gz::https://github.com/Stellarium/${pkgname}/releases/download/v${pkgver}/${pkgname}-${pkgver}.tar.gz")
sha256sums=('SKIP')

build() {
  PATH="/usr/bin/core_perl/:$PATH"

  cmake -S "${srcdir}/${pkgname}-${pkgver}/" \
        -B "${srcdir}/${pkgname}-${pkgver}/build/" \
        -G Ninja \
        -DCMAKE_BUILD_TYPE="None" \
        -DCMAKE_INSTALL_PREFIX="/usr/" \
        -DCMAKE_C_COMPILER="gcc" \
        -DCMAKE_CXX_STANDARD="17" \
        -DCMAKE_C_EXTENSIONS="Yes" \
        -DCMAKE_CXX_COMPILER="g++" \
        -DCMAKE_C_STANDARD="17" \
        -DCMAKE_CXX_EXTENSIONS="Yes" \
        -DENABLE_QT6="1" \
        -DENABLE_SHOWMYSKY="ON" \
        -DENABLE_TESTING="0" \
        -DENABLE_XLSX="1" \
        -DPREFER_SYSTEM_INDILIB="No" \
        -Wno-dev
  cmake --build "${srcdir}/${pkgname}-${pkgver}/build/" --target all
}

package() {
  DESTDIR="${pkgdir}" cmake --build "${srcdir}/${pkgname}-${pkgver}/build/" --target install

  install -Dm 644 ${pkgname}-${pkgver}/COPYING -t "${pkgdir}/usr/share/licenses/${pkgname}"

  find "${pkgdir}" -type d -empty -delete
}
