报错:
error: ‘index_sequence’ is not a member of ‘std’
  200 |   struct HessianTupleType<std::index_sequence<Ints...>> {
解决方案
在 CMakeLists.txt 中
修改
set(CMAKE_CXX_FLAGS "-std=c++11 -O2")
为
set(CMAKE_CXX_FLAGS "-std=c++14 -O2")

添加
find_package(FMT REQUIRED)
target_link_libraries(pose_graph_g2o_SE3 fmt::fmt)
target_link_libraries(pose_graph_g2o_lie fmt::fmt)


运行 pose_graph_g2o_SE3 可执行文件
build/pose_graph_g2o_SE3 sphere.g2o

运行 pose_graph_g2o_lie 可执行文件
在 pose_graph_g2o_lie_algebra 中第63行加入 return true;
重新编译并运行
cd build
make
build/pose_graph_g2o_lie sphere.g2o
