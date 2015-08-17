# Maintainer: Hugo Osvaldo Barrera <hugo@barrera.io>

pkgname=silicon-empire
pkgver=2.0.0
pkgrel=1
pkgdesc="Set of tools to manage and organize your optical discs like CDs, DVDs and Blu-rays."
arch=('i686' 'x86_64')
url="http://getsilicon.org/"
license=('GPL3')
depends=('fuseiso' 'phonon' 'taglib' 'cdrkit')
makedepends=('cmake')
conflicts=('silicon-empire-git')
source=("http://getsilicon.org/download/silicon_${pkgver}_source.tar.gz"
        qtlocalpeer.diff)
md5sums=('f68fde5d5fd72c8e271b885e64ce7a5a'
         '19fd34c24398f0ff2df99599b67fbda8')

build() {
  cd $srcdir/$pkgname/src
  patch -p0 < ../../qtlocalpeer.diff
  mkdir -p build
  cd build
  cmake .. -DCMAKE_BUILD_TYPE=Release \
        -DCMAKE_INSTALL_PREFIX=/usr \
        -DQT_QMAKE_EXECUTABLE=qmake-qt4

  make
}

package() {
  cd $srcdir/$pkgname/src/build
  make DESTDIR=${pkgdir} install
}
