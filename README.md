# 一、Linux命令

## 1.1 六个常用终端命令

| 序号 |      命令      |       对应英文       |           作用           |
| :--: | :------------: | :------------------: | :----------------------: |
|  01  |       ls       |         list         |  查看当前文件夹下的内容  |
|  02  |      pwd       | print work directory |    查看当前所在文件夹    |
|  03  |  cd [目录名]   |   change directory   |        切换文件夹        |
|  04  | touch [目录名] |        touch         | 如果文件不存在，新建文件 |
|  05  | mkdir [目录名] |    make directory    |         创建目录         |
|  06  |  rm [文件名]   |        remove        |     删除指定的文件名     |
|  07  |     clear      |        clear         |           清屏           |

> 小技巧
>
> ctrl+shift+= 放大终端窗口的字体显示
>
> ctrl+- 缩小终端窗口的字体显示

## 1.2 终端命令格式

`command [-options] [parameter]`

`command`：命令名，相应缩写
`[-options]`：选项，可用来对命令进行控制，可省略
`[parameter]`：传递给命令的参数，可以是0个，1个或者多个

> [ ]代表可选

## 1.3 查阅命令

`command --help`

显示`command`命令的帮助信息

`man command`

查阅`command`命令的使用手册

# 二、文件和目录常用命令

## 2.1 实用技巧

自动补全：在敲出 文件/目录/命令 的前几个字母后，按下`tab`键

- 如果输入没有歧义，则系统自动补全
- 如果存在相似名称，再按一下tab键，系统会提示可能存在的命令

曾经使用过的命令

- 按 上/下 光标键切换
- 使用ctrl+c退出选择，另起一行

## 2.2 ls 命令

Linux文件或者目录的名称最长可以有256个字符

- 以`.`开头的文件为隐藏文件
- `.`代表当前目录
- `..`代表上一级目录

| 选项参数 |                      含义                      |
| :------: | :--------------------------------------------: |
|    -a    | 显示指定目录下的所有子目录与文件，包括隐藏文件 |
|    -l    |         以列表的方式显示文件的详细信息         |
|    -h    |  `ls -l -h`配合`-l`以人性化的方式显示文件大小  |

> 选项可以联合使用，并且先后顺序不影响，例如`ls -lha`

| 通配符 |              含义              |
| :----: | :----------------------------: |
|   *    |       代表任意个数个字符       |
|   ?    |   代表任意一个字符，至少一个   |
|   []   | 表示可以匹配字符组中的任意一个 |
| [abc]  |    匹配a，b，c中的任意一个     |
| [a-f]  | 匹配从a到f范围内的任意一个字符 |

## 2.3 cd 命令

|  命令   |                含义                |
| :-----: | :--------------------------------: |
|  `cd`   |       切换到当前用户的主目录       |
| `cd ~`  |       切换到当前用户的主目录       |
| `cd .`  |         保持在当前目录不变         |
| `cd ..` |           切换到上级目录           |
| `cd -`  | 可以在最近两次工作目录之间来回切换 |

- 相对路径：在输入路径时，最前面不是/或者~，表示相对当前目录所在的目录位置
- 绝对路径：在输入路径时，最前面是/或者~，表示从根目录/家目录开始的具体目录位置

## 2.4 创建和删除操作

### 2.4.1 touch命令

创建文件或修改文件时间

如果文件不存在，则创建一个空白文件

如果文件已经存在，则修改文件的末次修改日期

### 2.4.2 mkdir命令

创建一个新目录

| 选项 |             含义              |
| :--: | :---------------------------: |
| `-p` | 递归创建目录 `mkdir -p a/b/c` |

> ps：同一目录下，文件和子目录不能同名

### 2.4.3 rm命令

删除文件或目录，且不能恢复

| 选项 |                      含义                      |
| :--: | :--------------------------------------------: |
| `-f` |      强制删除，忽略不存在的文件，无需提示      |
| `-r` | 递归地删除目录下的内容，删除文件夹必须加该参数 |

> ps：`rm`可以像`ls`一样使用通配符

