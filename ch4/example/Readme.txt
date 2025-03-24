Sophus库报错 fatal error:fmt/core.h: No such file or directory 
解决方案
在 CMakeLists.txt 中加入
find_package(Sophus REQUIRED)
target_link_libraries(trajectoryError Sophus::Sophus)

此外：
将
string groundtruth_file = "./example/groundtruth.txt";
string estimated_file = "./example/estimated.txt";
更改为
string groundtruth_file = "./groundtruth.txt";
string estimated_file = "./estimated.txt";
