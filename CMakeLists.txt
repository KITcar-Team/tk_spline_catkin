cmake_minimum_required(VERSION 2.8.3)
project(tk_spline_catkin)

find_package(catkin_simple REQUIRED)
catkin_simple()

include(ExternalProject)

set(VERSION 1.0.0)

# The configure step fails at catkin_package() if this directory
# doesn't exist yet. Create it at configure time!
file(MAKE_DIRECTORY ${CATKIN_DEVEL_PREFIX}/include)

ExternalProject_Add(tk_spline_src
  GIT_REPOSITORY https://github.com/cwecht/spline.git
  CONFIGURE_COMMAND ""
  BUILD_COMMAND ""
  INSTALL_COMMAND rm -rf ${CATKIN_DEVEL_PREFIX}/include/tk_spline_catkin && mkdir ${CATKIN_DEVEL_PREFIX}/include/tk_spline_catkin && cp ../tk_spline_src/src/spline.h ${CATKIN_DEVEL_PREFIX}/include/tk_spline_catkin/
)

include_directories(${CATKIN_DEVEL_PREFIX}/include/)

cs_install()

cs_export()
