报错:
error: ‘index_sequence’ is not a member of ‘std’
  200 |   struct HessianTupleType<std::index_sequence<Ints...>> {
解决方案
在工作目录下的 CMakeLists.txt 中
修改
set(CMAKE_CXX_FLAGS "-std=c++11 -Wall")
set(CMAKE_CXX_FLAGS_RELEASE  "-std=c++11 -O3 -fopenmp -pthread")
为
set(CMAKE_CXX_FLAGS "-std=c++14 -Wall")
set(CMAKE_CXX_FLAGS_RELEASE  "-std=c++14 -O3 -fopenmp -pthread")

报错:
test_triangulation.cpp:(.text+0x9e): undefined reference to `fmt::v9::detail::throw_format_error(char const*)'
解决方案
在工作目录下的 CMakeLists.txt 中
添加
find_package(FMT REQUIRED)
修改
set(THIRD_PARTY_LIBS
        ${OpenCV_LIBS}
        ${Sophus_LIBRARIES}
        ${Pangolin_LIBRARIES} GL GLU GLEW glut
        g2o_core g2o_stuff g2o_types_sba g2o_solver_csparse g2o_csparse_extension
        ${GTEST_BOTH_LIBRARIES}
        ${GLOG_LIBRARIES}
        ${GFLAGS_LIBRARIES}
        pthread
        ${CSPARSE_LIBRARY}
        )
为
set(THIRD_PARTY_LIBS
        ${OpenCV_LIBS}
        ${Sophus_LIBRARIES}
        ${Pangolin_LIBRARIES} GL GLU GLEW glut
        g2o_core g2o_stuff g2o_types_sba g2o_solver_csparse g2o_csparse_extension
        ${GTEST_BOTH_LIBRARIES}
        ${GLOG_LIBRARIES}
        ${GFLAGS_LIBRARIES}
        pthread
        ${CSPARSE_LIBRARY}
        fmt
        )

报错:
relocation R_X86_64_PC32 against symbol `stderr@@GLIBC_2.2.5' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: 最后的链结失败: bad value
解决方案
将 src 目录下的 CMakeLists 中
SHARED 
改为
STATIC

运行 test_triangulation 可执行程序
bin/test_triangulation

运行 run_kitti_stereo 可执行程序
注释 config/default.yaml 中
dataset_dir: /mnt/1A9286BD92869CBF/Dataset/Kitti/dataset/sequences/05
添加 dataset_dir: ./kitti00/dataset/sequences/00
终端输入
bin/run_kitti_stereo
