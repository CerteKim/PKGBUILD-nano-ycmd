pkgname=nano-ycmd
pkgver=4.9.2
pkgrel=1

pkgdesc="Modded GNU Nano using ycmd code completion and IntelliSense."
url="https://github.com/orsonteodoro/nano-ycmd"
arch=('i686' 'x86_64')
license=('GPL')
depends=('ncurses' 'file' 'sh')
conflicts=('nano')
provides=('nano')
makedepends_x86_64+=('gcc')

source=(
    "https://github.com/orsonteodoro/nano-ycmd/archive/v$pkgver.tar.gz"
)
sha256sums=(
    '6111ef17ff74317c75d4c104aed7485f70d0ef36b0be254701efc64206c8e0b8'
)

build() {
    cd "$pkgname-$pkgver"
    sed -i 's/git\:\/\/git\.sv\.gnu\.org\/gnulib\.git/https\:\/\/github\.com\/coreutils\/gnulib/g' ./autogen.sh
    bash ./autogen.sh
    ./configure
    if [[ "$CARCH" == x86_64 ]]; then 
        make
    fi
}
package() {
    cd "$pkgname-$pkgver"
    if [[ "$CARCH" == x86_64 ]]; then
        make DESTDIR="$pkgdir/" install
    fi
}
