# Maintainer: Ritchie <ritchie@macapinlac.com>
pkgname=pomodux
pkgver=0.5.0
pkgrel=1
pkgdesc="A command-line Pomodoro timer with persistent sessions and plugin support"
arch=('x86_64')
url="https://github.com/pomodux/pomodux"
license=('MIT')
source=("$pkgname-$pkgver.tar.gz::https://github.com/pomodux/pomodux/archive/v$pkgver.tar.gz")
sha256sums=('4d7dbb32e76988931cf9c4ac45765c79b644425351045cdf84f0f949367ea15a')
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
