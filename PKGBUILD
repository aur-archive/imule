# Maintainer: atterratio <atterratio at gmail dot com>

pkgname=imule
pkgver=2.3.2.3
pkgrel=2
pkgdesc="Anonymous P2P file sharing software"
arch=("i686" "x86_64")
url="http://www.imule.i2p/"
license=("GPL")
depends=("wxgtk2.8" "crypto++")
optdepends=("i2p: anonymous routing")
source=("http://aceini.no-ip.info/${pkgname}/${pkgver}/iMule-${pkgver}-src.tbz")
md5sums=("36f0397b65a1c481d68dd8f20551f2e7")

build() {
	cd "${srcdir}/iMule-${pkgver}-src"
	sed "s/wxString::wxString/wxString/g" -i src/PrefsUnifiedDlg.cpp
	# See ./configure --help for more options, it may be necessary if you are using KDE or want to install additional utilities.
	./configure --prefix=/usr --disable-debug --enable-optimize --disable-ed2k \
	--enable-imule-gui --enable-imule-daemon --enable-utf8-systray -with-wx-config=/bin/wx-config-2.8
	make
}

check() {
	cd "${srcdir}/iMule-${pkgver}-src"
	make -k check
}

package() {
	cd "${srcdir}/iMule-${pkgver}-src"
	make DESTDIR=${pkgdir} install
	#It's hack. If U know best way to not instal this desktop file tell me.
	rm ${pkgdir}/usr/share/applications/imulegui.desktop
}
