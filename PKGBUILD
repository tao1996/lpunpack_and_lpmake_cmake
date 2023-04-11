# Maintainer: Biswapriyo Nath <nathbappai@gmail.com>

_realname=adbwinapi
pkgbase=mingw-w64-${_realname}
pkgname=("${MINGW_PACKAGE_PREFIX}-${_realname}")
pkgver=33.0.3
pkgrel=1
pkgdesc='ADB API for Windows (mingw-w64)'
arch=('any')
mingw_arch=('mingw32' 'mingw64' 'ucrt64' 'clang64' 'clang32')
url='https://developer.android.com/studio/releases/platform-tools'
license=('spdx:Apache-2.0')
makedepends=("${MINGW_PACKAGE_PREFIX}-cmake")

build() {
  declare _build_arch

  if [ "${CARCH}" = "x86_64" ]; then
    _build_arch="x64"
  else
    _build_arch="Win32"
  fi

  MSYS2_ARG_CONV_EXCL="-DCMAKE_INSTALL_PREFIX=" \
    "${MINGW_PREFIX}"/bin/cmake.exe \
      -G "Visual Studio 17 2022" \
      -DCMAKE_INSTALL_PREFIX="${MINGW_PREFIX}" \
      -A "${_build_arch}" \
      -B "build-${MSYSTEM}"

  "${MINGW_PREFIX}"/bin/cmake.exe \
    --build "build-${MSYSTEM}" \
    --config Release
}

package() {
  cd "${srcdir}/build-${MSYSTEM}"
  DESTDIR="${pkgdir}" "${MINGW_PREFIX}"/bin/cmake.exe --install .
  install -Dm644 "${srcdir}/NOTICE" "${pkgdir}${MINGW_PREFIX}/share/licenses/${_realname}/LICENSE"
}
