# Contributor: V-Conet <admin@vconet.top>
# Maintainer: V-Conet <admin@vconet.top>
pkgname=zerotier-one
pkgver=1.16.0
pkgrel=0
pkgdesc="A Smart Ethernet Switch for Earth "
url="https://www.zerotier.com"
arch="all !riscv64"
license="MPL-2.0 AND LicenseRef-ZeroTier-Source-Available-NonCommercial-1.0"
depends="openssl libstdc++ libgcc"
makedepends="linux-headers cargo openssl-dev gcc make"
subpackages="$pkgname-doc $pkgname-openrc"
source="
	zerotier-one.initd
	$pkgname-$pkgver.tar.gz::https://github.com/zerotier/ZeroTierOne/archive/$pkgver.tar.gz
	"
builddir="$srcdir/ZeroTierOne-$pkgver"

build() {
	make
}

check() {
	make selftest
}

package() {
	make DESTDIR="$pkgdir" install
	install -Dm644 LICENSE.txt "$pkgdir"/usr/share/licenses/$pkgname/LICENSE.txt
	install -Dm644 nonfree/LICENSE.md "$pkgdir"/usr/share/licenses/$pkgname/nonfree/LICENSE.md
	install -Dm644 LICENSE-MPL.txt "$pkgdir"/usr/share/licenses/$pkgname/LICENSE-MPL.txt
}

openrc() {
	depends="$pkgname"
	install -Dm755 "$srcdir/$pkgname.initd" \
		"$subpkgdir/etc/init.d/$pkgname"
}

doc() {
	default_doc
}

sha512sums="
00c98d0cce3f39fd0ae30c2b0b36cd121ce03f758f388910b554d79954a16aa93701b90f54ba3bd05c1bda43c5ad476d77ceefb0665966ec087408a5601c744b  zerotier-one.initd
"
