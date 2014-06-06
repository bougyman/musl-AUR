# Maintainer: TJ Vanderpoel <tj@rubyists>

pkgname=musl
pkgver=1.0.2
pkgrel=2
pkgdesc="An implementation of the C/POSIX standard library intended for use on Linux-based systems"
arch=('i686' 'x86_64')
url="http://www.musl-libc.org/"
license=('MIT')
makedepends=('make')
source=(CHANGELOG http://www.musl-libc.org/releases/$pkgname-$pkgver.tar.gz)
options=(staticlibs !buildflags !strip)

build() {
  cd "$srcdir/$pkgname-$pkgver"

  CFLAGS="${CFLAGS} -fno-toplevel-reorder" ./configure --prefix=/usr/musl --exec-prefix=/usr && make
}

package() {
  cd "$srcdir/$pkgname-$pkgver"

  make DESTDIR="$pkgdir/" install
  install -d -m0755 "$pkgdir/usr/lib/"
  mv "$pkgdir/lib/"ld-musl*.so* "$pkgdir/usr/lib/"
  mkdir -p "$pkgdir"/usr/share/doc/musl
  cp COPYRIGHT README "$pkgdir"/usr/share/doc/musl/
  cp "$srcdir"/CHANGELOG "$pkgdir"/usr/share/doc/musl/CHANGELOG.archlinux
}
md5sums=('cd1feccb98112cf3685edb4499306d83'
         '15cd2290ae45a981019b69343113fd2b')
