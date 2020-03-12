# Contributor: Sasha Gerrand <alpine-pkgs@sgerrand.com>
# Maintainer: Sasha Gerrand <alpine-pkgs@sgerrand.com>
pkgname="certspotter"
pkgver="0.9"
pkgrel=0
pkgdesc="Certificate Transparency log monitor from SSLMate"
url="https://github.com/SSLMate/certspotter"
arch="all"
license="MPL-2.0"
depends=""
makedepends="go"
install=""
subpackages="$pkgname-doc"
source="https://github.com/SSLMate/certspotter/archive/$pkgver/certspotter-$pkgver.tar.gz"
builddir="$srcdir/src/github.com/SSLMate/certspotter"

build() {
	cd "$srcdir"
	export GOPATH="$PWD"

	mkdir -p $(dirname "$builddir")
	ln -s "$PWD/$pkgname-$pkgver" "$builddir"

	cd "$builddir"

	go get ./...
	go build ./...
}

check() {
	# Replace with proper check command(s)
	:
}

package() {
	cd "$srcdir"
	for exe in certspotter ctparsewatch submitct
	do
		install -Dm755 bin/$exe "$pkgdir"/usr/bin/$exe
	done
	cd "$builddir"
	for file in COPYING README
	do
		install -Dm644 $file "$pkgdir"/usr/share/doc/$pkgname/$file
	done
}

sha512sums="fe77cc212b58bce85c80c04e06a18c33bfc211b52920c9876ba3ff4b8bfbee92468c8f3915d576229f3c54417501ff042f95e57d9e46dbc5b35085062eee67d0  certspotter-0.9.tar.gz"
