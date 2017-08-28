## 几道JavaScript经典题目

> JavaScript是一门很诡异的，也非常灵活，更是个奇葩的计算机语言。


##### 1.

```
    var a = {n:1}; 
    var b = a;  
    a.x = a = {n:2}; 
    console.log(a.x); 
    console.log(b.x); 
```
这道题看起来不算很简单，考察了几个点：类型引用、连续赋值；但必须要理解JavaScript引用类型的赋值原理。

会打印出：
`undefined`
`{n: 2}`

参考：http://www.cnblogs.com/vajoy/p/3703859.html
http://www.cnblogs.com/xxcanghai/p/4998076.html


##### 2.

```
    var a=1,b=2,c=3;
     (function(){
        var a=b=4;
     })();
     console.log(a);
     console.log(b);
```     

这道题考察点也有几个：闭包、连续赋值、作用域。

会打印出：
`1`
`4`

其中闭包里面的b没有用var声明，所以在闭包中b是全局变量。

##### 3.

```

    var a=100;
     function a(){
    　　console.log(a);
     }
     a(); // --> a is not a function(…)
    
```

这道题考察点：变量声明提升（Hoisting）。
上面变成了：

```
     function a(){
    　　console.log(a);
     }
     var a；
     a = 100;
     a(); // --> a is not a function(…)
```

javascript中一个名字(name)以四种方式进入作用域(scope)，其优先级顺序如下：
- 1、语言内置：所有的作用域中都有 this 和 arguments 关键字
- 2、形式参数：函数的参数在函数作用域中都是有效的
- 3、函数声明：形如function foo() {}
- 4、变量声明：形如var bar;

##### 4.

```
   function foo() {
        var x = 1;
        if (x) {
            var x = 2;
        }
        console.log(x);
    }
    foo();// 2
```

ES6之前并没有块级作用域的概念。

```
function foo() {
    var x = 1;
    if (x) {
        (function() {
            var x = 2;
        }());
    }
    console.log(x);
}
foo();// 1
```

作用域是以函数为边界的。



##### 5.

```
    var a = 10;
    function fn() {
       console.log(a)
       var a = 100;
       console.log(a)
    }
    fn();
    
```


##### 6.

```
     if (!("a" in window)) {
        var a = 1;
     }
     console.log(a);
```

打印：undefined


##### 7. this, 闭包，作用域

```
    var length = 10;
    function fn() {
      console.log(this.length);
    }
    var obj = {
      length: 5,
      method: function(fn) {
        fn();
        arguments[0]();
      }
    };
      
    obj.method(fn, 1);
```

打印：10  2

第一次输出10应该没有问题。我们知道取对象属于除了点操作符还可以用中括号，所以第二次执行时相当于arguments调用方法，this指向arguments，而这里传了两个参数，故输出arguments长度为2。
你这段代码，在第三行加一行console.log(this)就知道为什么了。
在执行arguments[0]的时候 this上下文已经变成arguments啦。



##### 8.给基本类型数据添加属性，不报错，但取值时是undefined

```
    var a = 10;
    a.pro = 10;
    console.log(a.pro + a);
      
    var s = 'hello';
    s.pro = 'world';
    console.log(s.pro + s);
```

打印：NaN undefinedhello

给基本类型数据加属性不报错，但是引用的话返回undefined，10+undefined返回NaN，而undefined和string相加时转变成了字符串。


##### 9.基本类型和复杂类型的引用

```
    function setName(obj){
        obj.name = "obama";
        obj = {name:"clinton"};
    }
    var president = {name:"bush"};
    setName(president);
    console.log(president.name)
```

打印：{name:"obama"}


var president = {name:"bush"};
president指向{name:"bush"}对象
setName(president);
将obj指向president指向的对象, 也就是{name:"bush"}
obj.name = "obama";
将obj指向的对象(也就是president指向的对象)的name属性值改为"obama"
obj = {name:"clinton"};
把obj的指向从{name:"obama"}对象改为了{name:"clinton"}对象
而president仍然指向{name:"obama"}对象

##### 10.

