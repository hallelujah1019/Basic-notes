# CSS的高级技巧

## 移动  translate

### 单个写：  transform：translateX(100px)   延X轴向右移动100像素  正值向右

### 合起来写：  tranform: translate(100px,100px)   延X轴向右移动100像素   延Y轴向下移动100像素

### 百分数形式：  transform：translate（50%，50%）;这里的百分数，表示移动距离是自身的百分之50；并不是其所在父元素的百分之五十。
百分比是以自身宽高为基准
百分比也可以当个使用（transform：translateX/Y（100px）），也可以合起来使用

### 移动与定位（position、margin）的区别：
定位：定位和margin会影响其他盒子位置（定位并且脱离了标准流）
         行内元素使用定位，直接从行内元素转变为了块级元素。
移动：不影响其他元素的位置，简单调一下盒子位置，可以用一下translate来进行微调，因为使用translate来调整盒子位置，不会影响其他盒子位置。
          在行内元素无效，只对块级元素生效。
一句话概括position是为页面布局而生的，
                 transform是为动画而生的。两者的功能看起来是一样的，但是translate不会引起浏览器的重绘和重排（虽然我还不知道这句话是什么意思）。

### 2D中的居中转换（这是重点）这个就是万能的居中方案（工作中用到的比较多，这个方法的优势是，不再在意自身盒子的宽高，只需要设置百分之50就好）

- position：absolute；
（top值和left值相对于父亲的宽高来讲）
top：50%；
left：50%；
（transform是相对于自身自的宽高来讲）
tranform：translate（-50%，-50%）；

## 2d转换

### 变形之位移     transform:translate(Xpx,Xpx)

- 括号中写一个值的时候，是水平向右移动的距离
- 写两个值的时候，第二个值是垂直向下移动的的距离
- 如果写的是百分比，则移动的是自身宽度或高度的百分比，并不是其所在的父元素的百分比，所以尽量写具体的像素值，写百分比容易把自己干懵逼

### 变形之缩放    transform:scale(Xpx,Xpx);

- 第一个值是水平方向的缩放比
- 第二个值是垂直方向上的缩放比
- 若是写一个值的时候：是等比例缩放，长宽方向都使用一个缩放比
- 缩放的特点：
缩放会使CSS属性还有他的子元素都会被缩放，只要是盒子设置了缩放，缩放中的所有子元素都会被缩放。包括：border，文字
缩放后的元素不会影响其他盒子的位置。

### 变形之旋转  

-  transform:rotateX(Xdeg)      沿着X轴方向旋转多少度
- 默认和正值都是顺时针方向，负值为逆时针
- 旋转会改变盒子初始轴的方向
- transform：rotateY(Xdeg)     沿着Y轴方向旋转多少度
- 若是rotate后面没有跟X或者Y的话，那么需要旋转的对象就是沿着X和Y的中心点进行旋转。rotate后面只能跟一个数据，需要旋转的对象要不沿着X轴旋转要不就沿着Y轴旋转，若是写入两个值，浏览器会不知道对象到底该沿着哪个轴进行旋转，浏览器会蒙圈。
- 如果非要写两个值的的话，就这么写： transform:rotateX(Xdeg) rotateY(Xdeg);  两个方向之间不需要加逗号
- 专门控制旋转元素的中心点（这个属性用的比较低，作为了解就好）     transform-origin:center（中心点，这个中心点是垂直方向和水平方向交叉的中心点）left top(左上角)   right  top(右上角)   left bottom（左下角）   right bottom（右下角）里面不光可以写方位词，还可以写具体的数值比如：50px  30px  ;（也可以写百分比）  transf-origin：20px；（使用一个参数的时候，另一个参数默认是50%；）

### 变形之倾斜

- transform：skewX(Xdeg);  沿着X轴进行倾斜
- transform：skewY（Xdeg）；  沿着Y轴进行倾斜
- transform：skew（Xdeg，Ydeg）；里面可以写两个值，先沿着X轴进行倾斜，再沿着Y轴进行倾斜

### X轴正值方向水平向右，Y轴方向正值是锤子向下

### transform的特点：
后面所有的属性（移动，旋转，缩放）都不会影响其他盒子的位置，