## 2.5 拷贝和移动

### 2.5.1 tree命令

tree [目录名]：以树状图列出文件目录结构

| 选项 |    含义    |
| :--: | :--------: |
| `-d` | 只显示目录 |

### 2.5.2 cp命令

`cp 源文件 目标文件`：复制文件或者目录

>`cp ~/Documents/123.txt ./123.txt`
>
>`cp ~/Documents/123.txt .` 简化

| 选项 |                             含义                             |
| :--: | :----------------------------------------------------------: |
| `-i` |                        覆盖文件前提示                        |
| `-r` | 若给出的源文件是目录文件，则cp<br/>将递归复制该目录下的所有子目录和文件，目标文件必须为一个目录名 |

### 2.5.3 mv命令

`mv 源文件 目标文件`：移动文件或者目录/文件或者目录重命名

| 选项 |      含义      |
| :--: | :------------: |
| `-i` | 覆盖文件前提示 |

## 2.6 查看和查找

### 2.6.1 cat命令

cat 文件名：查看文件内容、创建文件、文件合并、追加文件内容等功能

> 一次显示全部内容，适合查看内容较少的文本文件

| 选项 |        含义        |
| :--: | :----------------: |
| `-b` |  对非空输出行编号  |
| `-n` | 对输出的所有行编号 |

### 2.6.2 more命令

`more 文件名`：分屏显示文件内容，每次显示一页

> 分屏显示，适合查看内容较多的文本文件

| 操作键  |         功能         |
| :-----: | :------------------: |
| 空格键  |  显示手册页的下一页  |
| Enter键 | 一次滚动手册页的一行 |
|    b    |       回滚一页       |
|    f    |       前滚一页       |
|    q    |         退出         |
|  /word  |    搜索word字符串    |



### 2.6.3 grep命令

`grep 搜索文本 文件名`：搜索文本文件内容

> 允许对文本文件进行模式查找

| 选项 |                   含义                   |
| :--: | :--------------------------------------: |
| `-n` |             显示匹配行及行号             |
| `-v` | 显示不包括匹配文本的所有行（相当于求反） |
| `-i` |                忽略大小写                |

常用模式查找

| 参数  |          含义          |
| :---: | :--------------------: |
| `^a`  | 行首，搜寻以a开头的行  |
| `ks$` | 行尾，搜寻以ke结束的行 |

## 2.7 其他命令

### 2.7.1 echo和重定向

echo：会在终端中显示参数指定的文字，通常与重定向联合使用

`>`：表示输出，会覆盖文件原有的内容

`>>`：表示追加，会将内容追加到已有文件的末尾

示例：`echo hello xgy > 123.txt`

### 2.7.2 管道 |

Linux允许将一个命令的输出通过管道作为另一个命令的输入

常用的管道命令有：

`more`：分屏显示内容

`grep`：在命令执行结果的基础上查询指定的文本

# 三、远程管理常用命令

## 3.1 关机/重启

`shutdown 选项 时间`：关机/重新启动

| 选项 |   含义   |
| :--: | :------: |
| `-r` | 重新启动 |

不指定选项和参数，默认1分钟之后关闭电脑

示例：

```c
shutdown -r now
立刻重启

shutdown now
立刻关机

shutdown 20:25
今天的20:25关机

shutdown +10
10分钟后自动关机

shutdown -c
取消指定的关机计划
```

## 3.2 网卡

`ifconfig`：查看/配置计算机当前的网卡配置信息

```c
ifconfig
查看网卡配置信息

ifconfig | grep inet
查看网卡对应的ip地址
```

`ping ip地址`：检测到目标ip地址的连接是否正常

提示：在Linux中，想要终止一个终端程序的执行，绝大多数都可以使用`CTRL+C`

# 四、用户权限

## 4.1 基本概念

对文件/目录的权限包括

| 序号 | 权限 |  英文  | 缩写 | 数字 代号 |
| :--: | :--: | :----: | :--: | :-------: |
|  01  |  读  |  read  |  r   |     4     |
|  02  |  写  | write  |  w   |     2     |
|  03  | 执行 | excute |  x   |     1     |

