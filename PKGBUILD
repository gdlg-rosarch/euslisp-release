# Script generated with Bloom
pkgdesc="ROS - EusLisp is an integrated programming system for the research on intelligent robots based on Common Lisp and Object-Oriented programming"
url='http://euslisp.github.io/EusLisp/manual.html'

pkgname='ros-kinetic-euslisp'
pkgver='9.23.0_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('libjpeg-turbo'
'libpng'
'libx11'
'libxext'
'mesa'
'postgresql-libs'
'ros-kinetic-catkin'
'ros-kinetic-cmake-modules'
'ros-kinetic-mk'
'xorg-fonts-100dpi'
'xorg-fonts-75dpi'
)

depends=('libjpeg-turbo'
'libpng'
'libx11'
'libxext'
'mesa'
'postgresql-libs'
'xorg-fonts-100dpi'
'xorg-fonts-75dpi'
)

conflicts=()
replaces=()

_dir=euslisp
source=()
md5sums=()

prepare() {
    cp -R $startdir/euslisp $srcdir/euslisp
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/kinetic/setup.bash ] && source /opt/ros/kinetic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/kinetic \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DPYTHON_BASENAME=-python2.7 \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

