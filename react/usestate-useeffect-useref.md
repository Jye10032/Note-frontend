# useState、useEffect、useRef

* State 做了哪些事情：
  * 1.接受一个初始值
  * 2.内部有一个函数去更新状态
  * 3.要有一个容器保存最新的值
* Ref 的改变不会引起当前组件的重新执行，自然视图也不会更新，这就是他与state的区别.
* useEffect 相当于遥控器，是用来去完成副作用操作的。

<pre><code>useEffect(()=>{

//我会在页面初始化完成执行一次
//页面每更新一次我就会执行一次
})

useEffect(()=>{

//我只会在页面初始化完成执行一次
//和componentDidMount vue中 mounted 相似
},[])

useEffect(()=>{

//我会在页面初始化完成执行一次
//当a和b的值发生变化我也会执行一次
**a,b的值必须是props或者state,否择我不会执行**
},[a,b])

<strong>useEffect(()=>{
</strong>
 return ()=>{
 //清理函数，见”生命周期“
 }
},[a,b])


</code></pre>
