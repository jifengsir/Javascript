# javascript基础

> 登录、注册的行为；网页特效（web api）
>
> 基本写法，知道怎么控制计算机去执行代码

js是一种运行在客户端的编程语言

## Javascript书写位置

- 行内Javascript
- 内部Javascript
- 外部Javascript

### 内部js

直接写在html标签里面，用script标签包住。规范：script标签写在</body>上面

```javascript
alert('你好，Javascript')； //页面弹出警告对话框
```

### 外部js

代码写在以.js结尾的文件里 语法：通过script标签，引入到html页面中。

引入外部js后，script标签内不要再写其他代码，否则会被忽略。

```javascript
<body>
  <script src="my.js"></script>
</body>
```

### 行内js（作为了解即可）

代码直接写在标签内部。 语法：直接在标签内部写js代码。

```javascript
<body>
  <button onclick="alert('逗你玩~~~')">点击我月薪过万</button>
</body>
```

## js注释

### 单行注释

符号：//

作用：//右边这一行代码会被忽略

快捷键：ctrl+/

### 块注释（多行注释）

符号：/* */

作用：在/*和*/之间的所有内容都会被忽略

快捷键：shift+alt+a

### 结束符

作用：使用英文的**;**代表语句结束

实际情况：在开发过程中可写可不写。为了风格统一，可以不加结束符

## js输入输出语句（重点）

### 输出语句

语句1：

```javascript
alert('页面警示框输出的内容')
```

作用：页面弹出警告框

语句2：在body标签内输出内容

```javascript
document.write('向页面文档输出内容')
```

提示：如果输出的内容写标签，也会被解析成网页元素

语句3：

作用：控制台输出语法，程序员调试使用

```javascript
console.log('控制台输出内容')
```

### 输入语句

语法：

```javascript
prompt('请输入姓名')
```

