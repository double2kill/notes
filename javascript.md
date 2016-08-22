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