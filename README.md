
## 前情提要

大概就是用官方的release链接的时候不能正常链接，似乎是因为msvc编译的不能和mingw兼容，所以自己编译了一个mingw的版本，并且把一些常用的库都编译好了，方便使用。  
编译过程参考：[OpenCV使用CMake和MinGW-w64的编译安装 | HuiHut](https://blog.huihut.com/2018/07/31/CompiledOpenCVWithMinGW64)  
OpenCV版本：4.12.0
mingw版本：[x86_64-13.2.0-release-posix-seh-ucrt-rt_v11-rev0](https://github.com/niXman/mingw-builds-binaries/releases/download/13.2.0-rt_v11-rev0/x86_64-13.2.0-release-posix-seh-ucrt-rt_v11-rev0.7z)  
编译环境：Windows11_22H2,Cmake_3.29.0,mingw-w64_13.2.0,OpenCV_4.12.0

## OpneCV_mingw_built  

本仓库存放了编译好的OpenCV库，包括头文件和lib文件，可以直接使用。  
使用OpenCV这种库时建议自己从源码编译（尽管可能有些费时），这样才能确保没有兼容性问题，并且自己编译也能进行个性化需求与优化。

## 使用方法

CMakeLists.txt

```cmake
set(OpenCV_DIR "D:/OpenCV_mingw_built")
find_package(OpenCV REQUIRED)
include_directories(${OpenCV_INCLUDE_DIRS})
link_directories(${OpenCV_LIBRARY_DIRS})
target_link_libraries(${PROJECT_NAME} ${OpenCV_LIBS})
```
main.cpp

```cpp
#include <opencv2/opencv.hpp>
#include <iostream>

using namespace std;
using namespace cv;

int main(int argc, char** argv)
{
    Mat img = imread("D:/test.jpg");
    imshow("test", img);
    waitKey(0);
    return 0;
}
```
