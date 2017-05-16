########################################
cross compiling camera_test on snap_cam
########################################

########################################
opencv
########################################

install opencv, following:
http://docs.opencv.org/2.4/doc/tutorials/introduction/crosscompilation/arm_crosscompile_with_cmake.html

cd ~/opencv-3.2.0/platforms/linux

mkdir -p build

cd build

cmake -DCMAKE_TOOLCHAIN_FILE=/home/legatus/opencv-3.2.0/platforms/linux/arm-gnueabi.toolchain.cmake -DCMAKE_CXX_COMPILER=/home/legatus/Qualcomm/Hexagon_SDK/3.0/gcc-linaro-4.9-2014.11-x86_64_arm-linux-gnueabihf_linux/bin/arm-linux-gnueabihf-g++ -DCMAKE_C_COMPILER=/home/legatus/Qualcomm/Hexagon_SDK/3.0/gcc-linaro-4.9-2014.11-x86_64_arm-linux-gnueabihf_linux/bin/arm-linux-gnueabihf-gcc-4.9.3 -DARM_LINUX_SYSROOT=/home/legatus/Qualcomm/Hexagon_SDK/3.0/gcc-linaro-4.9-2014.11-x86_64_arm-linux-gnueabihf_linux ../../..

The lib files in your-opencv-build-directory/install/lib should be copied to ~/lib/ of the snapdragon board

adb push your-opencv-build-directory/install/lib/. /lib

########################################
adapt CMakeLists.txt
########################################
adapt set(OpenCV_DIR /home/legatus/opencv-3.2.0/platforms/linux/build)
to set(OpenCV_DIR to-your-open-cv-build-directory)


########################################
compile
########################################

in your-snap_cam-directory/libcamera

make (fails undefined refs)

make