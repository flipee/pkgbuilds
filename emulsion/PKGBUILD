# Maintainer: Filipe Nascimento <flipee at tuta dot io>

pkgname=emulsion
pkgver=10.5.0
pkgrel=1
pkgdesc="A fast and minimalistic image viewer"
arch=('i686' 'x86_64')
url="https://github.com/ArturKovacs/emulsion"
license=('MIT')
depends=('gcc-libs' 'hicolor-icon-theme' 'libavif')
makedepends=('cargo')
source=("$pkgname-$pkgver.tar.gz::$url/archive/v${pkgver%.*}.tar.gz"
        "emulsion.desktop"
        "rustc_link_lib.patch")
sha256sums=('1047b215ed364daa77dc28ec07dc96768688af56f74d054b0dc1e7c188e561af'
            '0ddafdb9abec4887cab3e211f216e5c7e0f69bb15cd5426a6b85e469aeafd0aa'
            '09a8d447d97d97426812e5815147704e3999ef993b7b89258107f1f3dcb3b8f2')

prepare() {
    cd $pkgname-${pkgver%.*}
    cargo fetch --locked --target "$(rustc -vV | sed -n 's/host: //p')"

    patch -p1 < ../rustc_link_lib.patch
}

build() {
    cd $pkgname-${pkgver%.*}
    export RUSTUP_TOOLCHAIN=stable
    export CARGO_TARGET_DIR=target
    cargo build --frozen --release --features avif
}

package() {
    install -Dm644 $pkgname.desktop -t "$pkgdir/usr/share/applications"

    cd $pkgname-${pkgver%.*}
    install -Dm755 "target/release/$pkgname" -t "$pkgdir/usr/bin"
    install -Dm644 LICENSE.txt "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
    install -Dm644 resource_dev/emulsion.svg -t "$pkgdir/usr/share/icons/hicolor/scalable/apps"
}
