# Maintainer: Filipe Nascimento <flipee at tuta dot io>
# Contributor: Luca Cesari < luca AT cesari DOT me>

_gemname=xdg
pkgname=ruby-xdg
pkgver=8.4.0
pkgrel=1
pkgdesc="Provides a Ruby implementation of the XDG Base Directory Specification"
arch=('any')
url="https://www.alchemists.io/projects/xdg"
license=('Apache')
depends=('ruby>=3.1')
makedepends=('ruby-rdoc')
options=(!emptydirs)
source=("http://rubygems.org/downloads/xdg-$pkgver.gem")
noextract=("xdg-$pkgver.gem")
sha256sums=('1e2f154ef93d82fd423ce17980ce9fd9ddcaa4e9109f4a5f83e38cf42507ba72')

package() {
    local _gemdir
    _gemdir="$(ruby -e 'puts Gem.default_dir')"
    gem install --ignore-dependencies --no-user-install -i "$pkgdir/$_gemdir" -n "$pkgdir/usr/bin" $_gemname-$pkgver.gem
    rm "$pkgdir/$_gemdir/cache/$_gemname-$pkgver.gem"
}
