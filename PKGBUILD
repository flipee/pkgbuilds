# Maintainer: Filipe Nascimento <flipee at tuta dot io>
# Contributor: Morten Linderud <foxboron@archlinux.org>

pkgname=smenu
pkgver=1.4.0
pkgrel=1
pkgdesc="A powerful and versatile selection tool for interactive or scripting use"
arch=('x86_64')
url="https://github.com/p-gen/smenu"
license=('MPL-2.0')
depends=('ncurses')
source=("${pkgname}-${pkgver}.tar.gz::https://github.com/p-gen/smenu/archive/v${pkgver}.tar.gz")
sha256sums=('76b5f2ba181ac4d377fde30181fc6f2ecc7cdef82cf78796c18e59b7a033b9c9')

build() {
    cd "${pkgname}-${pkgver}"
    ./configure --prefix="/usr"
    make
}

package() {
    cd "${pkgname}-${pkgver}"
    make DESTDIR="${pkgdir}" PREFIX=/usr install
    install -Dm644 README.rst -t "$pkgdir/usr/share/doc/$pkgname"
    find examples/ -type f -exec install -Dm644 "{}" "$pkgdir/usr/share/doc/$pkgname/{}" \;
}
