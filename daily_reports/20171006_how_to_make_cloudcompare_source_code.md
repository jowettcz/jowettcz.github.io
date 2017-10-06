## MAC环境下CloudCompare源代码编译

### 官方文档：
请先看[官方编译文档](https://github.com/CloudCompare/CloudCompare/blob/master/BUILD.md)，有问题的话可参阅本文

### 准备步骤：
1. 安装cmake:
> 步骤见[cmake官网](https://cmake.org/download/)
2. 安装Qt:
> 可安装[Open Source版本](https://info.qt.io/download-qt-for-application-development)
3. 安装Boost库
> 见[官网](http://www.boost.org/)
4. 下载最新的CloudCompare的Trunk分支
> ```git clone --recursive https://github.com/cloudcompare/trunk.git```

### 编译：
1. 设置cmake的环境变量，

- QT5_ROOT_PATH={YourQtInstallPath}/Qt/5.X.X/clang_64/bin
- CMAKE_MODULE_PATH={YourQtInstallPath}/Qt/5.X.X/clang_64/lib/cmake
- Qt5Concurrent_DIR={YourQtInstallPath}／Qt/5.9.1/clang_64/lib/cmake/Qt5Concurrent
- Qt5Widgets_DIR={YourQtInstallPath}／Qt/5.9.1/clang_64/lib/cmake/Qt5Widgets
- Qt5Core_DIR={YourQtInstallPath}／Qt/5.9.1/clang_64/lib/cmake/Qt5Core
- Qt5Gui_DIR={YourQtInstallPath}／Qt/5.9.1/clang_64/lib/cmake/Qt5Gui
- Qt5PrintSupport_DIR={YourQtInstallPath}／Qt/5.9.1/clang_64/lib/cmake/Qt5PrintSupport
- Qt5Concurrent_DIR={YourQtInstallPath}／Qt/5.9.1/clang_64/lib/cmake/Qt5Concurrent
- Qt5OpenGL_DIR={YourQtInstallPath}／Qt/5.9.1/clang_64/lib/cmake/Qt5OpenGL
- Qt5OpenGLExtensions_DIR={YourQtInstallPath}／Qt/5.9.1/clang_64/lib/cmake/Qt5OpenGLExtensions


使用cmake来编译cc的各个模块，请准备步骤中的各软件库可调用

2. make
- sudo cp /usr/local/Cellar/boost/1.64.0_1/lib/libboost_thread-mt.dylib /CloudCompare/CloudCompare.app/Contents/Frameworks/
- sudo cp /usr/local/Cellar/boost/1.64.0_1/lib/libboost_thread-mt.dylib /CloudCompare/CloudCompare.app/Contents/Frameworks/

make

### 安装
sudo make install
- 默认安装在根目录下，见/CloudCompare/CloudCompare.app/Contents/MacOS/CloudCompare

搞定！

