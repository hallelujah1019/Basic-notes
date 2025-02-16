# 前端CSS3基础知识汇总

## CSS的书写位置

### 行内样式（内联样式）

- 行内样式是通过标签的style属性来设置元素的样式
- 行内样式只是控制当前标签的样式
- 结构和样式没有进行分离，实际开发中不推荐使用

### 内部样式（内嵌样式表）

- style标签一般是写在head标签中

	- 内嵌式样式表可以控制当前页面
	- 结构和样式只是部分分离，并没有完全分离开来
	- 特点：不能真正的实现结构和表现样式的分离，也不推荐使用

### 外联式样式表

- 通过head标签中的<link>来引入外部的.css文件，从而达到网页美化的修饰功能

	- <link rel="stylesheet" type="text/css" href="css/style.css">
	- link标签中的rel属性是类型的意思,rel的值决定了后面href的类型，link可以连接好多中文件，举个栗子：rel = "stylesheet",stylesheet这个值决定了后面href的类型就得是一个.css类型的文件
	- 可以通过link引入的方式，一个html可以引入多个css文件

- link标签中的内容主要是给浏览器搜索引擎看的，告诉搜索引擎的样式表的路径在哪里
- 特点：

	- 真的的做到了结构和表现的分离，推荐使用
	- 控制范围是整个项目

## 书写页面的重中之重属性

### margin：0；

### padding:  0；

### box-sizing:  border-box;

## div 中的内容垂直居中的六种常用方式

### 第一种方式：如果是将一行文字或者是几行文字垂直居中对齐，可以将行高设置成div的高度  line-height:div的高度；

### 第二种方式：模拟表格法：第一步：现将div容器定义成表格：display:table;
第二步：再将需要垂直居中的标签设置成：display:table-cell;  vertical-align:middle;

### 第三种方式：采用flex布局，将容器设置成：display:flex;
垂直居中:align-items: center;
水平居中:justify-content: center;

### 第四种居中方式：这是一种万能的方法，这种方法经常用的，所以要牢记
父标签：position:relative;
子标签：
position: absolute;
left: 50%;
top: 50%;
transform: translate(-50%,-50%);

- 解释：1.先将父容器的位置设置成相对位置position：relative；
2.再将子标签的位置设置成绝对位置position：absolute；
3.left:50%;的意思是：将子标签向右移动父容器宽度的一半；
4.top:50%;的意思是：将子标签向下移动父容器高度的一半；
5.tranform:translate(-50%,-50%);的意思是：再将子标签在x轴和y轴上分别移动自身的一半；这样就达到了将子容器在容器中垂直居中和水平居中的目的

	- 子主题 1

### 第五种方式：采用flex布局的另一种方式:在div容器中设置：
display: box;
box-pack:center;
box-orient:vertical;
display: -webkit-box;
-webkit-box-pack:center;
-webkit-box-orient:vertical;

### 第六种方式：先
将父容器转换成表格单元格类型，display;table-cell;
再在父容器中加入   vertical-align;middle;垂直对齐:中间;

## CSS3被划分成模块，其中最重要的CSS3模块包括：

### 标签选择器，也叫元素选择器（重点）

- 类选择器

	- 格式：.自定义类名{
属性：属性值;
.....
}

		- 类选择器的特点是：1.谁调用谁生效，不调用不生效；
		- 2.一个标签可以同时调用多个类选择器
		- 3.一个类选择器可以被多了标签重复调用；

- 标签选择器

	- 选择范围是页面上所有的同类标签
	- 但是标签选择器不能设置差异化

- id选择器

	- 使用id选择器要稍微谨慎一些

		- id选择器的特点是：1.使用的时候需要调用  id = “id名”
		- 2.一个id选择器只能被调用一次，多次调用不符合w3c标准规范；多次调用，js调用的时候会出错
		- 3.一个标签只能调用一个id选择器；id选择器我那个网之作用于一个标签，一个标签可以对应多个类选择器；
		- 4.同一个标签既可以调用类选择器也可以调用id选择器。

- 通配符选择器

	- 常用的通配符选择器是：
