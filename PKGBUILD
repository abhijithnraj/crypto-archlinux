pkgname=aocl-crypto
pkgver=5.0
pkgrel=1
pkgdesc="AOCL-Cryptography is a library consisting of basic cryptographic functions optimized and tuned for AMD Zen™ based microarchitecture. This library provides a unified solution for Cryptographic routines such as AES (Advanced Encryption Standard) encryption/decryption routines (CFB, CTR, CBC, CCM, GCM, OFB, SIV, XTS), Chacha20 Stream Cipher routines, Chacha20-Poly1305, SHA (Secure Hash Algorithms) routines (SHA2, SHA3, SHAKE), Message Authentication Code (CMAC, HMAC, Poly1305 MAC), RNG, ECDH (Elliptic-curve Diffie–Hellman), RSA (Encrypt/Decrypt and Sign/Verify Functions)."
arch=('x86_64')
url="https://github.com/amd/aocl-crypto"
license=('BSD')
depends=()
makedepends=('cmake' 'ninja' 'gcc')
source=("${pkgname}.tar.gz::${url}/archive/refs/tags/${pkgver}.tar.gz")
sha256sums=('b15e609943f9977e13f2d5839195bb7411c843839a09f0ad47f78f57e8821c23')

build() {
    cd ${srcdir}/${pkgname}-${pkgver}
    cmake -B build -DCMAKE_INSTALL_PREFIX=/usr -G Ninja
    cmake --build build
}

package() {
    cd ${srcdir}/${pkgname}-${pkgver}/build
    DESTDIR=${pkgdir} ninja install
}
