---
title: "使用谷歌云搭建google drive离线下载服务器"
date: 2020-04-28T11:43:18+08:00
#description: <descriptive text here>
# weight: 1
aliases: ["/2020/04/28/gcp-create-gdrive-download-server"]
tags: ["Aria2","Google Drive", "GCP", "gclone", "谷歌云"]
categories: ["服务器搭建"]
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: true
canonicalURL: "https://canonical.url/to/page"
disableShare: false
disableHLJS: false
hideSummary: false
searchHidden: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
cover:
    image: "<image path/url>" # image path/url
    alt: "<alt text>" # alt text
    caption: "<text>" # display caption under cover
    relative: false # when using page bundles set this to true
    hidden: true # only hide on current single page
---

#### 1.在google云中创建一个实例

选择可用的地区，这里我选择的是新加坡，然后下面服务器配置选择Micro，允许http和https访问，最后点击创建，等待一会儿，点击右侧ssh连接服务器终端

#### 2.安装rclone

我们使用官方的脚本进行安装

首先我们需要安装解压工具

```bash
yum -y install unzip
```

然后使用官方提供的命令

```bash
curl https://rclone.org/install.sh | sudo bash
```

稍等一会儿就安装成功了



#### 3.配置rclone

安装完成后，我们在命令行输入以下代码

```bash
rclone config
```

下面就开始进行配置操作

首先是创建一个新连接

```bash
n/s/q> n
```

输入名称(自己随便输入)

```bash
name> gdShare
```

然后下面类型输入drive

```bash
Storage> drive
```

后面两步都直接回车，不输入

```bash
client_id>
client_secret>
```

下一步选择第一个选项

```bash
scope> 1
```

再后面两步也是直接回车不输入

```bash
root_folder_id>
service_account_file>
```

是否编辑预先配置，我们选择No

```bash
y/n> n
```

使用自动配置我们这里也是选择No

```bash
y/n> n
```

这时候会出来一段链接，点击直接打开或者复制用浏览器打开都可以，打开后，这里会要你登录你想挂载的google drive的账号，授权选择允许后会生成一个代码，将代码复制到下面的选项中就可以了

```bash
Enter verification code> 【生成的代码】
```

然后会让你选择是否是团队账号，这里我们默认选择No

```bash
y/n> n
```

然后下一步我们选择yes完成创建

```bash
y/e/d> y
```

然后可以看到我们创建的项目了

最后输入q退出配置

```bash
e/n/d/r/c/s/q> q
```

#### 4.挂载磁盘

创建一个文件夹来挂载磁盘

```bash
mkdir /mnt/googledrive
```

在挂载之前，我们要先安装fuse文件系统

```bash
yum -y install fuse
```

然后输入挂载命令

```bash
rclone mount gdShare:/ /mnt/googledrive/ --allow-other --allow-non-empty --vfs-cache-mode writes &
```

输入命令查看是否挂载成功

```bash
# df -h
Filesystem      Size  Used Avail Use% Mounted on
devtmpfs        285M     0  285M   0% /dev
tmpfs           294M     0  294M   0% /dev/shm
tmpfs           294M  4.4M  289M   2% /run
tmpfs           294M     0  294M   0% /sys/fs/cgroup
/dev/sda2        20G  2.2G   18G  11% /
/dev/sda1       200M   12M  189M   6% /boot/efi
tmpfs            59M     0   59M   0% /run/user/1000
gdShare:         15G  848K   15G   1% /mnt/googledrive
```

可以看到gdShare已经在上面了

#### 5.设置开机自动挂载

每次开关机服务器，rclone都要重新手动挂载，为了方便，我们设置自动挂载命令

首先新建一个rclone.service文件

```bash
vim /usr/lib/systemd/system/rclone.service
```

写入

```bash
[Unit]
Description=rclone
    
[Service]
User=root
ExecStart=/usr/bin/rclone mount gdShare:/ /mnt/googledrive/ --allow-other --allow-non-empty --vfs-cache-mode writes
Restart=on-abort
    
[Install]
WantedBy=multi-user.target
```

保存退出后

重载daemon,让新的服务文件生效

```bash
systemctl daemon-reload
```

然后我们就可以通过systemctl来启动clone了

```bash
systemctl start rclone
```

设置开机自启

```bash
systemctl enable rclone
```

