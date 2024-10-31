#This is an unofficial script to build and install the AOCL-Cryptography library for Arch Linux AUR. 

pkgname=aocl-crypto
pkgver=5.0
pkgrel=1
pkgdesc="AOCL-Cryptography is a library consisting of cryptographic optimized functions for Zen."
arch=('x86_64')
url="https://github.com/amd/aocl-crypto"
options=("staticlibs")
depends=("aocl-utils")
makedepends=('cmake' 'ninja' 'gcc' 'clang' 'lsb-release')


source=("${pkgname}.tar.gz::${url}/archive/refs/tags/${pkgver}.tar.gz"
        "out.patch")
sha256sums=('b15e609943f9977e13f2d5839195bb7411c843839a09f0ad47f78f57e8821c23'
            '3e7f0c0c7ef22223ec3039dcf5b42f201d028ca6a326d7600f0458329f1b4cad')

prepare() {
    cd ${srcdir}/${pkgname}-${pkgver}
    patch -p1 < ../out.patch
}

build() {
    cd ${srcdir}/${pkgname}-${pkgver}
    #FIXME: Enable Assembly
    #FIXME: Enable Dynamic Compiler Picker
    cmake -B build -DAOCL_COMPAT_LIBS=openssl -DALCP_DISABLE_ASSEMBLY=ON -DALCP_ENABLE_EXAMPLES=OFF -DCMAKE_INSTALL_PREFIX=/usr \
    -DOPENSSL_INSTALL_DIR=/usr  -DAOCL_UTILS_INSTALL_DIR=/usr -DALCP_ENABLE_DYNAMIC_COMPILER_PICK=OFF \
    -G Ninja
    cmake --build build
}

package() {
    cd ${srcdir}/${pkgname}-${pkgver}/build
    DESTDIR=${pkgdir} ninja install
}
