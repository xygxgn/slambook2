报错:
dense_mapping.cpp:(.text+0x31): undefined reference to `fmt::v9::vprint(fmt::v9::basic_string_view<char>, fmt::v9::basic_format_args<fmt::v9::basic_format_context<fmt::v9::appender, char> >)'
解决方案
在 CMakeLists.txt 中
修改
set(CMAKE_CXX_FLAGS "-std=c++11 -march=native -O3")
为
set(CMAKE_CXX_FLAGS "-std=c++14 -march=native -O3")

警告:
In function ‘bool update(const cv::Mat&, const cv::Mat&, const SE3d&, cv::Mat&, cv::Mat&)’:
/home/pulsar/slambook2/ch12/dense_mono/dense_mapping.cpp:289:1: warning: no return statement in function returning non-void [-Wreturn-type]
解决方案
在bool update函数体最后（290行附近）添加 return true;(不修改会出现段错误)


在 CMakeLists.txt 中
添加
find_package(FMT REQUIRED)
target_link_libraries(dense_mapping fmt::fmt)

下载数据集
http://rpg.ifi.uzh.ch/datasets/remode_test_data.zip
运行 dense_mapping 可执行程序
build/dense_mapping ./remode_test_data/test_data