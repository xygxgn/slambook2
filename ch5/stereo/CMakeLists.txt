find_package(Pangolin REQUIRED)
# 搜寻 OpenCV 库文件
find_package(OpenCV REQUIRED)

add_executable(stereoVision stereoVision.cpp)
target_link_libraries(stereoVision ${OpenCV_LIBS} ${Pangolin_LIBRARIES})