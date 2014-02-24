# Maintainer: TJ Vanderpoel <tj@rubyists>

pkgname=musl
pkgver=0.9.15
pkgrel=1
pkgdesc="An implementation of the C/POSIX standard library intended for use on Linux-based systems"
arch=('i686' 'x86_64')
url="http://www.musl-libc.org/"
license=('MIT')
makedepends=('make')
source=(http://www.musl-libc.org/releases/$pkgname-$pkgver.tar.gz)
options=(staticlibs !buildflags !strip)

build() {
  cd "$srcdir/$pkgname-$pkgver"

  ./configure --prefix=/usr/musl --exec-prefix=/usr && make
}

package() {
  cd "$srcdir/$pkgname-$pkgver"

  make DESTDIR="$pkgdir/" install
  mv "$pkgdir/lib/*" "$pkgdir/usr/lib/"
}
