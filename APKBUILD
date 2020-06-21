# Contributor: Sasha Gerrand <alpine-pkgs@sgerrand.com>
# Maintainer: Sasha Gerrand <alpine-pkgs@sgerrand.com>
_php=php5
pkgname=$_php-imagick
_pkgrealname=imagick
pkgver=3.4.4
pkgrel=0
_phpver=${pkgname#php}
_phpver=${_phpver%%-*}
pkgdesc="PHP$_phpver extension: Provides a wrapper to the ImageMagick library"
url="https://pecl.php.net/$_pkgrealname"
arch="all"
license="PHP"
depends="php$_phpver-common"
depends_dev="$_php-dev"
makedepends="$depends_dev autoconf libtool imagemagick-dev pcre-dev"
install=""
subpackages="$pkgname-dev $pkgname-doc"
source="https://pecl.php.net/get/$_pkgrealname-$pkgver.tgz"

builddir="$srcdir"/$_pkgrealname-$pkgver

build() {
	cd "$builddir"
	phpize$_phpver || return 1
	./configure --prefix=/usr \
		--with-php-config=php-config$_phpver \
	|| return 1
	make || return 1
}

package() {
	local confdir="$pkgdir/etc/php$_phpver/conf.d"
	cd "$builddir"
	make INSTALL_ROOT="$pkgdir"/ install || return 1

	install -d "$confdir" || return 1
	echo "extension=$_pkgrealname.so" > "$confdir"/"$_pkgrealname".ini
	for _dev in *.h; do
		install -Dm644 $_dev $pkgdir/usr/include/$pkgname/$_dev
	done
	for _doc in CREDITS; do
		install -Dm644 $_doc $pkgdir/usr/share/doc/$pkgname/$_doc
	done
	install -Dm644 LICENSE $pkgdir/usr/share/licenses/$pkgname/LICENSE
}

sha512sums="73145a1f095849c32760db2dfc4acc13c57d99a037d65eca9b0ddf8f8e81cf6d28a50f2614e44bae1d90b4f881a2e9a64926e0e3b9403e491fd903ffeb30c4b7  imagick-3.4.4.tgz"
