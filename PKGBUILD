# Maintainer: Ritchie <ritchie@macapinlac.com>
pkgname=pomodux
pkgver=0.4.2
pkgrel=1
pkgdesc="A command-line Pomodoro timer with persistent sessions and plugin support"
arch=('x86_64')
url="https://github.com/pomodux/pomodux"
license=('MIT')
source=("$pkgname-$pkgver.tar.gz::https://github.com/pomodux/pomodux/archive/v$pkgver.tar.gz")
sha256sums=('9358ceecfad91c7b892a8b2d9c59f0b2327cb49818363106fe8dbd774af2412e')
depends=('glibc')
makedepends=('go' 'git')

prepare() {
  # Extract source tarball
  tar -xzf "$pkgname-$pkgver.tar.gz"
}

build() {
  cd "$pkgname-$pkgver"
  export CGO_ENABLED=0
  go build -ldflags="-s -w -X github.com/pomodux/pomodux/internal/cli.Version=$pkgver" -o "$pkgname" cmd/pomodux/main.go
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