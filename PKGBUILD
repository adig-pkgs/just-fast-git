# Maintainer: Aditya Gupta <ag15035 at gmail dot com>
pkgname=just-fast-git
pkgver=r37.af80685
pkgrel=1
pkgdesc="Just Fast is a CLI file manager with focus on speed in both execution times and usage"
arch=(x86_64)
url="https://github.com/GiuseppeCesarano/just-fast"
license=('MIT')
depends=()
makedepends=('git' 'gcc' 'cmake' 'ninja')
provides=("jf")
source=(${pkgname%-git}::'git+https://github.com/ArthurSonzogni/just-fast#branch=upgrade-ftxui')  # original source has a bug, which causes it's build to fail
md5sums=('SKIP')

pkgver() {
	cd "$srcdir/${pkgname%-git}"

	printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

prepare() {
	cd "$srcdir/${pkgname%-git}"
	cmake . -B build -G Ninja -DCMAKE_BUILD_TYPE=Release
}

build() {
	cd "$srcdir/${pkgname%-git}"/build
	cmake --build .
}

package() {
	cd "$srcdir/${pkgname%-git}"/build
	DESTDIR="$pkgdir/usr/local/bin"
	
	mkdir -p "$DESTDIR"
	cp jf "$DESTDIR/"
}
