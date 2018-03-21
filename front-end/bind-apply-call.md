# Function.prototype 之 bind/call/apply
## call/apply
> fun.call(thisArg, arg1, arg2, ...)
> fun.apply(thisArg, [argsArray])

两者在功能上完全一样，只是在参数的处理上有一定区别：
  `call()`接受的参数需要分别用‘,’隔开，比较适合已知有几个参数且数量不多时使用；
  `apply()`接受的参数只需用数组传入即可

## bind

`bind()`方法会返回一个函数

原生实现`Function.prototype.bind()`

```javascript
if(!Function.prototype.bind) {
  Function.prototype.bind = function(oThis) {
    if(typeof oThis !== 'function') {
      return new TypeError('the argument should be a function');
    }
    let argumentsArr = Array.prototype.slice.call(arguments, 1),
        judgeFun = function() {},
        funToBind = this,
        funToReturn = function() {
          return funToBind.apply(this instanceof judgeFun ? this : oThis, argumentsArr.concat(Array.prototype.slice.call(arguments)));
        }
    return funToReturn;
  }
}
```

# this 与 call/apply/bind
- 用这三种方法时`this`要看第一个参数
- 当该参数是`undefined/null/不填`时，`this`会指向全局对象——`window`(严格模式时为`undefined`)
- 当参数为字符串/数值/布尔值，`this`会分别指向`String/Number/Boolean`
- 当参数为`this`时，会指向当前的对象
