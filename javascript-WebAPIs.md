

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

