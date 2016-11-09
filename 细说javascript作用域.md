#细说javascript作用域

#####javascript作用域是一个老生常谈的问题，现在我就以最简单的方式去理解一下作用域这个概念。

#####在javascript里面没有块级作用域的区分，也不要把作用域的概念和上下文来混淆，javascript的作用域是由函数划分开的。

####先来看一个demo：

```javascript
var xisa = 'test';

// 在{}块里面
{
    // 这里没有块级的概念 所有xisa这个变量还是属于全局作用域！
    var xisa = 'new test';
}

// 输出为true
console.info( xisa === 'new test' );

// 创建新函数
function fn() {
    var xisa = "fn test";
}

// 直接在全局作用域执行 但是xisa只有在fn函数内部起作用
fn();

// 输出还是为true
console.info( xisa === 'new test' );

```
#####从上面的demo可以看出来，xisa这个变量只会在全局作用域起作用，fn函数里面重新声明一个xisa变量，这个变量只会在fn内部起作用，这就是作用域； 所有全局变量都是属于window对象的属性，比如直接打印 window.xisa，会直接输出'new test'，所以上面的demo展示了全局作用域和局部作用域。

#####在javascript里面如果不做变量声明，则此变量就会变成隐式全局作用域，如下：

```javascript
// 在一个fn方法里面写一个没有声明的xisa变量
function fn() {
    xisa = 'test';
}

// 直接调用
fn();

// 输出test
console.info( window.xisa )
```
#####这样的写法会污染全局变量，虽然javascript是一门不严谨的语言，但是如果这样的写法多了之后，就很不方便维护，所以尽量要先声明变量再去调用。

