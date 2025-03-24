find_package(Sophus REQUIRED)
include_directories(${Sophus_INCLUDE_DIRS})

# 搜寻 OpenCV 库文件
find_package(OpenCV REQUIRED)
# 搜寻 FMT 库文件
find_package(FMT REQUIRED)


find_package(Pangolin REQUIRED)

add_executable(joinMap joinMap.cpp)

target_link_libraries(joinMap ${OpenCV_LIBS} ${Pangolin_LIBRARIES})
# 链接 fmt 库文件
target_link_libraries(joinMap fmt::fmt)