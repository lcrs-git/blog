### 在树莓派 3 上运行 3CX-IP PBX
![raspberryboard](https://git.poker/lcrs-git/img/blob/master/20220722/raspberryboard.26jwhogofvpc.jpg?raw=true)

3CX 在 V16 版本以后，就可以运行在树莓派的最新硬件版本，3B+ 上了。最新版本的 3CX 可以在 Raspbian Stretch 上安装， Raspbian Stretch 这个 Debian Linux 的分支是基于树莓派的 ARM 架构的。对于高级用户而言，他们可以通过 3CX 网页管理控制台或 Linux 命令行（CLI）更好的管理系统。

在树莓派上安装需要下列条件：

32G 以上的 Class10 Micro SDHC 卡
树莓派 2.5A 的 Micro USB 电源

### 为树莓派准备 SD 卡
SD 卡就是树莓派的硬盘，所以我们应该尽可能选速度快的 SD 卡，这样才能保证体验。

树莓派在 SD 卡中有操作系统的情况下才会工作，所以我们需要提前在 SD 中安装系统，可按照以下步骤执行：

1、在下面网站中下载 Raspbian Stretch Lite 镜像：Raspbian
2、解压下载文件后得到一个镜像文件（.img 文件）
3、使用 Etcher 或者 Win32 Disk Imager 烧录 Raspbian Stretch Lite 镜像
   烧录完系统可能会提示需要格式化，这里千万不能格式化
   树莓派默认是关闭 SSH 的，我们需要在 boot 根目录下新建一个 SSH 的文件以开启 SSH
   ![etcher](https://git.poker/lcrs-git/img/blob/master/20220722/etcher.7ijs36kgafk0.jpg?raw=true)
   
4、把烧录完的 SD 卡插到树莓派的插槽中，通电并启动树莓派
5、在路由器中获取树莓派的 IP 地址，也可以通过 IP Scanner 之类的软件扫描网段内的 IP
6、通过 SSH 访问树莓派的 IP。默认的用户名和密码分别是：pi 和 raspberry
7、输入 passwd 命令可以更改 pi 用户的密码，系统会要求输入一次旧密码和两次新密码

### 设置主机名
默认的主机名为 raspberry，如果想修改这个可以按照下列步骤：

1、运行树莓派配置命令：

`sudo raspi-config`
2、选择 “2. Network Options”并按下回车键
![networkoptions](https://git.poker/lcrs-git/img/blob/master/20220722/networkoptions.3ffeg9xitfk0.jpg?raw=true)

3、选择 “N1 Hostname”，按下回车，并在弹出警告后选择 “OK”
4、输入 Pi 用户的主机名，主机名由数字字母和 “-“组成
5、选择 <Finish> 并选择 <Yes> 重启树莓派
6、当树莓派重启完后，再使用 pi 用户登录就可以看到主机名变成我们设置的名称了
