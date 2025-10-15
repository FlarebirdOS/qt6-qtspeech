pkgname=qt6-qtspeech
pkgver=6.9.2
pkgrel=1
pkgdesc="Qt Speech support"
arch=('x86_64')
url="https://www.qt.io"
license=(
    'GPL-3.0-only'
    'LGPL-3.0-only'
    'LicenseRef-Qt-Commercial'
    'Qt-GPL-exception-1.0'
)
depends=(
    'gcc-libs'
    'glibc'
    'qt6-qtbase'
    'qt6-qtmultimedia'
)
makedepends=(
    'cmake'
    'flite'
    'git'
    'ninja'
    'qt6-qtdeclarative'
    'speech-dispatcher'
)
source=(git+https://code.qt.io/qt/${pkgname#*-}#tag=v${pkgver})
sha256sums=(04d4081bc9be3024021a7961bc64c695c8057e65eb0ccf5a93436c1eebb20bf5)

build() {
    cd ${pkgname#*-}

    local cmake_args=(
        -B flarebird-build
        -G Ninja
        -D CMAKE_BUILD_TYPE=Release
        -D CMAKE_INSTALL_PREFIX=/usr
        -D INSTALL_LIBDIR=lib64
        -D CMAKE_MESSAGE_LOG_LEVEL=STATUS
    )

    cmake "${cmake_args[@]}"

    cmake --build flarebird-build
}

package() {
    cd ${pkgname#*-}

    DESTDIR=${pkgdir} cmake --install flarebird-build
}
