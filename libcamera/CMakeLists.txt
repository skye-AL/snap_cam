cmake_minimum_required(VERSION 2.8)

set(CMAKE_TOOLCHAIN_FILE ../toolchain/Toolchain-arm-linux-gnueabihf.cmake) #defining compiler etc...

project(cameraTest)

set(OpenCV_DIR /home/legatus/opencv-3.2.0/platforms/linux/build)
find_package(OpenCV REQUIRED)


#include_directories(
#  ${OpenCV_INCLUDE_DIRS}
#  ${CMAKE_CURRENT_SOURCE_DIR}/test
#  ${CMAKE_CURRENT_SOURCE_DIR}/inc
#  ${CMAKE_CURRENT_SOURCE_DIR}/src
#  )

include_directories(
        ${HEXAGON_ARM_SYSROOT}/usr/include
)

add_executable(cam_test test/camera_test.cpp)

LINK_DIRECTORIES(
  ${HEXAGON_ARM_SYSROOT}/usr/lib
  )

TARGET_LINK_LIBRARIES(cam_test camera turbojpeg ${OpenCV_LIBS})