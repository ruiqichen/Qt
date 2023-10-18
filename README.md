# Ubuntu Arm64 搭建Qt开发环境

目前无法在Ubuntu ARM64上使用Online安装包安装Qt开发环境，但是好在我们可以通过编译源码的方式安搭建Qt开发环境。笔者在搭建的过程中主要遇到了2个问题，第一个是QtCreator编译完成之后无法启动，第二个是QtCreator显示中文乱码。

# * 下载Qt source

  https://download.qt.io/archive/qt/6.5/6.5.3/single/

# * 安装编译Qt所需的依赖库

  https://wiki.qt.io/Building_Qt_5_from_Git（Ubuntu平台）

##### 注意事项：

libfontconfig-dev这个库一定要安装，否则会导致QtCreator显示中文乱码。

# * 编译和安装Qt

整体思路按照官网教程（https://doc.qt.io/qt-6/linux-building.html）一步步来，但是需要注意以下两点（尤其是配置参数，如果不添加 -feature-wayland-server参数，会导致QtCreator无法启动。）：

##### 注意事项：

###### 解压目录

如果解压到/tmp目录，重启之后该目录会自动删除,所以如果不能保证一次性编译和安装完成，需要解压的其他目录，笔者是解压到~/dev/目录下。

###### configue参数

步骤中，需要传入额外的参数，笔者所使用的参数如下：
    `cd ~`
    `mkdir dev`
    `cd dev`
    `tar -xvf ~/Downloads/qt-everywhere-src-6.5.3.tar.xz`
    `mkdir qt-build`
    `cd qt-build/`
    `../qt-everywhere-src-6.5.3/configure -feature-wayland-server -make examples -make tools -make libs`

# * 编译安装QtCreator

安装官方教程一步步来就可以了。https://wiki.qt.io/Building_Qt_Creator_from_Git_on_Ubuntu_22.04
