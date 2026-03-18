# Javascript-WebAPIs

> 操作页面元素做出各种好玩的效果。使用js去操作页面文档和浏览器
>
> - DOM 文档对象模型 使用js去操作文档
> - BOM 浏览器对象模型 使用js去操作浏览器
> - API 应用程序接口 无需关心内部如何实现，程序员只需要调用就可以很方便实现某些功能

## DOM（文档对象模型 Document Object Model）

操作网页文档，实现网页特效和用户交互，将页面的内容当作对象来处理，通过对象的属性和方法对网页内容操作。

|     描述     |            属性/方法            |             效果             |
| :----------: | :-----------------------------: | :--------------------------: |
| 获取DOM对象  |    document.querySelector()     |     获取指定的第一个元素     |
| 获取DOM对象  |   document.querySekectorALL()   |      获取指定的所有元素      |
| 操作元素内容 |         元素.innerText          |   操作元素内容，不解析标签   |
| 操作元素内容 |         元素.innerHTML          |    操作元素内容，解析标签    |
| 操作元素样式 |        元素.style.width         |      通过style操作样式       |
| 操作元素样式 |         元素.className          |       通过类名操作样式       |
| 操作元素样式 |      元素.classList.add()       |           增加类名           |
| 操作元素样式 |     元素.classList.remove()     |           删除类名           |
| 操作元素样式 |     元素.classList.toggle()     |           切换类名           |
|   间隔函数   | setInterval(function() {},1000) | 定时器，每隔指定时间重复执行 |

document对象

DOM里面提供的一个对象，是DOM**顶级对象**，作为网页的入口，他提供的属性和方法都是用来访问和操作网页内容的

### 获取DOM元素

想要操作页面元素，我们需要先利用DOM方式来获取这个元素。使用CSS选择器来获取DOM元素

```javascript
//选择匹配的第一个元素
document.querySelector('css选择器')
//只选择满足条件的第一个小li
//可以应用:nth-child()来完成精准选择
```

选择匹配多个元素对象

```javascript
document.querySelectorAll('ul li') //会把所有的小li都选择出来
//得到一个伪数组，有长度和索引号，没有数组一些常用的方法，没有push pop
```

其他获取方式(使用较少，但是要能看懂)

```javascript
//根据id获取
document.getElementById('box')
//根据类名获取
document.getElementByClassName('box')
//根据标签名获取
document.getElementByTagName('box')
//根据name属性获取
document.getElementByName('box')
```

### 操作元素内容

通过DOM对象的操作实现增删改查

```javascript
//对象.innerText 增删查改 不能解析标签
//查
console.log(box.innerText)
//改
box.innerText = '迪丽热巴'
//删
box.innerText = ''
//对象.innerHTML 能解析标签，标签会生效
```

### 操作元素常用的属性

还可以通过DOM操作元素属性，比如通过更换src更换的图片地址。比如href、title、src等等

语法：

```javascript
对象.属性 = 值
```

### 操作元素样式属性

实现轮播图小圆点自动更换颜色的效果，滚动图片的效果

通过style属性操作css

```javascript
//语法 对象.style.样式属性 = 值
const box = document.querySelector('.box')
box.style.width = '200px'
box.style.backgroundColor = 'pink'
```

通过类名操作元素样式：如果修改样式比较多，直接用style属性修改很繁琐，我们可以借助于css类名形式

```javascript
//active 是一个类名
对象.className = 'active'
利用类名添加属性，新的类名会覆盖原来的类名
```

通过classList操作元素样式：解决上一个方法会覆盖类名的情况，我们可以通过classList方式追加何删除类名

语法：

```javascript
//新增一个类名
对象.classList.add('类名')
//移除一个类名
对象.classList.remove('类名')
//切换一个类名
对象.classList.toggle('类名')
这些类名前不用额外加'.'
```

操作表单元素属性：可以点击眼睛看到密码，将表单类型转换成文本框

```javascript
获取：DOM对象.属性
设置：DOM对象.属性 = 新值
表单.value = '用户名'
表单.type = 'password'
```

### 自定义属性

标签天生自带属性，在h5中推出了专门的data-自定义属性，通过自定义属性存储数据，后期使用这个数据进行操作

```javascript
在标签上一律以data-开头
获取时一律以dataset对象的方式获取
data-id="10"
box.dataset.id //获取
```

## 定时器-间隔函数

网页中经常需要一种功能：每隔一段时间需要自动执行一段代码，不需要手动进行处罚

例如：网页中的倒计时。想要实现这个功能就要**定时器函数**。有两种，间隔函数和延迟函数

```javascript
//开启定时器
setInterval(函数， 间隔时间)
//每间隔一段时间自动调用函数，间隔时间单位为毫秒
//调用时候直接写函数名字，不需要小括号

//关闭定时器
let 变量名 = setInterval(函数, 间隔时间)
clearInterval(变量名)
```

## 事件核心

以前的代码都是自动执行，我们希望一段代码在某个特定的时机才去执行，比如：

- 点击按钮可以弹出警示框
- 比如鼠标经过下拉菜单等等

