报错:
/usr/local/include/sigslot/signal.hpp:109:79: error: ‘decay_t’ is not a member of ‘std’; did you mean ‘decay’?
解决方案
在 CMakeLists.txt 中
修改
set(CMAKE_CXX_FLAGS "-std=c++11 ${SSE_FLAGS} -g -O3 -march=native")
为
set(CMAKE_CXX_FLAGS "-std=c++14 ${SSE_FLAGS} -g -O3 -march=native")

修改
find_package(OpenCV 4 REQUIRED)
为
find_package(OpenCV 3 REQUIRED)

添加
find_package(FMT REQUIRED)
target_link_libraries(optical_flow fmt::fmt)
target_link_libraries(direct_method fmt::fmt)