*{
    margin：0；
    padding：0；
    box-sizing:border-box;
}
	- 通配符选择器是对该页面上的所有标签都设置了属性；
	- 通配符选择器选择范围太广了，但是不推荐使用通配符选择器
	- 通配符选择器会降低页面的加载速度，会影响网页的渲染时间，取而代之的是把所有要统一设置的元素放到一起一块儿设置。

- 复合选择器

	- 交集选择器/标签制定式选择器

		- 标签   类/id选择器{属性：属性值;}

			- 例如：div   .tp{
border:1px solid red;
}

		- 交集选择器是即...又的关系

	- 后代选择器（读的时候必须从右向左读取选择器）

		- 父选择器    子选择器    子选择器{属性:属性值;}

			- 例如：div p span{
  font-size: 30px;
}

		- 后代选择器生效的前提是必须要有嵌套关系

			- 父在前   子在后
			- 后代选择器可以无限制的隔代
			- 只要能代表父子元素可以任意选择选择器的组合

				- 标签   #id
				- #id  .class
				- class   标签

	- 子代选择器（平时用的不是特别多，也可以是任意选择器的组合）

		- 子代选择器选择的是父标签下的直接下一级，隔代后的相同的子标签不会被选择到，选择的是亲儿子，孙子不会选择到

			- 父选择器>子选择器{属性:值;}

				- .box > p{
  font-size: 35px;
}

	- 并集选择器

		- 很多选择器的样式是一样的时候就会用到并集选择器，作用是：减少冗余代码

			- 选择器,选择器,选择器,选择器,......{属性:值;}每个选择器之间通过逗号进行一个集体的声明

				- .bo,p{
  font-size: 30px;
  border:1px solid yellow;
}

	- 交集选择器，平时用的不多

		- 要满足两个条件，即是这个标签又调用了类选择器

			- 选择器选择器{}选择器中间不得有空格

				- 例如：div.box{color:red;}

	- 相邻选择器/兄弟选择器

		- 相邻选择器后选择器必须与前选择器紧挨着（必须是并列关系），中间不能有其他标签

			- 例如：
h3 + p{
  border:1px solid yellow;
}

		- 相邻选择器特点：

			- 后选择器和前选择器必须是在同一个父标签下
			- 如果后标签有多个，那么搜索引擎会将后面的标签都会解析

				- 举个栗子：
li+li{
  font-weight:700;
}
				- 解释：若ui标签下有多个li标签，除了第一个li标签文字不进行加粗，其他剩余的几个li标签都会进行加粗显示，直到遇到不是li标签而结束

- 链接的伪类

	- 伪类选择器（内植类）

		- 超链接的默认状态（默认和悬停状态用的比较多）

			- a:link{属性：属性值;}

				- 一般:link会省略不写

		- 鼠标悬停状态

			- a:hover{
  color: pink;
  text-decoration: none;
}

				- 鼠标悬停上去的时候更改超链接字体的颜色和并将超链接的下划线进行隐藏

		- 访问过后的状态（这个一般不用）

			- a:visited{color:pink;}

				- 解释:意思就是这个超链接被点击过之后就会变成粉色

		- 超链接激活状态（鼠标按住不松手）

			- a:active{
  color: green;
}

		- 获取光标焦点后的伪类    :focus

			- input:focus{
  color: pink;
  background-color: yellow;
}

				- 这个伪类应用于有焦点的元素，比如input中的单行/多行文本输入框，获取焦点后就改变输入的字体颜色和背景颜色，也就是说，在用户开始键入信息的时候，文本的样式就开始进行了更改。

	- 伪类不光超链接可以使用，div也可以使用

		- 如果一个页面中要用到所有的伪类，则按着l  v   h   a的顺序进行书写
		- link    visited    hover   actiove顺序
		- 书写顺序不可打乱，否则的话，一些伪类效果不会出现

	- 位置（结构）伪类选择器：IE6、7、8不兼容伪类选择器

		- 若是选择父亲的第一个孩子则使用：

			- 父类选择器  子类选择器:frist-child{属性：属性值;}

		- 若是选择父亲的第二个孩子则使用：

			- 父类选择器  子类选择器:nth-child(2){属性：属性值;}

		- 若选择父亲的第n个孩子则使用：

			- 父类选择器  子类选择器:nth-child(n){属性：属性值;}

		- 若是选择父亲的最后一个孩子则使用：

			- 父类选择器  子类选择器:last-child{属性：属性值;}

		- 若要选择倒数第几个孩子的话则使用：

			- 父类选择器  子类选择器:nth-last-child(n){属性:属性值;}

	- 目标伪类选择器

		- 以锚点为例，只有出发锚点后，样式才会发生变化

			- 先设置锚点
			- 在链接到锚点
			- 最后在.css文件中书写：目标标签/目标的类选择器/目标id选择器:target{属性:值;}
			- 目标标签就是设置锚点的标签

	- 伪元素选择器：首行，首字母选择器

		- 首行伪元素选择器

			- 选择器::first-line{属性：值;}	 语法是两个冒号，但是一般只会写一个冒号，一个冒号对浏览器搜索引擎的兼容性更好

		- 首字母伪元素选择器

			- 选择器:first-letter{属性:值;}

	- 文本选中状态选择器
	- 前后伪元素选择器

