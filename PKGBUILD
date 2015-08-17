# Maintainer: speps <speps dot aur dot archlinux dot org>

pkgname=rssguard-git
pkgver=2.0.0.4.r26.g05b9f92
pkgrel=1
pkgdesc="A simple (yet powerful) Qt5 feed reader."
arch=('i686' 'x86_64')
url="https://bitbucket.org/skunkos/rssguard"
license=('GPL3')
depends=('qt5-webkit')
makedepends=('cmake' 'qt5-tools')
provides=('rss-guard' 'rssguard')
conflicts=('rss-guard' 'rssguard')
replaces=('rss-guard')
install="$pkgname.install"
source=("$pkgname::git+https://bitbucket.org/skunkos/rssguard.git")
md5sums=('SKIP')

pkgver() {
  cd $pkgname
  git describe --long | sed -r 's/([^-]*-g)/r\1/;s/-/./g'  
}

prepare() {
  cd $pkgname
  [ -d b ] || mkdir b
}

build() {
  cd $pkgname/b
  cmake .. -DCMAKE_INSTALL_PREFIX=/usr \
           -DUSE_QT_5=ON
  make
}

package() {
  cd $pkgname/b
  make DESTDIR="$pkgdir/" install
}