### tranform在使用中不要上下连写，要横向连写，因为下边的效果会把上面的效果进行覆盖
2D的简写：transform：translate（移动）  rotate（旋转）
一般情况下，先写移动，在写旋转

## 元素的显示与隐藏

### display（显示）

- display：none；隐藏对象  隐藏之后不占位置   这个相比较于visibility：hidden用的比较多。
- display：block；除了有转换成块元素的作用，还有显示元素的作用

### visibility（可见性）

- visibility：hidden；对象隐藏   隐藏之后还是占用原来位置的

### overflow（溢出）

- overflow：hidden；  溢出隐藏   溢出的内容是不占位置的
- overflow:scroll;  不管内容是否溢出都生成滚动条
- overflow：auto;  内容不溢出不出现滚动条，内容溢出生成滚动条。

## 鼠标样式

### cursor：default  默认值，白色箭头

### cursor：pointer；小手儿样式

### cursor：move；   移动的样式

### cursor：text；   文本光标样式

### cursor：not-allowed；    禁止的鼠标样式

### cursor：help；   帮助的鼠标样式

## 轮廓线outline

### outline：none；清除轮廓线

## resize文本域多拽

### resize：none；禁止文本域拖拽

## 实现单行文本省略号有三步骤

### white-space：normal  默认值文字自动换行

### white-space：nowrap;  强制一行显示

### overflow：hidden；

### text-overflow：ellipse；溢出省略号

## vertical-aline垂直对齐（主要作用：清除图片底部与div之间的距离）
这个属性是行内元素，行内块元素垂直对齐使用的，行内元素，行内块元素的专有属性，，行内元素，行内块元素默认的对齐方式都是文字的基线对齐。块元素没有这个属性。注意：行内块元素默认基线对齐。所以如果一个div中有行内块元素需要对齐的话，需要让将对齐方式更改一下，不让行内块元素基线对齐，将值设置成middle/top/bottom都可以。

### vertical-aline：middle  垂直居中

### vertical-aline：top；顶对齐

### vertical-aline：bottom；底对齐

### 或者把图片转成块元素，display：block；

### vertical-aline：seline；基线对齐，一般不用

## 精灵图技术

### 第一步：先测量小背景图的的宽和高

### 第二步：将div的宽和高设置成背景的宽和高

### 第三部使用background：url(图片的相对路径) no-repeat  0  负值；
解释：0   负值，的意思是：背景图片在div中默认是左上角对齐（坐标值是0,0）距离y轴的距离为0   距离X轴的距离为负值；但是，为什么是负值呢？因为正值是将图片往下移动，负值是将图片往上移动。所以若是所需图片在下面的话，要将图片往上移动，所以应为负值。

## 结构伪类选择器

### 选择父元素里面同类型的第n个子元素.father h2:nth-of-type(n){}

## 占位符placeholder的选择器

### input::placeholder{color:green;}

## 属性选择器

### [属性]  通过标签的属性来选择标签

### [属性="属性值"]   通过标签的完成的属性值来选择标签

### [属性^=“字符”]   通过属性的值以某些字符开头来选择标签

### [属性$="字符"]  属性的值以某些字符结尾来选择标签

### [属性*='字符']   只要包含了字符的标签都会选中

## css书写顺序

### 布局定位属性

- display
- position
- float
- clear

### 自身属性

- width
- heighe
- background-color

### 文本属性

- color 
- font

### 其他属性是指CSS3特有的属性

- content
- cursor
- box-shadow
- border-radius
- text-shadow
- background:linear-gradient   线型渐变

## 过渡动画transition(从一个状态渐渐的过渡到另一种状态)

### 过渡必须要有触发条件的（比如鼠标悬停）

### 这个属性通常都写在开始的默认状态上。

### 过渡的属性   transition-property:  默认值为all（所有的属性都过渡）

### 花费的时间  时间属性是必写属性

### 运动曲线

- transition-timing-function:

	- ease:慢慢的慢下来，逐渐慢下来  默认值
	- linear  匀速

### 何时开始

- transition-delay

### 过渡属性的连写：

