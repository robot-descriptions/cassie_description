cmake_minimum_required(VERSION 2.8 FATAL_ERROR)
project(cassie_description VERSION 1.0.0)

add_compile_options(-std=c++11)

find_package(catkin REQUIRED COMPONENTS
    roscpp rospy roslib eigen_utilities cassie_common_toolbox
)

catkin_package()

install(DIRECTORY meshes urdf
    DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)
