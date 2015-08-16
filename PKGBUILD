# Maintainer: Limao Luo <luolimao+AUR@gmail.com>

pkgname=mcobj
pkgver=0.14
pkgrel=1
pkgdesc="Exports minecraft worlds to .obj or .prt -- premade binaries"
arch=(i686 x86_64)
url=https://github.com/quag/$pkgname/
license=(custom)
makedepends=(p7zip)
optdepends=(minecraft)
conflicts=($pkgname-git)
options=(!strip)
if [[ $CARCH == "i686" ]]; then
    _arch=x86
    sha256sums=('e62925bffab19cd02ebb34901cc34481ba320cf4987bdaf2c4547ba984ad1fe1')
    sha512sums=('dceda61cb3c22996b862bc2eb114f0385419a4a34802a5fec4141df41f7dd3fa3bca53796779aa2b2002b1473a9f30b5b6ee05a4ae0478e79fa06489edcb4924')
else
    _arch=x64
    sha256sums=('9e9cabf7dab7f5882de9935fe82a13bd1c0d9bd5de2fd2c2dfa1f92b5859bdb3')
    sha512sums=('e1b91ed95138ab85d283797653be4aee83cb8996e3d2d14149d7d0907fcf16d4e658f7fd2b574a81bb9d5b21f060fae6834866bb4f0cecd6ad5a524dca778d93')
fi
source=(https://github.com/downloads/quag/$pkgname/$pkgname-$pkgver-linux-$_arch.7z)
noextract=($pkgname-$pkgver-linux-$_arch.7z)

package() {
    cd "$srcdir"
    rm -rf $pkgname-src/
    install -d $pkgname-src/
    7z e -o$pkgname-src/ $pkgname-$pkgver-linux-$_arch.7z
    cd $pkgname-src/

    install -Dm755 $pkgname "$pkgdir"/usr/share/$pkgname/$pkgname
    install -Dm644 blocks.json "$pkgdir"/usr/share/$pkgname/blocks.json
    install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE

    install -d "$pkgdir"/usr/bin/
    ln -s /usr/share/$pkgname/$pkgname "$pkgdir"/usr/bin/$pkgname
}
