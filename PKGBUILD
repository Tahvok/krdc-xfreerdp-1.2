# $Id: PKGBUILD 226998 2014-11-24 07:20:15Z andrea $
# Maintainer: Andrea Scarpino <andrea@archlinux.org>

pkgname=kdenetwork-krdc
pkgver=4.14.3
pkgrel=1
pkgdesc='Remote Desktop Client'
url='http://kde.org/applications/internet/krdc/'
arch=('i686' 'x86_64')
license=('GPL' 'LGPL' 'FDL')
groups=('kde' 'kdenetwork')
depends=('kdebase-runtime' 'telepathy-qt')
makedepends=('cmake' 'automoc4' 'libvncserver' 'freerdp')
optdepends=('libvncserver: VNC support'
            'freerdp: RDP support'
            'kdebase-keditbookmarks: to edit bookmarks')
source=("http://download.kde.org/stable/${pkgver}/src/krdc-${pkgver}.tar.xz" "latest_xfreerdp.patch")
sha1sums=('e18b48757ab35b51520fd2972e498fc24f6b62ad' 'ed0336e46d724d3d379beb7fc6ac9174627ffb58')

prepare() {
cd $srcdir/krdc-${pkgver}
patch -p1 -i $srcdir/latest_xfreerdp.patch
}

build() {
   mkdir build
   cd build
   cmake ../krdc-${pkgver} \
     -DCMAKE_BUILD_TYPE=Release \
     -DKDE4_BUILD_TESTS=OFF \
     -DCMAKE_INSTALL_PREFIX=/usr
   make
}

package() {
  cd build
  make DESTDIR=$pkgdir install
}