- transition:all 1s linear  1s  (前面的1秒是过渡时间为1秒，后面的一秒是延迟1秒)，其中的过渡所需要的时间为必写项，其他不写的均为取默认值   all表示：监听所有的属性都会做到监听，只要有变化，就会有过渡效果。

## 动画

### 第一步：先定义一个动画集关键字是：@keyframes是定义动画集的意思
@keyframes move（move是动画集的名称，随便取名就行） {
   from{
			动画的开始状态
   }
   to{
           动画的结束状态
   /* 向右移动100px 向下移动200px 沿着中心点旋转360度 */
  transform: translate(100px,200px) rotate(360deg);
  }
}
时间节点的状态都是基于上一个时间节点状态的变化
时间节点可以实现更为细致的动画的控制

### 第二步：调用动画集

- animation-name: move;(动画集的名称)  Xs(动画完成的秒数)  infinite(动画循环执行)
- animation-duration：1s;  动画执行完成所需要的时间
- animation-lteration-count：X；   如果写的是数字的话，就是动画执行的次数  
										  infinite（英菲尼迪）   循环播放  
- animation-timing-function:ease(默认值平滑过渡)  
linear  线型过渡（常用）
ease-in：由慢到快
ease-out：又快到慢
ease-in-out：由慢到快再到慢
/*分帧图动画设置steps（分步）   把上面的一大步分成几小步来实现*/
steps-start：（遇到分帧图就设置两个时间节点）
遇到分帧图，
首先它的动画节点就是两个，（0%-100%），
设置背景图片的位置移动，需要让整个分帧图全部移动出去，
速度曲线：steps（）括号中的数字是写有几张分帧图，就写几
- animation-direction：
normal（默认值 动画回去的时候是以快闪的状态回去的）动画执行的方向
reverse：反向播放，从结束状态开始播放，到开   始状态结束
alternate：逆播动画回去的时候有一个播放的状态（在这里要清楚，逆向播放一次也算一次播放次数）
alternate-reverse：逆播+反向播放
- animation-fill-mode：
none：默认是动画播放完毕后停止到开始状态。
forwards：动画播放完毕后停止到结束状态（常用）。
backwards：动画结束后停止到开始状态和none相似；
both：根据播放次数和动画执行方向来决定动画完毕后来决定
           动画停止到什么状态。
           若是正常播放（没有逆向播放和反向运动时），动画结束状态始终停止到动画结    束状态
           若动画有反向运动但是没有逆向播放时，动画始终停止到开始状态。
           若动画有逆向播放没有反向时，播放次数为偶数时，动画播放完毕后停止到开始状态，播放次数为奇数时，动画播放完毕后停止到结束状态。
           若动画又有逆播又有反向的时候，播放次数为偶数时，动画播放完毕后停止到到结束状态，播放次数为奇数时，动画播放完毕后停止到开始状态。
- animation-fill-mode:动画结束状态
none：默认是动画播放完毕后停止在动画开始状态；
forwards：动画播放完毕后停止到结束状态。
backwards：动画播放完毕后停止到开始状态。
both：根据播放次数来决定动画播放完毕后停止到什么状态，若是正常播放的话，播放次数为偶数时，动画播放完毕后停止到开始状态
- animation-delay：1s   动画的延时
- animation-play-state:paused(播放暂定);这个属性一般是鼠标放到div上，滚动图就暂定滚动状态。
例如：.box:hover img{
            animation-play-state: paused;
}
- 动画属性的连写中，动画名和动画时间是必写项
name：动画名称
duration：动画所完成的时间
timing-function:  运动曲线  linear（匀速）
delay：延迟
animation-lteration-count：执行次数  infinite（循环播放）
direction  设置动画是否反向逆播
fill-mode  设置动画结束的位置，一般是结束在动画前进的位置forwards，
- 动画之间的组合，就是用英文逗号将不同的动画进行隔开就可以了：animation:动画名1  动画时间。。。,动画名2   动画时间。。。

## 3d转换

### 这个属性，一般是加到body上，形成统一的透视感，perspective  开启近大远小的透视感  眼睛距离屏幕的距离

