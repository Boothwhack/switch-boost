pkgname=switch-boost
pkgver=1.75.0
pkgrel=6
pkgdesc="Switch port of some Boost libraries"
arch=("any")
_git_boost="https://github.com/boostorg"
_git_tag="boost-${pkgver}"
source=("https://github.com/Boothwhack/asio-nx/releases/download/v1.18.0/asio-boostified-1.18.0.zip"
        "site-config.linux.jam"
        "site-config.win.jam"
        "boost-config-select-platform.patch"
        "${_git_boost}/boost/archive/${_git_tag}.tar.gz"

        "align-${_git_tag}.tar.gz::${_git_boost}/align/archive/${_git_tag}.tar.gz"
        "assert-${_git_tag}.tar.gz::${_git_boost}/assert/archive/${_git_tag}.tar.gz"
        "config-${_git_tag}.tar.gz::${_git_boost}/config/archive/${_git_tag}.tar.gz"
        "beast-${_git_tag}.tar.gz::${_git_boost}/beast/archive/${_git_tag}.tar.gz"
        "bind-${_git_tag}.tar.gz::${_git_boost}/bind/archive/${_git_tag}.tar.gz"
        "boost_install-${_git_tag}.tar.gz::${_git_boost}/boost_install/archive/${_git_tag}.tar.gz"
        "build-${_git_tag}.tar.gz::${_git_boost}/build/archive/${_git_tag}.tar.gz"
        "config-${_git_tag}.tar.gz::${_git_boost}/config/archive/${_git_tag}.tar.gz"
        "container-${_git_tag}.tar.gz::${_git_boost}/container/archive/${_git_tag}.tar.gz"
        "container_hash-${_git_tag}.tar.gz::${_git_boost}/container_hash/archive/${_git_tag}.tar.gz"
        "core-${_git_tag}.tar.gz::${_git_boost}/core/archive/${_git_tag}.tar.gz"
        "exception-${_git_tag}.tar.gz::${_git_boost}/exception/archive/${_git_tag}.tar.gz"
        "headers-${_git_tag}.tar.gz::${_git_boost}/headers/archive/${_git_tag}.tar.gz"
        "intrusive-${_git_tag}.tar.gz::${_git_boost}/intrusive/archive/${_git_tag}.tar.gz"
        "io-${_git_tag}.tar.gz::${_git_boost}/io/archive/${_git_tag}.tar.gz"
        "json-${_git_tag}.tar.gz::${_git_boost}/json/archive/${_git_tag}.tar.gz"
        "logic-${_git_tag}.tar.gz::${_git_boost}/logic/archive/${_git_tag}.tar.gz"
        "move-${_git_tag}.tar.gz::${_git_boost}/move/archive/${_git_tag}.tar.gz"
        "mp11-${_git_tag}.tar.gz::${_git_boost}/mp11/archive/${_git_tag}.tar.gz"
        "optional-${_git_tag}.tar.gz::${_git_boost}/optional/archive/${_git_tag}.tar.gz"
        "preprocessor-${_git_tag}.tar.gz::${_git_boost}/preprocessor/archive/${_git_tag}.tar.gz"
        "smart_ptr-${_git_tag}.tar.gz::${_git_boost}/smart_ptr/archive/${_git_tag}.tar.gz"
        "static_assert-${_git_tag}.tar.gz::${_git_boost}/static_assert/archive/${_git_tag}.tar.gz"
        "system-${_git_tag}.tar.gz::${_git_boost}/system/archive/${_git_tag}.tar.gz"
        "throw_exception-${_git_tag}.tar.gz::${_git_boost}/throw_exception/archive/${_git_tag}.tar.gz"
        "type_traits-${_git_tag}.tar.gz::${_git_boost}/type_traits/archive/${_git_tag}.tar.gz"
        "utility-${_git_tag}.tar.gz::${_git_boost}/utility/archive/${_git_tag}.tar.gz")
