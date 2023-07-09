# Maintainer: Bardia Moshiri <fakeshell@bardia.tech>

pkgname=glamor-hybris
pkgver=0.2.0
pkgrel=1
pkgdesc='Glamor Xserver 2D acceleration, modified to work with libhybris drivers'
url='https://github.com/gemian/glamor-hybris'
arch=(i686 x86_64 armv7h aarch64)
license=()
depends=(xorg-server xorgproto android-headers)
makedepends=(xorg-server-devel git)
source=('git+https://github.com/gemian/glamor-hybris#commit=6d369b94e8cc858587eb510af7bc97f6a3c1a453')
sha256sums=('SKIP')

prepare() {
  cd ${pkgname}
  sed -i 's/gl >= 7.1.0/gl/g' configure.ac
  NOCONFIGURE=1 ./autogen.sh
}

build() {
  cd ${pkgname}
  sed -i 's/gl >= 7.1.0/gl/g' configure.ac
  export CPLUS_INCLUDE_PATH=/usr/include/android:/usr/include/android/hybris
  export C_INCLUDE_PATH=/usr/include/android:/usr/include/android/hybris
  ./configure --prefix=/usr
  make
}

package() {
  cd ${pkgname}
  make DESTDIR="${pkgdir}" install
}
