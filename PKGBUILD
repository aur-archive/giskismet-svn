# Contributor: Oleander Reis <oleander@oleander.cc>
# PKGBUILD for ArchLinux

pkgname=giskismet-svn
pkgver=20110805
pkgrel=2
pkgdesc="GISKismet - a program to visually represent the Kismet data in a flexible manner."
arch=('i686' 'x86_64')
url="http://www.giskismet.org"
license=('GPL2')
depends=('perl-xml-libxml' 'perl-dbi' 'perl-dbd-sqlite')
options=('!emptydirs')
source=()
md5sums=()
makedepends=('subversion')
provides=('giskismet')
 
_svntrunk=https://my-svn.assembla.com/svn/giskismet/trunk
_svnname=giskismet
 
build() {
  msg "Starting SVN checkout..."
  cd ${srcdir}
    if [ -d $_svnname/.svn ]; then
      (cd $_svnname && svn up)
    else
      svn co $_svntrunk $_svnname
    fi
  msg "SVN checkout done or server timeout"
 
  cd "${srcdir}/${_svnname}"
  perl Makefile.PL
  make
}
package() {
  cd "${srcdir}/${_svnname}"
  make DESTDIR="${pkgdir}" MANDIR=/usr/share/man install
  cd ${pkgdir}/usr/bin
  ln -s site_perl/${_svnname} ${_svnname}
}
