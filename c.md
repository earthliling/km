#language feature
## C99
### Flexible array member
Flexible array member 是结构体的一个成员，类型是没有指定维度的数组，并且应该是结构体的最后一个成员。
```c
struct vectord {
  size_t len;
  double arr[];
};
```
在使用Flexible array member时，应对数组的实际大小进行约定。在上面的例子中，vectord成员arr大小由成员len确定。
在以前的C语言规范中，一般声明大小为0的数组来代替Flexible array member。
**C语言并不支持Flexible array member。**

## 编译器
### GCC
- 简介
  - GCC是GNU公社的一个项目。是一个用于编程开发的自由编译器。最初，GCC只是一个C语言编译器，他是GNU C Compiler 的英文缩写。随着众多自由开发者的加入和GCC自身的发展，如今的GCC以经是一个包含众多语言的编译器了。GCC也由原来的GNU C Compiler变为GNU Compiler Collection。
- windows下GCC
  - 在Windows下比较流行的GCC移植版主要有：MinGW、Cygwin。MinGW 的主要方向是让GCC的Windows移植版能使用Win32API来编程。Cygwin 的目标是能让Unix-like下的程序代码在Windows下直接被编译。
  - MinGW(Minimalistic GNU for Windows)，建立在GCC和binutils 项目上的编译器系统，MinGW几乎支持所有的Win32API，这也是MinGW的特色之一，所连接的程序，不需要任何第三方库就可以运行了。MinGW为Windows环境提供一套符合GNU的GNU工作环境。
  - Cygwin是让Windows拥有Unix-like环境的软件，对于开发者，Cygwin是一个开发环境。而对于用户来说Cygwin是一个运行环境。Cygwin唯一和MinGW最大的区别在于，使用Cygwin可以在Windows下调用Unix-like的系统函数，即使用Unix-like系统的函数和思想。
  - Cygwin是用一个dll模拟linux环境来“欺骗”应用程序，好像自己运行在linux环境下；而mingw是在编译时提供linux到windows必要代码的“翻译”转换，用到的还是windows运行时库。
  - 在cygwin下编译出来的程序需要cygwin.dll才能在windows下运行，源码拿到linux环境下重新编译就可以在linux下跑起来；mingw环境下编译出来的程序，只能在windows下跑，源码在linux环境下编译多半通不过。
