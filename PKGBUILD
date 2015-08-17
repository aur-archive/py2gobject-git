# Maintainer: Niklas Koep <niklas dot koep at gmail dot com>
pkgname=py2gobject-git
pkgver=20130206
pkgrel=2
pkgdesc="Python 2 bindings for GObject"
arch=("i686" "x86_64")
url="https://live.gnome.org/PyGObject"
license=("LGPL")
depends=("gobject-introspection" "python2-cairo" "pygobject-devel-git")
makedepends=("git")
provides=("python2-gobject")
conflicts=("python2-gobject")
options=("!libtool")
md5sums=("SKIP")
_gitroot="git://git.gnome.org/pygobject"

build() {
    cd "${srcdir}"
    msg "Connecting to GIT server...."

    if [ ! -d ${pkgname} ]; then
        git clone ${_gitroot} ${pkgname} --depth=1 || return 1
    fi

    cd ${pkgname}
    git pull origin || return 1

    msg "GIT checkout done"

    msg "Starting make..."
    ./autogen.sh --prefix=/usr --with-python=python2
    make
}

package() {
    cd ${pkgname}
    make DESTDIR="${pkgdir}" install
    rm -r "${pkgdir}"/usr/{include,lib/pkgconfig}
}