```
    x = 1;
    function bar() {
        this.x = 2;
        return x;
    }
    var foo = new bar();
    console.log(foo.x);
```
   打印出：2
   这里主要问题是最外面x的定义，试试把x=1改成x={}，结果会不同的。这是为什么呢？在把函数当作构造器使用的时候，如果手动返回了一个值，要看这个值是否简单类型，如果是，等同于不写返回，如果不是简单类型，得到的就是手动返回的值。如果，不手动写返回值，就会默认从原型创建一个对象用于返回。
   五种简单类型:null,undefined,boolean,String和Number；一种复杂类型：object。
   1、里面和外面总之得定义个返回值
   2、如果是简单类型，则是里面this的值
   3、如果定义返回值的不是简单类型，无论咋样都是 undefined;






### 考点

块级作用域（block scope）（函数式编程）
连续赋值与求值顺序、运算优先级、对象引用、对象拷贝
变量声明 函数声明 变量赋值
函数声明与函数表达式

把解析和赋值分开
把声明和赋值分开
var和function是会提前声明
JS中变量名和函数名重名

有 `var` 和没 `var` 的区别：不只是全局的区别，还有声明提升的区别。

变量声明不会覆盖的，赋值才会覆盖。

Javascript里有个神奇的东西叫Hoisting

声明部分会被提升，赋值部分不会被提升！
函数定义，或者叫我函数表达式。其实我就是变量定义，只不过恰好被赋值的类型是函数，所以也只提升变量名，不提升函数值！
函数声明，所以我全部被提升了，包括函数名和函数体


javascript中一个名字(name)以四种方式进入作用域(scope)，其优先级顺序如下：
- 1、语言内置：所有的作用域中都有 this 和 arguments 关键字
- 2、形式参数：函数的参数在函数作用域中都是有效的
- 3、函数声明：形如function foo() {}
- 4、变量声明：形如var bar;

参考
http://www.cnblogs.com/vajoy/p/3703859.html
http://www.cnblogs.com/xxcanghai/p/4998076.html


简单算法题：
http://ourjs.com/detail/52fb82e13bd19c4814000001
https://segmentfault.com/a/1190000003860689

去百度文库弄几道题来玩玩

https://github.com/xufei/blog/blob/master/posts/2013-12-02-%E4%B8%80%E4%BA%9BJS%E9%A2%98%E7%9B%AE%E7%9A%84%E8%A7%A3%E7%AD%94.md

5个典型的JavaScript面试题

https://segmentfault.com/a/1190000003860689
http://forums.fami2u.com/t/javascript-44/77/1
https://segmentfault.com/a/1190000007062464


训练数组API题目：
http://www.w2bc.com/Article/69447
http://www.cnblogs.com/wx1993/p/4827518.html


学习JavaScript网站：
http://www.codefordream.com/paths/javascript/courses
https://developer.mozilla.org/zh-CN/docs/Web/JavaScript

http://bonsaiden.github.io/JavaScript-Garden/zh/
http://www.liaoxuefeng.com/wiki/001434446689867b27157e896e74d51a89c25cc8b43bdb3000


####  参考

http://www.jianshu.com/p/e9cfaae7fe68
http://www.cnblogs.com/strick/p/4968200.html
http://www.jianshu.com/p/38f81f61e72c
http://www.cnblogs.com/Bond/p/4218639.html
http://www.tuicool.com/articles/ZfAvqe
http://www.cnblogs.com/fengfan/p/3993542.html
http://www.hidoger.com/show/index/cid/9/id/141.html
http://blog.jobbole.com/78738/
http://www.jianshu.com/p/c0b69c6c1486
http://blog.csdn.net/q121516340/article/details/51332454
http://www.jb51.net/article/75450.htm
http://www.cnblogs.com/hustskyking/p/javascript-attention.html

https://github.com/qiu-deqing/FE-interview
https://github.com/paddingme/Front-end-Web-Development-Interview-Question

http://www.infoq.com/cn/articles/talk-front-end-integrated-solution-part2/
https://segmentfault.com/q/1010000003028413

