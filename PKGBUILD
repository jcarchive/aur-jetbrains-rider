# Maintainer: Jose C.

pkgname=jetbrains-rider
pkgver='2021.3.2'
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

sha256sums=( '56699bf27289866d56e63d76b2f63d57cee02cc00034f52896e4204e7982362b'
	'56393c9688b46f4fcb709c09dd33d24f675c4fc647fbf160f14302dc55a5c1ef')

package() {
	#Create directories with permission rwxr-xr-x
	install -m755 -d "${pkgdir}/usr/share" "${pkgdir}/usr/bin" "${pkgdir}/usr/share/applications"

	#Copy files to pkg destination
	cp -r "${srcdir}/${_filextract}" "${pkgdir}/usr/share/${pkgname}"
  chown -R root:root "${pkgdir}/usr/share/${pkgname}"

	ln -s "/usr/share/${pkgname}/bin/rider.sh" "${pkgdir}/usr/bin/rider"
  install -m644 "${srcdir}/${pkgname}.desktop" "${pkgdir}/usr/share/applications"
}
