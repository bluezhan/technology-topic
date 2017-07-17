
HTTP协议
hHTTP（超文本传输协议）

保持有序和完整
MIME类型

#### URI(Uniform Resource Indentifier)统一资源标识符
其实URI有两种形式，分别为URL(Uniform Resource Locators)统一资源定位符和URN(Uniform Resource Names)统一资源名称。

#### HTTP事务
一条HTTP事务是由一条由客户端发往服务器端的请求命令和一条由服务器端返还给客户端的响应结果组成。

HTTP方法(HTTP method):
- GET 从服务器向客户端发送命名资源
- PUT 将客户端录入的数据存储到一个命名的服务器资源中去
- DELET 从服务器删除命名资源
- POST 将客户端数据发送到一个服务器网关应用程序
- HEAD 仅发送命名资源响应中的HTTP首部

其实我感觉PUT和POST的本质上的区别在于是否具有幂等性。

#### 状态码

#### HTTP报文

#### 报文流

HTTP报文会像河水一样流动，不管是请求报文还是响应报文，有“上游”“下游”的说法，报文流只能从上游流向下游而不能逆过来。


#### 参考
上网找资料
http://www.jianshu.com/c/47c604fe47af

各种学习资源：
1、《图解HTTP》，上野宣（入门级）
2、《HTTP权威指南》， David Gourley/ Brian Totty （纵向进阶篇）
3、《TCP/IP协议详解》，Lawrence Berkeley（横向进阶篇）

http://www.cnblogs.com/hr2014/p/4992495.html