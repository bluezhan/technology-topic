
## 1、arguments+apply+call

#### arguments

`arguments` 是一个对应于传递给函数的参数的类数组对象。

接下来，我会去了解面试者对于 arguments的理解，我们会要求面试者定一个log函数。
```
    log('hello world'); 
```
函数类似实现一个简单的控制台输出，在控制台输出传入的字符串。一边面试者都会在定义的函数里直接写console.log，不过还是有更优秀的面试者会直接使用apply。
```
    function log(msg){  
      console.log(msg);
    }
```
接下来，我会继续问如果我传入多个参数依旧输出一个字符串 ，我会提示面试者传入的 参数是不固定的，我会暗示作者console.log实际上也接受多个参数。
```
    log('hello', 'world');  
```
不过我还是希望您的面试者现在已经想起apply;面试者可能会在apply和 call上困惑，这个时候我会做点小提示，不过将console上下文传入也是非常重要的.
```
    function log(){  
      console.log.apply(console, arguments);
    };
```
接着我会继续追问，如果我希望在那个输出的字符串前统一加上(app) 这样的字符串，类似于这样:
```
    '(app) hello world'  
```
这个问题明显会复杂很多，面试者应该知道arguments是一个伪数组，我们需要先将它转换成正常的数组，我们可以使用Array.prototype.slice,代码如下:
```
    function log(){  
      var args = Array.prototype.slice.call(arguments);
      args.unshift('(app)');

      console.log.apply(console, args);
    };
```

arguments对象不是一个 Array 。它类似于Array，但除了长度之外没有任何Array属性。例如，它没有 pop 方法。但是它可以被转换为一个真正的Array：
```
var args = Array.prototype.slice.call(arguments);
var args = [].slice.call(arguments);

// ES2015
const args = Array.from(arguments);
```


#### Array.prototype.slice.call






