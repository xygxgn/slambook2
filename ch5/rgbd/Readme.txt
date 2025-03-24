报错1:
undefined reference to `cv::imread(cv::String const&, int)
解决方案
在 CMakeLists.txt 中加入
find_package(OpenCV REQUIRED)

报错2:
in function `fmt::v9::detail::error_handler::on_error(char const*)'
解决方案
在 CMakeLists.txt 中加入
find_package(FMT REQUIRED)
target_link_libraries(joinMap fmt::fmt)

