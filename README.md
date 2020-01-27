# Arch的学习使用心得

### 废话


&emsp;&emsp;以前看一些大佬用Vim感觉好爽的样子，劈里啪啦的命令行上输一大堆，就感觉Linux好有趣的样子，于是就试着在虚拟机上装一些Linux，Centos Kali Arch manjaro Ubuntu啊啥的感觉确实很有趣。
<br/>

输个sudo apt-get install XXX或sudo pacman -S XXX 看着一堆小进度条在窗口上滑啊滑感觉特别爽。
于是就想着装个实体机玩玩，但是家里没有多余的电脑，于是就想装个双系统。
<br/>

中间也遇到了特别多的错误，经过大量的查资料看wiki问大佬，解决了很多问题。**其中一个还让我卡了五天!难受死**所以说在这里把它给总结出来，以后再有问题会比较容易一些，也会有个参照。

---

### 目录
1. [前言](#前言)
    1. [参考文献](#参考文献)
2. [安装篇](#安装篇)
    1. [下载系统镜像和磁盘刻录工具](#下载系统镜像和磁盘刻录工具)
    2. [制作系统安装介质](#制作系统安装介质)
    3. [查看主板热键](#查看主板热键)
    4. [将磁盘分区](#将磁盘分区)
    5. [格式化分区](#格式化分区)
3. [配置篇](#配置篇)
    1. [设置](#设置篇)
    2. [虚拟机无法更改分辨率解决方案](#虚拟机无法更改分辨率解决方案)
    3. [中文字体设置](#中文字体设置)
    4. [时区设置](#时区设置)
    5. [系统本地化设置](#系统本地化设置)
    6. [桌面环境安装](#桌面环境安装)
    7. [vmware&nbsp;tools快速安装](#vmware&nbsp;tools快速安装)
4. [疑难解答篇](#疑难解答篇)
    1. [U盘启动盘如何恢复原样](#U盘启动盘如何恢复原样)
    2. [git出现443解决方案](#git出现443解决方案)
    3. [开机显示can't access tty job control turned off，无法进入图形化界面](#开机显示can't&nbsp;access&nbsp;tty&nbsp;job&nbsp;control&nbsp;turned&nbsp;off，无法进入图形化界面)
    4. [换源不生效，pacman -Syy速度小于4K/s](#换源不生效，pacman&nbsp;-Syy速度小于4K/s)
5. [使用方法篇](#使用方法篇)
    1. [pacman删除软件包](#pacman删除软件包)
    2. [AUR的使用](#AUR的使用)
    3. [SSR须知](#SSR须知)
    4. [git须知](#git须知)

6. [美化篇](#美化篇)
    1. [vim-Plug安装](#vim-Plug安装)

7. [插件推荐篇](#插件推荐篇)
    1. [Markdown All in One](#Markdown&nbsp;All&nbsp;in&nbsp;One)

---
        
### 前言：
##### &emsp;&emsp;这里讲一下哦，这篇文章是我使用Arch的经验总结，也是分享给还不会使用Arch的小白的，应该是比较详细的，比较适合什么都不懂的真小白，配有图文。但可能有一些错误，希望懂的大佬能够指出，谢谢！
#### 参考文献 : 
   1. https://wenku.baidu.com/view/37c420a75fbfc77da269b18e.html
   2. https://www.cnblogs.com/yuanchao-blog/p/11730296.html
   3. https://www.cf673.com/post/144.html
   4. https://www.jianshu.com/p/a2d2f284fc0a

## 安装篇

>你需要的工具：一个4G或4G以上的U盘，一台能联网的电脑。

如果没有U盘可以去买一个，不是怎么贵，几包方便面的价钱。(废话，逃...)

#### 下载系统镜像和磁盘刻录工具 

首先，你得去[Archlinux](http://blog.leanote.com/freewalk)官网下载页面下载。如下图：
![1nOaan.md.png](https://s2.ax1x.com/2020/01/27/1nOaan.md.png)

那里有一个**BitTorrent Download (recommended)**

可以用磁力和种子下载，打开你的迅雷，咱随便挑一个下载。

在下载过程中，咱要下个磁盘刻录工具，这里我使用的[USBWriter](https://sourceforge.net/projects/usbwriter/)，当然你也可以用[rufus](https://rufus-usb.cn.uptodown.com/windows)，看个人喜好。然后把它下下来。打开它，大概是这个样子，比较简陋，但五脏俱全，也很好用，我喜欢。它上面英文差不多就是红字那个的意思，我给它翻译的一遍。

![1njIDe.png](https://s2.ax1x.com/2020/01/27/1njIDe.png)

在你的Archlinux下载完毕后，你会发现有一个iso镜像文件，大概是这个样子，上头命名的格式为 **名称-发布时间-支持位数.文件后缀**(下面那个文件是我之前下的manjaro，不要在意)

![1nXezT.png](https://s2.ax1x.com/2020/01/27/1nXezT.png)
#### 制作系统安装介质
这时候你要 插入♂ 你的U盘，不要太用力，主机和U盘会很爽♂的。然后你需要打开你的USBWriter(咱刚下的内个，我用USBWriter来演示)或者rufus。

再看着这个图片，首先我们要点那个浏览，然后选中你刚才下载的iso镜像文件。然后再点一下目标设备那个框框最右边的小玩意，然后下面应该能看到你的U盘。

选中它，如果没有出现，那你再检查检查有没有插好电脑有没有识别，点一下刷新。

完事儿之后，你再点一下那个写入，等它蹦出来个框提示你写入完毕后，你的系统U盘算是做好了。

做好之后，你可能发现你的电脑识别不出你的U盘了，你也不要惊慌，虽然我也不知道啥回事儿。。。但没啥大问题

![1njIDe.png](https://s2.ax1x.com/2020/01/27/1njIDe.png)
#### 查看主板热键
然后你要明白一个东西。你的主板进入系统U盘的方式，你必须要知道你的主板是什么牌子的，查看方法：使用组合键win + r(win就是你键盘下面有着windows logo的玩意儿)输入dxdiag，确定。

然后就会蹦出来DirectX诊断工具，在DirectX诊断工具页面中，就可以看到主板型号，主板BIOS版本信息就是主板相关信息。

![1nxsYR.png](https://s2.ax1x.com/2020/01/27/1nxsYR.png)

知道了主板型号后再看下面这图，找到你主板进入系统U的方式，我的主板是微星的，所以在重启以后要狂撸F11键，进入选择菜单。

![1nvHLF.png](https://s2.ax1x.com/2020/01/27/1nvHLF.png)

知道以后，再重启，重启时狂按你主板的那个热键。

不一会你会看见一个选择菜单，我的是这样的，不知道你的是个啥子样，选择你的U盘，我的U盘是金士顿的4G，所以我选择底下的那个

![1nzFXT.jpg](https://s2.ax1x.com/2020/01/27/1nzFXT.jpg)

完事儿以后，你会看到Archlinux的安装界面，选第一个(键盘Enter选择，小键盘上下移动)。选完之后它会跳出来一堆一堆的字儿，我感觉看着挺爽。

![1nz3nO.png](https://s2.ax1x.com/2020/01/27/1nz3nO.png)

稀里哗啦的字儿跳完之后，你会来到这样一个界面，这叫liveCD。

![1nzQc6.png](https://s2.ax1x.com/2020/01/27/1nzQc6.png)

输入fdisk -l检查磁盘状态，你应该可以在上面找到你的磁盘。我的是这样的，讲个小秘密：我是用虚拟机演示的，但是和你的实体机应该差不多。

![1nzljK.png](https://s2.ax1x.com/2020/01/27/1nzljK.png)

##### 将磁盘分区
接下来的操作就是让你分几个区
我们这里要分一个EFI system
一个swap
一个系统盘

>EFI system : EFI是引导分区，它在你磁盘的最前面，每次开机最先被磁头读写到。我把Archlinux比作景点，引导分区比作导游，你想要进入景点必须要有导游带着你啊对吧。在你电脑开机以后，你的导游(引导分区)带你进景点(Archlinux)。如果没有导游你就无法进入景区，那你就开不了机咯，简单易懂。


>Swap : Swap分区（即交换区）在系统的物理内存不够用的时候，把硬盘空间中的一部分空间释放出来，以供当前运行的程序使用。那些被释放的空间可能来自一些很长时间没有什么操作的程序，这些被释放的空间被临时保存到Swap分区中，等到那些程序要运行时，再从Swap分区中恢复保存的数据到内存中。
转自:https://www.jianshu.com/p/a2d2f284fc0a； 作者：jnxc1888 来源：简述

>系统盘：那系统盘当然是存放你使用的软件和系统的咯

输入cfdisk 选择你的磁盘 再选择 gpt 进行分区(cfdisk是一个图形化的分区工具，对新手友好，如果你只有一个硬盘，就直接输入cfdisk)


如果你有多个磁盘但不知道你的磁盘是哪个。

可以分为两种情况：
1. 你准备装双系统，有两个及以上的磁盘。
2. 你刚买的电脑，电脑还没有系统，磁盘是空的。


>如果你是情况一那你可以输入：

>ls /dev&emsp;&emsp;#我这里解释一下命令ls是查看后面那个文件下的文件的，在linux中常用/dev (device) 来存放设备文件，比如磁盘 打印机啥的，所以ls /dev的意思就是查看用于存放设备文件的目录下的所有目录

进行查看，像那些sda,sdb,sdc的就是你的磁盘了，你可以再输入"cfdisk sda"或"cfdisk sdb"...以此类推。

一个一个地来试，哪个盘有上有写Freespace，那么那个区就是你之前再windows上压缩的区。

>(名称含义:sda是第一个磁盘，sdb是第二个磁盘，以此类推，sda1是sda磁盘的第一个分区sdb2是sdb磁盘的第二个分区，以此类推)

>如果你是第二种情况

如果你直接cfdisk，那么你的指令其实是cfdisk /dev/(你的/dev文件下的第一和磁盘)，也就是说，你只能看到你的第一个磁盘。你也要按着情况一的方式来找到你的其他磁盘，如果你有三个磁盘，那么你的磁盘名就分别是sda sdb sdc以此类推，cfdisk /dev/sda 给你的第一块磁盘分区，cfdisk /dev/sdb就是给你的第二个磁盘分区。


这里我把EFI设为sda1,
swap为sda2,
系统盘为sda3

看下面的gif动图来跟着我操作，很简单的

![1uFUZ6.gif](https://s2.ax1x.com/2020/01/27/1uFUZ6.gif)

看见了没？以上我首先输入了cfdisk，因为我用的是虚拟机只有一个磁盘，你有多个磁盘的话就先查看一下在cfdisk /dev/你的磁盘名。

然后我又选择了gpt，接着我new了一个分区，想用于引导系统，但是此时它只是一个普通的linux区，所以你要更改他的类别，选择Type，再选择EFI system。

接着你需要再分一个swap和一个系统盘。

最后不要选择每个分区再选择write输入yes并回车。

分完三个区就可以Quit来退出了！

#### 格式化分区
首先输入 fdisk -l来查看你的分区情况，然后你可以找到你的分区情况。你可以看见我的是这样的。

![Snipaste_2020-01-27_17-07-52.png](https://i.loli.net/2020/01/27/fXzlAZEG81I9D3N.png)

看到了吧，我的/dev/sdb1是EFI分区；/dev/sdb2是swap分区；/dev/sdb3是系统分区

现在要mkfs.ext4 /dev/sdb3以ext4格式来格式化系统分区
mkfs.fat -F32 /dev/sdb1以fat格式化EFI分区
再mkswap /dev/sdb2 格式化swap盘
接着启用SWAP分区 swapon /dev/sdb2

再挂载linux系统分区到根目录

mount /dev/sdb3 /mnt

然后建立启动目录mkdir -p /mnt/boot/efi

接下来把EFI分区挂载到启动目录下 ： mount /dev/sdb1 /mnt/boot/efi

接着使用vim更改镜像源以达到加速目的

vim /etc/pacman.d/mirrorlist


接着再安装系统pacstrap /mnt base linux base-devel
输入genfstab /mnt >> /mnt/etc/fstab


安装之后输入arch-chroot /mnt 离开liveCD切换到linux系统


用包管理器pacman下载个vim或neovim方便调试下载dhcpcd不然重启以后无法动态分配IP而导致无法安装桌面环境再下个intel-ucode(不是intel U不用下)双系统需求下os-prober

必须下efibootmgr 和 grub



输入grub-install --force --recheck /dev/sda

grub-mkconfig -o /boot/grub/grub.cfg

输入systemctl enable dhcpcd.service来获取dhcp动态分配ip地址服务
再输入exit退出系统

使用umount -R /mnt卸载已挂载的分区

使用reboot重启


## 配置篇

重启后输入root得到root权限

设置密码 passwd
再输入密码
创建用户useradd -m -s /bin/bash 用户名
输入passwd 用户名来设置用户密码


创建hostname：

vim /etc/hostname
输入hostname
```
127.0.0.1 localhost
::1 localhost
127.0.1.1 主机名.localdomain 主机名
```
#### 中文字体设置

vim /etc/locale.gen找到en_US.UTF-8和zh_CN.UTF-8去掉#:wq

再刷新区域信息locale-gen

将区域信息写入locale.conf文件：echo LANG=en_US.UTF-8 > /etc/locale.conf

需要说明：这里可以设置成中文，但是locale.conf文件是全局设置，在这里设成
中文或者其他非英语环境，桌面环境下会正常显示，但是命令行模式下会变成乱码。中文的问题在后面用其他方法解决。


#### 时区设置

ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime

hwclock --systohc --utc

timedatectl set-ntp true


#### 系统本地化设置
至少需要一种中文字体：pacman -S wqy-microhei
vim ~/.xprofile
输入
```
export LANG=zh_CN.UTF-8
export LANGUAGE=zh_CN:en_US
export LC_CTYPE=en_US.UTF-8
```
再cp ~/.xprofile /home/你的用户名

#### 桌面环境安装

输入pacman -S xorg xterm xorg-xinit sddm wqy-zenhei wqy-microhei plasma kde-applications xdg-user-dirs坐等下载

下载完成之后开启服务
xdg-user-dirs-update

sddm --example-config >/etc/sddm.conf

systemctl enable sddm.service

#### vmware&nbsp;tools快速安装：

1. git clone https://github.com/rasa/vmware-tools-patches.git
2. cd vmware-tools-patches
3. ./patched-open-vm-tools.sh


## 疑难解答篇

### U盘启动盘如何恢复原样：
Windows中右键此电脑，选择管理，打开磁盘管理，在右下角记住你的U盘的名称，假设我的U盘是磁盘2
Win+R键，输入cmd并打开，输入diskpart打开另一个命令行。
select disk 2选择到你的U盘
并输入clean。
清除成功，再在管理界面右键你的U盘，新建简单卷
之后再格式化磁盘
成功！

### 虚拟机无法更改分辨率解决方案
1.pacman -S xorg xorg-xinit xf86-video-vesa xf86-video-vmware  xf86-input-vmmouse open-vm-tools gtkmm

2.systemctl enable vmtoolsd.service vmware-vmblock-fuse.service

3.reboot



### git出现443解决方案：
先设置git 账号密码
git config --global --unset http.proxy
git config --global --unset https.proxy

然后


vim /etc/hosts

输入：

``` 127.0.0.1 localhost
::1 localhost
127.0.1.1 a.localdomain a（原有hosts配置）
192.30.253.112 github.com
151.101.88.249 github.global.ssl.fastly.net
192.30.253.113    github.com
192.30.252.131 github.com
185.31.16.185 github.global.ssl.fastly.net
74.125.237.1 dl-ssl.google.com
173.194.127.200 groups.google.com
192.30.252.131 github.com
185.31.16.185 github.global.ssl.fastly.net
74.125.128.95 ajax.googleapis.com
151.101.76.249 http://global-ssl.fastly.net
192.30.255.112 http://github.com  #此处112还是113根据自己的情况调整 方法:ping 一下github，会有显示)
```



### 开机显示can't&nbsp;access&nbsp;tty&nbsp;job&nbsp;control&nbsp;turned&nbsp;off，无法进入图形化界面
挺重要的之前遇到过三次


可使用fsck手动修复，不过fsck坑比较多，谨慎使用，详细了解命令并慎重考虑后再使用

格式：fsck.ext4 /dev/损坏的分区(ext4为文件系统)
一路yes

重启


成功！！！



### 换源不生效，pacman&nbsp;-Syy速度小于4K/s 

大坑，虽然这个问题真的很简单，但是我就是在这里卡了五天啊！！！！还是一个有过此问题的贴吧hxd教我的=======================================================

**解决方案**：*换DNS*

vim /etc/resolv.conf
```
nameserver 223.6.6.6
nameserver 8.8.8.8 
```

## 使用方法篇



#### pacman删除软件包

删除单个软件包，保留其全部已经安装的依赖关系

pacman -R package_name

删除指定软件包，及其所有没有被其他已安装软件包使用的依赖关系：

pacman -Rs package_name

要删除软件包和所有依赖这个软件包的程序:

pacman -Rsc package_name

警告: 此操作是递归的，请小心检查，可能会一次删除大量的软件包。

要删除软件包，但是不删除依赖这个软件包的其他程序：

pacman -Rdd package_name

pacman 删除某些程序时会备份重要配置文件，在其后面加上*.pacsave扩
展名。-n 选项可以删除这些文件：

pacman -Rn package_name

pacman -Rsn package_name


#### AUR的使用

编辑/etc/pacman.conf  with your favorite editor

在文件最后添加如下内容：
```
[archlinuxcn]

SigLevel = Optional TrustedOnly

Server = http://mirrors.163.com/archlinux-cn/$arch
```
保存退出刷新pacman数据库   sudo pacman -Syy


安装中文源密钥：

sudo pacman -S archlinuxcn-keyring

安装yaourt:
sudo pacman -S yaourt

Yaourt 不可使用可以更换镜像源再 sudo pacman -Syy


#### SSR须知
安装：
需要本地git 环境
yum install -y git

git clone https://github.com/SAMZONG/gfwlist2privoxy.git

cd gfwlist2privoxy/

mv ssr /usr/local/bin

chmod +x /usr/local/bin/ssr


ssr install


启动/关闭
ssr start
ssr stop



```
[root@localhost ~]# ssr config 		# 配置文件路径 /usr/local/share/shadowsocksr/config.json
{
    "server": "0..0.0.0",	// ssr服务器ip
    "server_ipv6": "::",
    "server_port": 8080,	// ssr服务器端口
    "local_address": "127.0.0.1",
    "local_port": 1080,

    "password": "123456",		// 对应password
    "method": "none",			// 这里对应SSGlobal配置中的Encryption
    "protocol": "auth_chain_a",		//对应protocl
    "protocol_param": "",
    "obfs": "http_simple",		//对应obfs
    "obfs_param": "hello.world",	//对应obfs_param
    "speed_limit_per_con": 0,
    "speed_limit_per_user": 0,

    "additional_ports" : {}, // only works under multi-user mode
    "additional_ports_only" : false, // only works under multi-user mode
    "timeout": 120,
    "udp_timeout": 60,
    "dns_ipv6": false,
    "connect_verbose_info": 0,
    "redirect": "",
    "fast_open": false
}
```



#### git须知
初始化为git仓库:
git init 
添加要提交的文件:
git add 文件名
git rm --cache 文件名  删除缓存区内容
查看当前缓存区状态
git status
本次提交说明:
git commit -m "Description" 文件名
推送本次提交到仓库:
git push origin master(分支名)
关联Github远程仓库：
git remote add origin 仓库地址（没有添加ssh key建议使用 https地址）
用户名git config --global user.name [username]
邮箱设置git config --global user.email [email]
可是当你第一次push的时候一般会遇到如下报错：
这种错误的主要原因是你的远程仓库的内容有改动但是你本地并没有拉去最新的代码所以会报错。
```
$ git push origin master
To https://github.com/yuanchao614/wecoder.git
 ! [rejected]        master -> master (non-fast-forward)

error: failed to push some refs to 'https://github.com/yuanchao614/wecoder.git'

hint: Updates were rejected because the tip of your current branch is behind

hint: its remote counterpart. Integrate the remote changes (e.g.

hint: 'git pull ...') before pushing again.

hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```
解决方案： git pull origin master --allow-unrelated-histories

然后建议做完上一步之后再重新：

git add .

git commit -m '提交说明'

git push origin master
## 美化篇




#### vim-Plug安装
curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
使用：
```
call plug#begin('~/.vim/plugged')

Plug 'vim-airline/vim-airline'

call plug#end()
```
说明：在~/.vimrc 中插入以上片段，在call内输入Plug '地址'
再:PlugInstall即可安装


命令：PlugInstall
PlugClean




## 插件推荐篇

### 常用vscode插件以及使用方法

#### Markdown&nbsp;All&nbsp;in&nbsp;One
支持以下功能 + 快捷键

按下 shift + command + p 可以查看。
![img](https://user-gold-cdn.xitu.io/2019/1/21/168705bae7bd1ed7?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)
| 键位             | 功能             |
| ---------------- | ---------------- |
| Ctrl + B         | 切换粗体         |
| Ctrl + I         | 切换斜体         |
| Alt + S          | 切换下划线       |
| Ctrl + Shift + ] | 标题升级         |
| Ctrl + Shift + [ | 标题降级         |
| Ctrl + M         | 切换数学环境     |
| Alt + C          | 选中/不选中任务  |
| Ctrl + Shift + V | 切换预览         |
| Ctrl + K V       | 将预览切换到侧边 |


我装过的工具：ranger zsh git neovim yum yay yaourt oh-my-zsh fzf 

>这个图床挺好用:https://imgchr.com/

一键提交：

git add README.md && git commit -m "Arch的安装心得分享" README.md && git push origin master














