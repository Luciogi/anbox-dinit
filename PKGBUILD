# Maintainer: Mobin Aydinfar <mobin at mobintestserver dot ir>

pkgname=anbox-dinit
pkgver=1
pkgrel=1
arch=(any)
pkgdesc="Dinit service scripts for Anbox"
depends=('dinit' 'anbox-nosystemd-git' 'fuse-dinit')
source=('anbox-container-manager'
        'anbox-container-manager-pre'
        'anbox-container-manager_start'
        'anbox-container-manager_stop'
        #'anbox-session-manager'
	)
sha256sums=('4404d742612c7eba98ba14ef5654c617ea50fb002a000a46333de1fbeaaddf1c'
            '4857754a6579f9a1a4d8587e3bab6b04cfcafd5486dcf159462211f1f494227d'
            '73c8d27e910a610078d689e6f9c261207652ae39682348b0f33c1c957273eef9'
            'd7aa40dd5a7ad03148f9b92e0f1622496a4bf124584ef13ad39646566bddef40'
            #'83b1566d0e2fdbe864cc606c7e2d9411768c29cc7ad01eb5302b280105007071'
	    )
package() {
  install -Dm 644  "$srcdir/anbox-container-manager"  "$pkgdir/etc/dinit.d/anbox-container-manager"
  install -Dm 644  "$srcdir/anbox-container-manager-pre"  "$pkgdir/etc/dinit.d/anbox-container-manager-pre"
  install -Dm 744  "$srcdir/anbox-container-manager_start"  "$pkgdir/etc/dinit.d/anbox.d/anbox-container-manager_start"
  install -Dm 744  "$srcdir/anbox-container-manager_stop"  "$pkgdir/etc/dinit.d/anbox.d/anbox-container-manager_stop"
#  install -Dm 644  "$srcdir/anbox-session-manager"    "$pkgdir/etc/dinit.d/anbox-session-manager"
}
