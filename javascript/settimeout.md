# 定时器

* setInterval函数的用法与setTimeout完全一致，区别仅仅在于setInterval指定某个任务每隔一段时间就执行一次，也就是无限次的定时执行。
* setTimeout和setInterval函数，都返回一个整数值，表示计数器编号。将该整数传入clearTimeout和clearInterval函数，就可以取消对应的定时器。

### 防抖动（debounce）

只执行最后一次操作 设置一个门槛值，表示两次 Ajax 通信的最小间隔时间。如果在间隔时间内，发生新的keydown事件，则不触发 Ajax 通信，并且重新开始计时。如果过了指定时间，没有发生新的keydown事件，再将数据发送出去。 这种做法叫做 debounce（防抖动）。假定两次 Ajax 通信的间隔不得小于2500毫秒，上面的代码可以改写成下面这样。

```javascript
$('textarea').on('keydown', debounce(ajaxAction, 2500));

function debounce(fn, delay){
  var timer = null; // 声明计时器
  return function() {
    var context = this;
    var args = arguments;
    clearTimeout(timer);//清空timer计时器
    timer = setTimeout(function () {
      fn.apply(context, args);
    }, delay);
  };
}
```

### 节流

只执行第一次操作 在节流函数中，我们同样使用了闭包来保存定时器变量 timer 和传入的函数 func。每次触发事件时，如果定时器不存在，就设置一个定时器，并在 delay 时间后执行传入的函数 func。如果在 delay 时间内再次触发事件，由于定时器还存在，就不会执行传入的函数 func。只有在 delay 时间后定时器到达时间后执行传入的函数 func 并且将 timer 设置为 null 之后，再次触发事件才会执行。

```javascript
function throttle(func, delay) {
  let timer = null;
  return function(...args) {
    if (!timer) {
      timer = setTimeout(() => {
        func.apply(this, args);
        timer = null;
      }, delay);
    }
  };
}

// 使用节流优化滚动事件
window.addEventListener('scroll', throttle(function() {
  console.log('scrolling...');
  // 计算滚动距离
}, 500));
```
