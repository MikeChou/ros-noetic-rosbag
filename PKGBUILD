# Script generated with import_catkin_packages.py.
# For more information: https://github.com/bchretien/arch-ros-stacks.
pkgdesc="ROS - This is a set of tools for recording from and playing back to ROS topics."
url='https://wiki.ros.org/rosbag'

pkgname='ros-noetic-rosbag'
pkgver='1.15.4'
arch=('i686' 'x86_64' 'aarch64' 'armv7h' 'armv6h')
pkgrel=1
license=('BSD')

ros_makedepends=(
	ros-noetic-std-srvs
	ros-noetic-xmlrpcpp
	ros-noetic-rosbag-storage
	ros-noetic-catkin
	ros-noetic-cpp-common
	ros-noetic-rosconsole
	ros-noetic-roscpp
	ros-noetic-roscpp-serialization
	ros-noetic-topic-tools
)

makedepends=(
	'cmake'
	'ros-build-tools'
	${ros_makedepends[@]}
	python-pillow
	boost
)

ros_depends=(
	ros-noetic-std-srvs
	ros-noetic-xmlrpcpp
	ros-noetic-rosbag-storage
	ros-noetic-genpy
	ros-noetic-rosconsole
	ros-noetic-roscpp
	ros-noetic-topic-tools
	ros-noetic-rospy
	ros-noetic-genmsg
	ros-noetic-roslib
)

depends=(
	${ros_depends[@]}
	python-rospkg
	boost
	python-gnupg
	python-crypto
)

_dir="ros_comm-${pkgver}/tools/rosbag"
source=("${pkgname}-${pkgver}.tar.gz"::"https://github.com/ros/ros_comm/archive/${pkgver}.tar.gz")
sha256sums=('d5c96a81e0c8554b77666bca5dcc68e03083a761a117038ff9b65f9643751c9e')

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
