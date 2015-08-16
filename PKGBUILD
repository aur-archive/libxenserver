# Maintainer: Si Feng <sci.feng at gmail.com>

pkgname=libxenserver
pkgver=6.0.0
pkgrel=2
pkgdesc="The XenServer SDK for C"
arch=(i686 x86_64)
url="http://community.citrix.com/cdn/xs/sdks"
license=('LGPL2')
depends=(libxml2 curl)
makedepends=(chrpath)
source=("libxenserver-$pkgver-1-src.tar.bz2::http://community.citrix.com/download/attachments/38633496/libxenserver-$pkgver-1-src.tar.bz2?version=1")
md5sums=('27faa9249092ad823cef3c3850240a21')

build() {
  cd "$srcdir/$pkgname"
  make -j1 all libxenserver.a include/xen/api/xen_all.h
  make -j1 DESTDIR="$pkgdir/" \
	INSTALL_PROG="install -D -m0755" \
	INSTALL_DATA="install -D -m0644" \
	LIBDIR=lib/ \
	install
  cp -r include/xen $pkgdir/usr/include/
  chrpath -d $pkgdir/usr/lib/libxenserver.so*
}
