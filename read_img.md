CV中的常见读取操作

> path = '1.jpg'

## 1.scipy.misc (imageio)
这个库老版本(1.3.0)是用 imread()和 imwirte()完成操作,

新版本改用imageio
```
import imageio
a1 = imageio.imread(path)
plt.imshow(a1)
plt.show()
imageio.imwrite('imageio.png',im2)

#默认4通道,且像素范围是0-255的整数
print(a1.dtype)
print(a1.size)
print(a1.shape)
```

## 2.PIL
这个是默认为存在一个图片对象中，处理自带对象方法或转换为数组

> RBG模式下维度顺序: [h,w,c]
```
from PIL import Image
a2= Image.open
a2.show()

#互转,也是4通道，0-255整数
im1  = np.array(a2)
im2   = Image.fromarray(im1)

im2.save('t1.png')
```

## 3.matploblib
- 这个是最直接的通过数组(像素)操作图片,

- 读取图片类型为np,值域为[0,1],维度为[h,w,c] 

- 存储的时候做过优化，0-1和0-255的都可以存储(-1->1的不行)

```
import matplotlib.image
import matplotlib.pyplot as plt

a3 = matplotlib.image.imread(path)
matplotlib.image.imsave('t2.png', a3)

plt.imshow(a3)
plt.show()

```

## 4.opencv

这个很经典，以前是c++的图像处理库

- 在python中安装时是叫
>pip install opencv-python

- 导入时是叫
>import cv2

- 这个导入默认是3通道的，也是0-255整数，但是其顺序是BGR,和所有上面的顺序(RGB)相反


```
import cv2

a4 = cv2.imread(path)
cv2.imwirte('t3.png',a4)

```