### 3D呈现：transform-style：preserve-3d（开启3D空间）还有一个默认值flat（平的）；
作用：有亲生子元素做3D转化，需要在其父元素上加上这个属性；父亲给亲生子元素开辟一个3D空间后，子元素做的3D转化才会被观察到，否则子元素做的3D呈现，不会出现效果。这个属性加在3D转化子元素的亲爹（div）上；

## 伸缩盒子

### display：flex（伸缩盒）；

### 默认情况下：主轴是X轴自左向右
侧轴是Y轴自上而下

### 通常我们都是将父元素设置为伸缩盒子，父元素中的子元素就可以伸缩了

- 主轴的对齐方式：
justify-content   设置或检索弹性盒子元素在主轴（横轴/也就是X轴方向）方向上的对齐方式
justify-content:设置元素在主轴上（水平方向/X轴）的对齐方式
flex-start（默认值）：延主轴开始的地方进行对齐，靠左对齐
flex-end：延主轴结束的地方进行对齐，靠右对齐
center：父元素中的子元素水平居中对齐，这个属性是经常用到的，一定要牢记
space-between： 两端对齐，中间等距，这个真的很方便，也是常用的，要牢记
space-around： 中间等距，左右两边的距离是中间距离的一半儿。
- 调整多行侧轴方向的对齐方式：
一般使用 align-content这个属性，因为这个属性有space-between   space-around属性，调整起来比align-items更灵活一些，和justify-content一样，有一样的属性值：
flex-start（默认值）：延主轴开始的地方进行对齐，靠左对齐
flex-end：延主轴结束的地方进行对齐，靠右对齐
center：父元素中的子元素水平居中对齐，这个属性是经常用到的，一定要牢记
space-between： 两端对齐，中间等距，这个真的很方便，也是常用的，要牢记
space-around： 中间等距，左右两边的距离是中间距离的一半儿。
- 调整主轴方向
flex-direction：row默认值，主轴水平方向
row-reverse  主轴结束位置对齐，元素反向显示
column：将主轴改变成垂直方向 ，侧轴改变成水平方向
column-reverse：主轴结束位置对齐，元素反向显示
- 多行和多行侧轴调整  flex-wrap:（这个属性对只有一行的元素是没有作用的，只有元素比较多的时候，使用这个元素才会起到换行的作用）
nowrap  默认值是不换行
wrap   换行
wrap-reverse  内容换行的反向显示
- 侧轴的对齐方式  align-items
stretch默认值，拉伸的意思，解释：若是父元素中的子元素没有设置高度的话，使用这个属性，子元素的高度就会和父元素的高度是一样的，但是，如果子元素设置了高度，再次使用这个属性是不起作用的，要不就把子元素的高度删掉，要不就将子元素的高度设置成自动（height:auto;）
flex-start:侧轴开始的地方对齐，默认是自上而下对齐，也就是上对齐
flex-end：延侧着结束的地方进行对齐，也就是底对齐
center：侧轴居中对齐
baseline：基线对齐，用的不多。

	- 若是调整侧轴上的对齐方式的时候，一般不用这个align-items属性

### 设置子元素在父元素中所占的比例

- flex：1；flex：2；flex：3；表示，将父元素分成6份， flex后面跟的数字，表示子元素所占父元素比例，1就是占父元素1份，2表示占父元素2份，3表示占父元素3份

## background-size：调整背景图的尺寸

### 1.后面可以跟px值，若是两个参数值，有可能会失去图片比例

### 2.后面若是跟一个值，高度省略（自适应），宽度会使用你设置的尺寸

### 3.后面若是跟百分数，相对于当前盒子的宽度来说的

### 4.后面若是跟cover（覆盖）值，当前盒子绝对不留白

### 5.contain（包含）绝对将背景图显示全

## margin的使用特点

### margin  若一个盒子的宽高，没有明确通过width/height属性设置，但是有明显的宽高，设置margin正值时，会出现向内挤的情况，设置margin负值时，会出现向外拉的效果（这里的margin正值和负值都是指的是margin-left和margin-right的值）。这个向内挤，挤的其实是内容区域的宽度，因为这个div的宽度没有给到具体的数值，所以会出现这种现象。

- 布局上好多盒子，都是这么挤出来的，

*XMind: ZEN - Trial Version*