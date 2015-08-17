# Maintainer: Antonio Rojas 

pkgname=telepathy-kde-common-internals-frameworks-git
pkgver=r1603.27ffa2d
pkgrel=1
pkgdesc='Common components for KDE-Telepathy'
arch=('i686' 'x86_64')
url='http://community.kde.org/Real-Time_Communication_and_Collaboration'
license=('GPL')
depends=('knotifyconfig' 'ktexteditor' 'libkpeople-frameworks-git' 'telepathy-qt5' 'libaccounts-qt5')
makedepends=('extra-cmake-modules' 'git' 'kdoctools' 'doxygen' 'python')
conflicts=('telepathy-kde-common-internals-frameworks' 'telepathy-kde-common-internals')
provides=('telepathy-kde-common-internals-frameworks')
source=("git://anongit.kde.org/ktp-common-internals.git#branch=frameworks")
sha256sums=('SKIP')

pkgver() {
  cd ktp-common-internals
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

prepare() {
  mkdir -p build
}

build() {
  cd build
  cmake ../ktp-common-internals \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DCMAKE_BUILD_TYPE=Release \
    -DLIB_INSTALL_DIR=lib \
    -DLIBEXEC_INSTALL_DIR=lib \
    -DKDE_INSTALL_USE_QT_SYS_PATHS=ON
  make
}

package() {
  cd build
  make DESTDIR="${pkgdir}" install
}
