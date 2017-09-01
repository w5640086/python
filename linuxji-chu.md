# **linux**

# Linux 目录

```
    /：根目录，一般根目录下只存放目录，在Linux下有且只有一个根目录。所有的东西都是从这里开始。当你在终端里输入“/home”，你其实是在告诉电脑，先从/（根目录）开始，再进入到home目录。
    /bin、/usr/bin: 可执行二进制文件的目录，如常用的命令ls、tar、mv、cat等。
    /boot：放置linux系统启动时用到的一些文件，如Linux的内核文件：/boot/vmlinuz，系统引导管理器：/boot/grub。
    /dev：存放linux系统下的设备文件，访问该目录下某个文件，相当于访问某个设备，常用的是挂载光驱 mount /dev/cdrom /mnt。
    /etc：系统配置文件存放的目录，不建议在此目录下存放可执行文件，重要的配置文件有 /etc/inittab、/etc/fstab、/etc/init.d、/etc/X11、/etc/sysconfig、/etc/xinetd.d。
    /home：系统默认的用户家目录，新增用户账号时，用户的家目录都存放在此目录下，~表示当前用户的家目录，~edu 表示用户 edu 的家目录。
    /lib、/usr/lib、/usr/local/lib：系统使用的函数库的目录，程序在执行过程中，需要调用一些额外的参数时需要函数库的协助。
    /lost+fount：系统异常产生错误时，会将一些遗失的片段放置于此目录下。
    /mnt: /media：光盘默认挂载点，通常光盘挂载于 /mnt/cdrom 下，也不一定，可以选择任意位置进行挂载。
    /opt：给主机额外安装软件所摆放的目录。
    /proc：此目录的数据都在内存中，如系统核心，外部设备，网络状态，由于数据都存放于内存中，所以不占用磁盘空间，比较重要的目录有 /proc/cpuinfo、/proc/interrupts、/proc/dma、/proc/ioports、/proc/net/* 等。
    /root：系统管理员root的家目录。
    /sbin、/usr/sbin、/usr/local/sbin：放置系统管理员使用的可执行命令，如fdisk、shutdown、mount 等。与 /bin 不同的是，这几个目录是给系统管理员 root使用的命令，一般用户只能"查看"而不能设置和使用。
    /tmp：一般用户或正在执行的程序临时存放文件的目录，任何人都可以访问，重要数据不可放置在此目录下。
    /srv：服务启动之后需要访问的数据目录，如 www 服务需要访问的网页数据存放在 /srv/www 内。
    /usr：应用程序存放目录，/usr/bin 存放应用程序，/usr/share 存放共享数据，/usr/lib 存放不能直接运行的，却是许多程序运行所必需的一些函数库文件。/usr/local: 存放软件升级包。/usr/share/doc: 系统说明文件存放目录。/usr/share/man: 程序说明文件存放目录。
    /var：放置系统执行过程中经常变化的文件，如随时更改的日志文件 /var/log，/var/log/message：所有的登录文件存放目录，/var/spool/mail：邮件存放的目录，/var/run:程序或服务启动后，其PID存放在该目录下。
```

# linux基础命令大全

```
    --help  帮助信息

    man 命令手册

    tab自动补全

    history  上下键  历史命令
```

> ## 文件管理

#### 

> # **用户、权限管理**

### 查看当前用户：whoami {#查看当前用户：whoami}

### 查看登录用户：who {#查看登录用户：who}

```
-m或am I    只显示运行who命令的用户名、登录终端和登录时间
-q或--count    只显示用户的登录账号和登录用户的数量
-u或--heading    显示列标题
```

### 退出登录账户： exit {#退出登录账户：-exit}

```
如果是图形界面，退出当前终端；

如果是使用ssh远程登录，退出登陆账户；

如果是切换后的登陆用户，退出则返回上一个登陆账号。
```

### 添加用户账号：useradd {#添加用户账号：useradd}

```
-d    指定用户登录系统时的主目录，如果不使用该参数，系统自动在/home目录下建立与用户名同名目录为主目录
-m    自动建立目录
-g    指定组名称
```

### 设置用户密码：passwd {#设置用户密码：passwd}

```
在Unix/Linux中，超级用户可以使用passwd命令为普通用户设置或修改用户口令。
用户也可以直接使用该命令来修改自己的口令，而无需在命令后面使用用户名。
```

### 删除用户：userdel {#删除用户：userdel}

```
userdel abc(用户名)    删除abc用户，但不会自动删除用户的主目录
userdel -r abc(用户名)    删除用户，同时删除用户的主目录
```

### 切换用户：su {#切换用户：su}

```
可以通过su命令切换用户，su后面可以加“-”。su和su –命令不同之处在于，
su -切换到对应的用户时会将当前的工作目录自动转换到切换后的用户主目录：

如果是ubuntu平台，需要在命令前加“sudo”，如果在某些操作需要管理员才能操作，ubuntu无需切换到root用户即可操作，只需加“sudo”即可。
sudo是ubuntu平台下允许系统管理员让普通用户执行一些或者全部的root命令的一个工具，减少了root 用户的登陆和管理时间，提高了安全性。

su    切换到root用户
su root    切换到root用户
su -    切换到root用户，同时切换目录到/root
su - root    切换到root用户，同时切换目录到/root
su 普通用户    切换到普通用户
su - 普通用户    切换到普通用户，同时切换普通用户所在的目录
```

### 查看有哪些用户组 {#查看有哪些用户组}

```
cat /etc/group
groupmod +三次tab键
```

### 添加、删除组账号：groupadd、groupdel {#添加、删除组账号：groupadd、groupdel}

```
groupadd 新建组账号 groupdel 组账号 cat /etc/group 查看用户组
```

### 修改用户所在组：usermod {#修改用户所在组：usermod}

```
使用方法：usermod -g 用户组 用户名
```

### 查看用户在哪些组![](/assets/impoSrt.png) {#查看用户在哪些组}

### 为创建的普通用户添加sudo权限 {#为创建的普通用户添加sudo权限}

```
sudo usermod -a -G adm 用户名

sudo usermod -a -G sudo 用户名
```

### 修改文件权限：chmod {#修改文件权限：chmod}

```
chmod 修改文件权限有两种使用格式：字母法与数字法。

字母法：chmod u/g/o/a +/-/= rwx 文件

[ u/g/o/a ]    含义
u    user 表示该文件的所有者
g    group 表示与该文件的所有者属于同一组( group )者，即用户组
o    other 表示其他以外的人
a    all 表示这三者皆是
[ +-= ]    含义
+    增加权限
-    撤销权限
=    设定权限
rwx    含义
r    read 表示可读取，对于一个目录，如果没有r权限，那么就意味着不能通过ls查看这个目录的内容。
w    write 表示可写入，对于一个目录，如果没有w权限，那么就意味着不能在目录下创建新的文件。
x    excute 表示可执行，对于一个目录，如果没有x权限，那么就意味着不能通过cd进入这个目录。

数字法：“rwx” 这些权限也可以用数字来代替
字母    说明
r    读取权限，数字代号为 "4"
w    写入权限，数字代号为 "2"
x    执行权限，数字代号为 "1"
-    不具任何权限，数字代号为 "0"
如执行：chmod u=rwx,g=rx,o=r filename 就等同于：chmod u=7,g=5,o=4 filename

chmod 751 file：

文件所有者：读、写、执行权限
同组用户：读、执行的权限
其它用户：执行的权限
```

### 修改文件所有者：chown {#修改文件所有者：chown}

### 修改文件所属组：chgrp {#修改文件所属组：chgrp}



