### Linux的应用领域

* 服务器领域应用最强：免费，稳定，高效
* 嵌入式领域：运行稳定，对网络的良好支持，低成本，可以裁剪软件，降低内核大小。

### Linux概述

* 源码网址：https://www.kernel.org/
* Linux主要发行版：
  * Ubuntu
  * RedHat
  * CentOS等等

### Linux和Unix的关系

* Unix先出现后分离出了一个Minix，延伸出GNU/Linux内核
* Linux内核上进行开发出的Ubuntu,Redhat，CentOS等等

### VM和CentOS的安装

* 下载VM
* 迅雷下载IOS镜像
* 设置虚拟环境
  * 分区：
    * boot分区（1G）
    * 交换分区（2G）
    * 根分区（剩余部分）
* 慢慢安装

### 三种网络连接方式介绍

* 桥接模式
  * 虚拟系统可以和外部系统通讯，但是容易由IP冲突
* NAT模式
  * 网络地址转换模式，虚拟系统可以和外部系统通讯，且不造成IP冲突（使用不同网段）
* 主机模式
  * 独立系统

### 虚拟机克隆（快速构建集群）

* 直接拷贝一份安装好的虚拟机文件
* 使用VMware的克隆操作
  * 注意：克隆时，需要先关闭Linux系统

### 虚拟机快照

* 误操作造成系统异常，需要回到原先某个正常运行的状态，可以借助快照管理
* 相当于存档

### VMtools

* vmtools安装后，可以让我们再windows下更好的管理vm虚拟机
* 可以设置windows和centos的共享文件夹
* 安装步骤
  * 进入centos
  * vm菜单-》install vmware tools
  * centos出现vm安装包
  * 拷贝到/opt
  * 使用解压命令 tar，得到安装目录 tar -zxvf 文件名
  * 进入安装目录 ./安装文件 成功安装
  * 注意：安装vmtools，需要有gcc
* 设置共享文件夹
  * 在主文件夹-》其他位置-》计算机-》mnt/hgfs/下

### Linux目录结构

* LInux的文件系统采用级层式的树状目录结构
* LInux系统下，把硬件识别为文件进行管理
* 根目录： /
* /bin【常用】
  * 存放常用指令
* /sbin
  * S代表super User，存放系统管理员使用的系统管理程序
* /home
  * 存放普通用户的主目录，在Linux种每个用户都有自己的一个目录
* /root
  * 该目录位系统管理员
* /lib
  * 系统开机所需要的最基本的动态链接共享库
* /lost+found（隐藏）
  * 该目录位空，存放系统非法关机的记录文件
* /etc
  * 所有系统管理所需要的配置文件和子目录
* /usr
  * 用户应用程序和文件存放在这个目录下
* /boot
  * Linux启动时的核心文件
* /proc【不能动】
  * 虚拟目录
* /srv和/sys【不能动】
* /tmp
  * 存放临时文件
* /dev
  * 类似于windows的设备管理器，把所有硬件用文件的形式存储
* /media
  * Linux系统会自动识别一些设备
* /mnt
  * 系统提供该目录让了让用户临时挂载别的文件系统
* /opt
  * 主机额外安装软件所存放的目录
* /usr/local
  * 这是另一个给主机额外安装软件所安装的目录
* var
  * 存放日志

### 远程登录Linux服务器

* Xshell远程登录
* Xftp对文件进行远程传输和下载
* 命令：ifconfig可以查看ip
* Xshell远程通过reboot命令重启Linux系统

### vi和vim的基本介绍

* Linux基本的文本编辑器
* vi和vim的常用模式
  * 正常模式
  * 插入模式：按下i,I,o,O,a,A,r,R
  * 命令行模式：输入：esc:
* 进入vim：vim hello.java
* 命令模式: `:wq`强制退出 `:q`退出 `:q!`强制退出不保存
* vim和vi快捷键
  * 拷贝当前行（一般模式）：yy
  * 删除当前行（一般模式）:  dd
  * 查找：`/关键词`或者`:关键词`，n可以切换匹配词
  * 设置行号：命令行`:set nu`
  * 一般模式下G最末行，gg最首行
  * 一般模式下，输入`u`
  * 一般模式定义行号：`20 shift+g`

