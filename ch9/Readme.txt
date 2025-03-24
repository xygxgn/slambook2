报错:
‘integer_sequence’ is not a member of ‘std’
   64 | struct SumImpl<std::integer_sequence<T, N, Ns...>> {
解决方案
在 CMakeLists.txt 中
修改
set(CMAKE_CXX_FLAGS "-O3 -std=c++11")
为
set(CMAKE_CXX_FLAGS "-O3 -std=c++14")

添加
find_package(FMT REQUIRED)
target_link_libraries(bundle_adjustment_ceres fmt::fmt)
target_link_libraries(bundle_adjustment_g2o fmt::fmt)


运行 bundle_adjustment_ceres 可执行文件
build/bundle_adjustment_ceres problem-16-22106-pre.txt

运行 bundle_adjustment_g2o 可执行文件
先在 build 目录下输入指令 
sudo ldconfig
然后在工作目录下输入
build/bundle_adjustment_g2o problem-16-22106-pre.txt
