# Merged with official ABS kjsembed PKGBUILD by dr460nf1r3, 2021/12/05 (all respective contributors apply herein)
# Contributor: Antonio Rojas <arojas@archlinux.org>

pkgname=discover-git
pkgver=5.23.80_r8441.gd9014cb40
pkgrel=1
pkgdesc='KDE and Plasma resources management GUI'
arch=(x86_64)
url='https://kde.org/plasma-desktop/'
license=(LGPL)
depends=(knewstuff-git kitemmodels-git kcmutils-git kidletime-git qt5-graphicaleffects appstream-qt archlinux-appstream-data
         hicolor-icon-theme kirigami2-git discount kuserfeedback-git)
makedepends=(extra-cmake-modules-git plasma-framework-git packagekit-qt5 flatpak fwupd)
optdepends=('packagekit-qt5: to manage packages from Arch Linux repositories' 'flatpak: Flatpak packages support'
            'fwupd: firmware update support')
conflicts=(${pkgname%-git})
provides=(${pkgname%-git})
groups=(plasma-git)
source=("git+https://invent.kde.org/plasma/${pkgname%-git}.git")
sha256sums=('SKIP')

pkgver() {
  cd ${pkgname%-git}
  _ver="$(grep -m1 'set(PROJECT_VERSION' CMakeLists.txt | cut -d '"' -f2 | tr - .)"
  echo "${_ver}_r$(git rev-list --count HEAD).g$(git rev-parse --short HEAD)"
}

build() {
  cmake -B build -S ${pkgname%-git} \
    -DCMAKE_INSTALL_LIBEXECDIR=lib \
    -DBUILD_TESTING=OFF \
    -DWITH_KCM=OFF
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
}
