---
title: 代码规范
---


### 项目命名

全部小写，以下划线分割
例：my_project_name


### 目录命名

参照项目命名规则。
有复数的时候要加s
例：scripts, styles, images


### JS文件命名

参照项目命名规则。
例：account_model.js

### CSS HTML文件命名

参照项目命名规则。
例：account_model.html, account_model.css

## 代码通用规范

1.一次缩进四个空格


### HTML风格规范

1. 标签全都用小写
2. 属性用双引号

### CSS风格规范

1.常规命名用中划线（小型）
例： page-bd

2.[BEM规范命名][1]（现在对这套命名规范还未彻底理解），用单下滑线或者双下划线，这里为了和css modules中不能用中划线统一(中大型)
例：person__body__head

3. 属性值'0'后面不要加单位
4. 用 border: 0; 代替 border: none;

```css
/* not good */
.element {
    color :red! important;
    background-color: rgba(0,0,0,.5);
}

/* good */
.element {
    color: red !important;
    background-color: rgba(0, 0, 0, .5);
}

/* not good */
.element ,
.dialog{
    ...
}

/* good */
.element,
.dialog {

}

/* not good */
.element>.dialog{
    ...
}

/* good */
.element > .dialog{
    ...
}

/* not good */
.element{
    ...
}

/* good */
.element {
    ...
}

```


## JS命名规范
-----

### 空格
```javascript
// not good
var a = {
    b :1
};

// good
var a = {
    b: 1
};

// not good
++ x;
y ++;
z = x?1:2;

// good
++x;
y++;
z = x ? 1 : 2;

// not good
var a = [ 1, 2 ];

// good
var a = [1, 2];

// not good
var a = ( 1+2 )*3;

// good
var a = (1 + 2) * 3;

// no space before '(', one space before '{', one space between function parameters
var doSomething = function(a, b, c) {
    // do something
};

// no space before '('
doSomething(item);

// not good
for(i=0;i<6;i++){
    x++;
}

// good
for (i = 0; i < 6; i++) {
    x++;
}

```

### 空行
以下几种情况需要空行：

> 变量声明后（当变量声明在代码块的最后一行时，则无需空行）
> 
> 注释前（当注释在代码块的第一行时，则无需空行）
> 
> 代码块后（在函数调用、数组、对象中则无需空行）
> 
> 文件最后保留一个空行

```javascript
// need blank line after variable declaration
var x = 1;

// not need blank line when variable declaration is last expression in the current block
if (x >= 1) {
    var y = x + 1;
}

var a = 2;

// need blank line before line comment
a++;

function b() {
    // not need blank line when comment is first line of block
    return a;
}

// need blank line after blocks
for (var i = 0; i < 2; i++) {
    if (true) {
        return false;
    }

    continue;
}

var obj = {
    foo: function() {
        return 1;
    },

    bar: function() {
        return 2;
    }
};

// not need blank line when in argument list, array, object
func(
    2,
    function() {
        a++;
    },
    3
);

var foo = [
    2,
    function() {
        a++;
    },
    3
];


var foo = {
    a: 2,
    b: function() {
        a++;
    },
    c: 3
};

```

### 单行注释

> 双斜线后，必须跟一个空格；
> 
> 缩进与下一行代码保持一致；
> 
> 可位于一个代码行的末尾，与代码间隔一个空格。

```javascript

if (condition) {
    // if you made it here, then all security checks passed
    allowed();
}

var zhangsan = 'zhangsan'; // one space after code

```

### 多行注释

最少三行, '*'后跟一个空格，具体参照右边的写法；

建议在以下情况下使用：

> 难于理解的代码段
> 
> 可能存在错误的代码段
> 
> 浏览器特殊的HACK代码
> 
> 业务逻辑强相关的代码


```javascript

/*
 * one space after '*'
 */
var x = 1;

```

### 变量命名

 - 标准变量采用驼峰式命名（除了对象的属性外，主要是考虑到cgi返回的数据）
 - 'ID'在变量名中全大写

 - 'URL'在变量名中全大写

- 'Android'在变量名中大写第一个字母

- 'iOS'在变量名中小写第一个，大写后两个字母

- 常量全大写，用下划线连接

- 构造函数，大写第一个字母

- jquery对象必须以'$'开头命名

```javascript
var thisIsMyName;

var goodID;

var reportURL;

var AndroidVersion;

var iOSVersion;

var MAX_COUNT = 10;

function Person(name) {
    this.name = name;
}

// not good
var body = $('body');

// good
var $body = $('body');

```

### 变量声明

一个函数作用域中所有的变量声明尽量提到函数首部，用一个var声明，不允许出现两个连续的var声明。

```javascript
function doSomethingWithItems(items) {
    // use one var
    var value = 10,
        result = value + 10,
        i,
        len;

    for (i = 0, len = items.length; i < len; i++) {
        result += 10;
    }
}

```

### 函数

- 用驼峰法命名，函数第一个单词最好是动词

- 一个函数别干太多事情，最好只干一个事情，函数太长可以拆分成小函数

- 函数参数别超过四个


```javascript

// not good
function do_Something() {
    
}

// good
function doSomething() {
    
}

```


参考：[Code Guide by @AlloyTeam][2]


  [1]: https://www.cnblogs.com/pied/p/4732426.html
  [2]: http://alloyteam.github.io/CodeGuide/