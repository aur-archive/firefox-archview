# Maintainer: Giancarlo Bianchi <giancarlobianchi76 [at] gmail [dot] com>

pkgname=firefox-archview
_pkgname=archview
pkgver=0.7.2
pkgrel=2
pkgdesc="Firefox extension to open archive files online without downloading the whole archive"
arch=('i686' 'x86_64')
url="https://github.com/Infocatcher/ArchView"
license=('MPL' 'GPL2' 'LGPL2.1')
depends=('firefox')
noextract=("$_pkgname-$pkgver-fx-sm.xpi")
source=("https://github.com/Infocatcher/ArchView/releases/download/$pkgver/$_pkgname-$pkgver-fx-sm.xpi")
md5sums=('61f0c50493f787ea2f27f72653e00ecb')

package() {
  cd $srcdir
  if [[ ! -d $_pkgname-$pkgver ]]; then
    mkdir $_pkgname-$pkgver
  fi
  cd $_pkgname-$pkgver
  bsdtar -xf ../$_pkgname-$pkgver-fx-sm.xpi

  local emid=$(sed -n -e '/<\?em:id>\?/!d; s/.*\([\"{].*[}\"]\).*/\1/; s/\"//g; p; q' install.rdf)
  local dstdir=$pkgdir/usr/lib/firefox/browser/extensions/${emid}

  install -d $dstdir
  cp -R * $dstdir
}

# vim:set ts=2 sw=2 et:
