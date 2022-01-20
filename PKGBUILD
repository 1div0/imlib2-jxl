# Maintainer: TODO

# Basde on PKGBUILD-git - https://github.com/jamesan/linux-templates/blob/master/PKGBUILD-git
# template for writing a PKGBUILD file with a git VCS source

# Copyright 2014 James An

# THIS PROGRAM is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.

# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.

# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.

_pkgname=imlib2-jxl
pkgname="$_pkgname"
pkgver=0.1
pkgrel=1
pkgdesc="JPEG XL loader for imlib2"
arch=('x86_64')
url="https://github.com/alistair7/$_pkgname"
license=('BSD')
depends=('imlib2' 'libjxl' 'lcms2')
makedepends=('git')
provides=("$_pkgname")
conflicts=("$_pkgname-git")
options=()
install=
source=("$_pkgname"::"git+https://github.com/alistair7/$_pkgname.git")
md5sums=('SKIP')

_branch=v0.1.x

pkgver() {
    cd "$_pkgname"
    git describe --tags --abbrev=0 "$_branch" | sed s/v//
}

build() {
    cd "$_pkgname"
    git checkout --quiet "$_branch"
    make
}

package() {
    cd "$_pkgname"
    install -Dm 644 jxl.so $pkgdir`pkg-config imlib2 --variable=libdir`/imlib2/loaders/jxl.so
    install -Dm644 LICENSE-BSD-ab "$pkgdir/usr/share/licenses/$pkgname/LICENSE-BSD-ab"
    install -Dm644 LICENSE-BSD-dh "$pkgdir/usr/share/licenses/$pkgname/LICENSE-BSD-dh"
}