### Linux关机和重启的命令

* `shutdown -h now` 立刻关机
* `shutdown -h 1`  “hello 1分钟之后关机”
* `shutdown -r now` 现在重新启动计算机
* `halt` 关机（少用）
* `reboot` 重新启动计算机
* `sync` 把内存的数据同步到磁盘

### 用户登录与注销

* 登录少用root账号登录，因为是系统管理员，最大的权限，避免操作失误，可以普通用户登录，然后`su - 用户名`来切换系统管理与身份
* 注销：`logout 用户名` / `exit`
  * 完全注销后就是退出系统

### 用户管理

* `useradd 用户名`
  * 自动文件创建在/home/目录下
* `useradd -d /home/test king`
  * 创建用户king，`-d`指定目录
* `passwd 用户名`
  * 设置密码，如果没有写用户名，就是给当前机子修改
* `pwd`显示当前用户所在的目录
* `userdel milan`
  * 删除用户
  * `userdel -r milan`删除用户同时删除用户文件
* `id 用户名` 查询用户信息
* `su - 用户名` 切换用户名
  * 从低到高需要输入密码，反之不需要
* `whoami / who am I` 查看登录的当前用户

* 用户组
  * 添加组 `groupadd 组名称`
    * 不指定组创建用户，会自动创建一个和用户名相同的组
  * 删除组 `groupdel 组名称`
  * 添加用户直接带组 `useradd -g 组id zwj`
  * 修改用户的组 `usermod -g mojiao zwj`
  * /etc/passwd 文件
    * 含义：用户名：口令：用户标识号：组标识号：注释性描述：主目录：登录Shell
  * /etc/shadow 文件
    * 含义：登录名：加密口令：最后一次修改时间：最小时间间隔：最大时间间隔：警告时间：不活动时间：失效时间：标志
  * /etc/group 文件
    * 组的配置文件，记录Linux包含的组的信息
    * 含义：组名：口令：组标识号：组内用户列表

### 运行级别

* 0：关机；1：单用户【找回丢失密码】；2：多用户状态没有网络服务；
* 3：多用户状态有网络服务；（multi-user.target）04：系统未使用保留给用户；5：图形界面；（graphical.target）
* 6：系统重启
  * 常用运行级别是3和5，也可以制定默认运行级别，后面演示。
* 命令：init[0123456] 应用案例：通过init来切换不同的运行级别，比如动5-3，然后关机。
* 命令：`systemctl get-default` 查看当前运行级别
* 命令：`systemctl set-default TARGET.target` 设置当前运行级别

### 找回Root密码

* 启动系统，输入e
* 找到Linux16开头所在的行数，输入init=/bin/sh，输入ctrl+x进入单用户模式
* mount -o remount,rw /，
* 输入新的：passwd，再次确认密码
* 鼠标闪烁最后输入：touch /.autorelabel
* 继续输入：exec /sbin/init

### 帮助指令

* man 获得帮助信息
  * `man [命令或者配置文件]`
  * 例如`man ls`
* help指令
  * `help 命令` 获得Shell内置命令的帮助信息

### 文件目录类指令

* pwd指令：查看当前目录绝对路径
  * 基本语法： `pwd`
  * 显示当前工作目录的绝对路径
* ls指令：查看目录下文件
  * 基本语法：`ls [选项] [目录或者文件]`
  * 常用选项
    * -a：显示当前目录所有文件和目录，包括隐藏
    * -l：以列表的形式显示全部信息
    * -h：以人更能理解的方式看
* cd指令：切换目录
  * `cd [参数]` 切换到指定目录
  * `cd ~ 或者cd`回到自己的家目录
  * `cd ..`回到上级目录
    * `cd ../../root` 从`/home/tom/来到/root`
* mkdir指令：创建目录
  * `mkdir [选项]` 指令用于创建目录
    * 默认只能创建一级目录
  * 常用选项：
    * -p 创建多级目录
* rmdir指令：删除空目录
  * `rmdir [选项] 目录 ` 删除空目录
