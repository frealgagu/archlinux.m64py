# Maintainer: Fredy García (frealgagu@gmail.com)
# Contributor: Pedro Gabriel (pedrogabriel@dcc.ufmg.br)
# Contributor: cookiengineer

pkgname=m64py
pkgver=0.2.5
pkgrel=3
pkgdesc="A Qt5 front-end (GUI) for Mupen64Plus, a cross-platform plugin-based Nintendo 64 emulator"
arch=("any")
url="https://github.com/mupen64plus/mupen64plus-ui-python"
license=("GPL")
depends=("desktop-file-utils" "libxkbcommon-x11" "mupen64plus" "python-pyqt5" "python-pysdl2")
makedepends=("python-distribute")
source=(
  "https://github.com/mupen64plus/mupen64plus-ui-python/releases/download/${pkgver}/${pkgname}-${pkgver}.tar.gz"
  "fix_core_dump_by_int_cast.patch"
  "fix_setup.patch"
)
sha256sums=(
  "0223569ec031b6e6c1d96ac51a19b9262cccce7705c84b5ca5044c94afb75fca"
  "598672aa8f821a9b28cdeae8a8058661e379460d9f1201104146623dc59ba7c1"
  "786bffed4d3c625b6d98c4c5dababdae88f80c7d8bc26f4f0267b883cf92cb9e"
)

prepare() {
  cd "${srcdir}/${pkgname}-${pkgver}"

  # https://github.com/mupen64plus/mupen64plus-ui-python/issues/191
  patch -Np1 -i "${srcdir}/fix_core_dump_by_int_cast.patch"

  # https://github.com/mupen64plus/mupen64plus-ui-python/issues/229
  patch -Np1 -i "${srcdir}/fix_setup.patch"
}

package() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  python setup.py install --optimize=1 --prefix=/usr --root="${pkgdir}/"
}
