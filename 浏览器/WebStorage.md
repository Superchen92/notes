##### WebStorage是HTML5引入的一个非常重要的功能，可以将数据存储在本地，类似于Cookie，但相比Cookie可以减少网络流量，因为WebStorage存储的数据不会发送给服务器，而Cookie存储的数据会由浏览器通过HTTP请求自动发送给服务器。数据响应快，性能好。

##### WebStorage 中包含两个关键的对象，分别是LocalStorage 和 SessionStorage对象。

1. LocalStorage对象用于本地存储，SessionStorage用于区域存储。
2. 两者的存储大小都是5M
3. 只能存储字符串，所以需要使用JSON.stringify()序列化后存入。
4. SessionStorage的数据只在用户浏览同源同窗口中有效。例如：当用户打开一个页面，只要这个刘拉你窗口没有关闭，即使刷新页面或进入同源另一个页面，数据仍然存在。只要关闭窗口，数据就会自动消失，同时独立打开的不同窗口，即使是同一页面，SessionStorage对象也是不同的

