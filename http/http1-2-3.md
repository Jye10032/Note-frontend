# HTTP1/2/3

* HTTP1.1是一种基于文本的协议，而HTTP2和HTTP3是基于二进制的协议。HTTP1.1使用明文文本进行通信，而HTTP2和HTTP3使用二进制帧进行通信，这使得HTTP2和HTTP3可以更高效地传输数据。
* HTTP2引入了多路复用技术，允许在单个TCP连接上同时发送多个请求和响应，从而提高了性能。HTTP1.1只能在一个TCP连接上发送一个请求和响应。
* HTTP3使用QUIC协议，而HTTP1.1和HTTP2使用TCP协议。QUIC是基于UDP协议的，具有更好的性能和安全性。HTTP3还引入了0-RTT（零往返时间）握手，可以更快地建立连接。
* HTTP2和HTTP3都支持服务器推送，可以在客户端请求之前向客户端发送资源，从而提高性能。HTTP1.1不支持服务器推送。