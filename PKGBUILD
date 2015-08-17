pkgname=utouch-frame-bzr
pkgver=81
pkgrel=1
pkgdesc="Touch Frame Library"
arch=('i686' 'x86_64')
url="https://launchpad.net/utouch-frame"
license=('GPL')
depends=('utouch-evemu-bzr' 'mtdev')
makedepends=('bzr' 'asciidoc' 'xorg-server-devel')
provides=('utouch-frame')
conflicts=('utouch-frame')
options=('!libtool')

_bzrtrunk=lp:utouch-frame
_bzrmod=utouch-frame

build() {
  cd "${srcdir}"
  
  if [ -d ${_bzrmod} ]; then
    bzr up ${_bzrmod}
    msg "The local files are updated."
  else
    bzr co ${_bzrtrunk} ${_bzrmod}
  fi

  cd "${srcdir}/${_bzrmod}"
  ./autogen.sh
  ./configure --prefix=/usr
  make
}

package() {
  cd "${srcdir}/${_bzrmod}"
  make DESTDIR="${pkgdir}" install
}

