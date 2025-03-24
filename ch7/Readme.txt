报错1:
/usr/local/include/g2o/core/base_fixed_sized_edge.h:200:32: error: ‘index_sequence’ is not a member of ‘std’
  200 |   struct HessianTupleType<std::index_sequence<Ints...>> {
      |                                ^~~~~~~~~~~~~~
/usr/local/include/g2o/core/base_fixed_sized_edge.h:200:32: error: ‘index_sequence’ is not a member of ‘std’
/usr/local/include/g2o/core/base_fixed_sized_edge.h:200:51: error: expected parameter pack before ‘...’
  200 |   struct HessianTupleType<std::index_sequence<Ints...>> {
      |                                                   ^~~
/usr/local/include/g2o/core/base_fixed_sized_edge.h:200:51: error: template argument 1 is invalid
/usr/local/include/g2o/core/base_fixed_sized_edge.h:200:54: error: expected unqualified-id before ‘>’ token
  200 |   struct HessianTupleType<std::index_sequence<Ints...>> {
  
解决方案
在 CMakeLists.txt 中
修改
set(CMAKE_CXX_FLAGS "-std=c++11 -O2 ${SSE_FLAGS} -msse4")
为
set(CMAKE_CXX_FLAGS "-std=c++14 -O2 ${SSE_FLAGS} -msse4")
这是因为 ubuntu 20.04 默认下载 c++ 编译器为 c++14

在 CMakeLists.txt 中
添加
find_package(FMT REQUIRED)
target_link_libraries(orb_cv fmt::fmt)
target_link_libraries(orb_self fmt::fmt)
target_link_libraries(pose_estimation_2d2d fmt::fmt)
target_link_libraries(triangulation fmt::fmt)
target_link_libraries(pose_estimation_3d2d fmt::fmt)
target_link_libraries(pose_estimation_3d3d fmt::fmt)


运行 orb_cv 可执行程序指令
build/orb_cv 1.png 2.png

运行 pose_estimation_2d2d 可执行程序指令
build/pose_estimation_2d2d 1.png 2.png

运行 pose_estimation_3d2d 可执行程序指令
build/pose_estimation_3d2d 1.png 2.png 1_depth.png 2_depth.png

运行 pose_estimation_3d3d 可执行程序指令
build/pose_estimation_3d3d 1.png 2.png 1_depth.png 2_depth.png

运行 triangulation 可执行程序指令
build/triangulation 1.png 2.png