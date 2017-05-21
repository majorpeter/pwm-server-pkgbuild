# Maintainer: Peter Major <majorpeter29@gmail.com>

_pkgname="pwm-server"
pkgname="$_pkgname-git"
pkgver=VERSION
pkgrel=1
pkgdesc="A website that controls the STM32F1 PWM extender, written in node.js."
arch=('any')
url="https://github.com/majorpeter/pwm-server"
license=('ISC')
depends=('npm')
makedepends=('npm')
source=("$_pkgname::git+https://github.com/majorpeter/pwm-server.git")
md5sums=('SKIP')

pkgver() {
  cd "$srcdir/$_pkgname"
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
  cd "$srcdir/$_pkgname"
  npm install
}

package() {
  INSTALLDIR="$pkgdir/usr/share/webapps/$_pkgname"
  mkdir -p "$INSTALLDIR"
  cp -R "$srcdir/$_pkgname/node_modules" "$INSTALLDIR/"
  cp -R "$srcdir/$_pkgname/static" "$INSTALLDIR/"
  cp "$srcdir/$_pkgname/package.json" "$INSTALLDIR/"
  cp "$srcdir/$_pkgname/server.js" "$INSTALLDIR/"
  cp "$srcdir/$_pkgname/index.html" "$INSTALLDIR/"

  mkdir -p "$pkgdir/usr/lib/systemd/system/"
  cp "$srcdir/../pwm-server.service" "$pkgdir/usr/lib/systemd/system/"
}