多个用户，添加到组，统一设置权限

## 4.2 ls -l 拓展

ls -l：可以查看文件夹下文件的详细信息，从左到右依次是

- 权限：第一个字符如果是d表示目录

- 硬链接数：就是有多少种方式可以访问到当前目录/文件

```C
文件：1（绝对路径）

目录：1（绝对路径）+1（cd .）+子目录数目（cd ..）
```

- 拥有者：家目录下文件/目录的拥有者通常都是当前用户

- 组：在Linux中，多出现组名和用户名相同的情况

- 文件大小

- 修改时间

- 文件/目录名称

| 目录 | 拥有者权限 | 组权限 | 其他用户权限 |
| :--: | :--------: | :----: | :----------: |
|  -   |   r w -    | r w -  |    r - -     |
|  d   |   r w x    | r w x  |    r - x     |

## 4.3 chmod命令

`chmod +/-rwx 文件名/目录名`

修改**用户/组**对**文件/目录**的权限

提示：该方式会一次性修改**拥有者/组**的权限

## 4.4 超级用户

`sudo`：使用其他用户身份执行命令，预设身份为`root`

> 使用`sudo`时，必须输入密码，之后有5分钟有效期限

## 4.5 组管理

> 提示：创建组/删除组 的终端命令都需要通过sudo执行

| 序号 |            命令             |         作用          |
| :--: | :-------------------------: | :-------------------: |
|  01  |       `groupadd 组名`       |        添加组         |
|  02  |       `groupdel 组名`       |        删除组         |
|  03  |       `cat/etc/group`       |      确认组信息       |
|  04  | `chgrp -R 组名 文件/目录名` | 修改文件/目录的所属组 |

> 提示：
>
> - 组信息保存在/etc/group文件中
> - /etc目录是专门用来保存系统配置信息的目录

## 4.6 用户管理

### 4.6.1 新建和删除

> 提示：创建组/删除组 的终端命令都需要通过sudo执行

| 序号 |              命令              |     作用     |                             说明                             |
| :--: | :----------------------------: | :----------: | :----------------------------------------------------------: |
|  01  | `useradd -m -g 组 新建用户名`  |  添加新用户  | -m 自动建立家目录<br/>-g 指定用户所在的组，否则会建立一个同名的组 |
|  02  |        `passwd 用户名`         | 设置用户密码 |     如果时普通用户，直接用passwd，可以修改自己的账户密码     |
|  03  |      `userdel -r 用户名`       |   删除用户   |                 -r 选项会自动删除用户家目录                  |
|  04  | `cat/etc/passwd | grep 用户名` | 确认用户信息 |        新建用户后，用户信息会保存在/etc/passwd文件中         |

### 4.6.2 查看

| 序号 |     命令      |            作用            |
| :--: | :-----------: | :------------------------: |
|  01  | `id [用户名]` |   查看用户的UID和GID信息   |
|  02  |     `who`     | 查看当前所有登录的用户列表 |
|  03  |   `whoami`    |  查看当前登录用户的账户名  |

passwd文件

`/etc/passwd`文件存放的是用户的信息，由6个分号组成的7个信息，分别是

1. 用户名
2. 密码（x，表示加密密码）
3. UID（用户标识）
4. GID（组标识）
5. 用户全名或本地账号
6. 家目录
7. 登录使用的Shell，就是登录以后，使用的终端命令，Ubuntu默认是dash

### 4.6.3 主组&附加组

usermod 可以用来设置用户的主组/附加组和登录Shell

- 主组：通常在新建用户时指定，在`etc/passwd`的第4列GID对应的组
- 附加组：在`etc/group`中最后一列表示该组的用户列表，用于指定用户的附加权限

> 提示：设置了用户的附加组之后，需要重新登录才能生效

```c
usermod -g 组 用户名
修改用户的主组（passwd中的GID）

usermod -G 组 用户名
修改用户的附加组

usermod -s /bin/bash
修改用户登录Shell
```

