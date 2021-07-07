---
title: "pip安装模块时报错 ModuleNotFoundError:No module named '_ctypes'"
date: 2020-05-06T19:51:51+08:00
#description: <descriptive text here>
# weight: 1
aliases: ["/2020/05/06/pip-install-module-error-ctypes"]
tags: ["pip", "python", "解决错误"]
categories: ["Python"]
showToc: false
TocOpen: false
draft: false
hidemeta: false
comments: true
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

最近一直在折腾GoogleDrive，用了rclone，又装AutoClone，最近又用上了gclone

在安装AutoClone依赖文件时报错



```bash
ERROR: Command errored out with exit status 1:
     command: /usr/local/python3/bin/python3.8 -c 'import sys, setuptools, tokenize; sys.argv[0] = '"'"'/tmp/pip-install-c6woj60b/progress/setup.py'"'"'; __file__='"'"'/tmp/pip-install-c6woj60b/progress/setup.py'"'"';f=getattr(tokenize, '"'"'open'"'"', open)(__file__);code=f.read().replace('"'"'\r\n'"'"', '"'"'\n'"'"');f.close();exec(compile(code, __file__, '"'"'exec'"'"'))' egg_info --egg-base pip-egg-info
         cwd: /tmp/pip-install-c6woj60b/progress/
    Complete output (11 lines):
    Traceback (most recent call last):
      File "<string>", line 1, in <module>
      File "/usr/local/python3/lib/python3.8/site-packages/setuptools/__init__.py", line 20, in <module>
        from setuptools.dist import Distribution, Feature
      File "/usr/local/python3/lib/python3.8/site-packages/setuptools/dist.py", line 35, in <module>
        from setuptools import windows_support
      File "/usr/local/python3/lib/python3.8/site-packages/setuptools/windows_support.py", line 2, in <module>
        import ctypes
      File "/usr/local/python3/lib/python3.8/ctypes/__init__.py", line 7, in <module>
        from _ctypes import Union, Structure, Array
    ModuleNotFoundError: No module named '_ctypes'
    ----------------------------------------
ERROR: Command errored out with exit status 1: python setup.py egg_info Check the logs for full command output.
```

Google了一下，找到解决方法是安装 `libffi-devel`

Python3中有个内置模块叫ctypes，它是Python3的外部函数库模块，它提供兼容C语言的数据类型，并通过它调用Linux系统下的共享库，此模块需要使用CentOS7系统中外部函数库的开发链接库(头文件和链接库)。
由于在CentOS7系统中没有安装外部函数库(libffi)的开发链接库软件包，所以用pip安装模块的时候就报了`ModuleNotFoundError: No module named ‘_ctypes’`的错误。

于是输入下面的命令进行了安装

```bash
yum -y install libffi-devel
```

然后再次执行命令

```bash
pip3 install -r requirements.txt
```

还是报同样的错，又试着找了很多博客，最后才发现问题，就是安装好 `libffi-devel` 后，要回到 python文件夹，重新编译安装

```bash
cd /root/Python-3.8.2
make && make install
```

然后就可以重新安装pip模块了