* `rm -rf [目录]` 强行删除目录包括里面的文件
* touch指令：创建空文件
  * `touch 文件名称` 创建一个空文件
* cp指令：拷贝
  * `cp [选项] source dest`	把源文件拷贝到目标位置
  * 常用选项
    * -r 递归复制整个文件夹
  * `\cp -r /home/bbb/ opt` 强制覆盖，不提示
* rm指令：删除文件或者目录
  * `rm [选项] 要删除的文件或者目录`  
  * 常用选项
    * -r：递归删除整个文件夹
    * -f：强制删除不提示
* mv指令：移动文件，或者重命名文件
  * `mv oldNameFile newNameFile` 同一个目录下，则是重命名
  * `mv /temp/movefile /targetFolder` 不在同一个目录就是移动文件
* cat指令：查看文件内容
  * `cat [选项] 要查看的文件`
  * 常用选项
    * -n：显示行号
  * 为了使用方面，一般会带入管道命令 | more
    * 把前面的结果交给more处理
* more指令：基于VI编辑器的文本过滤器，以全屏幕方式按页显示文本内容
  * `more 要查看的文件`
  * 操作与对应功能
    * space 翻一页
    * Enter 下一行
    * q 离开more展示的文件
    * ctrl +F 向下滚动一屏幕
    * ctrl + B 返回上一屏
    * = 输出当前行号
    * :f 输出文件名和当前行的行号
* less指令：和more类似，但是比more更强大，支持各种终端，并且是动态加载文件，因此看大文件用less好
  * `less 要查看的文件`
  * 操作与对应功能
    * space 向下翻动一页
    * q离开
    * /字串：向下搜寻 n：向下查找 N：向上查找
    * ?字串：向上搜索
    * [pagedown] 向下
    * [pageup]向上
* echo指令：输出内容到控制台
  * `echo [选项] [输出内容]`
    * `echo $PATH / $HOSTNAME`可以输出环境变量
* head指令：显示文件的开头部分内容，默认显示前十行
  * `head 文件`
  * `head -n 5 文件` 
* tail指令：和head相反
  * 特殊点：
    * `tail -f 文件` 实时追踪该文档的所有更新
* \> 指令 >> 指令
  * \> 输出重定向和 >> 追加
  * `ls -l > 文件` 输出到文件
  * `ls -al >> 文件` 输出到文件
  * `cat 文件1 > 文件2` 文件1覆盖文件2
  * `echo “内容”  > >  文件` echo内容输出到文件
* ln指令：软连接或者符号链接，类似于快捷方式
  * `ln -s [原文件或者目录] [软链接名]`
* history指令：查看已经执行过历史命令，也可以执行历史命令
  * `history 10` 没有数字默认显示全部历史，有数字就最近10条
  * `!387` 执行曾经执行过的指令

### 时间日期类

* date指令：显示当前日期
  * `date`显示当前时间
  * `date +%Y` 当前年份
  * `date +%m` 当前月份
  * `date +%d` 当前是哪一天
  * `date "+%Y-%m-%d %H%:%M:%S"` 格式化显示年月日时分秒
  * 设置日期：`date -s 字符串时间`
    * 案例：`date -s "2020-11-03 20:02:10"`
  * `hwclock -s` 修改回来
* cal指令：查看日历指令
  * `cal [选项]` 不加选项显示本月日历
  * `cal 2020` 查看2020年所有月份的日历

### 搜索查找类

* find指令：将从指定目录向下递归遍历查找子目录，将满足条件的文件或者目录显示在终端
  * `find [搜索范围] [选项]`
  * -name<查询方式> 按照指定文件名进行查找
    * `find /home -name hello.txt`
  * -user<用户名> 查找属于指定用户名的文件
    * `find /opt -user nobody`
  * -size<文件大小> 按照指定的文件大小查找文件
    * `find / -size +200M`（+代表大于，-代表小于，不写代表等于）
* locate指令：可以快速定位文件路径。locate指令借助实现建立的系统中的文件名称以及路径的locate数据库实现快速给定文件。如果为了保证查询结果的准确度，需要定期更新locate时刻
  * `locate 搜索文件`
    * 由于locate基于数据库进行查询，所以第一次运行完需要使用updatedb指令激活locate数据库
