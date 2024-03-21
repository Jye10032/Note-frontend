# 函数组件和类组件

### 编写形式

#### 类组件

类组件是通过 ES6 类的编写形式去编写组件，该类必须继承 React.Component

如果想要访问父组件传递过来的参数，可通过 this.props的方式去访问

在组件中必须实现 render 方法，在 return 中返回 React 对象，如下：

```javascript
class Welcome extends React.Component {
  constructor(props) {
    super(props)
  }
  render() {
    return <h1>Hello, {this.props.name}</h1>
  }
}

```

#### 函数组件

函数组件，顾名思义，就是通过函数编写的形式去实现一个 React 组件，是 React 中定义组件最简单的方式

```javascript
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```

函数第一个参数为props用于接收父组件传递过来的参数

### 区别

* 函数式组件捕获了渲染时所使用的值，而类组件的 this 是实时调用的，在每次调用时都会更新成最新的 this ，因此在数据更改后得到的值可能并不是原来的值，函数组件能够将数据与渲染绑定在一起，这是两类组件最大的不同。
* 类组件有生命周期，函数组件没有
* 类组件需要继承 Class，函数组件不需要
* 类组件可以获取实例化的 this，并且基于 this 做各种操作，函数组件不行
* 类组件内部可以定义并维护 state， 函数组件都称为无状态了，那肯定不行。
* 函数组件相比较类组件，优点是更轻量与灵活，便于逻辑的拆分复用。



***

[React类组件和函数组件的本质区别](https://github.com/jappp/Blog/issues/12#top)



