# OpenCV-for-C-MacOS
## Install OpenCV

Setting up OpenCV for C++ on MacOS

```bash
echo "Init opencv for macos..."
echo "Cloning repo..."
mkdir opencv
cd opencv
git clone https://github.com/opencv/opencv.git
cd opencv
git checkout tags/4.2.0
cd ..
git clone https://github.com/opencv/
cd opencv_contrib 
git checkout tags/4.2.0
cd ..

echo "Installing..."
mkdir install build_opencv
cd build_opencv
cmake -D CMAKE_BUILD_TYPE=RELEASE \
      -D CMAKE_INSTALL_PREFIX=../install \
      -D INSTALL_C_EXAMPLES=ON \
      -D OPENCV_EXTRA_MODULES_PATH=../opencv_contrib/modules \
      -D BUILD_EXAMPLES=ON ../opencv

# this step takes very long time
export CPUS=$(sysctl -n hw.physicalcpu)
make -j $CPUS
make install
```

## Set up CMakeFile for project C++
Sample cmake file:
```cmake
cmake_minimum_required(VERSION "3.17")

# name of project
project(lab1)

# set OpenCV_DIR variable equal to the path to the cmake
# files within the previously installed opencv
set(OpenCV_DIR /Users/lamnguyen5464/dev/onClass/CV/opencv/install/lib/cmake/opencv4)
 
set(CMAKE_CXX_STANDARD 14)
find_package( OpenCV REQUIRED )
include_directories( ${OpenCV_INCLUDE_DIRS} )

# specify the executable target to be built
add_executable(lab1 main.cpp)

target_link_libraries(lab1 ${OpenCV_LIBS} )

```

## Reference
https://thecodinginterface.com/blog/opencv-cpp-vscode/
