# Redis

Redis 也可以理解成一个 **Map**：key 是 String，value 是 Object。

Java 是基于内存的，Redis 也是基于内存的，内存速度快、读取很快，所以 **Redis 的核心是"快"**。

---

## 💡 为什么用 Redis：公共变量

假设有 A、B 两个模块需要通讯和存储，A 模块产生的数据需要被 B 模块访问，这时可以把数据存到**公共变量**上（也就是 Redis），B 就可以读取了。

- A 模块通过远程 **RPC 调用**，通过 HTTP 把数据存到 Redis 里；
- B 模块通过 HTTP 去 Redis 里面拿。

可以把 Redis 理解成一个 **Java 服务**，部署在服务器上。

---

## 🖥️ Redis 集群

Redis 集群其实就是为了**防崩**：把主节点的数据拷贝到子节点上，哪怕主节点崩了也不怕。拷贝也是通过 **HTTP 请求**完成的。

---

## 🔗 关联知识点
- [[Map集合]] - Redis 本质是 key-value 结构的 Map
- [[网络编程]] - 模块间通过 HTTP/RPC 通信
- [[进程与线程]] - Redis 作为独立服务部署