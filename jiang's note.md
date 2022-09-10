# 01-移动端

## day01

## 1.字体图标

长的像图片的字体
使用场景：简单、单一的小图标
优势：体积小，加载速度快。更改样式CSS。不会失真。

## 2.iconfont使用

1.下载
2.解压，放到项目位置
3.打开demo
4.选择第二个选项font class 
5.引入css（注意路径）
6.复制标签<span class="iconfont icon-xxx"></span>
7.选择你喜欢的字体图标放在XX中 更新字体包
SVG图标  UI设计师

## 3.平面转换

平移、旋转、缩放、倾斜

### ①平移-translate

```css
transform:translate(x,y); /*同时控制X，y轴方向*/
transform:translate(%,%);  /*%相对于自身的大小*/
transform:translateX(200px);
transform:translateY(100px);/*下层覆盖上层，只能实现一个*/
```

### ②旋转-rotate

```css
transform:rotate(30deg);/*所有的2D效果的属性名都叫transform*/
```

正值顺时针 负值逆时针

#### 设置中心点-origin：		

```css
transform-origin:left bottom;
transform-origin:0px 0px;
transform-origin:0% 0%;/*相对于盒子本身大小进行百分比旋转*/
```

如果要同时设置多个属性：空格

```css
transform:translateX(1000px) rotate(720deg);
```

##### 注：2D属性的顺序不同，可能会影响最终的结果（一般情况先偏移再旋转）

### ③缩放-scale

```css
transform:scale(x,y);
transformX:scale(x);
transformY:scale(y);
/*x，y填数字*/
```

​     注意：当x，y的数值相同时，可以只写一个

### ④倾斜-skew

让图片、盒子倾斜、倒下

```css
transform: skew(13deg,0deg);
transform: skewX(13deg);
transform: skewY(13deg);
```

### ⑤渐变-linear/radical-gradient

让背景颜色从一种颜色过渡到另一种（多种）颜色
      

```css
background:linear-gradient(方向（省略）,颜色1，颜色2);
/*线性渐变*/
background:radical-gradient(方向（省略）,颜色1，颜色2);
/*径向渐变*/
```

## day02

## 4.3D

### ①空间转换-transform

又称3D转换 属性：transform
          场景：绝对定位居中

### ②空间位移

```css
transform:translate3d(x,y,z)
transform:translateX(x)
transform:translateY(y)
transform:translateZ(z)
```

### 透视语法

```css
perspective:1000px;     
//取值最好800-1000px 近大远小。写在父级
```

### ③空间旋转

场景：模拟翻书、翻台历、风车
语法：rotateZ和rotate效果一样

```css
transform: rotateZ(360deg);
transform: rotate3d(x,y,z,角度度数);用来设置自定义旋转轴的位置及旋转角度，取值0-1
```

### 呈现立体图形：代码演示

```css
transform-style:preserve-3d;                 
//使子元素处于真正的3d空间
transform-style:flat;
//子元素不开启3d立体空间 默认值，以平面去展示
```

### ④空间缩放

语法：

```css
transform:scale3d(x,y,z)
transform:scaleeX(x)
transform:scaleY(y)
transform:scaleZ(z)   必须为倍数
```

## 5.动画

替代一些简单的动图、效果

### ①定义动画  方法一

```css
@keyframes 动画名称{
                        from{
                              从哪里来
                        }
                        to{
                              到哪里去
                        }
}
```

### ②定义动画 方法二

```css
@keyframes 动画名称{
      0%{} 10%{} 15%{} 100%{}
}
```

### ③调用动画：

```css
animation:名称 2s;
```

### ④动画的复合属性：

```css
animation:动画名称 动画时长 速度曲线 延迟时间 重复次数 动画方向 执行完毕时状态;
                   animation:change 1s linear/steps(3) 1s infinite/alternate/normal/backwards/forwards;//取值不分先后
无限循环/逆向循环/正向循环/
```

