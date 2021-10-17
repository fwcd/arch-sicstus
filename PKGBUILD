pkgname=sicstus
pkgver=4.6.0
pkgrel=1
pkgdesc="SICStus Prolog"
arch=("x86_64")
license=("custom")
depends=("perl")
_glibcver=2.17

source=(
  "https://sicstus.sics.se/sicstus/products4/sicstus/${pkgver}/binaries/linux/sp-${pkgver}-${arch}-linux-glibc${_glibcver}.tar.gz"
)
sha1sums=(
  "6ffab8031583e0cf480ee366f6fd099c47af8b5e"
)

package() {
  if [ -z "$SICSTUS_LICENSE_SITENAME" ]; then
    echo "Please set a SICSTUS_LICENSE_SITENAME in your env!"
    exit 1
  fi

  if [ -z "$SICSTUS_LICENSE_CODE" ]; then
    echo "Please set a SICSTUS_LICENSE_CODE in your env!"
    exit 1
  fi

  if [ -z "$SICSTUS_LICENSE_EXPIRES" ]; then
    echo "Please set a SICSTUS_LICENSE_EXPIRES in your env!"
    exit 1
  fi

  cd "sp-${pkgver}-${arch}-linux-glibc${_glibcver}"

  cache_file="./install.cache"
  echo "installdir=${pkgdir}/opt/sicstus-${pkgver}" > $cache_file
  echo "sitename=$SICSTUS_LICENSE_SITENAME" >> $cache_file
  echo "licensecode=$SICSTUS_LICENSE_CODE" >> $cache_file
  echo "expires=$SICSTUS_LICENSE_EXPIRES" >> $cache_file
  echo "prebuilt=yes" >> $cache_file

  ./InstallSICStus --batch
}
