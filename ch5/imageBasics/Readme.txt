报错:
CMakeFiles/undistortImage.dir/undistortImage.o: in function `main':
undistortImage.cpp:(.text+0xdc): undefined reference to `cv::imread(cv::String const&, int)'
解决方案:
在 CMakeLists.txt 中加入
find_package(OpenCV REQUIRED) 

运行 imageBasic 可执行文件时需要终端输入
build/imageBasics ubuntu.png

问题:
Failed to load module "canberra-gtk-module"
解决方案
sudo apt install libcanberra-gtk-module
