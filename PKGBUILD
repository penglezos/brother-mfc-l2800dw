# Maintainer: Panagiotis Englezos <info@penglezos.dev>
# Based on <https://aur.archlinux.org/packages/brother-mfc-l2820dw/>
pkgname=brother-mfc-l2800dw
pkgver=4.1.0
pkgrel=1
pkgdesc="LPR and CUPS driver for the Brother MFC-L2800DW printer"
url="https://support.brother.com/g/b/producttop.aspx?c=as_ot&lang=en&prod=mfcl2800dw_eu_as"
arch=("i686" "x86_64")
license=('custom:brother commercial license')
depends=(cups)
depends_x86_64=(lib32-glibc)
source=("https://download.brother.com/welcome/dlf106049/mfcl2800dwpdrv-$pkgver-$pkgrel.i386.rpm")
md5sums=("8714528f4f61eadfa255ed7e5ce00bf6")

package() {
  local -r model=MFCL2800DW
  local -r basedir=/usr/share/brother/Printers/$model

  # using `/usr/share` instead of `/opt`
  mkdir -p "$pkgdir/usr/share"
  cp -R "$srcdir/opt/brother" "$pkgdir/usr/share"
  sed -i 's|/opt|/usr|' "$pkgdir/$basedir/cupswrapper/lpdwrapper"
  sed -i 's|/opt|/usr|' "$pkgdir/$basedir/lpd/lpdfilter"

  # CUPS manages `/etc/printcap`
  find "$pkgdir" -type f -name 'setupPrintcap*' -delete

  # symbolic link for `lpdwrapper` so it correctly figures out the
  # printer model from the path
  install -d "$pkgdir/usr/lib/cups/filter/"
  ln -s "$basedir/cupswrapper/lpdwrapper" "$pkgdir/usr/lib/cups/filter/brother_lpdwrapper_$model"

  # symlink for the PPD
  install -d "$pkgdir/usr/share/cups/model/"
  ln -s "$basedir/cupswrapper/brother-$model-cups-en.ppd" "$pkgdir/usr/share/cups/model/"

  # a couple architecture-specific symbolic links
  ln -s "$basedir/lpd/$CARCH/brprintconflsr3" "$pkgdir/$basedir/lpd/"
  ln -s "$basedir/lpd/$CARCH/rawtobr3" "$pkgdir/$basedir/lpd/"

  # symlink for `inf` because it tries to execute it there
  rmdir "$pkgdir/$basedir/lpd/inf"
  ln -s "$basedir/inf" "$pkgdir/$basedir/lpd/"
}
