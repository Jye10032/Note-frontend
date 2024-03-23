# 数据存储

**Cookie、Session和LocalStorage**

Cookie、Session和LocalStorage都是在Web开发中用于存储和管理数据的机制。

1. 存储位置：
   * Cookie：存储在浏览器的Cookie文件中，每次发送 Http 请求都会携带Cookie信息。
   * Session：存储在服务器端，通常使用Session ID 在客户端和服务器之间进行交互，而 Session ID 通常被存储在 Cookie 中 ，由客户端通过无状态的 Http 发送请求，得到存储的会话状态。
   * LocalStorage：存储在浏览器的本地，仅在客户端使用，不会向服务器发送信息。
2. 存储容量：
   * Cookie：每个Cookie的存储容量通常限制在几KB，不同浏览器有不同的限制。
   * Session：在服务器端存储，没有明确的大小限制，但会占用服务器的内存和资源。
   * LocalStorage：通常限制在几MB，不同浏览器有不同的限制。
3. 生命周期：
   * Cookie：可以设置过期时间，可以是会话级的（关闭浏览器后失效）或长期的（设置了过期时间）。
   * Session：通常在用户会话期间（登录状态）有效，超过一定时间或用户注销后失效。
   * LocalStorage：长期有效，除非显式清除或通过代码删除。

***

**session的id是从哪里来的，sessionID是如何使用的：**

当客户端第一次请求session对象时候，服务器会为客户端创建一个session，并将通过特殊算法算出一个session的ID，用来标识该session对象，当浏览器下次（session继续有效时）请求别的资源的时候，浏览器会偷偷地将sessionID放置到请求头中，服务器接收到请求后就得到该请求的sessionID，服务器找到该id的session返还给请求者（Servlet）使用。一个会话只能有一个session对象，对session来说是只认id不认人。

***

**LocalStorage和SessionStorage 的区别**

LocalStorage：

* 生命周期：数据会一直保留在客户端，除非通过代码或用户手动删除。
* 作用域：数据在同一域名下的所有页面和标签页之间共享。

SessionStorage：

* 生命周期：数据仅在当前会话（即打开的浏览器窗口或标签页）有效，当会话结束时数据会被清除。
* 作用域：数据仅在同一标签页或窗口中有效，不会与其他标签页或窗口共享。

***

* cookie 和 localstorage 保存在客户端，session 保存在服务器端
* cookie 目的可以跟踪会话，也可以保存用户喜好或者保存用户名密码

***

* [https://www.cnblogs.com/ityouknow/p/10856177.html](https://www.cnblogs.com/ityouknow/p/10856177.html)
* [https://www.zhihu.com/question/19786827](https://www.zhihu.com/question/19786827)
