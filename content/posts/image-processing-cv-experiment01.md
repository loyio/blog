---

title: "图像处理第一次实验-初识CV"
date: 2021-03-20T21:14:43+08:00
#description: <descriptive text here>
# weight: 1
# aliases: ["/first"]
tags: ["图像处理", "Pillow", "灰度化", "模糊化", "手绘效果", "Python"]
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



1.jpg

![1_processed_blur](https://cdn.jsdelivr.net/gh/loyio/oss@main/blogs/2021/07/ijod171_processed_blur.jpg)



2.jpg

![2.jpg](https://cdn.jsdelivr.net/gh/loyio/oss@main/blogs/2021/07/OZjOMh2.jpg)



## 1.对1.jpg 分别作灰度化, 模糊化处理.

代码如下

```python
"""
 @Project: imageProcessing
 @Author: loyio
 @Date: 3/20/21
"""
from PIL import Image, ImageFilter

if __name__ == '__main__':
    # greyscale
    imgfileOne = "Sample/1"
    sample_img = Image.open(imgfileOne+".jpg").convert('L')
    sample_img.save(imgfileOne+"_processed_gray.jpg")

    # Blur
    # sample_img = Image.open(imgfileOne+".jpg").filter(ImageFilter.BLUR)
		sample_img = Image.open(imgfileOne+".jpg").filter(ImageFilter.BoxBlur(5))
    sample_img.save(imgfileOne + "_processed_blur.jpg")
```

图片效果如下

灰度处理

![1_processed_gray](https://cdn.jsdelivr.net/gh/loyio/oss@main/blogs/2021/07/Vf11QI1_processed_gray.jpg)



模糊处理

![1_processed_blur](https://cdn.jsdelivr.net/gh/loyio/oss@main/blogs/2021/07/qbO1eq1_processed_blur%201.jpg)



## 2.对2.jpg生成手绘效果

代码如下

```python
"""
 @Project: imageProcessing
 @Author: loyio
 @Date: 3/20/21
"""
from PIL import Image, ImageFilter
import numpy as np

if __name__ == '__main__':
    # Paint
    imgfileTwo = "Sample/2"
    sample_img_ary = np.asarray(Image.open(imgfileTwo+".jpg").convert('L')).astype('float')

    depth = 10.
    grad_x, grad_y = np.gradient(sample_img_ary)
    grad_x = grad_x * depth / 100.
    grad_y = grad_y * depth / 100.

    A = np.sqrt(grad_x ** 2 + grad_y ** 2 + 1.)
    uni_x = grad_x / A
    uni_y = grad_y / A
    uni_z = 1. / A

    vec_el = np.pi / 2.2
    vec_az = np.pi / 4.
    dx = np.cos(vec_el) * np.cos(vec_az)
    dy = np.cos(vec_el) * np.sin(vec_az)
    dz = np.sin(vec_el)

    sample_processed_ary = (255 * (dx*uni_x + dy*uni_y + dz*uni_z)).clip(0, 255)

    im = Image.fromarray(sample_processed_ary.astype('uint8'))
    im.save(imgfileTwo+"_processed_handpaint.jpg")
```

1. 首先将图片灰度化，然后转换为float类型，存放在numpy array中
2. 通过`np.gradient`求灰度图像的梯度（即灰度的变化率），将其赋值给`grad_x`, `grad_y` ，并根据深度级别计算新的梯度，同时归一化。将其控制在（0，1）
3. 为x,y轴梯度构建三维归一化单位坐标系。
4. 建立光源效果，可以将`np.cos(vec_el)`分析为单位射线在地平面上的投影长度。 `dx`，`dy`和`dz`是光源在x / y / z方向上的影响。
5. 梯度与光源相互作用，最终将梯度转换为灰度。即`sample_processed_ary = 255 * (dx*uni_x + dy*uni_y + dz*uni_z)` 
6. 为避免越过边界，最后还要调用函数`.clip(0,255)` 

图片效果如下

![2_processed_handpaint.jpg](https://cdn.jsdelivr.net/gh/loyio/oss@main/blogs/2021/07/W4fHYO2_processed_handpaint.jpg)

手绘效果

