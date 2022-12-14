# Socket

- 编写TCP时一般会用到（基本都会用到）以下的Socket模块：

- ```python
  connect(address):连接远程计算机
  send(bytes[,flags]):发送数据
  resv(bufsize[,flags]):接受数据
  bind(address):绑定地址
  listen(backlog):开始监听，等待客户连接
  accept():响应客户端的一个请求
  ```

- 注：进行TCP通信的流程是，先开启服务端等待监听——>客户端开始建立与服务器端的连接——>服务器端收到响应包再给客户端发送回应包——>客户端收到回应包继续响应进行循环——>循环到通信结束后关闭连接（释放资源，必须要做！）

```python
"""客户端"""
import socket, sys
host = "127.0.0.1"
port = 2222
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)  # 声明socket类型面向连接，套接字家族为AF_INET
try:
    s.connect((host, port))
except Exception as e:
    print("服务端不存在！")
    sys.exit()
while True:
    conn = input("you say：")
    s.sendall(conn.encode())  # 发送信息你叫什么名字？
    data = s.recv(2048)  # 接受数据并指定大小为2048字节
    data = data.decode()  # 解码接受的数据
    print("接受到的数据：", data)
    if conn.lower == "再见":  # 如果最后输入再见，表示会话结束！
        break
s.close()  # 会话关闭

"""服务端"""
import socket
language = {
    "who are you": "I am xiaofeng",
    "how old are you": "21",
    "where are you from": "china!",
}  # 设置字典language为后面对话所对应的服务端和客户端语句
host = "127.0.0.1"
port = 2222
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)  # 声明socket类型面向连接，套接字家族为AF_INET
s.bind((host, port))  # 绑定地址和端口
s.listen(3)  # 开始监听，表示可以使用3个链接排队
print("正在监听2222端口呢")
conn, addr = s.accept()  # 这串代码代表的意思是，等待响应客户端请求，接受连接，其实是返回两个值，一个是地址127.0.0.7，一个是随机监听的端口
print("连接的地址和端口：", addr)  # conn是客户端链接过来，在服务器端为期生成的一个链接实例(没啥用）
while True:
    data = conn.recv(2048)  # 接受数据为2048字节
    data = data.decode()  # 数据解码
    if not data:
        break
    print("接受到的数据：", data)  # 打印接受到数据
    conn.sendall(language.get(data, "Nothing").encode())  # 然后再发送数据为language字典里面的内容
conn.close()  # 连接关闭
s.close()  # 会话关闭
```

socket实例化()

```python
socket.scoket([family[,type[,proto]]])            protocol协议
参数
family:套接字家族可以使用AF_UNIX或者AF_INET(用的多,ip地址)
type：套接字类型，面向连接(TCP)SCOK_STREAM  非面向连接(UDP)SOCK_DGRAM
protocol：一般不填，默认为0

例子： 
s =socket.socket()
s = socket.socket(socket.AF_INET,socket.SOCK_STREAM)
```