使用方法：
把 xdisp_virt.exe， xdisp_virt.ini， dx_hook32.dll, dx_hook64.dll复制到本地电脑某个目录下，
直接运行 xdisp_virt.exe 按照提示使用即可。默认端口是11000，
可以用浏览器在本地打开 http://localhost:11000 即可进行各种配置， 
假设运行xdisp_virt的机器是192.168.1.1
在别的机器或者手机浏览器上打开 http://192.168.1.1:11000 即可远程控制。

把xdisp_server.exe和xdisp_server.ini复制到公网服务器上运行，
然后所有xdisp_virt设置连接到运行xdisp_server的服务器，即可跨域局域网远程控制。

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
     因为目前程序中使用的是应用层的鼠标键盘模拟，因此游戏中的鼠标键盘无法远程控制。
     基本上需要提供驱动模拟才能彻底解决这个问题，以后有时间会考虑增加。
     详细信息，请查看：
     https://blog.csdn.net/fanxiushu/article/details/89363222
     https://blog.csdn.net/fanxiushu/article/details/89426367

 fanxiushu 2019-04-21

     