* which指令，可以查看某个指令在哪个目录
  * `which 指令`
    * `which ls`
* grep指令和管道符号 |
  * grep过滤查找，管道符号|，表示将前一个命令的处理结果输出传递给后面的指令处理。
  * `grep [选项] 查找内容 源文件`
    * `cat dog/hello.txt | grep -ni "yes"`
  * 常用选项
    * -n 匹配行以及行号
    * -i 忽略字母大小写

### 压缩和解压文件

* gzip/gunzip指令
  * gzip用于压缩文件，gunzip用于解压文件
  * `gzip 文件` 
  * `gunzip 文件.gz`
* zip/unzip指令
  * zip用来压缩文件，unzip用于解压
  * `zip [选项] XXX.zip 将要压缩的内容` 压缩文件和目录的命令
  * `unzip [选项] XXX.zip` 解压缩文件
  * 常用选项
    * zip：-r 递归压缩，即压缩目录
    * unzip：-d<目录>：指定解压后文件的存放目录 
* tar指令：可以用来打包，可以解压
  * `tar [选项] XXX.tar.gz 打包的内容`
  * 选项：
    * -c 产生tar文件，可以指定路径
    * -v 显示详细过程
    * -f 指定压缩后的文件名
    * -z 打包同时压缩
    * -x 解包.tar文件
  * `tar -cvf pc.tar.gz /home/pig.txt /home/cat.txt`
  * `tar -cvf myhome.tar.gz /home`
  * `tar -xvf pc.tar.gz`
  * `tar -zxfv /home/myhome.tar.gz -C /opt/tmp2`

### 组管理和权限管理

* Linux每一个用户都在组内
* Linux的每个文件都有所有者，所在组，其他组的概念
* 查找文件所有者
  * `ls -ahl` 用户名栏指示了所有者
* 修改文件所有者
  * `chown 用户名 文件名`
* 组的创建
  * `groupadd 组名`
    * `useradd -g monster username`
    * `id 用户名` 查看用户信息
* 修改文件或者目录所在的组
  * `chgrp 组名 文件名/目录名`
* 改变用户所在组
  * `usermod -g 新组名 用户名`
  * `usermod -d 目录名 用户名` 修改该用户登录的初始目录。
    * 用户需要有进入到新目录的权限。
* 查看组
  * `cat /etc/group/`
* 权限的基本介绍
  * 0~9位说明
    * 第0位确定文件类型(d,-,I,c,b)
      * I是链接，相当于快捷方式
      * d是目录
      * c是字符设备文件，鼠标，键盘
      * -是普通文件
      * b是块设备，例如硬盘
    * 第1-3位置确定所有者，拥有该文件的权限
    * 第4-6位置确定所属组（同用户组的）拥有该文件的权限
    * 第7-9位置确定其他用户拥有该文件的权限
  * rwx权限详解
    * 作用在文件
      * [r]代表可读：可以读取，查看
      * [w]代表可写：可以修改，但是不可以删除，删除文件的前提是对该文件所在的目录具有写文件，才可以删除文件
      * [x]代表可执行:可以被执行
    * 作用在目录
      * [r]代表可读：ls查看目录内容
      * [w]代表可写：可以修改，对目录内创建+修改+重命名目录
      * [x]代表可执行：可以进入该目录
  * 案例`drwxr-xr-x.`
* 文件及目录权限实际案例
  * drwxr-xr-x.  3 root root     4096 6月  18 10:00 animal
  * r=4,w=2,x=1
  * 之后的元素3，如果是文件代表硬链接数字，如果是目录则是文件数
  * 所有者
  * 所在组
  * 字节数
  * 最后修改日期
  * 文件名
* 修改权限-chomd
  * 第一种方式：+、-、=变更权限
    * u：所有者，g：所有组，o：其他人，a：所有人
    * `chmod u=rwx,g=rx,o=x 文件/目录名`
    * `chmod o+w 文件/目录名`
    * `chmod a-x 文件/目录名`
  * 第二种方式：通过数字变更权限
    * r=4,w=2,x=1
    * `chmod 755 abc.txt`