> 注意：默认使用useradd添加的用户是没有权限使用sudo以root身份执行命令的，可以使用以下命令，将用户添加到sudo附加组中

```c
usermod -G sudo 用户名
修改用户的附加组
```

### 4.6.4 which命令

> 提示：
> /etc/passwd是用于保存用户信息的文件
> /usr/bin/passwd是用于修改用户密码的程序

which命令可以查看执行命令的所在位置

```c
which ls
输出
/bin/ls

which useradd
输出
/usr/sbin/useradd
```

补充：

在Linux中，绝大多数可执行文件都是保存在/bin、/sbin、/usr/bin、/usr/sbin

- /bin（binary）是二进制执行文件目录，主要用于具体应用
- /sbin（system binary）是系统管理员专用的二进制代码存放目录，主要用于系统管理
- /usr/bin（user commands for applications）后期安装的一些软件
- /usr/sbin（super user commands for applications）超级用户的一些管理程序

### 4.6.5 su切换用户

| 序号 |    命令    |          作用          |                  说明                   |
| :--: | :--------: | :--------------------: | :-------------------------------------: |
|  01  | su -用户名 | 切换用户，并且切换目录 | -可以切换到用户家目录，否则保持位置不变 |
|  02  |    exit    |    退出当前登录账户    |                                         |

`su`不接用户名，可以切换到`root`，不推荐使用，不安全

### 4.6.6 修改文件权限

| 序号 | 命令  |    作用    |
| :--: | :---: | :--------: |
|  01  | chown | 修改拥有者 |
|  02  | chgrp |   修改组   |
|  03  | chmod |  修改权限  |

```c
chown 用户名 文件名|目录名
修改文件|目录的拥有者

chgrp -R 组名 文件名|目录名
递归修改文件|目录的组

chmod -R 755 文件名|目录名
递归修改文件权限
```

> - -R 递归修改
>
> - 使用sudo命令

| 目录 | 拥有者权限 | 组权限 | 其他用户权限 |
| :--: | :--------: | :----: | :----------: |
|  -   |   r w -    | r w -  |    r - -     |
|  d   |   r w x    | r w x  |    r - x     |

|  r   |  w   |  x   |
| :--: | :--: | :--: |
|  4   |  2   |  1   |

|  r   |  w   |  x   |  和  | 权限 |
| :--: | :--: | :--: | :--: | :--: |
|  4   |  2   |  1   |  7   | rwx  |
|  4   |  2   |  0   |  6   | rw-  |
|  4   |  0   |  1   |  5   | r-x  |
|  r   |  0   |  0   |  4   | r--  |
|  0   |  2   |  1   |  3   | -wx  |
|  0   |  2   |  0   |  2   | -w-  |
|  0   |  0   |  1   |  1   | --x  |
|  0   |  0   |  0   |  0   | ---  |

常用组合（u表示用户，g表示组，o表示其他）

`777`===>`u=rwx，g=rwx，o=rwx`

`755`===>`u=rwx，g=r-x，o=r-x`

`644`===>`u=rw-，g=r--，o=r--`

# 五、系统信息相关

## 5.1 时间和日期

| 序号 |  命令  |                    作用                     |
| :--: | :----: | :-----------------------------------------: |
|  01  | `date` |                查看系统时间                 |
|  02  | `cal`  | calendar 查看日历，-y选项可以查看一年的日历 |

## 5.2 磁盘信息

| 序号 |       命令       |              作用               |
| :--: | :--------------: | :-----------------------------: |
|  01  |     `df -h`      |   disk free 显示磁盘剩余空间    |
|  02  | `du -h [目录名]` | disk usage 显示目录下的文件大小 |

> -h 以人性化的方式显示文件大小

## 5.3 进程信息

> 所谓进程，就是当前正在执行的一个程序

| 序号 |         命令         |                           作用                           |
| :--: | :------------------: | :------------------------------------------------------: |
|  01  |       `ps aux`       |            process status 查看进程的详细状况             |
|  02  |        `top`         |                动态显示运行中的进程并排序                |
|  03  | `kill [-9] 进程代号` | 终止指定代号的进程，-9表示强行终止，进程代号使用`ps`查看 |

