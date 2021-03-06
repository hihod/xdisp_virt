﻿目录包含：
   xdisp_virt.exe程序，xdisp_virt.ini是它的配置文件，
   xdisp_server.exe程序，xdisp_server.ini是它的配置文件。
   dx_hook32.dll, dxhook64.dll是自动注入进每个界面进程挂钩DirectX和OpenGL绘图的动态库。
   配置文件有详细的每个字段说明。
   已经配置成默认设置，可以直接运行exe程序。
   xdisp_server.exe提供了服务器中转解决内网访问等问题, 同时能把多台被控制机器集中到一起，
   对于维护人员来说有一定好处

使用方法：
   把 xdisp_virt.exe， xdisp_virt.ini 复制到本地电脑某个目录下，
   直接运行 xdisp_virt.exe 按照提示使用即可。默认端口是11000，
   可以用浏览器在本地打开 http://localhost:11000 即可进行各种配置， 
   假设运行xdisp_virt的机器是192.168.1.1
   在其他PC，手机，平板等浏览器上打开 http://192.168.1.1:11000 即可远程控制。
   程序运行会生成xdisp_virt.db文件，这是保存各种配置参数和识别不同机器的唯一ID，勿复制此文件到不同的机器。

   把xdisp_server.exe和xdisp_server.ini复制到公网服务器上运行，默认端口32000，
   然后所有xdisp_virt设置连接到运行xdisp_server的服务器，
   假设xdisp_server的机器的公网IP是13.14.15.16
   则在其他PC，手机，平板等浏览器上打开 http://13.14.15.16:32000 就能看到所有连上来的xdisp_virt列表，
   从而可跨越域局域网远程控制。

   如果有必要，可以安装driver目录下的镜像驱动和hid_driver目录下的虚拟鼠标键盘驱动。

2019-6月更新：
1，优化RGB转YUV代码，使得转换时间更少，转换之后的图像质量更好。
2，修改HID虚拟鼠标键盘驱动在WIN10 1703,1709版本中蓝屏问题，
     同时修正在多显示器的环境中，HID虚拟绝对鼠标 在WIN7，WIN8，WIN10 1511 这些系统只识别主显示器的问题。
3，WIN10 1607 之后的系统，增加 Indirect Display驱动添加新的虚拟显示器。

2019-5月更新：
1，新增加了对 主程序 xdisp_virt.exe的xdisp_virt.ini 配置文件，
     可以通过网页方式进行配置，不用再像以前一样非得打开xdisp_virt.ini文件来做配置。

2，把 DirectX HOOK 动态库打包进 xdisp_virt.exe 程序中，
      在配置 启动DXHOOK的情况下，会自动从程序释放出 dx_hook32.dll和dx_hook64.dll动态库。

3,  进一步优化采集时间间隔，使用NtSetTimerResolution 把系统时间精度设置最大，从而确保Sleep精确睡眠，
     保证图像采集间隔尽量精确。尤其针对这对 60 FPS这样的高采集率。
     不过网页客户端本身的资源消耗挺大，可能无法承受高采集率，需使用性能良好的网页客户端或者使用原生客户端。

2019-4月新增功能：

1, 支持多显示器远程控制，可以把多个显示合并到一起或者单独显示。
     在xdisp_virt.ini配置文件中，添加
     multi_display_supported=2 即可支持多显示器远程控制。

2，在WIN7等平台，增加 DirectX HOOK 方式截取全屏独占程序。
     在xdisp_virt.ini配置文件中，添加
     fulld3d_supported=aero, true_full, uwp 
     即可支持DirectX Hook截取独占全屏，dx_hook32.dll和  dx_hook64.dll会被注入所有界面程序中。
     dll动态库是依靠系统自带的 rundll32.exe 来运行。
     目前测试的程序包括WIN7中的Windows Media Center，
     极品飞车17，极品飞车18, 极品飞车6（热力追踪2）， CS1.6， CrossFire，鬼泣2，古墓丽影8，
     生化危机5，正当防卫2，暗黑地牢，魔兽争霸3之冰封王座，英雄联盟
     由于游戏实在太多，无法都做测试，而且测试的时候基本上是不超过10分钟就退出，不清楚长久运行之后的稳定如何。
     如果使用中，影响到你的程序，或者出现程序莫名的崩溃。
     请屏蔽  fulld3d_supported 配置字段，并重启xdisp_virt程序或者重启系统。
     如果愿意，可以告诉我崩溃程序。
     
     详细信息，请查看：
     https://blog.csdn.net/fanxiushu/article/details/89363222
     https://blog.csdn.net/fanxiushu/article/details/89426367

3，增加虚拟的HID鼠标键盘驱动来代替原来的应用层鼠标键盘控制，
   安装hid_driver目录中对应的驱动，然后重启xdisp_virt程序，就会自动切换到虚拟鼠标键盘驱动控制。
   这是为某些全屏游戏无法通过应用层模拟鼠标键盘控制而增加的功能。

 fanxiushu 2017-2019

=======================================
The directory contains:
   The xdisp_virt.exe program, xdisp_virt.ini is its configuration file.
   The xdisp_server.exe program, xdisp_server.ini, is its configuration file.
   Dx_hook32.dll, dxhook64.dll is a dynamic library that automatically injects into each interface process hooking DirectX and OpenGL drawing.
   The configuration file has detailed descriptions of each field.
   Already configured as the default, you can run the exe program directly.
   Xdisp_server.exe provides server relay to solve problems such as intranet access, and can bring together multiple controlled machines.
   There are certain benefits for maintenance personnel

Instructions:
   Copy xdisp_virt.exe, xdisp_virt.ini to a directory on your local computer.
   Run xdisp_virt.exe directly as prompted. The default port is 11000.
   You can do various configurations by opening http://localhost:11000 locally with your browser.
   Suppose the machine running xdisp_virt is 192.168.1.1
   Open http://192.168.1.1:11000 on other PCs, mobile phones, tablets and other browsers to remotely control.
   The program will generate the xdisp_virt.db file, which is the unique ID for saving various configuration parameters and identifying different machines. Do not copy this file to a different machine.

   Copy xdisp_server.exe and xdisp_server.ini to the public network server, the default port is 32000.
   Then all xdisp_virt settings are connected to the server running xdisp_server.
   Suppose the public network IP of the xdisp_server machine is 13.14.15.16
   Then open http://13.14.15.16:32000 on other PCs, mobile phones, tablets and other browsers to see all the xdisp_virt lists that are connected.
   This allows remote control across domain LANs.

   If necessary, you can install the mirror driver in the driver directory and the virtual mouse and keyboard driver in the hid_driver directory.

fanxiushu 2017-2019


     