事件：在程序运行的时候，发生的特定动作或者特定的事情。

### 事件监听

```javascript
元素对象.addEventListener('事件类型', 事件处理函数)
//事件发生后，将想要执行的代码写道事件处理函数里面
//事件类型：点击、经过等触发状态
//事件类型是字符串
```

### 回调函数

**把函数当作参数来传递给另外一个函数**的时候，这个函数就是回调函数（回头调用的函数）

```javascript
setInterval(function() {}, 1000) //每隔一秒钟回头调用函数一次
//事件监听函数也是同理，例如每点击一次回头调用函数一次
```

### 事件监听版本

```javascript
//DOM L0版本
//对象.on事件类型
btn.onclick = function() {
  //缺点：注册同名事件后面的事件会把前面的事件覆盖掉
}
//DOM L2版本（推荐使用）
btn.addEventListener('click', function() {
  //注册同名事件不会出现事件覆盖的情况
})
```

### 事件类型

事件类型的大小写敏感字符串，统一用小写字母

| 鼠标事件 | click 鼠标点击              | mouseenter 鼠标经过 | mouseleave 鼠标离开       |
| -------- | --------------------------- | ------------------- | ------------------------- |
| 焦点事件 | focus 获得焦点              | blur 失去焦点       |                           |
| 键盘事件 | keydown 键盘按下            | keyup键盘抬起       | keydown得不到最后一次的值 |
| 文本时间 | input 表单value被修改时触发 |                     |                           |

对象.click()方法是程序可以模拟用户点击事件，自动执行

键盘事件中三者的执行顺序：keydown--input--keyup

### 事件对象

也是个对象，对象里面有事件触发时的相关信息，包含属性和方法

可以判断用户点击了哪个按键，从而判断点击了哪个元素，做相应的操作

语法：

注册事件中，回调函数的第一个参数就是事件对象

一般命名为event、ev、e

```javascript
元素.addEventListener('click', function(e) { //e为事件对象
  
})
```

常见属性：

| 属性名  |  类型  |                说明                 |
| :-----: | :----: | :---------------------------------: |
| offsetX | number | 事件发生时，鼠标相对于事件源的x坐标 |
| offsetY | number | 事件发生时，鼠标相对于事件源的y坐标 |
| target  | object |             事件源对象              |
|   key   | string |      判断键盘上按下的是什么键       |

### 环境对象-this

函数内部特殊的this，它指向一个对象，并受当前环境影响。可以让我们的代码更加简洁

谁调用，this就指向谁：

- 在全局环境下，this指向window对象
- 在普通函数下，this指向window对象，因为函数被window调用（谁调用指向谁）
- 在对象方法的情况下，this指向该对象
- 在事件情况下，this指向这个事件的对象

### 排他思想

目的是突出显示某个元素，比如有多个元素，当鼠标经过的时候，只有当前元素会高亮显示。

口诀：注意排序。1.先排除其他人 2.然后保留我自己

## 事件进阶

### 事件流

事件流指的是事件完整执行过程中的流动路径。当触发事件时，会经历两个阶段，分别是捕获阶段、冒泡阶段。

### 事件捕获

事件捕获需要些对应的代码才能看到效果

代码：

```javascript
DOM.addEventListener(事件类型,事件处理函数,是否使用捕获机制)
//说明：传入第三个参数是true代表捕获阶段触发（很少使用）
//若传入false代表冒泡阶段触发，默认就是false
```

### 阻止冒泡

问题：因为默认就有冒泡阶段的存在，所以容易导致事件影响到父级元素

需求：若想把事件就限制在当前元素内，就要阻止事件冒泡

前提：阻止事件冒泡需要拿到事件对象

语法：

```javascript
事件对象.stopPropagation()
```

注意：此方法可以阻断事件流动传播，不光在冒泡阶段有效，捕获阶段也有效

### 鼠标经过/离开事件的区别

鼠标经过/离开事件:

- mouseover 和 mouseout 会有冒泡
- mouseenter 和 mouseleave 没有冒泡(常用)

### 事件委托

是js中注册事件的技巧,原本要注册在子元素的事件寄托给父元素,让父元素担当监听的职务,减少注册监听的次数,可以提高程序的性能.

原理:利用事件冒泡的特点,在子元素会冒泡到父元素.给父元素注册事件,当触发子元素的时候,会冒泡到父元素身上

**实现**:事件对象.target.tagName可以获得真正触发事件的元素

### 阻止默认按钮

阻止元素发生默认的行为

例如:

- 当提交按钮时阻止对表单的提交
- 阻止连接跳转等等

语法:

```javascript
事件对象.preventDefault()
```

### 移除事件监听

移除事件处理函数也称为解绑事件

```javascript
//使用addEventListener方式注册，必须使用
removeRventListener(事件类型，事件处理函数，[捕获或者冒泡阶段]) //进行解绑，匿名函数无法解绑
//这是移除L2事件监听

//移除L0事件监听
on事件方式，直接使用null覆盖偶就可以实现事件的解绑
```

## 页面加载事件

