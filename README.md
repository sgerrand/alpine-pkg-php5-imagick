# alpine-pkg-php5-imagick

[![CircleCI](https://circleci.com/gh/sgerrand/alpine-pkg-php5-imagick/tree/master.svg?style=svg)](https://circleci.com/gh/sgerrand/alpine-pkg-php5-imagick/tree/master)

This is the [PHP5 extension for ImageMagick][php-imagick] as an Alpine Linux package.

The package provided by Alpine Linux was removed from their repositories in the
3.6 release. A package for PHP7 is still [available there](https://pkgs.alpinelinux.org/packages?name=php7-pecl-imagick*).

## Releases

See the [releases page](https://github.com/sgerrand/alpine-pkg-php5-imagick/releases) for the latest
download links.

## Installing

The current installation method for these packages is to pull them in using
`wget` or `curl` and install the local file with `apk`:

    apk --no-cache add ca-certificates wget
    wget -q -O /etc/apk/keys/sgerrand.rsa.pub https://raw.githubusercontent.com/sgerrand/alpine-pkg-php5-imagick/master/sgerrand.rsa.pub
    wget https://github.com/sgerrand/alpine-pkg-php5-imagick/releases/download/3.4.3-r0/php5-imagick-3.4.3-r0.apk
    apk add php5-imagick-3.4.3-r0.apk

[php-imagick]: https://pecl.php.net/imagick
