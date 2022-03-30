# Maintainer: Jose C.

pkgname=jetbrains-rider
pkgver='2021.3.3'
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

source=("https://download.jetbrains.com/rider/${_filename}"
	"${pkgname}.desktop")

sha256sums=( '1dc57d5d7932d4a8dea51fc5cbdaa52f9626490092978f02fa15bb41cb84068f'
	'193f632d75e0810d3bf94673aae99faa01fb5f13b891cd694e7c87dcd08db8b1')

package() {
	#Create directories with permission rwxr-xr-x
	install -m755 -d "${pkgdir}/usr/share" "${pkgdir}/usr/bin" "${pkgdir}/usr/share/applications"

	#Copy files to pkg destination
	cp -r "${srcdir}/${_filextract}" "${pkgdir}/usr/share/${pkgname}"
  chown -R root:root "${pkgdir}/usr/share/${pkgname}"

	ln -s "/usr/share/${pkgname}/bin/rider.sh" "${pkgdir}/usr/bin/rider"
  install -m644 "${srcdir}/${pkgname}.desktop" "${pkgdir}/usr/share/applications"
}