> ps命令
>
> - 默认只会显示当前用户通过终端启动的应用程序
> - 接选项不需要“`-`”，多用`ps au`

| 选项 |                   含义                   |
| :--: | :--------------------------------------: |
| `a`  | 显示终端上的所有进程，包括其他用户的进程 |
| `u`  |            显示进程的详细状态            |
| `x`  |          显示没有控制终端的进程          |

> 提示：使用kill命令时，最好只终止由当前用户开启的进程，而不要终止root身份开启的进程，否则可能系统崩溃

> 退出top，直接输入q

> PID：进程代号

# 六、其他命令

## 6.1 find查看文件

| 序号 |            命令            |                    作用                     |
| :--: | :------------------------: | :-----------------------------------------: |
|  01  | `find [路径] -name "*.py"` | 查找指定路径下扩展名是.py的文件，包括子目录 |

- 如果省略命令，表示在当前文件夹下查找
- find可使用通配符

## 6.2 ln -s软链接

| 序号 |              命令               |                   作用                    |
| :--: | :-----------------------------: | :---------------------------------------: |
|  01  | `ln -s 被链接的源文件 链接文件` | 建立文件的软连接，类似于Windows的快捷方式 |

- 没有`-s`选项，则建立一个硬链接文件（两个文件占用相同大小的硬盘空间，工作中几乎不会建立文件的硬链接）
- 源文件要使用**绝对路径**，方便移动链接文件后还能正常使用

# 七、安装&压缩

## 7.1 apt安装

`apt`是`advanced packaging tool`，可以在终端中安装/卸载/更新软件包

> 必须使用sudo命令

```c
sudo apt install 软件包
安装软件

sudo apt remove 软件名
卸载软件

sudo apt upgrade
更新已安装的包
```

## 7.2 打包压缩

### 7.2.1 tar命令

`tar`是`Linux`常用的备份工具，此命令可以把一系列文件打包到一个大文件中，也可以把一个打包的大文件恢复成一系列文件

```c
tar -cvf 打包文件.tar 被打包的文件/路径（多个文件用空格隔开）
打包文件

tar -xvf 打包文件.tar
解包文件
```

| 选项 |                          含义                           |
| :--: | :-----------------------------------------------------: |
| `c`  |               生成档案文件，创建打包文件                |
| `x`  |                      解开档案文件                       |
| `v`  |            列出归档解档的详细过程，显示进度             |
| `f`  | 指定档案文件名称，f后面一定是`.tar`文件，必须放选项最后 |

注意：`f`选项必须放最后，其他选项顺序随意

### 7.2.2 gzip命令

`gzip`命令可以与`tar`命令结合实现文件的打包和压缩

> - `tar`只负责打包文件，但不压缩
> - `gzip`压缩打包文件，扩展名为`xxx.tar.gz`

使用`tar`命令时，添加`-z`选项，便可以调用`gzip`

```c
tar -zcvf 打包文件.tar.gz 被压缩的文件/路径
压缩文件

tar -zxvf 打包文件.tar.gz
解压缩文件

tar -zxvf 打包文件.tar.gz -C 目标路径
解压缩到指定路径
```

| 选项 |                             含义                             |
| :--: | :----------------------------------------------------------: |
|  -C  | 解压缩到指定目录（指定目录必须存在） 同时适用于`gzip`和`bzip2` |

### 7.2.3 bzip2命令

`bzip2`命令可以与`tar`命令结合实现文件的打包和压缩

> - `tar`只负责打包文件，但不压缩
> - `bzip2`压缩打包文件，扩展名为`xxx.tar.bz2`

使用`tar`命令时，添加`-j`选项，便可以调用`bzip2`

```c
tar -jcvf 打包文件.tar.bz2 被压缩的文件/路径
压缩文件

tar -jxvf 打包文件.tar.bz2
解压缩文件
```