##### <!-- 名称和时长是必填项 -->

```css
@keyframes 动画名称{
        from{从哪里来}
        to{到那里去}
        }
```

百分比控制
名称	                               属性	                                             说明	                              属性值
动画名称	                      animation-name	                           动画名称	
动画时长	                      animation-duration	                       动画执行时间	
速度曲线	                      animation-timing-function	            动画执行速度	               linear 匀速
                                        ease                                                 先慢后快再慢
                                        ease-in                                             先慢后快
                                        ease-out                                           先开后慢
延迟时间	                      animation-delay	                            动画延迟时间	
重复次数	                      animation-itearaion-count	             动画执行次数	n 次数
                                        infinite                                              是无限次数
动画方向	                      animation-direaction	                     动画执行完毕后
继续执行的方向	           normal                                               正向
                                        alternate                                            逆向
动画执行完毕时状态	   animation-fill-mode	                        动画执行完毕后
保持位置	                     backwoards                                       回到初始位置
                                        forwards                                             停在终点位置
动画播放状态	              animation-play-state	

动画是否停止	              running运行
                                        paused                                              停止

## day03

## 6.物理分辨率 

手机出厂的配置 2K3K4K   2000px、3000px 越大越好 不可改变

## 7.逻辑分辨率 

由软件（驱动）决定。

## 8.视口标签

制作适配不同设备宽度的网页，网页宽度和设备宽度（分辨率）相同

<meta name="viewport" content="width=device-width,initial-scale=1.0">'
不写适口这句话，网页会按照980的默认标准来
手机开发以逻辑像素为标准
相比网页，手机逻辑像素（尺寸）变小，但里面的物理像素不变，所以写逻辑像素时会根据比例放大物理像素

pc逻辑像素和物理像素比：1：1
手机逻辑像素和物理像素比：1：2
如果图片本身就是100*100 写成了100*100 真正的物理200*200，图片会失真变模糊。

## 9.二倍图：

能够使用像素大厨软件测量二倍图中元素的尺寸 

## 10.百分比布局：

又称流式布局。//宽度自适应，高度固定

```css
width:100%;height:50px;
```



## 11.弹性布局(flex布局/伸缩布局)：

### ①优点：

​	  1、是一种浏览器提倡的布局模型
​      2、布局网页更简单、灵活
​      3、避免浮动脱标的问题 有兼容性问题

### ②设置方式：

①给父元素添加display:flex;     //子元素可以自动的挤压或拉伸
②调节主轴或侧轴的对齐方式来设置盒子之间的间距：
③写在父身上，让子元素开启弹性布局，写在父级身上，控制子元素

### ③修改主轴对齐方式（添加在父级）：

#### 1.从左至右：

justify-content：flex-start

#### 2.从右至左

justify-content：flex-end

#### 3.居中

justify-content：center

#### 4.平均分配：两端对齐，剩下空间平分

justify-content：space-between

#### 5.平均分配：每一个元素都拥有属于自己的左右间距

justify-content：space-around

#### 6.平均分配：每一个元素间距完全一样

justify-content：space-evenly

### ④修改侧轴对齐方式：

align-items：flex-start  默认值, 起点开始依次排列
align-items：flex-end  终点开始依次排列
align-items：center 沿侧轴居中排
align-items：stretch 默认值, 弹性盒子沿着主轴线被拉伸至铺满容器  //需去除子盒子的高度

### ⑤控制单个盒子:

align-self：flex-start
align-self：flex-end  
align-self：center 
align-self：stretch

### ⑥flex-弹性伸缩比：

占用父级剩余尺寸的份数 ：

```css
flex:1;
```

如果其中一个使用，获取剩余的所有：flex：1
如果多个使用flex：1，平分剩下的所有
如果多个使用flex不同数值，按照不同的个比例划分。

<!-- 子元素特点：可以设置宽高 并且由内容撑开 -->、
<!-- flex一旦使用，其他的布局将失效 -->

### ⑦修改主轴方向：

```css
flex-direction:  ;
             row        //默认值（水平），行
             column     //列 垂直 最重要
             row-reverse //行，从右向左
             column-reverse //列，从下向上
```



### ⑧弹性盒子换行flex-wrap：

```css
flex-wrap:wrap;
不换行：flex-wrap:nowrap
```

### ⑨调节侧轴对齐方式（多行）：									  

```css
align-content:center;
space-around
space-between
```

### ⑩调节侧轴对齐方式（单行）：

```css
align-items  
```



## day05



## 12.移动适配（rem）:

①rem:目前多数企业在用的解决方案单位
    让网页实现宽度、高度、字体（等比缩放）都跟随移动屏幕大小变化。

​	rem和em都是相对单位
​	rem相对于html根标签的font-size 

​	//所有的标签都只和HTML挂钩，改变某一元素，不会对里面的子元素产生影响
​	em相对于父级的标签的font-size //维护的工作量较大
​	vw/vh:未来的解决方案

​	1rem=1html标签字号大小
​	min-width{从小到大写}
​	max-width{从大到小写}

### rem布局：长度单位 

作用：实现网页等比例缩放
场景：非常多的移动端/移动端适配
1rem=1HTML字号大小

跟随HTML的根标签的字体大小变化而变化
所有的标签都只跟html有关，改变中间不会对子元素造成影响

## 13.媒体查询 （手动写）

作用：根据屏幕大小来改变css样式

```css
@media(width:375px){  html{}  div{};}
 @media(max/min-width:375px){  html{}  div{};}
```

 当屏幕条件符合设定条件的时候，触发对应的样式。
 顺序，严格要求：

#### 注：

连续的max：从大到小写
连续的min：从小到大写

#### 交集区间（and连接）：

and连接：

```css
@media(width:375px) and （width：414px）
```

特性属性：width、height、max-width、min-width、max-height、min-height、orientation（屏幕方向）|portrait竖屏 landscape横屏

另一种link写法：<link rel="stylesheet" href="./one.css" media="=(min-width:992px)">

## 14.替代媒体查询（自动写） flexible.js 

作用：替代媒体查询，自动的识别屏幕宽度，换算HTML的font-size
flexible.js是手淘开发出的一个用来适配移动端的js框架。
核心原理就是根据不同的视口宽度给网页中html根节点设置不同的font-size。
语法:<script src="./flexible.js"></script>
步骤：在网页的最后加入

## 15.px转换rem的公式 

rem值=测量的值px/html根标签的font-size
rem单位的尺寸 = px单位数值 / 基准根字号
准备工作：
1.flexible.js
2，vscode插件 cssrem
开发
方法一：量，手动算
方法二
1.引入flexible.js
2.vscode插件 css rem
3.确认项目设计稿的尺寸，跟设计人员拿设计稿psd
4.修改vscode中cssrem默认尺寸html的font-size大小
5.测量对应尺寸的二倍图测量的值，如果测量的值为14px
6.填入14px，自动转为rem

## 16.less语法:

css的预处理语言，专门处理生成css的一种东西
场景：大项目需要多人协作的时候
 -->
嵌套、变量、计算
注意：浏览器不识别Less代码，目前阶段，网页要引入对应的CSS文件。

## 17.注释：

### 	单行注释 ：

​		语法：// 注释内容
​		快捷键：ctrl + /

### 	块注释：

​		语法：/* 注释内容 */
​		快捷键： shift + alt + A

## 18.运算（&）

l 加、减、乘直接书写计算表达式
l 除法需要添加 小括号 或 ./
注意：
表达式存在多个单位以第一个单位为准
&:相当于包裹着：.father   //表示当前选择器
例：

```css
.father{
      width:100px;
      .son{
            color:pink;
            &:hover{
                  color:green;
            }
      }
} 
```

## 19.变量语法(@)：

定义变量：@变量名: 值;
使用变量：CSS属性：@变量名;
统一修改，方便维护

## 20.混入 

.类名（）
<!-- 混入 灵活变动版本-->
默认5px，需要变的时候填写

### .类名（@num：5px）{ }

### 导入: @import “文件路径”;

减少css引入
如果是less文件，可以省略后缀.less

less文件完全兼容css

### 禁止导出：out:false    //添加第一行



## day06

vw/vh：视口的宽度
vw=viewport width
vh=viewport height

rem和vw/vh的区别：
rem需要借助html的font-size
vw/vh不需要，直接获取屏幕的大小、视口

VW：把视口、屏幕划分为100份，1vw就是视口宽度的1%
VH：把视口、屏幕划分为100份，1vh就是视口高度的1%
存在兼容性问题

## 21.vh适配原理 

效果：实现在不同宽度的设备中，网页元素尺寸等比缩放效果
vh单位尺寸

1. 确定设计稿对应的vh尺寸 （1/100视口高度）
   查看设计稿宽度 → 确定参考设备高度 (视口高度) → 确定vh尺寸 （1/100 视口高度）

2. vh单位的尺寸 = px单位数值 / ( 1/100 视口高度 )
   例：

```css
    .box{
      width:(68/3.75vw);
     height:(29/3.75vw);
     background-color:pink;
     }
     .box2{
      //vh
      width:(68/6.67w);
     height:(29/6.67vw);
     background-color:green;
    }
```

## 22.响应式布局：bootstrap 

  ```xml

BootStrap:前端UI框架，提供大量编写好的CSS样式  
                 超小屏幕    小屏幕      中等屏幕         大屏幕
响应断点           <768px   >=768px       >=992px      >=1200px
别名               xs         sm            md            lg
容器宽度           100%       750px         970px         1170px
类前缀             col-xs-*   col-sm-*     col-md-*       col-lg-*
列数             12
列间隙           30px

l .container是 Bootstrap 中专门提供的类名，所有应用该类名的盒子，默认已被指定宽度且居中。 
l .container-fluid也是 Bootstrap 中专门提供的类名，所有应用该类名的盒子，宽度均为 100%，左右内边距15px。 
l 分别使用.row类名和 .col类名定义栅格布局的行和列。
注意: 
1. container版心样式，自带左右各15px的padding
2. row类自带间距-15px
  ```

## 23.使用全局CSS样式美化标签

步骤：网站首页 → BootStrap3中文文档 → 全局CSS样式 → 按分类导航查找目标类

## 24.网格布局

### ①基础概念

网格布局是一种布局方式，它类似于弹性布局，它技术更新、功能更强，但兼容也更差。

弹性布局：基于轴的线性布局，可以看做一维布局

网格布局：像表格一样划分成行和列布局，可以看做二维布局

容器：父级元素

项目：子级元素

行、列、网格线、单元格

### ②容器

#### 容器模式
#### 1.display:grid

块级模式，独占一行（不和其他元素一排显示）

```css
.father{
    display:grid
}
```

#### 2.display:inline-grid

行内模式，一行多个（可以和其他行内元素一排显示）

```css
.father{
    display:inline-grid
}
```



### ③主体网格行、列布局

#### 1.控制列（grid-template-columns）

每一列分别的取值属性为：grid-template-columns

```css
.father{
    grid-template-columns:30px 60px 30px;
}
```

显示效果和属性值个数以及具体数值有关，个数决定，一行显示几个、数值当前列显示多长，上述代码为显示3列，分别为30px、60px、30px。

简述：数值有几个，就有几列。

#### 2.控制行（grid-template-rows）

每一行分别的取值  属性为：grid-template-rows

```css
.father{
    grid-template-rows:30px 60px 30px;
}
```

显示效果和属性值个数以及具体数值有关，个数决定，一列显示几个、数值当前行显示多长，上述代码为显示3列，分别为30px、60px、30px。

简述：数值有几个，就有几行。

### ④grid-template-rows/columns取值：

1. px     固定值

2. %      百分比

3. 1fr    比例，比如 1fr、2fr

4. auto    自适应，获取剩余所有

5. repeat()      重复规则

   ```css
   .father {
       grid-template-rows:repeat(3,100px);
       grid-template-rows:100px 100px 100px;   /*等于*/
   }  
   /*重复3次后面模式，每行100px*/
   .father {
       grid-template-rows:repeat(3,100px 200px);
       grid-template-rows:100px 200px 100px 200px 100px 200px;  /*等于*/
   }  
   /*重复3次后面模式，按照100px 200px的模式*/
   ```
   
### ⑤主体网格行、列的间距

控制单元格与单元格之间的间距。

#### 1.行间距(grid-row-gap)

```css
.father {
    grid-row-gap:20px;
    每一行之间间距20px
}  
```

#### 2.列间距(grid-column-gap)

```css
.father {
   grid-column-gap:20px;
   每一列之间间距20px
}  
```

### ⑥缩写(gap):

```css
    gap:行间距 列间距;
```

```css
.father {
    gap:10px 20px;
    /*每一行之间间距10px
    每一列之间间距20px*/
    gap:10px;
    /*行和列的间距都为10px*/
}
```

### ⑦父容器对齐方式

控制父容器整体的布局。

当设置的父元素（width:300）比较大，设置父盒子中的网格布局（grid-template-columns:100px 100px）比较小的时候。（父元素300，网格200，可以控制整体网格的位置）

#### 1.水平方向（justify-content）

```css
.father {
    justify-content:start/end/center/space-between/space-around/space-evenly;
    属性值类似于弹性布局属性
}  
```

#### 2.垂直方向（align-content）

```css
.father {
    align-content:start/end/center/space-between/space-around/space-evenly;
    属性值类似于弹性布局属性
}  
```

#### 3.简写(place-content)

```css
.father {
    place-content: 垂直 水平;
    place-content: 同属性垂直水平只写一个;
    start/end/center/space-between/space-around/space-evenly
}  
```

### ⑧子项目对齐方式

控制子项目的布局。

当设置网格布局单个的子项目（grid-template-columns:100px 100px）比较大，设置子元素的盒子大小（width:50px）的比较小的时候（网格100，元素50，可以控制元素在单个网格内的位置）

#### 1.水平方向（justify-items）

```css
.father {
    justify-items:start/end/center 
     左/中/右
}  
```

#### 2.垂直方向（align-items）

```css
.father {
    align-items:start/end/center
    上/中/下
}
```

#### 3.简写（place-item）

```css
.father {
    place-item: 垂直 水平;
    place-item: 同属性垂直水平只写一个;
    start/end/center
}  
```

### ⑨指定单个子项目对齐方式

性质同上，只是控制单个，不是控制里面的每一个

#### 1.水平方向（justify-self）

```css
.son {
    justify-self:start/end/center 
     左/中/右
}  
```

#### 2.垂直方向（align-self）

```css
.son {
    align-self:start/end/center 
    上/中/下
}  
```

#### 3.简写(place-self)

```css
.son {
    place-self: 垂直 水平;
    place-self: 同属性垂直水平只写一个我;
    start/end/center
}  
```

### ⑩指定单个子项目的位置

控制某一个子项目的特殊位置 (网格布局定位-位置按照缝缝来计算-缝缝从1开始数)

#### 1.设定行、列起止位（grid-column-start/end）

```css
.son{
    grid-column-start:2;
    从列的第2个缝缝位置开始
    grid-column-end:4;
    到列的第4个缝缝位置结束（并且占据2列）
    grid-row-start:2;
    从行的第2个缝缝位置开始
    grid-row-end:4;
    到行的第4个缝缝位置结束（并且占据2行）
}

```

#### 2.简写（grid-column/row）

```css
.son{
    grid-column: 2/4;
    控制列从第2个缝缝位置开始/第4个缝缝位置结束（并且占据2行）
    grid-row: 2/4;
    控制行从第2个缝缝位置开始/第4个缝缝位置结束（并且占据2行）
}
```

### 11.设定行、列占据位数 （grid-column-start/end:span 2）

```css
.son{
    grid-column-start:2;
    从列的第2个缝缝位置开始
    grid-column-end:span 2;
    一共占据2列
    grid-row-start:2;
    从行的第2个缝缝位置开始
    grid-row-end:4;
    一共占据2行
}
```

#### 1.简写(grid-column/row: 2/span 2)

```css
.son{
    grid-column: 2/span 2;
    从列的第2个缝缝位置开始/一共占据2列
    grid-row: 2/span 2;
    从行的第2个缝缝位置开始/一共占据2行
}
```

### 12.设置元素定位至指定位置

给网格布局区域命名，控制子项目到指定命名区域中

```css
.father {
   grid-template-areas:'a b c'
                       'd e f'
                       'g i i'
}
.son1 {
    grid-column-start:a-start
    控制列从a的左侧缝缝开始
    grid-column-end:a-end
    控制列从a的右侧缝缝位置结束
    grid-row-start：a-start
    控制行从a的顶部缝缝开始
    grid-row-end：a-end
    控制行从a的顶部缝缝结束
    效果：占据a的位置
}
.son2 {
    grid-column-start:a-start
    控制列从a的左侧缝缝开始
    grid-column-end:a-end
    控制列从a的右侧缝缝位置结束
    grid-row-start：a-start
    控制行从a的顶部缝缝开始
    grid-row-end：d-end
    控制行从a的顶部缝缝结束
    效果：占据ad的位置
}
.son3 {
    grid-area:a
    效果：占据a的位置
}
.son4 {
    grid-area:i
    效果：占据i的位置
}
```

# 02-Git

## 1.管理工具分类 

1.本地：自己管，文件夹
2.集中式：一台专门的服务器进行管理 所有人的代码都统				 一放在我、某一台电脑中  --svn
3.分布式：每个人都拥有一整套完成的代码可以自己管理  				 --git
          优点：联网、多人、断网提交、服务器奔溃后也可以恢复

## 2.git的三个区域 

Git 是一个开源的分布式版本控制系统，是目前世界上最先进、最流行的版本控制系统。可以快速高效地处理从很小到非常大的项目版本管理。

### 		①工作区

### 		②暂存区

### 		③git仓库

## 3.git的三种状态

### 		①已修改 modified     

### ②已暂存 staged       

### 		③已提交 commited

## 4.安装全局配置用户名、邮箱

​	1.安装完git之后
​	2.全局配置用户信息（用户名\邮箱）

​		使用 --global 选项，只需配置一次，该电脑永久邮箱

```git
用户名 git config --global user.name 'jiangfenglin'
邮箱 git config --global user.email 'jfl@qq.com'
```

会被写入到 C:/Users/用户名文件夹/.gitconfig 文件中。这个文件是 Git 的全局配置文件，配置一次即可永久生效。

除了使用记事本查看全局的配置信息外，还可以运行如下终端命令：

## 5.查看所有的全局配置项

### git config --list --global

## 6.查看指定的全局配置项

### git config user.name

### git config user.email

## 7.获取帮助信息

可以使用 git help <verb> 命令，无需联网即可在浏览器中打开帮助手册，例如：

//打开 git config 命令的帮助手册：

#### git help config

## 8.获取更简明的help

如果不想查看完整的手册，那么可以用 -h 选项获得更简明的“help”输出：

### git config -h

## 至此git的安装、配置完成

## 9.以下为git的基本操作

### 1.通过鼠标右键打开Git Bash

### 2.git init  初始化

初始化git（让git接管我的项目）将当前的目录转化成git仓库
创建一个名为 .git 的隐藏目录，这个 .git 目录就是当前项目的 Git 仓库，里面包含了初始的必要文件，这些文件是 Git 仓库的必要组成部分。

### 3.git status 查看文件状态

​        红色的标记====未跟踪==还未被git管理起来的文件
​        绿色的标记====已跟踪==已经被git管理起来的文件
​        working tree clear  所有文件都已经提交 没有任何工作了

###4.以精简方式显示文件状态：git status -s

git status -s
git status --short

### 5.跟踪新文件git add

git add 文件名   如要跟踪index.html文件，运行如下命令：git add index.html

输入git status -s，会显示Changes to be committed。说明已被跟踪，并处于暂存状态

管理代码 管理对应的文件  git add .   //一次性将所有的新增和修改过的文件加入暂存区

#### Git提交暂存区命令  git add .

### 6.clear 快速清空

### 7.git commit -m'描述'   提交更新

把暂存区的内容提交到git仓库.

其中 -m 选项后面是本次的提交消息，用来对提交的内容做进一步的描述：git commit -m “日志信息”

##10.若对已提交的文件进行修改

1.git status
git status -s

已跟踪文件的内容发生了变化，但还没有放到暂存区。

![image-20220824145047413](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220824145047413.png)

注意：修改过的、没有放入暂存区的文件前面有红色的 M 标记。

2.暂存已修改的文件:git add index.html  //把已修改的文件放入暂存区

git status  //查看详细的文件状态报告

git status -s //查看精简的文件状态报告.绿色的M表示文件已修改且已放入暂存区

 git commit -m     //"提交消息" 命令，即可将暂存区中记录的 index.html 的快照，提交到 Git 仓库中进行保存.(将暂存区中的文件提交到Git仓库)

git status    //检查状态

## 11.git的基本操作

### ①git checkout -- index.html  撤销对index文件的修改

把对工作区中对应文件的修改，还原成 Git 仓库中所保存的版本。所有的修改会丢失，且无法恢复！危险性比较高，请慎重操作！

### ②git add .向暂存区中一次性添加多个文件

常用命令:将新增和修改过后的文件加入暂存区

### ③git reset HEAD 取消暂存的文件

要移除的文件名称

### ④git commit -a -m “日志”    跳过使用暂存区域

Git 标准的工作流程是工作区 → 暂存区 → Git 仓库，但有时候这么做略显繁琐，此时可以跳过暂存区，直接将工作区中的修改提交到 Git 仓库，这时候 Git 工作的流程简化为了工作区 → Git 仓库.

跳过了git add 步骤.

### ⑤移除文件rm

① 从 Git 仓库和工作区中同时移除对应的文件
          git rm -f index.js
② 只从 Git 仓库中移除指定的文件，但保留工作区中对应的文件
          git rm --cached index.css

### ⑥忽略文件.gitignore 

1.创建一个名为 .gitignore 的配置文件

2. .gitignore格式如下:

   ① 以 # 开头的是注释
   ② 以 / 结尾的是目录
   ③ 以 / 开头防止递归
   ④ 以 ! 开头表示取反

   ![image-20220824150640689](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220824150640689.png)

例:

1创建一个 .gitignore 文件
2在里面配置忽略的一个文件 index.html
3在里面配置忽略的一个文件夹  test
4右键打开 Git Bash
5命令行输入 git add .
6命令行输入 git status 来查看文件状态

### ⑦git log 查看提交历史

查看所有提交的版本信息（当前时间轴之前的）,最近的提交在最上面.
get log -2  检查最近两条提交历史
get log -2 --pretty＝oneline  在一行上展示最近两条提交历史的信息   

### ⑧回退到指定的版本

![image-20220824154229534](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220824154229534.png)

git reflog（所有时间轴）
git reset --hard <版本id>     回退到指定版本

## 12.总结

对代码的基本操作
新增 修改 删除
1.git add .
2.git commit -m'1'  提交此次问的理由 '备注'
Q：退出 

## 13.开源

开源:不仅提供程序还提供程序的源代码

闭源:只提供程序，不提供源代码

开源许可协议:GPL    MIT

开源项目托管平台(免费):Github   Gitlab(企业用户)   Gitee(码云,中文)

## 14.Github

Github 是全球最大的开源项目托管平台。因为只支持 Git 作为唯一的版本控制工具，故名 GitHub。

1.注册github:官网首页 https://github.com/
2.sign-up注册页面   填写资料

3.create account注册    填写邮箱,激活链接,完成注册

#### ①新建空白远程仓库

![image-20220824155445991](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220824155445991.png)

最好用英文

### ②远程仓库的两种访问方式(HTTPS/SSH)

HTTPS：零配置；但是每次访问仓库时，需要重复输入 Github 的账号和密码才能访问成功

SSH：需要进行额外的配置；但是配置成功后，每次访问仓库时，不需重复输入 Github 的账号和密码

注意：在实际开发中，推荐使用 SSH 的方式访问远程仓库。

#### 基于 HTTPS 将本地仓库上传到 Github

![image-20220824155629362](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220824155629362.png)

步骤:

①登录进入github
②在github中创建远程仓库
③拷贝 https 的远程仓库地址
④在本地仓库地址里面打开git命令行
⑤命令:
     git remote add origin 远程仓库地址
     git push origin master

**git push**:把本地仓库代码推送到远程仓库(第二次以上).

#### SSH key

优点:免登录身份认证、数据加密传输.

配置SSH key步骤:

​		① 打开 Git Bash

​		②ssh-keygen -t rsa -b 4096 -C "邮箱" 

​		③连续敲击 3 次回车,在 C:\Users\用户名文件夹\.ssh 目录中生成 id_rsa 和 id_rsa.pub 两个文件

​		④使用记事本打开 id_rsa.pub 文件，复制里面的文本内容

​		⑤在浏览器中登录 Github，点击头像 -> Settings -> SSH and GPG Keys -> New SSH key

​		⑥将 id_rsa.pub 文件中的内容，粘贴到 Key 对应的文本框中

​		⑦在 Title 文本框中任意填写一个名称，来标识这个 Key 从何而来

​		⑧打开 Git Bash输入命令 ssh -T git@github.com     检测 Github 的 SSH key 是否配置成功

![image-20220824160350630](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220824160350630.png)

yes  配置成功图片

![image-20220824160413067](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220824160413067.png)

#### 基于 SSH 将本地仓库上传到 Github







```js

```





<!--  -->
知识点：克隆
作用：把互联网上的项目克隆下来
场景：刚进公司，参与到一个已经存在的项目中
语法：git clone 地址
步骤：
1.打开git bash here
2.输入命令
其他（注意、优势）

创建git仓库：创建一个test1文件
mkdir test1
让命令进入test1文件夹
cd test1
初始化项目（让git来接管项目）
git init
创建 README.md说明文件
touch README.md
添加至暂存区
git add README.md
添加至git


<!-- 6.28下 -->
更新项目代码
场景：平常更新的话，更新别人在此项目中新增的文件
命令：git pull 地址  //git pull origin代替地址


如果出现大片黄色报错 里面包含了git pull
解决：git pull --rebase origin master      //--rebase  强势覆盖
git push origin master

<!-- 分支 -->
主分支 master 不写代码，专门用来合并分支
功能分支 login、reg、pay 专门用来开发代码
git branch 查看所有分支  git branch -a查看所有分支详细信息
git branch plusmeng  创立一个plusmeng的分支
git checkout -b meng  创立一个meng的分支，且切换到这个分支
git checkout plusmeng 切换到plusmeng的分支
git merge 被合并的分支名

其他：当一个分支进行开发时，未保存突然切换分支，会导致写的内容跟随切换分支的动作一起转移切换分支之前，add、commit
合并分支时，需注意，你所在的应该是主分支，把其他分支合并入主分支上