重启你的服务器，然后看一下rclone的服务启动了没有，再查看一下谷歌硬盘有没有挂载成功：

```bash
reboot
systemctl status rclone
df -h
```

#### 6.安装Aria2

我们这里要使用到wget，所以先安装wget

```bash
yum -y install wget
```

然后我们使用P3TERX的一键安装版本

```bash
wget -N git.io/aria2.sh && chmod +x aria2.sh && ./aria2.sh
```

首先我们输入1，安装Aria2，然后这个脚本会自动安装并启动Aria2

安装时间可能比较长，会卡在一个地方很久，请不要中断安装，等待即可

#### 7.配置自动上传脚本

我们创建一个脚本

```bash
vim rcloneupload.sh
```

填入以下内容,记得RemoteDIR和LocalDIR根据自己的实际情况进行设置

```shell
#!/bin/bash

GID="$1";
FileNum="$2";
File="$3";
MinSize="5"  #限制最低上传大小，默认5k
MaxSize="157286400"  #限制最高文件大小(单位k)，默认15G
RemoteDIR="/mnt/googledrive/";  #rclone挂载的本地文件夹，最后面保留 /
LocalDIR="/root/download/";  #Aria2下载目录，最后面保留 /

if [[ -z $(echo "$FileNum" |grep -o '[0-9]*' |head -n1) ]]; then FileNum='0'; fi
if [[ "$FileNum" -le '0' ]]; then exit 0; fi
if [[ "$#" != '3' ]]; then exit 0; fi

function LoadFile(){
  IFS_BAK=$IFS
  IFS=$'\n'
  if [[ ! -d "$LocalDIR" ]]; then return; fi
  if [[ -e "$File" ]]; then
    FileLoad="${File/#$LocalDIR}"
    while true
      do
        if [[ "$FileLoad" == '/' ]]; then return; fi
        echo "$FileLoad" |grep -q '/';
        if [[ "$?" == "0" ]]; then
          FileLoad=$(dirname "$FileLoad");
        else
          break;
        fi;
      done;
    if [[ "$FileLoad" == "$LocalDIR" ]]; then return; fi
    EXEC="$(command -v mv)"
    if [[ -z "$EXEC" ]]; then return; fi
    Option=" -f";
    cd "$LocalDIR";
    if [[ -e "$FileLoad" ]]; then
      ItemSize=$(du -s "$FileLoad" |cut -f1 |grep -o '[0-9]*' |head -n1)
      if [[ -z "$ItemSize" ]]; then return; fi
      if [[ "$ItemSize" -le "$MinSize" ]]; then
        echo -ne "\033[33m$FileLoad \033[0mtoo small to spik.\n";
        return;
      fi
      if [[ "$ItemSize" -ge "$MaxSize" ]]; then
        echo -ne "\033[33m$FileLoad \033[0mtoo large to spik.\n";
        return;
      fi
      eval "${EXEC}${Option}" \'"${FileLoad}"\' "${RemoteDIR}";
      if [[ $? == '0' ]]; then
        rm -rf "$FileLoad";
      fi
    fi
  fi
  IFS=$IFS_BAK
}
LoadFile;
```

给脚本添加可执行权限

```bash
chmod +x rcloneupload.sh
```

然后再编辑Aria2配置文件，设置下载完成后执行的命令为rcloneupload.sh

```bash
vim /root/.aria2/aria2.conf
```

内容如下所示

```conf
# 下载完成后执行的命令
# 此项未定义则执行下载停止后执行的命令（on-download-stop）
on-download-complete=/root/rcloneupload.sh
```

最后重启aria2即可

```bash
service aria2 restart
```

#### 8.使用可视化面板进行操作

Aria2只是一个命令行程序，我们在这里需要配合前端面板才能获得更好的操作体验，AriaNg就是一个很不错的前端面板，但是，在这里我使用的是一个本地程序，他可以支持Windows和macOS，不需要用浏览器

项目地址如下

https://github.com/mayswind/AriaNg-Native

下载合适的版本后，我们安装打开首先设置RPC，地址也就是你Aria2的服务器ip，协议我们选择http，请求方法为POST，密钥也就是我们在服务端生成的密钥

视频教程请访问

Youtube https://youtu.be/GFtZHti6P78

Bilibili https://b23.tv/Efpg4F