# Visual Studio Code #

## 简介 #
一个运行于 Mac OS X、Windows和 Linux 之上的，针对于编写现代 Web 和云应用的跨平台源代码编辑器。

## 使用方法 #

- 常用插件
    - C/C++
    - cpp-symbols
    - C++ Intellisense
        - 依赖GNU GLOBAL
    - Markdown All in One
    - Python

- 离线使用

## 参考 #

- GNU GLOBAL

源代码标签工具，可以跨环境使用，例如Emacs、Vi等等。

可以用于定位函数、宏定义、结构体、类等不同种类对象，跳转方便。

原生支持C, C++, Yacc, Java, PHP4 and assembly，通过 Pygments + Universal Ctags plug-in 扩展支持25种语言，包括Python,Java等。

下载地址：http://adoxa.altervista.org/global/，解压，并添加环境变量PATH到GNU Global目录的/bin目录下，这个目录下包含gtag.exe等二进制文件。 

选择资源管理器中的目录，右键“在命令提示符中”打开，执行gtags，在目录下生成GTAGS, GRTAGS, and GPATH 三个文件。源代码更新后，需要执行该命令。



