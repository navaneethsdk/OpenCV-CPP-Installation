# Installation Guide
## Window 10 - Visual Studio
Follow [this](https://towardsdatascience.com/install-and-configure-opencv-4-2-0-in-windows-10-vc-d132c52063a1) blog to set up OpenCV on Windows 10

## Ubuntu 18.04/20.04, Linux Mint 20 "Ulyana"
### 1. Update the System Package

```
$ sudo apt-get update && sudo apt-get upgrade
```
### 2. Install Required tools and packages

```
$ sudo apt-get install build-essential cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev
$ sudo apt-get install python3-numpy libtbb2 libtbb-dev
$ sudo add-apt-repository ppa:deadsnakes/ppa
```
Press "Enter" if prompted.
```
$ sudo apt-get install python3.5-dev
```
In case any error ("Couldn't find package") appears try executing it in a new terminal
```
$ sudo add-apt-repository "deb http://security.ubuntu.com/ubuntu xenial-security main"
$ sudo apt update
$ sudo apt install libjasper1 libjasper-dev
```
```
$ sudo apt-get install libjpeg-dev libpng-dev libtiff5-dev libdc1394-22-dev libeigen3-dev libtheora-dev libvorbis-dev libxvidcore-dev libx264-dev sphinx-common libtbb-dev yasm libfaac-dev libopencore-amrnb-dev libopencore-amrwb-dev libopenexr-dev libgstreamer-plugins-base1.0-dev libavutil-dev libavfilter-dev libavresample-dev
```
### 3. Download OpenCV Sources using git
We need to clone the OpenCV sources using “git” to build and install it. We will download the source in /opt/ directory.
Downloading, building and installation process requires root permission. Execute the commands to proceed further.
```
$ sudo -s
$ cd /opt
$ git clone https://github.com/Itseez/opencv.git
$ git clone https://github.com/Itseez/opencv_contrib.git
```
### 4. Build & Install OpenCV
```
$ cd opencv
$ mkdir release
$ cd release
```
```
$ cmake -D BUILD_TIFF=ON -D WITH_CUDA=OFF -D ENABLE_AVX=OFF -D WITH_OPENGL=OFF -D WITH_OPENCL=OFF -D WITH_IPP=OFF -D WITH_TBB=ON -D BUILD_TBB=ON -D WITH_EIGEN=OFF -D WITH_V4L=OFF -D WITH_VTK=OFF -D BUILD_TESTS=OFF -D BUILD_PERF_TESTS=OFF -D OPENCV_GENERATE_PKGCONFIG=ON -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local -D OPENCV_EXTRA_MODULES_PATH=/opt/opencv_contrib/modules /opt/opencv/
```
```	
$ make -j4
```
It will take some time to build.
```
$ make install
```
```
$ ldconfig
$ exit
$ cd ~
```
### 5. Check OpenCV version installed
```
$ pkg-config --modversion opencv
```
If you encounter error like “pakage opencv not found” then follow the next step otherwise move to step 6.
```
$ apt-file search opencv.pc
$ ls /usr/local/lib/pkgconfig/
$ sudo cp /usr/local/lib/pkgconfig/opencv4.pc  /usr/lib/x86_64-linux-gnu/pkgconfig/opencv.pc
$ pkg-config --modversion opencv
```
### 6. Compile & Run a Test Program
```
$ git clone https://github.com/navaneethsdk/OpenCV-CPP-Installation.git
$ cd OpenCV-CPP-Installation
$ g++ test.cpp -o testoutput -std=c++11 `pkg-config --cflags --libs opencv`
$ ./testoutput
```
If the image appears then OpenCV has been successfully set up

![out](./OpenCV_Logo.png)

Happy learning !!! ;)


### References
1. http://techawarey.com/programming/install-opencv-c-c-in-ubuntu-18-04-lts-step-by-step-guide/
2. https://towardsdatascience.com/install-and-configure-opencv-4-2-0-in-windows-10-vc-d132c52063a1
3. https://askubuntu.com/questions/1052322/python3-5-dev-in-ubuntu-18-04


