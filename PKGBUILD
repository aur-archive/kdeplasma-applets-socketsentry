# Maintainer: laloch <lalochcz@gmail.com>
# Contributor: Frikilinux <frikilinux at frikilinux.com.ar>

pkgname=kdeplasma-applets-socketsentry
pkgver=0.9.3
pkgrel=2
pkgdesc="KDE Plasma widget that displays real-time network traffic"
url="http://code.google.com/p/socket-sentry/"
license=('GPL3')
arch=('i686' 'x86_64')
depends=('kdebase-runtime' 'libpcap')
makedepends=('cmake' 'automoc4' 'gmock')
install=${pkgname}.install
conflicts=('kdeplasma-addons-applets-socketsentry')
replaces=('kdeplasma-addons-applets-socketsentry')
source=("http://socket-sentry.googlecode.com/files/socketsentry-${pkgver}.tar.gz"
	"libpthread.patch")
md5sums=('b737c58ccf79d63bf15c87d99728518a'
         'a6617ac810f2ed3ddd19061125a5df7d')

build() {
  cd ${srcdir}/socketsentry-${pkgver}
  patch -p0 -i "${srcdir}/libpthread.patch"
  
  rm -rf ${srcdir}/build
  mkdir ${srcdir}/build
  cd ${srcdir}/build
  cmake ../socketsentry-${pkgver} \
    -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` \
    -DQT_QMAKE_EXECUTABLE=/usr/bin/qmake-qt4 \
    -DCMAKE_BUILD_TYPE=Release
  make
}

package() {
  cd build
  make DESTDIR=${pkgdir} install
}
