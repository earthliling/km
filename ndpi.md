nDPI
---
编译ndpi
- windows
  - 安装CYGWIN
    - 默认选择路径
    - 选择包，category-Devel：autoconf、autoconf2.5、automake、automake1.15、binutils、cmake、cygwin-devel、gcc-core、gcc-tools-epoch2-autoconf、gcc-tools-epoch2-automake、libtool、make、pkg-config、w32api-headers、w32api-runtime
    - 安装winpcap开发包：解压WpdPack_4_1_2.zip，将其lib目录下的libpacket.a和libwpcap.a放入到cygwin\lib目录下，64位环境中将x64下wpcap.lib同时拷贝到cygwin\lib目录下。拷贝libwpcap.a并重命名为libpcap.a，wpcap.lib重命名为pcap.lig；在cygwin/usr/include下创建pcap目录，并将WpdPack的Include下目录和文件均拷贝至该目录；确认c:/windows/system32目录下有pcaket.dll和wpcap.dll。
  - 编译nDPI
    - 打开CYGWIN终端，切换到nDIP-dev目录下
    - ./autogen.sh
    - 修改example目录下Makefile，在DEFAULT_INCLUDES中增加 -I/usr/include/pcap
    - make

wireshark插件
- 简介
  - nDpi为wireshark提供协议解析器实现内部协议的解码，nndpiReader应用提供了协议解析器和用于解释nDPI信息的wireshark插件。
- 安装
  - 拷贝ndpiReader应用（nDPI/example)至Extcap路径，路径参见菜单Wireshark-帮助-关于-文件夹。
  - 拷贝ndpi.lua引擎至~/.wireahrk/plugins(或者全局wireshark引擎目录)。
- 使用
  - wireshark启动后有一个名为“nDPI interface”的新extcap接口。选择该接口，指定一个接口名字（实时录包）或者一个pcap文件路径（从pcap文件中读取数据包）。在捕获数据包的过程中，ndpiReader引擎会通过增加一个包含nDPI信息的以太包尾，将信息传递给wireshark。lua引擎解释该信息并显示到wireshark界面上。
