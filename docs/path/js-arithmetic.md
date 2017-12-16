
# 算法



### 十大经典算法

牢牢记住

#### 冒泡排序

```js
function bubbleSort(arr) {
    var len = arr.length;
    for (var i = 0; i < len; i++) {
        for (var j = 0; j < len - 1 - i; j++) {
            if (arr[j] > arr[j+1]) {        //相邻元素两两对比
                var temp = arr[j+1];        //元素交换
                arr[j+1] = arr[j];
                arr[j] = temp;
            }
        }
    }
    return arr;
}
var arr=[3,44,38,5,47,15,36,26,27,2,46,4,19,50,48];
console.log(bubbleSort(arr));//[2, 3, 4, 5, 15, 19, 26, 27, 36, 38, 44, 46, 47, 48, 50]

```

用控制台的（注意单线程）

trace
console.trace()用来追踪函数的调用过程。

profile
使用console测试程序性能

time timeEnd
控制台计算程序的执行时间

概述
使用计时器可以对代码运行过程进行测速。你可以给每个计时器取一个名字，每个页面上最多可以运行一万个计时器。当你使用计时器名字调用 console.timeEnd() 函数时，浏览器会返回一个毫秒值，该值表示该计时器启动到你调用 console.timeEnd() 时的时间。
语法
console.time(timerName);
timerName
计时器名称，该名称用于标识一个计时器，当使用该名称调用 console.timeEnd() 时会停止相应的计时器，并在控制台输出计时时间。
如何捕获计时器返回值
很可惜，console.time() 和 console.timeEnd() 只能在控制台输出计时时间，但不能返回输出内容，也就不能赋给变量保存。
如果需要计时作为变量使用，可以使用 window.performance.now() 函数计时：
var start = window.performance.now();
var end = window.performance.now();
var duration = end - start;
window.performance.now() 返回一个浮点值表示当前距离页面被加载时的毫秒时间，如果想知道页面是何时被加载的，可以获取 window.performance.timing.navigationStart 值，该表示页面加载时的 Unix 时间戳。
你也可以使用 Date.now() 函数来计时，该函数返回一个整数毫秒值。
var start = Date.now();
var duration = Date.now() - start;
又或者 Date().getTime() 对象计时，该对象返回的是 Unix 时间戳：
var start = new Date().getTime();
var end = new Date().getTime();
var duration = end - start
PS：window.performance.now() 会比 Date.now() 慢很多。

```js
function f1() {
    console.time('time span');
}
function f2() {
    console.timeEnd('time span');
}
setTimeout(f1, 100);
setTimeout(f2, 200);

function waitForMs(n) {
    var now = Date.now();
        while (Date.now() - now < n) {
    }
}
waitForMs(500);//time span: 0ms
```


### 参考

十大经典算法总结(Javascript描述) 
http://www.cnblogs.com/jztan/p/5878630.html

前端常见算法的JS实现
https://segmentfault.com/a/1190000008593715

web计时机制——performance对象
http://www.cnblogs.com/xiaohuochai/archive/2017/03/09/6523397.html

初探 performance – 监控网页与程序性能
http://www.alloyteam.com/2015/09/explore-performance/

使用 W3C Performance 对象通过 R 和 JavaScript 将浏览器内的性能数据可视化
https://www.ibm.com/developerworks/cn/data/library/bd-r-javascript-w3c/



































