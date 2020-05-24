# Script generated with import_catkin_packages.py.
# For more information: https://github.com/bchretien/arch-ros-stacks.
pkgdesc="ROS - This package attempts to show the features of ROS python API step-by-step, including using messages, servers, parameters, etc."
url='https://www.wiki.ros.org/rospy_tutorials'

pkgname='ros-noetic-rospy-tutorials'
pkgver='0.9.1'
_pkgver_patch=0
arch=('any')
pkgrel=1
license=('BSD')

ros_makedepends=(
	ros-noetic-message-generation
	ros-noetic-std-msgs
	ros-noetic-catkin
	ros-noetic-rostest
)

makedepends=(
	'cmake'
	'ros-build-tools'
	${ros_makedepends[@]}
)

ros_depends=(
	ros-noetic-message-runtime
	ros-noetic-rospy
	ros-noetic-std-msgs
)

depends=(
	${ros_depends[@]}
)

_dir="ros_tutorials-${pkgver}/rospy_tutorials"
source=("${pkgname}-${pkgver}.tar.gz"::"https://github.com/ros/ros_tutorials/archive/${pkgver}.tar.gz")
sha256sums=('b39929a2ac912326fc114256e755fff5d0f0e5e5e7c99640d013eb7f916b85f4')

build() {
	# Use ROS environment variables.
	source /usr/share/ros-build-tools/clear-ros-env.sh
	[ -f /opt/ros/noetic/setup.bash ] && source /opt/ros/noetic/setup.bash

	# Create the build directory.
	[ -d ${srcdir}/build ] || mkdir ${srcdir}/build
	cd ${srcdir}/build

	# Build the project.
	cmake ${srcdir}/${_dir} \
		-DCATKIN_BUILD_BINARY_PACKAGE=ON \
		-DCMAKE_INSTALL_PREFIX=/opt/ros/noetic \
		-DPYTHON_EXECUTABLE=/usr/bin/python \
		-DSETUPTOOLS_DEB_LAYOUT=OFF
	make
}

package() {
	cd "${srcdir}/build"
	make DESTDIR="${pkgdir}/" install
}
