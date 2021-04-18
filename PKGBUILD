# Maintainer: Jose C.

pkgname=jetbrains-rider
pkgver='2021.1.1'
pkgrel=1
pkgdesc='JetBrains Rider is a cross-platform .NET IDE based on the IntelliJ platform'
arch=('x86_64')
options=('!strip' 'staticlibs')
url='https://www.jetbrains.com/rider/'
license=('Commercial')
optdepends=('mono: Free implementation of the .NET platform including runtime and compiler', 'dotnet-sdk: The .NET Core SDK')
provides=('rider')
conflicts=('rider')

_filename="JetBrains.Rider-${pkgver}.tar.gz"
_filextract="JetBrains Rider-${pkgver}"


source=("https://download-cf.jetbrains.com/rider/${_filename}" 
	"${pkgname}.desktop")

sha256sums=( '52a9c80debc82b1fe5897e2f09287a22900536d54ccb4b523fb8c2c4a55e6d02'
	'1f8d462739189235996cf50e158570d9e992125fa0674e70cb4d9fd3658e85ce')

package() {
	cd "${srcdir}"

	#Create directories with permission rwxr-xr-x
	install -d -m755 "${pkgdir}/usr/share" 
	install -d -m755 "${pkgdir}/usr/bin"
	install -d -m755 "${pkgdir}/usr/share/applications"

	#Copy files to pkg destination
	cp -a "${_filextract}" "${pkgdir}/usr/share/${pkgname}"
	chown -R root:root "${pkgdir}/usr/share/${pkgname}"

	ln -s "/usr/share/${pkgname}/bin/rider.sh" "${pkgdir}/usr/bin/rider"
	sed -i "s#\#{name}#Name=${_filextract}#g" "${pkgname}.desktop"
    	sed -i "s#\#{icon}#Icon=/user/share/${pkgname}/bin/rider.png#g" "${pkgname}.desktop"
    	sed -i "s#\#{exec}#Exec=\"/user/share/${pkgname}/bin/rider.sh\" %f#g" "${pkgname}.desktop"
    	sed -i "s/#{comment}/Comment=${pkgdesc}/g" "${pkgname}.desktop"
    	install -m644 "${srcdir}/${pkgname}.desktop" "${pkgdir}/usr/share/applications"

}