* 修改文件所有者-chown
  * `chown newowner 文件/目录 改变所有者`
  * `chown newowner:newgroup 文件/目录 改变所有者和所在组`
  * -R 如果是目录，则使其下子文件递归改变
* 修改文件/目录所在组-chgrp
  * `chgrp newgroup 文件/目录` 改变所在组
* 权限详解
  * x：目录的执行权限，可以进入目录，但不能读取目录
  * r：能否查看目录
  * w：能否在目录里进行增删改

### crond-定时任务调度

* 任务概述：是指系统在某个时间执行特定的命令或者程序
  * `crontab -e` 添加定时任务调度
  * `crontab -r` 终止任务调度
  * `crontab -i` 列出当前有那些任务调度
  * `service crond restart` 重启任务调度
  * 五个占位符说明：第一个*代表一小时的第几分钟，第二个代表一天当中的第几个小时，第三个代表一个月的第几天，第四个代表一年的第几月，第五个代表一周的星期几（0和7都代表星期天）
  * 特殊符号含义：
    * \* 代表任意时间
    * , 代表不连续的时间
    * \- 代表连续的时间范围
    * \* / n 代表每隔多久执行一次
* 多个任务时，可以写sh文件，让crond调度文件
  * `./脚本文件` 执行文件

### at-定时计划

* 基本介绍：at命令是一次性定时计划任务，at的守护进程atd会以后台模式运行，检查作业队列运行。（使用at命令，需要保证atd进程运行）
  * `ps -ef | grep atd` 检测当时正在运行的atd进程
  * `at [选项] [时间]`
  * Ctrl + D代表at命令输入结束
* 案例：
  * 两天后的下午五点执行`/bin/ls/home`
  * `atq`可以查看系统当中没有执行的命令
  * 明天17点，输出时间到指定文件内
  * 两分钟后，输出时间到指定文件
  * 删除已经设置的任务：`atrm 1` 删除需要1任务

### Linux分区

* Linux不论有几个分区，分给哪个目录使用，他归根结底只有一个根目录，一个独立且唯一的文件结构。
  * 查看所有设备挂在情况：`lsblk`
    * -f 代表输出更加详细的分区信息：给出文件系统类型，每个分区40位的唯一标识符，挂载点
  * sd代表是SCSI硬盘

### Linux挂载的经典案例

* 虚拟机增加硬盘
  * 虚拟机菜单选择设置，设备列表添加硬盘，然后重启系统
* 虚拟机添加硬盘
  * `fdisk /dev/sdb` dev文件夹下包含全部的物理设备
    * m 查看命令列表
    * p 显示磁盘分区
    * n 新增分区
    * d 删除分区
    * w 写入并且推出

*  虚拟机添加硬盘进行格式化
  * `lsblk -f` 先查看添加硬盘后的事情
  * `mkfs -t ext4 /dev/sdb1  `格式化硬盘
* 挂载
  * `mount /dev/stb1 /newdisk/` 
  * `lsblk -f` 可以查看是否挂载成功
* 卸载挂载
  * `umount 设备名称/挂载目录`
    * `umount /dev/stb1 或者umount /newdisk`
* 永久挂载
  * 使用命令行挂载重启会失效
  * 永久挂载：修改 `/etc/fstab` 实现挂载
    * 再运行`mount -a`立刻生效

### 磁盘情况查询

* `df - h` 查看系统整体磁盘使用情况
* `du -h /目录` 查询指定目录的磁盘占用情况
  * -s 指定目录占用大小汇总
  * -h 带计量单位
  * -a 含文件（默认只统计目录）
  * --max-depth=1 查询子目录深度
  * -c 列出明细同时增加汇总值
  * 案例：查询opt目录的磁盘占用情况，深度为1
    * `du -ha --max-depth=1 /opt`

### 磁盘情况-工作实用指令

* 统计文件夹下文件个数
  * `ls -l /opt | grep "^-" | wc -l` 查询文件个数
* 统计文件夹下目录的个数
  * `ls -l /opt | grep "^d" | wc -l` 查询目录个数
