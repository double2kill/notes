JavaScript
===

学习[廖雪峰教程](http://www.liaoxuefeng.com/wiki/001434446689867b27157e896e74d51a89c25cc8b43bdb3000)
笔记

> Brendan Eich在两周之内设计出了JavaScript语言。

> 几个公司联合ECMA（European Computer Manufacturers Association）组织定制了JavaScript语言的标准，被称为ECMAScript标准。

> JavaScript语言是在10天时间内设计出来的，虽然语言的设计者水平非常NB，但谁也架不住“时间紧，任务重”

字符串
---

多行字符串可以采用`` `...` ``表示
```
`#demo
first
second`;
```

方法
---

`map()`方法：

> ```
function pow(x) {
    return x * x;
}
var arr = [1, 2, 3, 4, 5, 6, 7, 8, 9];
arr.map(pow); // [1, 4, 9, 16, 25, 36, 49, 64, 81]
```

`reduce()` 超级厉害！！！

> ```
// [x1, x2, x3, x4, x5].reduce(f) = f(f(f(f(x1, x2), x3), x4), x5)
var arr = [1, 3, 5, 7, 9];
arr.reduce(function (x, y) {
    return x + y;
}); // 25
```

箭头函数：ES6的语法糖，（还有另一个效果见[廖雪峰官方网站-箭头函数](http://www.liaoxuefeng.com/wiki/001434446689867b27157e896e74d51a89c25cc8b43bdb3000/001438565969057627e5435793645b7acaee3b6869d1374000)）

generator函数：由`function*`定义，通过`yield`标记位置表示暂停，用`next()`方法执行下一步。

时间戳，用`parse(date)`来得到时间戳
> 时间戳是一个自增的整数，它表示从1970年1月1日零时整的GMT时区开始的那一刻，到现在的毫秒数。
```
var d = Date.parse('2015-06-24T19:49:22.875+08:00');
d; // 1435146562875
var d = new Date(1435146562875);
d; // Wed Jun 24 2015 19:49:22 GMT+0800 (CST)
```

正则
---

一直都不会，认真学一次。

1. `\d{3}`表示匹配3个数字，例如`'010'`；
* `\s`可以匹配一个空格（也包括Tab等空白符），所以`\s+`表示至少有一个空格，例如匹配`' '`，`'\t\t'`等；
* `[0-9a-zA-Z\_]`可以匹配一个数字、字母或者下划线；

总结：`^`表示行的开头，`$`表示行的结束。`\d`表示数字，`\s`表示空格或者tab符号。`{n}`表示n个，`*`任意个数，`+`表示至少一个，`?`表示0或1个，用`[]`可以详细匹配。

创建正则的方法有

1. `/.../` 
2. `new RegExp('...')`

`test()`方法可以检测是否满足条件。

面向对象
---

看了这么多，你是不是想用面向对象来进行编程呢？那么请看。

原型链的搜索方式。

```
对象：
arr ----> Array.prototype ----> Object.prototype ----> null
函数：
foo ----> Function.prototype ----> Object.prototype ----> null
```

`new 普通函数`可以变成`构造函数`。按照约定，构造函数首字母应当大写，而普通函数首字母应当小写，这样，一些语法检查工具如jslint将可以帮你检测到漏写的`new`

如果我们是一个容易健忘的人，可以创建一个`createStudent()`函数来用于防止漏掉的new，如果创建的对象有很多属性，我们只需要传递需要的某些属性，剩下的属性可以用默认值，这样无需记忆相关参数的顺序。请看！

```
function Student(props) {
    this.name = props.name || '匿名'; // 默认值为'匿名'
    this.grade = props.grade || 1; // 默认值为1
}

Student.prototype.hello = function () {
    alert('Hello, ' + this.name + '!');
};//如果大家的hello方法都一样，那就不必在Student里面创建，用prototype可以节约内存。因为每个实例出来的方法长得一样，但是实际是不一样的。用原型链的知识可以很容易理解这个方法可以节省内存。

function createStudent(props) {
    return new Student(props || {})
}//封装！！！
```

原型继承  这一节讲的很不错，虽然这是一个坑，但是考虑问题能够这么棒！也是很佩服，真心欣赏。

浏览器
---

`window`对象有`innerWidth`和`innerHeight`属性，可以获取浏览器窗口的内部宽度和高度。内部宽高是指除去菜单栏、工具栏、边框等占位元素后，用于显示网页的净宽高。

要加载一个新页面，可以调用`location.assign()`。如果要重新加载当前页面，调用`location.reload()`方法非常方便。

为了确保安全，服务器端在设置Cookie时，应该始终坚持使用`httpOnly`。禁用javascript读取cookie。

html5
---

`<input type="color" value="#ff0000">`可用于让用户选择颜色。

充分利用`<input type="hidden">`来传递数据。用这个可以处理加密信息。

```
<form id="test-form" onsubmit="return checkForm()">
    <input type="text" name="test">
    <button type="submit">Submit</button>
</form>
```
然后可以写checkForm()函数，来对表单进行一些处理。返回true则发送submit