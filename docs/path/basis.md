# JavaScript收集的实现基础

#### LazyMan

https://juejin.im/entry/588037d38d6d810058af5d01


#### undersercore 源码分析

https://juejin.im/entry/58636fd1128fe10069eff4ec

https://www.gitbook.com/book/yoyoyohamapi/undersercore-analysis/details


https://github.com/hangyangws/article/blob/master/javascript.md


#### 使用 typeof bar === "object" 判断 bar 是不是一个对象有神马潜在的弊端？如何避免这种弊端？ 

使用 typeof 的弊端是显而易见的(这种弊端同使用 instanceof)：

```
    let obj = {};
    let arr = [];
     
    console.log(typeof obj === 'object'); //true
    console.log(typeof arr === 'object'); //true
    console.log(typeof null === 'object'); //true
```

从上面的输出结果可知，typeof bar === "object" 并不能准确判断 bar 就是一个 Object。可以通过 Object.prototype.toString.call(bar) === "[object Object]" 来避免这种弊端：

```
    let obj = {};
    let arr = [];
     
    console.log(Object.prototype.toString.call(obj)); //[object Object]
    console.log(Object.prototype.toString.call(arr)); //[object Array]
    console.log(Object.prototype.toString.call(null)); //[object Null]
```

另外，为了珍爱生命，请远离 ==：

```
if([]){alert(1)} // alert(1)
[] == false // true

```
而 [] === false 是返回 false 的

http://www.jb51.net/article/77140.htm
http://www.jb51.net/article/79461.htm
https://zhuanlan.zhihu.com/p/25855075
http://www.cnblogs.com/moqiutao/p/6591776.html

数组去重，打乱数组，统计数组各个元素出现的次数， 字符串各个字符的出现次数，获取地址链接的各个参数


https://segmentfault.com/a/1190000005994196

