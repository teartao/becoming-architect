# 前端布局笔记



## 常见布局方式：

https://blog.csdn.net/zhang79513/article/details/102666861

1. 静态布局
2. 弹性布局（flexbox）
3. 自适应布局（bootstrap）
4. 流式布局（fluid）
5. 响应式布局
6. 浮动布局
7. 定位布局



其中PC常用的以静态布局为主，可和混合浮动布局定位布局综合使用。

弹性布局、自适应布局、流式布局、响应式布局常用于移动端适应不同尺寸的移动设备



**本文主要介绍PC常用的布局方式，涉及的css属性如下：**

外边距：margin （含 margin-left margin-top margin-right margin-bottom）

内边距：Padding ( padding-left padding top padding-right padding-bottom)

display : 块元素（block）；行内块元素（ inline-block）；行内元素（ inline ）

position ：静态（static ）相对位置（relative）绝对位置（absolute）固定位置（fixed）

left top right bottom

浮动（float）：left right



## 基础认识：

说到css布局肯定要提一下『盒模型』，所谓盒模型可以理解为：

页面元素都是一个个大小不一的盒子，大盒子套小盒子；

大盒子中可以放下一行或者多行小盒子。

大盒子中每一行盒子内部还可以放更小的盒子，(方形套娃🐶)

这里的盒子不要完全理解成生活中的盒子，因为生活中的盒子都是有厚度的，css的盒子可以厚度为0( border = 0 )

![image-20210710172014027](./imgs/image-20210710172014027.png)























有了盒模型的概念，元素间便有了父parent / 子children /兄弟 (前一个prev，后一个 next)

上面的图可以看成：

**最外面红色**理解成浏览器窗口，就是window，里面有各种各样元素。

**第一行**有1 2 两个红色大框

**第二行**有一个红色大框，里面有蓝色 绿色小框 7 8 9 等等

**第三行**有三个红色大框 3 4 5



第二行的红色框其实可以不用，但是如果里面蓝色绿色是一个大的整体，那么最好是套一层，以便于后面统一移动比如变成下面这样

![image-20210710172403084](./imgs/image-20210710172403084.png)

这样只要移动一下原来第二行的大框，所有的小元素就 可以很简单地移动到1 2的上方。

说到这里就需要提一下文档布局地规划：

虽然css地盒模型可以随意嵌套， 比如"田" 字 布局可以设计成左右两个"日"  也可以设计成 上下两个横过来的"日"，

但是如果页面结构根据我们习惯 一看就是左右结构，那么你肯定不能设计为上下结构布局，

万一需要调整，那么你的上下结构就会很难分割或者太过零散导致修改工作量巨大。



比如下面的w3c网站，看上去多半是我下面画的这种布局方式。

![image-20210710173010503](./imgs/image-20210710173010503.png)



下面这种规划肯定也是可以的

![image-20210710173145928](./imgs/image-20210710173145928.png)



上面这两种基本是把文档分成了 头部(logo + 搜索)

一级导航：灰色的 html css browser sige ...

二级导航： 左侧菜单

内容：xxxx

三级导航(快速导航): 参考手册



这样一看，内容就各自放在一个大盒子里，如果你非要下面这样规划，看看会不会觉得奇怪？

![image-20210710173512910](./imgs/image-20210710173512910.png)



上面这个布局硬生生把二级导航的"html 教程"和 "浏览器脚本" 分成了凉快，参考手册也变成了上下两块，这样显然不符合我们正常理解的文档结构，不是说不可以，但是这会不会很奇怪？

万一二级导航哪天变成了横向的，放在一级导航下面，不就不好改了嘛，是不是？



**所以：**盒模型第一步是按照页面布局，把文档划分为合理的文档结构，头部，导航菜单，左侧，右侧，内容等等 各自在一个盒子里，盒子里面可以一层，也可以根据内容嵌套多层盒子，所有的盒子都是为了把内容合理地划分归类，便于整体修改和移动。



## 外边距 margin

外边距主要用于移动元素本身，可以理解为修改该元素在父元素中地位置，这个操作会统一移动元素内部的所有子元素。比如，你把书架上的文具盒拿了下来，那么文具盒里面的铅笔是不是都被拿走了？

(有的元素可以通过css属性脱离父元素，这个后面会说)

<img src="./imgs/image-20210710174332352.png" alt="image-20210710174332352" style="zoom: 33%;" />



比如上面的例子，我们把黑色框里面的大红框移到了第一行，那么里面所有小元素就都到了上面一行。

![image-20210710175858018](./imgs/image-20210710175858018.png)

通过浏览器检查元素也可以看见，当选中最大的红框时，将鼠标箭头移动到调试框(左下)的margin部分，会在页面元素(右边)看到同样橙色的边框，修改红框的`margin:20px ` 中的值，便可以看到大红框内部的所有元素都跟着移动了。随着20增大 边距变大，20缩小，边距变小



**所以：**margin是移动元素(修改元素本身所在的位置)，以父元素为参考，调整它在父元素中的位置。



并且该属性会让后面的兄弟节点跟着移动（挤掉兄弟节点的空间 / 让出空间给兄弟节点)。

如果元素往右移动，那么它后面的兄弟也被挤到右边，不够的话，兄弟会换行。



## 内边距：padding






![image-20210710175813794](./imgs/image-20210710175813794.png)





































