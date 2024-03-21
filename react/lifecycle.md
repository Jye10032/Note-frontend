# 生命周期

#### 类组件

每个 React 组件（类组件）都经历相同的生命周期：

* 当组件被添加到屏幕上时，它会进行组件的 **挂载**。
* 当组件接收到新的 props 或 state 时，通常是作为对交互的响应，它会进行组件的 **更新**。
* 当组件从屏幕上移除时，它会进行组件的 **卸载**。

{% embed url="https://cloud.tencent.com/developer/article/2204517" %}

#### Effect

当从组件的角度思考时，很容易将 Effect 视为在特定时间点触发的“回调函数”或“生命周期事件”，例如“渲染后”或“卸载前”，这种思考方式会很复杂。与组件不同的是，Effect 只能做两件事：开始同步某些东西，然后停止同步它。

下面是一段创建聊天室的代码，useEffect 是一个回调函数

```javascript
// Some code
function ChatRoom({ roomId /* "general" */ }) {
  useEffect(() => {
    const connection = createConnection(serverUrl, roomId); // 连接到 "general" 聊天室
    connection.connect();
    return () => {
      connection.disconnect(); // 断开与 "general" 聊天室的连接
    };
    // ...
```

在 React 中，`useEffect` 的清理函数会在以下情况下执行：

1. 在组件卸载时：当组件从 DOM 中移除时，React 会自动调用清理函数。
2. 在下一次 `useEffect` 执行之前：如果依赖项数组发生变化，React 会先执行上一次 `useEffect` 返回的清理函数，然后再执行新的 `useEffect`。

**开始同步：**

每一次重新渲染时会更换开始同步的组件

**停止同步：**

当前组件卸载时停止同步这个组件
