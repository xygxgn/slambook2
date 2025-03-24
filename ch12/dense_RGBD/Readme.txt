报错:
error: ‘enable_if_t’ in namespace ‘std’ does not name a template type; did you mean ‘enable_if’?
  813 |     using HasNoXY = std::enable_if_t<!has_xy_v<PointT>, bool>;
解决方案
在 CMakeLists.txt 中
修改
set(CMAKE_CXX_FLAGS "-std=c++11 -O2")
为
set(CMAKE_CXX_FLAGS "-std=c++14 -O2")
安装依赖
sudo apt-get install libpcl-dev pcl-tools


运行 pointcloud_mapping 可执行文件
build/pointcloud_mapping
终端输入
pcl_viewer map.pcd

运行 surfel_mapping 可执行文件
终端输入
build/surfel_mapping map.pcd


运行 octomap_mapping 可执行文件
安装依赖项
sudo apt-get install liboctomap-dev octovis
build/octomap_mapping
pcl_viewer map.pcd