### 框模型

- 元素的显示模式：不管是行内元素还是行内块元素，只要换行就会有间隙，这句话很重要
- 块元素的标签

	- div
	- h1-h6
	- form
	- table
	- dl
	- ul
	- ol

- 行内元素

	- span
	- a
	- em
	- i
	- del
	- u
	- s
	- ins
	- strong
	- b

- 行内块

	- img
	- input
	- textarea
	- select
	- td
	- 表单控件大多数都属于行内块元素

### 标签的嵌套规范

- p标签可以嵌套除了块元素以外的任意元素
- p标签不能嵌套块儿元素，但是可以嵌套行内元素，行内块元素
- 不推荐标题里面嵌套其他块元素，但是可以嵌套行内元素，行内块儿元素
- 行内块不能嵌套块儿元素，但是可以嵌套行内元素，行内块儿元素
- 行内元素不能嵌套块元素和行内块元素，只能嵌套行内元素
- a标签中不能嵌套a标签，但是a标签属于比较特殊的行内元素，因为有的时候会嵌套img标签（行内块元素）

### 行高  line-height(行高是文字之间基线与基线的距离)

- 默认值是normal     约等于文字的1.1-1.3倍
- 一行文字，行高与盒子高度一致的时候，那么这行文字就会垂直居中
- 一行文字，行高小于容器高度的时候，这行文字偏上显示
- 一行文字，行高大于容器高度的时候，这行文字偏下显示

### 背景和边框

- 背景（背景是在内容的下边）

	- background-color   背景颜色

		- 默认值是transparent透明的

	- background-image  背景图片地址

		- 属性值是url(背景图片的路径)

	- background-repeat  是否平铺

		- 默认值是repeat（平铺）沿着X周Y周铺满盒子
		- repeat-x:沿着X周水平方向平铺
		- repeat-y：沿着Y周垂直方向平铺
		- no-repeat：不平铺

	- background-position  背景定位

		- 可以设置方位值   left  right  center  top   bottom
		- 可以写两个方位值background-position:left  top（左上角）   right top（右上角）    center  center（水平居中，垂直居中）
		- 写一个方位值，另外一个值默认为center（居中）
		- 可以写具体的数值

			- 写两个数值，第一个数值是距离左边距离（x值），第二个数值是距离顶部的距离（y值）
			- 写一个数值，另外一个数值就是center

		- 方位值和数字混合使用

			- background-position:left  30px;(水平方向左对齐，垂直距离30px)
			- 如果第一个数值是方位值，只能写水平方向的方位值：left   right   center
			- 如果第二个数值是方位值，只能写垂直方向的方位值：top  bottom  center

		- 使用百分比的时候，是盒子宽度减去图片宽度剩下的数值的百分比

	- background-attachment  背景是否会随着滚动条固定还是滚动（背景附着）

		- 默认值是：scroll  滚动
		- 固定：fixed

			- 当背景附着的值是fixed的时候，图片的背景定位位置参考的不是盒子大小，而是参考的是浏览器的位置

	- 盒子在没有设置宽高的时候，背景颜色和背景图片撑不开盒子的宽高的
	- 背景属性的连写  background:背景颜色 背景图片路径 背景平铺 背景滚动 背景位置；

		- 例如：background:#ccc url(路径) no-repeat scrol center center;

	- 大背景 处理方式是：在body中引入大图片

		- body{background:url(图片路径) repeat center top}

	- 背景色的渐变：有两种方式

		- 方式一：  background：-webkit -linear-gradient（left/top，颜色，颜色）
		- 方式二： background-image:linear-gradient(to bottom,red,green);

