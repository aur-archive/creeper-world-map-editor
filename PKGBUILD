# Maintainer:  Felix Berkenkamp      <felix1012 at gmx.de>

pkgname=creeper-world-map-editor
pkgver=0380
pkgrel=2
pkgdesc="The map editor for Creeper World"
arch=('i686' 'x86_64')
url="http://knucklecracker.com/creeperworld/mapeditor.php"
license=('custom')
depends=('adobe-air-sdk')
makedepends=('unzip')
source=(http://knucklecracker.com/creeperworld/mapeditor/CreeperMap-${pkgver}.air
	    mapeditor-cw1.desktop)
noextract=(CreeperMap-${pkgver}.air)

package() {
  cd "${srcdir}"

  unzip CreeperMap-${pkgver}.air

  mkdir -p "${pkgdir}"/usr/share/{cwe,applications}
  mkdir -p "${pkgdir}/usr/bin"

  cp -r icons  META-INF  mimetype  CreeperMap.swf "${pkgdir}/usr/share/cwe/"

  cp -p mapeditor-cw1.desktop "${pkgdir}/usr/share/applications/"

  cat <<EOF >> "${pkgdir}/usr/bin/cwe"
#!/bin/sh
/opt/adobe-air-sdk/bin/adl -nodebug /usr/share/cwe/META-INF/AIR/application.xml /usr/share/cwe &
EOF

  chmod +x "${pkgdir}/usr/bin/cwe"
}

md5sums=('5ff5774f4e60bc4537e000016b446ced'
         '870fd3204ec7b053b7c534f5295b1d7a')
