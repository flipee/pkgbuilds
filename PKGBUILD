# Maintainer: Filipe Nascimento <flipee at tuta dot io>

pkgname=scriptisto
pkgver=2.2.0
pkgrel=1
pkgdesc="A language-agnostic \"shebang interpreter\" that enables you to write scripts in compiled languages"
arch=('i686' 'x86_64')
url="https://github.com/igor-petruk/scriptisto"
license=('Apache')
depends=('gcc-libs')
makedepends=('cargo')
source=("$pkgname-$pkgver.tar.gz::$url/archive/v$pkgver.tar.gz")
sha256sums=('192d20885b563eeaf66766695314ab3e2711dc10c44f938aeeee6271e9720397')

prepare() {
    cd $pkgname-$pkgver
    cargo fetch --locked --target "$CARCH-unknown-linux-gnu"
}

build() {
    cd $pkgname-$pkgver
    export RUSTUP_TOOLCHAIN=stable
    export CARGO_TARGET_DIR=target
    cargo build --frozen --release
}

#check() {
#    cd $pkgname-$pkgver
#    cargo test --release --locked
#}

package() {
    cd $pkgname-$pkgver
    install -Dm755 "target/release/$pkgname" -t "$pkgdir/usr/bin"
}