md5sums=('f2f5d53f5fd9a2fb9c4a8b0015e2f141'
         'e71c61cafedc390a6af74567edb195f7'
         '0f51046b36a14232ed531f701883717b'
         'b4c9e9867c4ccf4bed388135cc191869'
         'f417099c0d8bba7cdb91e314c9ccfcd0'
         '85b59958d7cf1e29b08386b349c76136'
         '813207972e1f8ce266e079e11089df38'
         'd0adbdb9dcfe217722c453024ee66e7e'
         '917bf2b69cb753ca9f0dcd886f3e6127'
         '80343ca2c6b94d321618fe111657deb4'
         '51ff68db46408fec32487f1df74836ac'
         '4028efa928ebd2cb97cd8686b3b7416a'
         'd0adbdb9dcfe217722c453024ee66e7e'
         '3092adbbd6ecea48222c27b59534653e'
         'c2e460d1fb61f718fb50cdf56cf8c9aa'
         '0777aaabc7e633d38bf1a427219b6530'
         '8a9ed8a021a39c1b371b9d7c2d2bb5d7'
         '95b264d196534c9f8899c5131e67be48'
         'e3ae4604d4c207e37775c56597afc265'
         '41ec5f48cb6068ccdba58386072374d4'
         '27a88c05e6d9c9802eced6100c92ee32'
         'bacd29e3146ab1eb0bfe4d4851a1b441'
         '54bb9d8eb9083c832427a3909e3391a2'
         '64411ded157561fe66db4fefe0636dec'
         '8fd5b9da9ac62368caa2e91454d5d86d'
         '21f0c2c079f23d017e86dd8384493909'
         '5d3d3e618128bf9c123ca4620118b706'
         'aded16e5dfb671a77a6e54ad35b29780'
         '13da48473a07acb196301f310ba68161'
         '54255cae8411cf133c0626dbb7a753eb'
         '314b2395d2a38bb6d1ba0aa1ef1629e1'
         'c5f339146be1d1b11fc76c28598662ce')

prepare() {
    cd $srcdir/boost-$_git_tag

    # Setup required build tools and supported libraries
    local libs=(
        "align"
        "assert"
        "beast"
        "bind"
        "config"
        "container"
        "container_hash"
        "core"
        "exception"
        "intrusive"
        "io"
        "json"
        "headers"
        "logic"
        "move"
        "mp11"
        "optional"
        "preprocessor"
        "smart_ptr"
        "static_assert"
        "system"
        "throw_exception"
        "type_traits"
        "utility"
    )
    for lib in "${libs[@]}"; do
        cp -R $srcdir/$lib-$_git_tag/* libs/$lib
    done

    cp -R $srcdir/boost_install-$_git_tag/* tools/boost_install
    cp -R $srcdir/build-$_git_tag/* tools/build

    # Apply patches
    patch -p1 -i $srcdir/boost-config-select-platform.patch -d libs/config

    # Prepare ASIO switch port
    cp -r $srcdir/libs/* $srcdir/boost-$_git_tag/libs/

    # Choose the correct compiler configuration for the host platform
    if [ -x /opt/devkitpro/devkitA64/bin/aarch64-none-elf-g++.exe ]; then
        cp $srcdir/site-config.win.jam $srcdir/site-config.jam
    elif [ -x /opt/devkitpro/devkitA64/bin/aarch64-none-elf-g++ ]; then
        cp $srcdir/site-config.linux.jam $srcdir/site-config.jam
    else
        echo "Unable to locate devkitA64 compiler"
        exit 1
    fi
}

build() {
    cd $srcdir/boost-$_git_tag

    export "PATH=$PATH:/opt/devkitpro/devkitA64/bin"

    ./bootstrap.sh --prefix=$srcdir/dist
    BOOST_BUILD_PATH=$srcdir ./b2 \
        toolset=gcc-aarch64 \
        target-os=linux \
        runtime-link=static \
        link=static \
        variant=release \
        -q \
        cflags="-DSWITCH -D__SWITCH__ -DHAVE_MMAP=0 -DLACKS_SYS_MMAN_H -march=armv8-a+crc+crypto -mtune=cortex-a57 -mtp=soft -ftls-model=local-exec -ffunction-sections -fdata-sections -fPIE" \
        install
}

package() {
    install -d $pkgdir/opt/devkitpro/portlibs/switch
    cp -R $srcdir/dist/* $pkgdir/opt/devkitpro/portlibs/switch
}
