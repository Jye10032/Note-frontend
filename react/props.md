# Props

`props`（属性）是一种用于向组件传递数据的机制。

```javascript
// 父组件向子组件传递props的例子

// 父组件
function ParentComponent() {
  const name = "John";
  const age = 30;

  return <ChildComponent name={name} age={age} />;
}

// 子组件
function ChildComponent(props) {
  return (
    <div>
      <h2>Name: {props.name}</h2>
      <h2>Age: {props.age}</h2>
    </div>
  );
}
```

`ParentComponent` 通过设置 `name` 和 `age` 属性将数据传递给 `ChildComponent`。在 `ChildComponent` 中，我们可以通过 `props.name` 和 `props.age` 来访问传递的属性值。
