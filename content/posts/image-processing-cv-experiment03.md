---
title: "图像处理第三次实验-图像预处理"
date: 2021-03-26T21:25:11+08:00
#description: <descriptive text here>
# weight: 1
# aliases: ["/first"]
tags: ["图像处理", "Fiji", "灰度化", "模糊化", "手绘效果", "Python"]
categories: ["图像处理实验WTU"]
showToc: true
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

## 一.对比度优化方法CLAHE

### 1.使用软件fiji优化图片序列

实验过程：

1）下载安装Fiji

2）解压`30-T4N2, 24_pre_waterT1C.nii.zip` 

3）打开一张图片

4）在fiji中, Process -> Enhance Local Contrast（CLAHE, Contrast Limited Adaptive Histogram Equalization 直方图均衡化算法），将参数设置为如下，观察图片变化

blocksize = 64
histogram bins = 128
max slope = 2.0

![](https://cdn.jsdelivr.net/gh/loyio/oss@main/blogs/2021/07/Ip3gCdUntitled.png)

图片效果如下

{{< figure align="left" src="https://cdn.jsdelivr.net/gh/loyio/oss@main/blogs/2021/07/tRBEfMUntitled%201.png" title="原图" >}}

![原图]()

{{< figure align="right" src="https://cdn.jsdelivr.net/gh/loyio/oss@main/blogs/2021/07/krJHSkUntitled%202.png" title="处理后的图" >}}



可以看到部分区域对比度增强，图像中体现的信息也更为突出。

### 2.使用fiji脚本批量处理一组图片

1）使用fiji打开`16-T2N2,33+_post_waterT1C.nii.gz` 

![](https://cdn.jsdelivr.net/gh/loyio/oss@main/blogs/2021/07/OOS7A9Untitled%203.png)

2）使用Fiji's scripting editor，将语言更改为IJ1 Macro，运行脚本

![](https://cdn.jsdelivr.net/gh/loyio/oss@main/blogs/2021/07/Untitled%204.png)

![](https://cdn.jsdelivr.net/gh/loyio/oss@main/blogs/2021/07/Untitled%205.png)

3）最后点击菜单栏`File` → `Save As` → `Image Sequence` 

保存为png格式，存储在文件夹中。

## 二.图像x-ray去噪

使用median filter算法，批处理文件`/x-ray-images-enhancement-master/images/` 

中值滤波器：中值滤波器是众所周知的阶数统计滤波器之一，因为它对某些特定的噪声类型（例如“高斯”，“随机”和“盐和胡椒”噪声）具有良好的性能。根据中值滤波器，将M×M邻域的中心像素替换为相应窗口的中值。注意，噪声像素被认为与中值有很大差异。使用这种思想，中值滤波器可以消除这种类型的噪声问题。

批处理代码实现如下：

```python
path='images/'
file_list = [f for f in os.listdir(path) if not f.startswith('.')]
file_num = len(file_list)
i = 1
print("file_num", file_num)
for img_dir in file_list:
    im = Image.open("images/"+img_dir)
    for sz in [3, 7, 15]:
        im1 = im.filter(ImageFilter.MedianFilter(size=sz))
        im.save("imagesProcessed/"+"spnoise_"+str(sz)+"_"+img_dir)
    print(img_dir + " processed")
```

这里我们通过调节size来观察效果。

其中一张图片对比如下；

原图003：

{{< figure src="https://cdn.jsdelivr.net/gh/loyio/oss@main/blogs/2021/07/003.jpg" title="原图003" >}}

其中一张图片003的输出如下

{{< figure src="https://cdn.jsdelivr.net/gh/loyio/oss@main/blogs/2021/07/123.png" title="图片输出" >}}