* 统计文件夹下的文件个数，包括子文件夹
  * `ls -lR /opt | grep "^-" | wc -l` 查询全部文件个数
* 统计文件夹下的目录个数，包括子文件夹
  * `ls -lR /opt | grep "^d" | wc -l` 查询全部目录个数
* 目录格式用树形式展示：默认情况没有tree命令`yum instll tree` 下载tree命令
  * `tree /目录`

### 网络配置

* Linux的IP通过中间一个代理和主机连通网络，再借助外界的网关访问外网（NAT模式）
* 查看网络IP和网关
  * ping命令，ifconfig命令
  * VMware的编辑可以查看网络设置
* Linux网络环境配置
  * 自动分配IP，在IP冲突时会分配别的IP
  * 指定IP，修改配置文件来指定IP，并且可以链接到外网
    * 编辑 `vi /etc/sysconfig/network-scripts/ifcfg-ens33`
    * 要求把IP地址配置为静态的，比如：ip 地址为192.168.30.130
    * ifcfg-ens33文件说明
      * DEVICE设备名
      * UUID随机ID
      * ONBOOT系统启动时网络接口是否有效
      * TYPE网络类型
    * BOOTPROTO：网络协议，DHCP为自动分配，static为静止，指定
    * IPADDR：设置的IP地址
    * GATEWAY：设置网关
    * DNS1：设置域名解释器

### 设置主机名和host映射

* 为了方便记忆，可以给Linux设置主机名，也可以根据需要修改主机名
  * `hostname`： 可以查看主机名
  * 修改文件在 /etc/hostname指定
  * 修改后重启生效
* 设置host映射
  * windows在`C:\Windows\System32\drivers\etc\hosts`文件指定即可
    * IP 主机名添加到文件里
  * Linux在`/etc/hosts`文件指定
    * IP 主机名
* Hosts是什么
  * 文本文件，记录IP和Hostname（主机名）的映射关系
* DNS
  * DNS就是域名系统，是互联网上作为域名和IP地址相互映射的一个分布式数据库
  * windows下：`ipconfig /displaydns` 查看DNS域名解析缓存
  * `ipconfig /flushdns` 手动清理DNS缓存

### 进程管理

* Linux中，每个执行的程序都称为一个进程，每一个进程都分配一个ID号=》windows=》Linux，每个进程都可能以两种方式存在，前台和后台，前台就是占住用户屏幕，后台是实际在操作，但由于屏幕上没法看到的进程。一般来说，系统服务都是在后台进程的方式存在，并且常驻于系统，直到关机才结束。
* 显示系统执行的进程
  * `ps`
    * -a显示当前终端的全部进程信息
    * -u以用户的格式显示进程信息
    * -x显示后台进程运行的参数
    * PID：进程识别号
    * USER：进程执行用户
    * %CPU：当前这个线程占用CPU的百分比
    * %MEM：当前占用物理内存的备份比
    * VSZ：占用物理内存
    * RSS：占用物理内存的
    * TTY：终端信息
    * STAT：当前运行状态：S代表休眠，R代表运行状态
    * START：代表进程开始执行时间
    * TIME：表示进程占用的CPU时间
    * COMMAND：代表执行改进程的指令
* 应用实例：以全格式显示当前所有进程，查看进程的父进程
  * `ps -ef` 以全格式显示当前的所有进程
* 终止进程kill和killall
  * `kill [选项] 进程号` 通过进程号终止进程
  * `killall 进程名称` 通过进程名称杀死进程，子进程也会被终止
  * -9 表示强迫进程立即停止
  * 强迫踢走用户：
    * `ps -aux | grep sshd` 查询用户登录进程
    * `kill 11421(进程号)` 终止该进程即可
  * 终止远程登陆服务sshd，并在适当时候重启sshd服务
    * `ps -aux | grep sshd` 找到sshd服务的进程号
    * `kill 10719`
    * `/bin/systemctl start sshd.service` 重新开启sshd服务
  * 终止多个gedit
    * `killall gedit` 和进程相关的进程全部关闭，使用进程的名称进行删除
  * 强制终止一个终端
    * `kill -9 进程号` 强行删除
