cmake_minimum_required( VERSION 2.8 )
project( visualizeGeometry )

# 不适合Ubuntu20.04的环境
# set(CMAKE_CXX_FLAGS "-std=c++11") # 需要注释掉


# 添加Eigen头文件
include_directories( "/usr/include/eigen3" )

# 添加Pangolin依赖
find_package( Pangolin )
include_directories( ${Pangolin_INCLUDE_DIRS} )

add_executable( visualizeGeometry visualizeGeometry.cpp )
target_link_libraries( visualizeGeometry ${Pangolin_LIBRARIES} )
