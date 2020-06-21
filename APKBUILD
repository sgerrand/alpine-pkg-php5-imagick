# Contributor: Sasha Gerrand <alpine-pkgs@sgerrand.com>
# Maintainer: Sasha Gerrand <alpine-pkgs@sgerrand.com>
_php=php5
pkgname=$_php-imagick
_pkgrealname=imagick
pkgver=3.4.3
pkgrel=1
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

sha512sums="2cb2b856cf83a78d3542cdf7c69554dcc063a0541e9092b24e5e1fbd8928066a4a3de154049d0202c35addbc5055ccfbb5910ae92f2f13da80ddfc025340ddcd  imagick-3.4.3.tgz"
