# Maintainer: Mobin Aydinfar <mobin at mobintestserver dot ir>

pkgname=anbox-dinit
pkgver=1
pkgrel=1
arch=('x86_64')
pkgdesc="dinit service scripts for Anbox"
depends=('dinit' 'anbox-nosystemd-git' 'fuse-dinit')
source=('anbox-container-manager'
        'anbox-container-manager-pre'
        'anbox-container-manager_script'
        'anbox-container-manager_stop'
        'anbox-session-manager')
sha256sums=('4404d742612c7eba98ba14ef5654c617ea50fb002a000a46333de1fbeaaddf1c'
            '6dd8f2a7ea9f219377a36c7084fa575675213c9fde09a47cfa02b6166ec11268'
            'd236d41b01dd58e8ffa6bae5dd837ccf00822fe78e3d774dd1ec00099cd5b8a8'
            '4301b7c79a4c69800859d8030d2e2c8ec4eb1d4b4ef66c6780c3be32ff547d93'
            '2ab929308260094bc8982694202f17af4b2be5ec5018c9df438383d8a81567aa')
package() {
  install -Dm 644  "$srcdir/anbox-container-manager"  "$pkgdir/etc/dinit.d/anbox-container-manager"
  install -Dm 644  "$srcdir/anbox-container-manager-pre"  "$pkgdir/etc/dinit.d/anbox-container-manager-pre"
  install -Dm 744  "$srcdir/anbox-container-manager_script"  "$pkgdir/etc/dinit.d/anbox.d/anbox-container-manager_script"
  install -Dm 744  "$srcdir/anbox-container-manager_stop"  "$pkgdir/etc/dinit.d/anbox.d/anbox-container-manager_stop"
  install -Dm 644  "$srcdir/anbox-session-manager"    "$pkgdir/etc/dinit.d/anbox-session-manager"
}