* 查看进程树 pstree
  * `pstree [选项]`
    * -p 查看进程的PID
    * -u 查看进程所属的用户

### 服务管理

* 后台程序称之为守护进程（服务），通常监听某个端口，等待其他程序的请求。
* service
  * `[start | stop | restart | reload | status]`
  * 查看service可以管理的服务
    * `ls -l /etc/init.d/`
    * 绿色的就是现在还可以管理的
    * 全部服务：`setup`
* 服务的运行级别（系统运行级别）
* chkconfig指令：可以给服务的各个运行级别设置自启动/关闭
  * chkconfig指令管理的服务在 /etc/init.d查看
  * 查看服务的在不同运行级别是否开启：`chkconfig --list | grep network`
  * 管理某个服务在某个级别是否自启动：`chkconfig --level 5 服务名 on/off`
  * 重新启动后才会生效
* systemctl管理指令
  * 基本语法：`systemctl [start | stop | restart | reload | status]`（临时启动）
  * 查看管理的指令：`ls - l /usr/lib/systemd/system`
  * 设置服务的自启动状态
    * `systemctl list-unit-files | grep 服务名`
    * `systemctl enable 服务名` 设置服务开机启动（永久生效）
    * `systemctl disable 服务名` 设置服务不开启启动（永久生效）
    * `systemctl is-enabled 服务名` 查看服务是否开机自启动
  * 关闭或者启动防火墙，立即生效
  * 但只是临时生效，重启系统后还是回到之前的设置
  * 永久生效需要使用`systemctl enable/disable 服务名`
* 开启防火墙的一个端口（firewall指令）
  * `netstat -anp | more` 可以查看协议
  * 打开端口：`firewall-cmd --permanent --add-port=端口号/协议`
  * 关闭端口：`firewall-cmd --permanent --remove-port=端口号/协议`
  * 重新载入才能生效：`firewall-cmd --reload`
  * 查询端口是否开放：`firewall-cmd --query-port=端口/协议`

* 动态监控进程
  * top与ps类型，可以监控正在执行的进程，不过top会动态更新进程的状态
  * `top [选项]`
    * -d 秒数 指定top命令每隔几秒更新，默认为3
    * -i 使top不显示任何闲置或者僵死的进程
    * -p 通过指定监控进程ID来仅仅监控某个进程的状态
  * 交互操作：
    * P：以CPU使用率排序
    * M：按照内存使用率排序
    * N：以PID排序
    * q：退出top
  * 监控某个用户：输入u，输入用户名
  * 终止指定的进程：输入k，输入PID
  * 指定系统状态更新的时间：top -d 10

* 监控网络状况
  * `netstat | more`
  * -an 按照一定顺序排列输出
  * -p 显示哪个进程在调用
  * `netstat -anp | grep sshd`

### RPM与YUM

* RPM包的管理
  * rpm用户互联网下载包的打包以及安装工具，它包含在某些Linux分发版中，它具有.RPM扩展名的文件
  * 查询已经安装的包：`rmp -qa | grep xx`
  * firefox-60.2.2-1.el7.centos.x86_64
    * firefox文件名
    * 60.2.2-1 版本号
    * el7.centos
    * x86_64 操作系统
  * 查询软件包是否安装： `rpm -q firefox`
  * 查询软件包相关信息：`rpm -qi firefox`
  * 查询软件包包含的文件：`rpm -ql firefox`
  * 查询文件所属的软件包：`rpm -qf 文件全路径名`
  * 卸载RPM包：`rpm -e RPM包名称` 
  * 安装RPM包：`rpm -ivh RMP包全路径名称`
    * i = install 安装
    * v = verbose 提示
    * h = hash 进度条
* YUM
  * Yum是一个Shell前端软件包管理器，基于RPM包管理，能够从指定的服务器自动下载RPM包并且安装，可以自动处理依赖性关系，并且一次安装所有依赖的软件包。
  * 查询yum服务器是否有需要安装的软件：`yum list | grep xx软件列表`
  * 安装指定的yum包：`yum install xxx`



























