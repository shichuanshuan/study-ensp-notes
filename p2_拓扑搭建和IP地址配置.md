# 交换机的特性
交换机是数据链路层的，三层交换机是网络层设备。

交换机所有端口都在同一个广播域的，而每一个端口就是一个冲突域。

# 路由器
Route 的每个端口属于不同的广播域

# 添加 IP 命令
## 路由器
进入系统视图

进入接口：int g0/0/0

配置IP：ip address 192.168.1.254 24

## 三层交换机
需要通过 vlan 来封装。

进入系统视图

创建vlan: vlan 10

进入vlan接口：int vlan 10

配置IP：ip address 192.168.2.254 24 `此时网络是不通的，因为还没有把地址加入到相应的接口上`

进入链接网线的接口：int g0/0/1

加入到接口：port link-type access

设置默认网口: port default vlan 10

# 删除 IP
进入系统视图 

进入接口: int g0/0/0 `g0/0/0:代表千兆，e0/0/0代表百兆`

删除IP：undo ip address 192.168.1.254 24

![alt text](pngs/p2_ip.png)



ip & 网关
![alt text](pngs/p3_gw.png)