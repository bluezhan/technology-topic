
# 归纳JavaScript两道经典题目


##  第一道，坑爹的出题人

链接：https://segmentfault.com/q/1010000006179450

```js
function Foo()
{
    getName = function(){return 1;}
    return this;
}

Foo.getName=function(){return 2;}
Foo.prototype.getName=function(){return 3;}
var getName=function(){return 4;}
function getName(){return 5;}

//以下内容会输出什么？
console.log(Foo.getName())
console.log(getName());
console.log(Foo().getName());
console.log(getName());
console.log(new Foo.getName());
console.log(new Foo().getName());
console.log(new new Foo().getName());
```



##  第二道，坑爹的出题人

链接：https://segmentfault.com/q/1010000008430170

```js
function Foo() {
  getName = function () {
    alert(1);
  };
  return this;
}
Foo.getName = function () {
  alert(2);
};
Foo.prototype.getName = function () {
  alert(3);
};
var getName = function () {
  alert(4);
};
function getName() {
  alert(5);
}

Foo.getName();
getName();
Foo().getName();
getName();
new Foo.getName();
new Foo().getName();
new new Foo().getName();
```


##  第三道，坑爹的出题人

链接：https://segmentfault.com/a/1190000008888142

```js

var A = function() {
    this.name = 'apple';
}
A.prototype.getName = function() {
    return this.name;
}

// 补充代码

var B = A.extend({
    initialize: function() {
        this.superclass.initialize.call(this);
        this.total = 3;
    },
    say: function() {
        return '我有' + this.total + '个' + this.getName()
    }
});
var b = new B();
console.log(b.say()); //我有3个apple

```

分析

题目希望生成一个新的构造函数，B继承于A。（尽量不要更改A）
题目表达出希望有initialize方法实现构造函数继承，又需要原型继承。不难想到我们要用组合继承、寄生组合继承或者ES6继承。
如果所有的函数都可以使用extend方法生成一个新的构造函数，那方法的通用性会更强。
initialize的this指向显然要改成指向子类构造函数中的this。



