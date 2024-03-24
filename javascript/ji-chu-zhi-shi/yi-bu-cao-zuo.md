# Promise

Promise为异步操作提供统一接口，使代码更加易读

```
// 传统写法
step1(function (value1) {
  step2(value1, function(value2) {
    step3(value2, function(value3) {
      step4(value3, function(value4) {
        // ...
      });
    });
  });
});

// Promise 的写法
(new Promise(step1))
  .then(step2)
  .then(step3)
  .then(step4);
```

### Promise 三种状态

promise对象通过自身的状态，来控制异步操作。Promise 实例具有三种状态。

* 异步操作未完成（pending）
* 异步操作成功（fulfilled）
* 异步操作失败（rejected）

上面三种状态里面，fulfilled和rejected合在一起称为resolved（已定型）。 pending-> fulfilled（成功：传回值（value））/rejected（失败，抛出错误（error）） 一旦状态发生变化，就不会再有新的状态变化。 Promise 实例的状态变化只可能发生一次。

```
var promise = new Promise(function (resolve, reject) {
  // ...

  if (/* 异步操作成功 */){
    resolve(value);
  } else { /* 异步操作失败 */
    reject(new Error());
  }
});
```

### then

then() 方法最多接受两个参数；第一个参数是 Promise 兑现时的回调函数，第二个参数是 Promise 拒绝时的回调函数。每个 `.then()` 返回一个新生成的 Promise 对象，这个对象可被用于链式调用。



```javascript
var p1 = new Promise(function (resolve, reject) {
  resolve('成功');
});
p1.then(console.log, console.error);
// "成功"

var p2 = new Promise(function (resolve, reject) {
  reject(new Error('失败'));
});
p2.then(console.log, console.error);
// Error: 失败

```

#### **链式调用**

一个 Promise 的终止条件决定了链中下一个 Promise 的“已敲定”状态。链中每个已兑现的 Promise 的返回值会传递给下一个 `.then()`，而已拒绝的 Promise 会把失败原因传递给链中下一个拒绝处理函数。

在每个 `.then()` 中处理被拒绝的 Promise 对于 Promise 链的下游有重要的影响。

* 错误必须立即被处理的情况下，必须抛出某种类型的错误以维护链中的错误状态。
* 在没有迫切需要的情况下，最好将错误处理留到最后一个 `.catch()` 语句。`.catch()` 其实就是一个没有为 Promise 兑现时的回调函数留出空位的 `.then()`。

```
myPromise
  .then((value) => `${value} and bar`)
  .then((value) => `${value} and bar again`)
  .then((value) => `${value} and again`)
  .then((value) => `${value} and again`)
  .then((value) => {
    console.log(value);
  })
  .catch((err) => {
    console.error(err);
  });

```

#### 结果的值

[`Promise.reject()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global\_Objects/Promise/reject)

返回一个新的 `Promise` 对象，该对象以给定的原因拒绝。

[`Promise.resolve()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global\_Objects/Promise/resolve)

返回一个新的 `Promise` 对象，该对象以给定的值兑现。

* 如果值是一个 thenable 对象（即具有 `then` 方法），则返回的 Promise 对象会“跟随”该 thenable 对象，采用其最终的状态；
* 否则，返回的 Promise 对象会以该值兑现。
* 通常，如果你不知道一个值是否是 Promise，那么最好使用 [`Promise.resolve(value)`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global\_Objects/Promise/resolve) 将其转换成 Promise 对象，并将返回值作为 Promise 来处理。

```
const promiseA = new Promise((resolve, reject) => {
  resolve(777);
});
// 此时，“promiseA”已经敲定了
promiseA.then((val) => console.log("异步日志记录有值：", val));
console.log("立即记录");

```

总结：.then会处理前一个 Promise的结果并且返回Promise，Promise 的结果会以 Promise 或者值的方式传给 .then。

{% embed url="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise" %}

