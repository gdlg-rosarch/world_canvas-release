# Script generated with Bloom
pkgdesc="ROS - Storage manager and server for WCF semantic maps."
url='http://ros.org/wiki/world_canvas_server'

pkgname='ros-kinetic-world-canvas-server'
pkgver='0.2.0_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('ros-kinetic-catkin'
)

depends=('python2-pymongo'
'ros-kinetic-nav-msgs'
'ros-kinetic-rospy'
'ros-kinetic-rostest'
'ros-kinetic-visualization-msgs'
'ros-kinetic-warehouse-ros'
'ros-kinetic-world-canvas-msgs'
'ros-kinetic-world-canvas-utils'
)

conflicts=()
replaces=()

_dir=world_canvas_server
source=()
md5sums=()

prepare() {
    cp -R $startdir/world_canvas_server $srcdir/world_canvas_server
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

