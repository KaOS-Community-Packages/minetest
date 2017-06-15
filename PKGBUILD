pkgname=minetest
pkgver=0.4.16
pkgrel=1
pkgdesc="An InfiniMiner/Minecraft inspired game."
arch=('x86_64')
url="http://www.minetest.net/"
license=('GPL')
depends=('sqlite' 'freetype2' 'leveldb' 'openal' 'libvorbis' 'curl' 'irrlicht' 'cmake' 'hiredis' 'luajit')
source=("${pkgname}_${pkgver}.tar.gz::https://github.com/${pkgname}/${pkgname}/archive/${pkgver}.tar.gz"
        "minetest_game_${pkgver}.tar.gz::https://github.com/${pkgname}/minetest_game/archive/${pkgver}.tar.gz"
)
md5sums=('70e40bc170e8f8a5aa7c35102a314b76'
         'e97efb4618f345ae3039af7ba844fb9c'
)

package() {
    cp -r $srcdir/minetest_game-${pkgver}/ $srcdir/${pkgname}-${pkgver}/games/minetest_game/
    cd $srcdir/${pkgname}-${pkgver}
    cmake ../$pkgname-$pkgver \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DBUILD_CLIENT=1 \
    -DENABLE_GETTEXT=1 \
    -DENABLE_FREETYPE=1 \
    -DENABLE_LEVELDB=0 \
    -DENABLE_REDIS=0
    make
    make DESTDIR="$pkgdir" install
}
