# OpenCV-for-C-MacOS
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

## Reference
https://thecodinginterface.com/blog/opencv-cpp-vscode/
