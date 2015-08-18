# Maintainer: David J. Haines <dhaines@gmail.com>
_hkgname=yeganesh
pkgname=yeganesh-patched
pkgver=2.2.1
pkgrel=1
pkgdesc="small dmenu wrapper for newer Haskell and dmenu releases"
url="http://hackage.haskell.org/package/${_hkgname}"
license=('custom:BSD3')
arch=('i686' 'x86_64')
makedepends=('ghc' 'haskell-containers>=0.3.0.0' 'haskell-directory>=1.0.1.1' 'haskell-filepath>=1.1.0.4' 'haskell-process>=1.0.1.3' 'haskell-strict>=0.3' 'haskell-time>=1.1.4' 'haskell-xdg-basedir>=0.2')
depends=('gmp' 'dmenu-path-c')
conflicts=('yeganesh')
options=('strip')
source=(http://hackage.haskell.org/packages/archive/${_hkgname}/${pkgver}/${_hkgname}-${pkgver}.tar.gz \
	newline.patch \
	${pkgname}.install)
install=$pkgname.install
build() {
    cd ${srcdir}/${_hkgname}-${pkgver}
    patch -Ni "${srcdir}/newline.patch" || return 1
    runhaskell Setup configure --prefix=/usr --docdir=/usr/share/doc/${pkgname} -O
    runhaskell Setup build
}
package() {
    cd ${srcdir}/${_hkgname}-${pkgver}
    runhaskell Setup copy --destdir=${pkgdir}
    install -D -m644 LICENSE ${pkgdir}/usr/share/licenses/${pkgname}/LICENSE
    rm -f ${pkgdir}/usr/share/doc/${pkgname}/LICENSE
}
md5sums=('6d6c1f7c546131eeda46770d7bd129a7'
         '064c840d635ae21e609ce54cdcc6954d'
         '1e00c9f37c7d3c569e876efd3a4f5fc4')

# vim:set ts=2 sw=2 et:
