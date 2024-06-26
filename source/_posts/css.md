---
title: css
date: 2020-03-06 19:53:06
categories:
- CSS
tags:
- CSS
---

# base
浏览器会把CSS解析成CSSOM

## Route-Map
{% asset_img css_map.jpeg %}
### RWD
Responsive Web Design：响应式 Web 布局

> 响应式这个词源自于建筑学领域，原本指的是建筑物本身会“响应”实际的使用情况，来自我调整。在Web开发领域，“响应式”的意思就变成了，我们开发的 Web 页面会“响应”用户的设备尺寸而自动调整布>局。在这篇文章中提到过，我们可以基于 流体网格（Fluid Grids）、灵活的图片（Flexible Images）和媒体查询（Media Queries） 三种技术来构建一个响应式 Web 网站或 Web 应用。

### IWD
Intrinsic Web Design：内在 Web 设计
以最少的代码量来实现复杂的 Web 设计。
浮动（float）还是引用外部第三方 CSS 框架（CSS Frameworks）和库（比如Bootstrap）将内容放置在 Web 页面上想要的任何位置（即布局），几乎都有一些 Hack 的身影存在！

> 内在 Web 设计（Intrinsic Web Design）不是内容以设计为导向（Content Design-Driven），而是只专注于让设计受内容驱动（Design Content-Driven）。

### CDWD
Component-Driven Web Design：组件驱动式Web设计
一种新的响应式
基于组件驱动的开发，即CSS新增的特性将直接基于组件而不是基于页面注入式响应能力

## 技术术语
### Web坐标轴
#### 平面
{% asset_img coord.png %}

#### 三维
除平面画布中的 x 和 y 轴, 还有三维度的 z 轴
transform 绘制 3D 图形或使用第三维度从前往后对对象进行分层：
{% asset_img z.png %}
在定位元素（显式使用position 属性值为非 static 的元素）上使用 z-index 控制其层叠的顺序（z 轴上的层叠顺序），它表示的是用户与屏幕的这条看不见的垂直线：
{% asset_img z2.png %}

内联与块元素

### 容器和容器空间
HTML 的每一个元素在 CSS 中都是一个盒子，这个盒子又被称为 容器
容器的称呼也会有不同。它主要由 CSS 的 display 属性的值来决定：
- block 时称为块容器；
- inline 时称为内联容器；
- flex 或 inline-flex 时称为Flexbox容器；
- grid 或 inline-grid 时称为 Grid 容器（网格容器）。

外边距：元素与元素之间的间距，margin 或 gap
内边距：元素内容与元素边框，padding

### 逻辑属性
多语言
```css
.thumb {
    margin-inline-end: 1rem;
}
```
文档排版无论从左还是右，都可以兼容

## initial & inherit
initial 初始值或默认值
inherit 继承父元素

## 引用CSS样式方式
内联式 > 嵌入式 > 外部式

## color
cascading style sheets
css提供了一种方法来告诉浏览器页面中的元素如何显示

#000000 十六进制
## a标签
无下划线 
text-decoration:none;
## 不能加分号
样式显示不出来，也不会报错
{% asset_img semicolon.png %}

## 文字修饰
text-decoration-line
文本修饰的位置, 如下划线underline，删除线line-through
text-decoration-color
文本修饰的颜色
text-decoration-style
文本修饰的样式, 如波浪线wavy实线solid虚线dashed
text-decoration-thickness
文本修饰线的粗细

text-indent 首行缩进

## font-family
font-family: tahoma, arial, 宋体, sans-serif;
sans-serif: 如果其他字体都找不到，就使用浏览器默认字体

## vertical-align
一个元素属于inline或是inline-block水平，其身上的vertical-align属性才会起作用。

所谓inline-block水平的元素，就是既可以“吸”又可以“咬”的元素，既可以与inline水平元素混排，又能设置高宽属性的元素。哪些元素呢，例如图片，按钮，单复选框，单行/多行文本框等HTML控件，只有这些元素默认情况下会对vertical-align属性起作用。

baseline，默认。元素的基线与父元素的基线对齐。

## 字间距
letter-spacing
## 旋转
transform: rotate(90deg);

## 伪类
``` css
&::before {
  display: inline-block;
  content: '';
  width: px2rem(18px);
  height: px2rem(10px);
  background: #006889;
  border-top-left-radius: px2rem(10px);
  border-bottom-left-radius: px2rem(10px);
}
```

## display:inline-block
div  display: inline-block;
会多出margin值

使用display：flex

## text-align
微信文章两端对其，justify

## font-weight
normal
正常粗细。与400等值。
bold
 加粗。 与700等值。
lighter
比从父元素继承来的值更细(处在字体可行的粗细值范围内)。
bolder
比从父元素继承来的值更粗 (处在字体可行的粗细值范围内)。
<number>
一个介于 1 和 1000 (包含) 之间的 <number> 类型值。更大的数值代表字体重量粗于更小的数值 (或一样粗)。一些常用的数值对应于通用的字体重量名称，如章节常见粗细值名称和数值对应所描述。

## calc()
calc() 此 CSS 函数允许在声明 CSS 属性值时执行一些计算。它可以用在如下场合：<length>、<frequency>, <angle>、<time>、<percentage>、<number>、或 <integer>。

## object-fit
图片和视频 适应容器 
`<img> or <video></video>`
object-fit: cover;

# 浏览器兼容
## 前缀
``` css
-webkit-transform:rotate(-3deg); /*为Chrome/Safari*/
-moz-transform:rotate(-3deg); /*为Firefox*/  /*已经认标准写法*/
-ms-transform:rotate(-3deg); /*为IE*/
-o-transform:rotate(-3deg); /*为Opera*/    /*欧朋已经换webkit内核*/
transform:rotate(-3deg);
```





# 样式
## 不同大小的字体底部对齐
display: flex
align-items: baseline;

## 超出部分省略号
``` css
overflow: hidden; // 超出的文本隐藏
text-overflow: ellipsis; // 溢出用省略号显示
white-space: nowrap; // 溢出不换行

/* msg 中 /n 换行 */
white-space: pre-wrap;
```

两行自适应
```css
-webkit-box-orient: vertical;
max-height: 40px;
line-height: 20px;
overflow: hidden;
text-overflow: ellipsis;
display: -webkit-box;
-webkit-line-clamp: 2;
```

## 超出部分自动换行
``` css
word-wrap: break-word;
```

## 英文/数字 换行
``` css
word-break: break-all;
```

## 无序列表样式
https://developer.mozilla.org/zh-CN/docs/Web/CSS/list-style

li+li {
  margin-left: 152px;
}

## 长单词换行
word-wrap: break-word;

## placeholder 颜色
``` css
input {
  &::-webkit-input-placeholder {
    color: red;
  }
  &::-moz-placeholder {
    color: red;
  }
  &::-ms-input-placeholder {
    color: red;
  }
}
```

## 背景色透明
``` css
background-color: transparent;
```

## 背景色渐变
linear-gradient() 函数用于创建一个表示两种或多种颜色线性渐变的图片
<gradient> 是一种<image>CSS数据类型的子类型，用于表现两种或多种颜色的过渡转变。
``` css
background: linear-gradient(#e66465, #9198e5);
background: linear-gradient(to right, #3494e6, #ec6ead);
```

## display:flex
### justify-content: space-between;
均匀排列每个元素，首个元素放置于起点，末尾元素放置于终点


## 移动端input 内阴影
``` css
input,
textarea {
  border: 0; /* 方法1 */
  -webkit-appearance: none; /* 方法2 */
}
```

## background-size
https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-size

## 列表最后一项去除margin-right
不用给item再加类名，item-right, 再加样式
``` css
&:nth-child(4n) {
  margin-right: 0;
}
```

p:nth-child(odd){} //奇数行
p:nth-child(even){} //偶数行

## 区域事件失效
pointer-events: none;


## css 盒子模型
IE怪异盒子  和 标准盒子
box-sizing：
border-box
width = border + padding + 内容的宽度

content-box
width = width

应用场景
希望子元素整个盒子撑满父元素的内容区域

## 动画
transition: all .3s linear

## 可见性
visibility: visible

## flexd
display: flex; // 错了
position: fixed;

## 高度
document.body.clientHeight ==> BODY对象高度
document.documentElement.clientHeight ==> 可见区域高度
window.innerHeight，内部的高度
window.screen.height，用户屏幕的高度

### window和document区别
Window对象表示浏览器中打开的窗口；window对象可以省略。比如alert()、window.alert()。
Document对象是Window对象的一部分。那么document.body 我们可以写成window.document.body；浏览器的HTML文档成为Document对象。

## 字体
``` css
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  font-family: 'Roboto', sans-serif;
}
```
Webkit 实现了名为-webkit-font-smoothing的相似属性。这个属性仅在 Mac OS X/macOS 下生效。
- none - 关闭字体平滑；展示有锯齿边缘的文字。
- antialiased - 平滑像素级别的字体，而不是子像素。从亚像素渲染切换到黑暗背景上的浅色文本的抗锯齿使其看起来更轻。
- subpixel-antialiased - 在大多数非视网膜显示器上，这将会提供最清晰的文字。

Firefox 实现了名为 -moz-osx-font-smoothing 的相似属性。这个属性仅在 Mac OS X / macOS 下生效。
- auto - 允许浏览器选择字体平滑的优化方式，通常为grayscale。
- grayscale - 用灰度抗锯齿渲染文本，而不是子像素。从亚像素渲染切换到黑暗背景上的浅色文本的抗锯齿使其看起来更轻。
- inherit
- unset

## 长度
length
- 相对长度单位
  + 字体相对长度
    * rem
  + 视口(Viewport)比例长度
    * vh  视口的初始包含块的高度的1%
    * vw  视口的初始包含块的宽度的1%
- 绝对长度单位
  + px

### fr
fr：fraction，分数
网格剩余空间比例单位
```css
.container {
    grid-template-columns: 200px 1fr 1fr;
}
```

### platform-client 皮卡堂公告 字体在多设备显示不一致问题
由于网页会根据屏幕宽度调整布局，所以不能使用绝对宽度的布局，也不能使用具有绝对宽度的元素。
width:xxx px;

安卓机,千奇百怪,各种尺寸的机型都有,而且有1倍屏,2倍屏，3倍屏之分

rem是一个相对单位，1rem等于html元素上字体设置的大小。

根据不同设备的分辨率设置字体。

 @media screen and (max-width:980px) {
      html {
        font-size: 50px;
      }
    }

### px2rem
``` scss
// Convert to REM function
@function px2rem($px) {
  $rem: 50px;
  @return ($px / $rem / 2) + rem;
}
```

## div水平剧中
网易
```
width: 56.25vh;
height: 100vh;
position: absolute;
left: 50%;
-webkit-transform: translateX(-50%);
transform: translateX(-50%);
overflow: hidden;
background-color: #448aff;
background-image: url(./resource/neteaselogo.png);
background-position: center center;
background-repeat: no-repeat;
background-size: 35.625vh 11.71875vh;
```

### 水平垂直剧中
retryEle.style.cssText = 'display: inline-block; padding: 6px 16px; background: #4d37b3; color: #ffffff; border-radius: 10px; position: absolute; left: 50%; transform: translateX(-50%); top: 50%;';

## 垂直居中
最多显示两行文本。一行文本的时候垂直居中，两行文本的时候超出部分 省略号。
```css
// 会有兼容问题，safari
// 父级：display: flex; align-items: center;
display: -webkit-box;
-webkit-box-orient: vertical;
-webkit-line-clamp: 2;
overflow: hidden;
```

## 无滚动条，列表
顶部悬浮
其余部分列表
```scss
.app{
  height: 100vh;
  display: flex;
	flex-direction: column;
  .top{
    height: 308rpx;
  }
  .list-wrap{
    min-height: calc(100vh - 308rpx) !important;
    fix: 1; // 也可以，剩余空间放大
  }
}
```

fix: 1;
flex-grow : 1;    ➜ The div will grow in same proportion as the window-size       
flex-shrink : 1;  ➜ The div will shrink in same proportion as the window-size 
flex-basis : 0;

# 适配
``` css
css: {
  loaderOptions: {
    postcss: {
      plugins: [
        require('postcss-px-to-viewport')({
          unitToConvert: 'px',
          viewportWidth: 750,
          unitPrecision: 3,
          propList: ['*'],
          viewportUnit: 'vw',
          fontViewportUnit: 'vw',
          selectorBlackList: [],
          minPixelValue: 1,
          mediaQuery: false,
          replace: true,
          exclude: /(\/|\\)(node_modules)(\/|\\)/
        })
      ]
    }
  }
}
```

## input 问题
ios 光标变大
原因：
- Chrome：该行无文字时，光标高度与line-height一致；该行有文字时，光标高度从input顶部到文字底部(这两种情况都是在有设定line-height的时候)，如果没有line-height，则是与font-size一致。
- IOS中情况和Chrome 相似。

方法：
设置字体大小和行高一致，然后通过 padding 撑开大小

ios placeholder 位置偏上
``` css
input::-webkit-input-placeholder {
  font-size: 30px;
  line-height: 50px;
}
```

## @viewport
viewport-fit
auto
此值不影响初始布局视图端口，并且整个web页面都是可查看的。
contain
视图端口按比例缩放，以适合显示内嵌的最大矩形。
cover
视图端口被缩放以填充设备显示。强烈建议使用 safe area inset 变量，以确保重要内容不会出现在显示之外。

## input focus 边框
style="outline:none;"属性即可去掉边框。



# css3 动画
## transition 过渡
石器时代
在 CSS3 出现之前，网页上的动画都是靠 JavaScript 来实现的，在这个时代，你可能会经常看见这样的代码片段：
``` js
const timeout = setTimeout(test, 2000);
function test() {
  document.getElementById("test").style.opacity += 0.1
};
```

css3时代
``` css
.box {
  width: 100px;
  height: 200px;
  background: red;
  transition: all 1s ease;
}
.box:hover {
  width: 200px;
  height: 100px;
  background: yellow;
}
```
过渡是css3中颠覆性特征之一，可以不用Flash动画或JavaScript，当元素从一种样式变换为另一种样式时为元素添加效果

过渡动画：是从一个状态 渐渐的过渡到另一个状态

- 经常与`:hover`一起 搭配使用
- 如果要过渡多个属性，用逗号分割

四个属性 （后两个可以省略）
### transition-property 过渡属性
需要过度的 数字量化的 css属性

颜色系，如color，background-color，border-color，outline-color等

数字系，实在太多了，如width，height，top，right，bottom，left，zoom，opacity，line-height，background-position，word-spacing，font-weight，vertical-align，outline-outset，z-index等。

01系，如visibility（0表示隐藏，1表示显示）

如果要所有的属性都过渡，写：all

使用过渡口诀：谁做过渡给谁加

### transition-duration 延时时间，花费时间
过渡需要的时间，单位可指定s秒。默认是0, 表示立刻变化

### transition-timing-function 过渡方法，运动曲线
{% asset_img timing-function.png %}
看贝赛尔曲线就知道了，linear是匀速过渡，ease是先快再慢的节奏，ease-in是加速冲刺的节奏，ease-out是减速到停止的节奏，ease-in-out是先加速后减速的节奏。

### transition-delay 过渡延迟，何时开始
延迟开始过渡的时间，默认值是0，表示不延迟，立即开始过渡动作。单位是s秒或ms毫秒。

### eg
``` css
.box {
  width: 100px;
  height: 200px;
  background: blue;
  transition: all 1s ease;
}
.box:hover {
  width: 200px;
  height: 100px;
  background: yellow;
}
```

## transform 转型，变形
transform本质上是一系列变形函数，分别是translate位移，scale缩放，rotate旋转，skew扭曲，matrix矩阵。

我们应该都知道二八法则(巴莱多定律)，即任何一组东西中，最重要的只占其中一小部分，约20%，其余80%的尽管是多数，却是次要的。如果你有上述的感觉，那你就属于那80%, 一抓一大把，没有特色的页面仔。

### translate 平移
设置元素在 X轴或者 Y轴上的平移变换

### scale 缩放
/* 等同于变换: scaleX(2) scaleY(2);*/
transform: scale(2);

### rotate 旋转
transform: rotate(45deg); 顺时针旋转 45度

### skew 倾斜
 skew() 函数指定一个或两个参数，它们表示在每个方向上应用的倾斜量。
transform: skew(10deg, 10deg);

### matrix 矩阵
matrix(1, 2, 3, 4, 5, 6);

## animation 动画
| 值 | 描述  |
| :--- | :--- |
| name | 用来调用@keyframes定义好的动画，与@keyframes定义的动画名称一致 |
| duration | 指定元素播放动画所持续的时间，默认 0 |
| timing-function | 规定速度效果的速度曲线，默认 ease ；是针对每一个小动画所在时间范围的变换速率 |
| delay | 延迟时间, 默认0；定义在浏览器开始执行动画之前等待的时间，值整个animation执行之前等待的时间 |
| iteration-count | 定义动画的播放次数，默认 1 ; 可选具体次数或者无限(infinite) |
| direction | 默认 normal ；设置动画播放方向：normal(按时间轴顺序),reverse(时间轴反方向运行),alternate(轮流，即来回往复进行),alternate-reverse(动画先反运行再正方向运行，并持续交替运行) |
| play-state | 默认 running ；控制元素动画的播放状态，通过此来控制动画的暂停和继续，两个值：running(继续)，paused(暂停) |
| fill-mode | 默认 none ；控制动画结束后，元素的样式，有四个值：none(回到动画没开始时的状态)，forwards(动画结束后动画停留在结束状态)，backwords(动画回到第一帧的状态)，both(根据animation-direction轮流应用forwards和backwards规则)，注意与iteration-count不要冲突(动画执行无限次)

### animation-direction
normal
每个循环内动画向前循环，换言之，每个动画循环结束，动画重置到起点重新开始，这是默认属性。
alternate
动画交替反向运行，反向运行时，动画按步后退，同时，带时间功能的函数也反向，比如，ease-in 在反向时成为ease-out。计数取决于开始时是奇数迭代还是偶数迭代
reverse
反向运行动画，每周期结束动画由尾到头运行。
alternate-reverse
反向交替， 反向开始交替
动画第一次运行时是反向的，然后下一次是正向，后面依次循环。决定奇数次或偶数次的计数从1开始。

### 帧
帧就是视频或动画中的每一张画面
只要一秒钟记录15帧画面，观众看起来就会觉得它是运动的，是「动画」。

# 例子
## 进度条 transition
``` css
.line-c {
  width: 50%;
  height: 100%;
  background-color: #f00;
  border-radius: 40px;
  transition: width 1s ease;
}
.line-c:hover {
  width: 100%;
}
```

# 知识点
块格式化上下文（Block Formatting Context，BFC） 是Web页面的可视CSS渲染的一部分，是块盒子的布局过程发生的区域，也是浮动元素与其他元素交互的区域。

## 空格
早期对html不熟练 会使用 &nbsp
缺点：
连接两个单词的时候，会把它认为是一个单；在排版的时候会出现分词的问题。
看起来能显示出来，但实际破坏了语义。

建议使用：css属性，white-space 去控制空格被显示出来
white-space: pre;
white-space CSS 属性是用来设置如何处理元素中的 空白。

## 响应式
Responsive Web Design，简称 RWD，响应式 Web 设计
响应式这个词源自于建筑学领域，原本指的是建筑物本身会“响应”实际的使用情况，来自我调整。在Web开发领域，“响应式”的意思就变成了，我们开发的 Web 页面会“响应”用户的设备尺寸而自动调整布局。在这篇文章中提到过，我们可以基于 流体网格（Fluid Grids）、灵活的图片（Flexible Images）和媒体查询（Media Queries） 三种技术来构建一个响应式 Web 网站或 Web 应用。

# 性能
## table
由于浏览器使用流式布局，对Render Tree的计算通常只需要遍历一次就可以完成，但table及其内部元素除外，他们可能需要多次计算，通常要花3倍于同等元素的时间，这也是为什么要避免使用table布局的原因之一。

# 新项目初始化
## html
### 页面语言设置
``` html
<html lang="zh-cmn-Hans">
```

## css
``` css
body,h1,h2,h3,h4,h5,h6,p {
  margin: 0;
}
ul {
  padding: 0;
  margin: 0;
}
ul li {
  list-style: none;
}
a {
  color: inherit;
  text-decoration: none;
}
a:hover {
  text-decoration: underline;
}
.cursor-pointer {
  cursor: pointer;
}
```

### 待定
``` css
box-sizing: border-box;
```

### 公共样式导入项目
vue
main.js 中

# 解决方案
## 彩带
https://www.kirilv.com/canvas-confetti/

## 阴影,投影
``` css
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
```

# Future
子网格（subgrid）、容器查询 和 父选择器 :has()
Shapes 能帮助我们打破矩形的布局模式，CSS 的多列布局能让我们在 Web 中实现报纸排版的效果
[CSS发展报告](https://2021.stateofcss.com/en-US/opinions/#currently_missing_from_css_wins)

