pkgname=e2fsporgs
pkgver=1.0
pkgrel=1
pkgdesc="File system utilities for ext2/ext3/ext4 file systems with FSP patches applied"
arch=('x86_64')
url="https://github.com/fsp/e2fsprogs"
license=('GPL')
depends=('e2fsprogs')
#source=("https://github.com/fsp/e2fsprogs/archive/v${pkgver}.tar.gz")

build() {
  dir
  mkdir build
  cd build
  MSYS2_ARG_CONV_EXCL="-DCMAKE_INSTALL_PREFIX=" \
    "${MINGW_PREFIX}"/bin/cmake.exe \
      -GNinja \
      -DCMAKE_INSTALL_PREFIX="${MINGW_PREFIX}" \
      -DCMAKE_BUILD_TYPE=Release \
      -DCMAKE_CXX_FLAGS="${CXXFLAGS}" \
      -DCMAKE_C_FLAGS="${CFLAGS}" \
      ../
}

package() {
  cd "${srcdir}/e2fsprogs-${pkgver}"
  #make DESTDIR="${pkgdir}" install
}
