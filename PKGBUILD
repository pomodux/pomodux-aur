# Maintainer: Ritchie <ritchie@macapinlac.com>
pkgname=pomodux
pkgver=0.3.0
pkgrel=1
pkgdesc="A command-line Pomodoro timer with persistent sessions and plugin support"
arch=('x86_64')
url="https://github.com/pomodux/pomodux"
license=('MIT')
source=("$pkgname-$pkgver.tar.gz::https://github.com/pomodux/pomodux/archive/main.tar.gz")
sha256sums=('a36a6dbccb9706e4c2c510b3d3a1d68aa8418f9bd93d2a4d3c21ed045652a6e5')
depends=('glibc')
makedepends=('go' 'git')

prepare() {
  # Extract source tarball
  tar -xzf "$pkgname-$pkgver.tar.gz"
  # Rename the extracted directory from main to the expected name
  mv pomodux-main "$pkgname-$pkgver"
}

build() {
  cd "$pkgname-$pkgver"
  export CGO_ENABLED=0
  go build -ldflags="-s -w -X main.Version=$pkgver" -o "$pkgname" cmd/pomodux/main.go
}

package() {
  cd "$pkgname-$pkgver"
  
  # Install binary
  install -Dm755 "$pkgname" "$pkgdir/usr/bin/$pkgname"
  
  # Install documentation
  install -Dm644 README.md "$pkgdir/usr/share/doc/$pkgname/README.md"
  install -Dm644 docs/README.md "$pkgdir/usr/share/doc/$pkgname/docs/README.md"
  
  # Install license
  install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
} 