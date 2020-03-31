pkgname=stellarium
pkgver=0.20.0
pkgrel=1
pkgdesc="A stellarium with great graphics and a nice database of sky-objects"
arch=('x86_64')
url="https://stellarium.org/"
license=('GPL2')
depends=('libpng' 'libgl' 'freetype2' 'openssl' 'qt5-script'
	'qt5-serialport' 'qt5-multimedia' 'qt5-location' 'gpsd')
makedepends=('cmake' 'boost' 'mesa' 'qt5-tools')
source=(https://github.com/Stellarium/stellarium/releases/download/v$pkgver/$pkgname-$pkgver.tar.gz)
sha256sums=('07ed1785d28f761511dc22f9b09ce70e96b5113fc7769fcdf4478f7a5a035370')

build() {
  cd ${pkgname}-${pkgver}

  cmake . -DCMAKE_INSTALL_PREFIX=/usr
  make
}


package() {
  cd ${pkgname}-${pkgver}
 
  make DESTDIR="${pkgdir}" install
}
