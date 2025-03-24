报错:
undefined reference to `cv::imread(cv::String const&, int)
解决方案
在 CMakeLists.txt 中加入
find_package(OpenCV REQUIRED)
