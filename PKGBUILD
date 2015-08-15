# Maintainer: boenki <boenki at gmx dot de>
# Contributor: Joao Cordeiro <jlcordeiro at gmail dot com>
# Contributor: mosra <mosra@centrum.cz>
# Contributor: Xyne <xyne@archlinux.ca>
pkgname=brainparty
pkgver=0.61
pkgrel=3
pkgdesc="36 puzzle games for all the family"
arch=('i686' 'x86_64')
url="http://www.tuxradar.com/$pkgname"
license=('GPL3')
depends=('sdl_gfx' 'sdl_ttf' 'sdl_mixer' 'sdl_image' 'mesa' 'glu' 'ttf-freefont')
source=(https://launchpad.net/$pkgname/trunk/$pkgver/+download/brainparty0.61.tar.gz
        'path2data.patch'
        'change-config-file-path.patch'
        'brainparty_gcc49.patch')
md5sums=('d6bcdf6261697d206dbbda3362632002'
         'ef8be0d4160c7c9dc936698d6c6aa672'
         '3bef8710cb6ef57291361a03d34a556f'
         '48e80a8babe8e7f8719316e4ba3ac977')

prepare() {
  cd "$pkgname"
  patch -p1 -i ../path2data.patch
  patch -p1 -i ../change-config-file-path.patch
  sed -i "s|Content/freesans.ttf|/usr/share/fonts/TTF/FreeSans.ttf|g" BPGame.cpp
  patch -p2 -i ../brainparty_gcc49.patch
}

build() {
  cd "$pkgname"
  make
}

package() {
  cd "$pkgname"
  install -Dm755 brainparty "$pkgdir/usr/bin/brainparty"
  install -d "$pkgdir/usr/share/games/brainparty/"
  install -m644 Content/* "$pkgdir/usr/share/games/brainparty/"
}