pkgname=ally-motion-evdev
pkgver=1.0.0
pkgrel=1
pkgdesc='Exposes bmi323 chip over an evdev interface'
arch=('x86_64')
url='https://github.com/NeroReflex/ally-motion-evdev/'
license=('BSD')
depends=()
makedepends=('cmake')
provides=('ally-motion-evdev')
source=(
    "git+https://github.com/NeroReflex/ally-motion-evdev.git"
    "ally-motion-evdev.service"
    "10-ally-motion-evdev.rule"
)
sha256sums=(
    'SKIP'
    '07baa9eeb42fec28b13985286afd15d91188c5214ee87f8b4a97a1c4e9e5832f' # ally-motion-evdev.service
    '6954a9e1c614be8ff7ebf5456713d31735f1d3b0dfc92365e2c378ca3e99de6d' # 10-ally-motion-evdev.rule
)

prepare() {
    cd "${pkgname}"
    #mkdir "${pkgname}/build"
    cd ..
}

build() {
    cmake \
        -B build \
        -S "${pkgname}" \
        -G 'Unix Makefiles' \
        -DCMAKE_BUILD_TYPE:STRING='Release' \
        -DCMAKE_INSTALL_PREFIX:PATH='/usr' \
        -Wno-dev
    cmake --build build
}

#check() {
#    ctest --test-dir build --output-on-failure
#}

package() {
    DESTDIR="$pkgdir" cmake --install build
    #cd "${pkgname}-${pkgver}"
    
    # udev
    install -D -m644 ally-motion-evdev.service   -t "${pkgdir}/usr/lib/udev/rules.d/"

    # systemd
    install -D -m644 ally-motion-evdev.service   -t "${pkgdir}/usr/lib/systemd/system"
    
    # license
    #install -D -m644 LICENSE -t "${pkgdir}/usr/share/licenses/${pkgname}"
}
