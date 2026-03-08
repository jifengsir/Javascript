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

