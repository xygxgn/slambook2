问题:
配置Sophous出现“/usr/local/include/sophus/common.hpp:36:10: fatal error: fmt/core.h: 没有那个文件或目录”。
原因:
之所以出现该问题是因为原书使用Sophous库时，仅仅需要Eigen一个依赖，而如今版本的Sophous库还需要fmt依赖。

解决方案:
git clone https://github.com/fmtlib/fmt.git
cd fmt
mkdir build
cd build
cmake ..
make
sudo make install
