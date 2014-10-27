# Maintainer: Adrien RAFFIN <raffinadrien@gmail.com> 

pkgname=advcp
pkgver=0.5.4
pkgrel=1

_pkgname=coreutils
_pkgver=8.21
pkgdesc="'cp' and 'mv' utilities with progress bar patches" 
arch=('i686' 'x86_64')
license=('GPL3')
url="http://www.gnu.org/software/coreutils"
groups=('base')
depends=('glibc' 'pam' 'acl' 'gmp' 'libcap')
provides=('acp' 'amv')
install=${pkgname}.install
source=(ftp://ftp.gnu.org/gnu/$_pkgname/$_pkgname-$_pkgver.tar.xz{,.sig}
        advcpmv-${_pkgver}_${pkgver}.patch)

build() {
  cd ${srcdir}/${_pkgname}-${_pkgver}
    
  patch -p1 -i ${srcdir}/advcpmv-${_pkgver}_${pkgver}.patch

  ./configure --prefix=/usr --libexecdir=/usr/lib \
              --enable-no-install-program=groups,hostname,kill,uptime
  make $MAKEFLAGS -j1
}

package() {
  cd ${srcdir}/${_pkgname}-${_pkgver}
  install -D src/cp ${pkgdir}/usr/bin/acp
  install -D src/mv ${pkgdir}/usr/bin/amv
}

md5sums=('065ba41828644eca5dd8163446de5d64'
				 'SKIP'
				 '7ccfcb864f36fccc07291778934daf02')