- 边框

### 文本效果

- 颜色的表达方式

	- color：red、green、blue、pink、yellow...直接写颜色英文单词的形式，在开发中一般是用不到的
	- 十六进制表示法

		- #ff0000:  红色
		- #ooffoo: 绿色
		- #0000ff:蓝色
		- #000：纯黑色
		- #fff：纯白色

	- RGB表示法

		- color：rgb（x,x,x);    x表示数字，数字范围是0-255
		- 255,0,0		红色
		- 0，255,0	绿色
		- 0，0,255	蓝色

	- rgba(x,x,x,x);  最后一个x表示a的取值，a的取值范围是0-1，越接近1，显示越清楚，rgba的方式作用是将背景属性设置成透明色，这种方式是设置单颜色的透明度。
	- opacity：数字  作用是控制元素整体透明度的（取值范围是0-1）

		- opacity属性IE6.0-8.0浏览器是不支持的，9.0+的IE浏览器才支持该属性，若要兼容IE6.0-8.0的IE浏览器则可写成：  filter:alpha(opacity = 数字，数字范围在0-100)，这个写法不推荐使用

	- 文字的属性

		- color 文字 颜色
		- font-size  文字大小
		- font-family：arial,'宋体'；这种方式一般就写两个值，这个设置英文字体，一个设置中文字体
		- 文字渐变色
 background: -webkit-linear-gradient(30deg,#f15a52,#ff9143);
                -webkit-background-clip: text;
                color: transparent;

### 2D/3D转换

### 动画

### 多列布局

### 用户界面

## div标签介绍

### div是一个块标签，通常用来网页的布局，他一旦出现就会独占一行，当其内容超出一行的时候，则自动换行，div标签独占一行时div标签的特性。

## 常用的属性

### font-size  文字大小，现在网页上最小的文字的像素是12px，文字的大小一般选用偶数像素

### font-weight：

- 900
- 700（通常加粗为700）
- 400（其实写了400也是没有被加粗）
- normal  默认值400不加粗
- bold  加粗700
- lighter  更细

### color		文字颜色

### width		宽度

### height		高度

### text-align	内容的水平对齐方式

- 默认是左对齐left
- center水平居中
- right右对齐

### text-indent	首行缩进，text-indent：2em；一个em相当于一个汉字的大小，em是一个相对文字大小

### word-spacing	单词与单词之间的距离，只对单词有效，对英文字母无效（这个属性对中文是无效的），可以是负值也可以是正值，值越大间距越大

### letter-spacing	中文字符之间的距离（中英文字符都有效）它的值可以是负值可以是正值，值越大，间距越大

### line-height	调整行与行之间的距离，简称行高

### margin-left:auto	 

### margin-right:auto

### font-family:	  字体

- 浏览器解析字体的时候，顺序是先用第一个字体解析，第一个字体解析不了，交给下一个字体进行解析
- font-family:"microsoft  yehei";   微软雅黑
- font-family: "黑体";  也可以直接写汉字
- 若不知道什么字体，可以在浏览器中进行查找：打开浏览器，按下F12键，在console界面输入escape("字体")+回车，复制到代码中后，"%u"用"\"反斜杠代替。escape就是转码的意思

	- 例如：font-family: '\5B8B\4F53';

- font-family:arial,'宋体';

	- arial:解析英文，这种方式是经常用的
	- ‘宋体’：解析中文，用单引号括起来
	- 多个字体之间用逗号隔开，英文字体写到前边，中文字体写到后边

### border:0/none

- 清除浏览器的默认变宽

### outline:0/none

- 清除轮廓线

### caret-color:red/blue....；改变输入框光标颜色。

### border-radius:	圆角（IE678都不支持）

- 将div设置成一个圆圈  border-radius:50%;(圆心放到边线的一半，div就变成了一个圆)
- 如果是两个值border-radius-top-left：30px  40px;第一个值是水平半径，第二个值是垂直半径

### box-shadow	阴影效果

- box-shadow：阴影水平偏移量（正值向右，负值向左）   阴影垂直偏移量（正值向下，负值向上）   模糊的范围(没有负值)   阴影大小   阴影颜色    内(inset)/外(默认outset一般不写)阴影；   其中水平阴影和垂直阴影是必写属性。
- 多组阴影之间用逗号隔开

	- box-shado:20px -10px 20px 2px #ccc，20px -10px 20px 2px red;

### padding-top  内容距离上边框的距离

### font-style	文字风格

- 默认值是normal（正常）
- italic（斜体）一般使用这个
- oblique(倾斜)

### margin:   0   auto;

- 这个属性用于将标准流中的块元素，进行进行居中，但是前提是这个块元素的宽度要小于其父元素的宽度；

### text-align:  center;

- 可以使块元素中的行内块元素、行内元素、文字、图片进行居中显示；

### background-color	 背景颜色

### text-decoration:none;	将超链接的下划线进行隐藏，这个属性经常用的，一定要牢记

### text-decoration: underline;  

-   鼠标放上去的时候显示下划线。这个属性是放到链接的伪类中使用

### text-decoration: line-through;

- 贯穿线

	- 没什么卵用

### text-decoration: blink;

- 闪烁

	- 这个属性只能在网景浏览器上使用，其他浏览器都不支持，没毛线用

### text-decoration：overline    上划线

### visibility: hidden;   隐藏复选框的框框（能见度：隐藏）

### list-style:none;   清除无序列表小圆点儿

###  disabled禁用------input按钮的禁用，这是input的标签的一个属性，并不是style的样式

## CSS的三大特性

### 层叠性

- 层叠性指的是CSS样式的叠加，多个样式作用于同一类标签的时候，发生了样式冲突，后边的样式会把前边的样式给覆盖掉（层叠掉），实际就是css执行的就近原则，和样式调用的顺序是没有关系的，只是看哪一个样式离标签近就使用哪一个样式

### 继承性

- 所谓继承性，就是书写css的时候，子标签会继承父标签的某些样式，子元素可以继承父元素的标签包含：text-     font-    line-    color这些样式子元素都可以继承，

	- 继承图解

- 但是a标签不能继承父元素的字体颜色，标题标签不能继承父元素的文字大小

### 优先级 是解决样式冲突的能力，权重高的优先级大优先执行，权重低的，不执行

- 权重相同的时候，采取就近原则
- 1.标签选择的权重是   0001
- 2.类选择器的权重是  0010
- 3.id选择器权重是    0100
- 4.行内样式权重是   1000
- 最大的权重是   !important   无穷大

	- 举个栗子：color：red !important;

- 继承的权重为0

	- 1.如果子元素自身没有样式，就会继承父元素的样式；
2.如果子元素的样式和父元素的样式发生冲突，永远执行子元素自身的样式；
3.父元素继承过来的样式，对于子元素来说，权重为0，
   即使父元素中有!important，权重依然是0.

- 权重会叠加

	- 1.如果选择器（样式）作用到元素自己身上，权重会叠加；
2.如果选择器（样式）作用到元素的父元素上，对于元素自身来      说，就是继承，那么继承过来的权重就是为0；

## CSS3的新特性

### 过渡

### 动画

### 形状转换

### 选择器

### 阴影

### 边框

### 背景

### 文字阴影

### 渐变颜色

### 弹性布局

### 栅格布局

### 多列布局

### 盒子模型

- box-sizing:border-box的时候，边框和padding包含在元素的宽高之内
box-sizing:content-box的时候，边框和padding不包含在元素的宽高之内！

### 媒体查询

- 就在监听屏幕尺寸的变化，在不同尺寸的时候显示不同的样式！在做响应式的网站里面，是必不可少的一环！

*XMind: ZEN - Trial Version*