加载外部资源（如图片、外联css和javascript等）加载完毕时触发的事件

事件名：load           给window添加load事件

```javascript
window.addEventListener('load', function() {
  //执行的操作
})
```

当初始的HTML文档被完全加载和解析之后就触发，而无需等待样式表、图像等完全加载

事件名：DOMContentLoaded

```javascript
document.addEventListener('DOMContentLoaded',function() {
  //执行的操作
})
```

## 页面滚动事件

滚动条在滚动时候持续触发事件，可以实现固定导航栏的效果和搜索框的固定。

事件名：scroll

```javascript
//页面滚动事件
window.addEventListener('scroll',function() {
  //执行的操作
})
```

document.documentElement.scrollTop 来获取页面向下滚动的距离

## 页面尺寸事件

会在窗口尺寸改变的时候触发事件：

resize

 ```javascript
window.addEventListener('resize',function() {
  //执行了代码
})
 ```

## 元素的尺寸和位置

获得元素的尺寸大小和页面中的位置

使用场景：

- 可以通过js方式，得到元素在页面中的位置
- 可以通过js方式得到元素的实际大小

offset家族：

| 大小                                                         | 位置                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| offsetWidth和offsetHeight 获取元素自身的宽高、包括元素自身设置的宽高，返回的数字不带单位而且是制只读属性。 | offsetLeft和offsetTop ，获取元素距离自己定位父级元素的左、上距离，跟绝对定位类似。返回的是数字不带单位，并且是只读属性。 |

 ## 日期对象Date

用来表示时间和日期的对象，可以得到当前系统的日期和时间，当代码中发现了new关键字时，一般将这个操作称为实例化。

获得当前日期

```javascript
const date = new Date()
```

获得指定日期

```javascript
const date = new Date('2099-9-9')
```

### 格式化日期对象

使用场景：因为日期对象返回的数据我们不能直接使用，所以需要转换为实际开发中的常用格式（格式化日期对象）

| 方法                 | 作用                                         | 说明                 |
| -------------------- | -------------------------------------------- | -------------------- |
| toLocaleString()     | 返回该日期对象的**字符串**（包含日期和时间） | 2099/9/20 18：30：43 |
| toLocaleDateString() | 返回日期对象日期部分的**字符串**             | 2099/9/20            |
| toLocaleTimeString() | 返回日期对象时间部分的**字符串**             | 18：30：43           |

### 时间戳

从1970年1月1日0时0分0秒起始到现在的总毫秒数，它是一种特殊的时间计量方式。

使用方式：计算倒计时的效果，需要借助时间戳来完成

算法：将来的时间戳-现在的时间戳 = 剩余时间毫秒数 ，将剩余时间毫秒数转换成年月日时分秒就是倒计时时间

```javascript
// 1.getTime() 需要实例化
const date = new Date()
console.log(date.getTime())
// 2. +new Date() 本质转换为数字  此种方法使用次数较多
console.log(+new Date())
//3. Date.now() 无需实例化，但是只能得到当前的时间戳
console.log(Date.now())
```

## DOM节点

DOM树：DOM将HTML文档以树状结构直观表现出来，我们称之为DOM树或节点树

节点：是DOM树中的单个点。包括文档本身、元素、文本以及注释都是属于节点

- 元素节点（重点） 所有标签比如body、div 、     html是根节点
- 属性节点 所有的属性比如herf
- 文本节点 所有的文本

学习节点的好处：利用节点关系可以更好操作元素（查询更方便）

### 查找节点

利用节点关系查找结点，返回的都是对象

```javascript
//父节点查找
子元素.parentNode //返回最近一级的父节点对象，找不到返回null

//子节点查找
节点对象.children //获取所有子元素节点，返回的是一个为数组
console.log(li2.previousElementSibling) //获取上一个兄弟 
console.log(li2.nextElementSibling) //获取下一个兄弟
```

### 增加节点

很多情况下，我们需要在页面中增加元素。比如，点击发布按钮，可以新增一条信息。

一般情况下，我们新增节点，按照如下操作：

1.创建一个新节点

2.把创建的新的节点放到指定元素内部

```javascript
//创造一个新的节点元素
document.createElement('标签名')
//追加节点，想要在界面看到，必须插入到某个父元素中
//父元素最后一个子节点之后，插入节点元素
element.append()
//父元素第一个子元素的之前，插入节点元素
element.prepend()
```

### 删除节点

若一个节点在页面中已经不需要，可以删除它

```javascript
element.remove()
//把对象从他所属的DOM树中删除
```

## M端时间

移动端有自己独特的地方，比如触摸事件touch，安卓和ios都有

touch对象代表一个触摸点，触摸点可能是一根手指，也可能是一根触摸笔。触摸事件可响应用户手指对屏幕或者触控板的操作。
常见的触屏事件如下：

| 触屏touch事件 | 说明                          |
| ------------- | ----------------------------- |
| touchstart    | 手指触摸到一个DOM元素时触发   |
| touchmove     | 手指在一个DOM元素上滑动时触发 |
| touchend      | 手指从一个DOM元素上移开时触发 |

