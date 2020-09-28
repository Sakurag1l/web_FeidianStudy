# 执行上下文类型
 **可执行代码**
 * 全局代码
 * 函数代码
 * eval代码

# 执行上下文栈
创建执行上下文栈(Execution context stack)
```js
ECStack = [];
```
在执行代码的时候，最先就要执行全局代码，将全局执行上下文压入ECStack中
```js
ECStack = [
    globalContext
]
```
```js
function foo1(){
    console.log("foo1);
};
foo1();
function foo2(){
    console.log("foo2);
};
foo2();       //foo2
```
碰到要执行函数时，函数执行上下文压入ECStack中,
```js
// 执行函数foo1;
ECStack.push(<foo1> functionContext);

// 执行完成;
ECStack.pop();

// 执行函数foo2;
ECStack.push(<foo2> functionContext);

// 执行完成;
ECStack.pop();
```
# 创建执行上下文
每个执行上下文都有三个属性
* 变量对象(Variale Object)
* 作用域链(Scope Chain)
* this 

创建执行上下文有两个阶段:创建阶段、执行阶段

分析代码
```js
function foo(text){
    var scope = "scope";
    function f(){
        console.log(scope);
        console.log(text)
    }
}
foo(1);
```
1.首先执行全局代码;创建全局执行上下文,并且压入执行上文栈
```js
ECStack = [
    globalContext
];
```
2.全局上下文初始化，并且创建foo()函数
3.执行foo()函数,fooContext压入全局上下文栈中
```js
ECStack = [
    fooContext,
    globalContext
];
```
4.foo函数执行上下文初始化
```js
创建阶段
foo = {
    AO = {
        arguments: {
            length: 1,
        },
        text: 1,
        scope: undefined,
        f: reference to function c(){}
    }
}
执行阶段
foo = {
    AO = {
        arguments: {
            length: 1,
        },
        text: 1,
        scope: "scope",
        f: reference to function c(){}
    }
}
```
5.执行f函数，fContext函数压入执行上下文栈
....过程同上
>参考 MrPanda's blog / https://juejin.im/post/6844903479429824526