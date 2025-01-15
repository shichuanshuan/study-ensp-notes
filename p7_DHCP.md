# DHCP
## 定义
动态主机配置协议，是一个应用在局域网中的协议，它使用 UDP 协议工作。

## 作用
动态分配 IP 地址，过程自动化，终端无需手工配置，配置信息统一管理。


## 命令格式
### 配置 global 模式
`[R2]dhcp enable`: 开启 DHCP 功能

`[R2]ip pool huawei1`:创建一个全局地址池，地址池名称为 huawei1

`[R3-ip-pool-huawei1]network 192.168.4.0 mask 255.255.255.0`:动态分配地址范围，如果不指定掩码，则默认使用自然掩码

`[R3-ip-pool-huawei1] ease day 2`:全局地址池下的地址租期

`[R3-ip-pool-huawei1]gateway-list 192.168.4.254`: 配置 DHCP 客户端的网关地址

`[R3-ip-pool-huawei1]excluded-ip-address 192.168.4.250 192.168.4.253`:从 DHCP 地址池中排除特定的 IP 地址范围.

`[R3-ip-pool-huawei1]dns-list 8.8.8.8`:设置 DHCP 服务器为客户端分配的 DNS 服务器地址。这样客户端不用配置 DNS 也能访问域名

`[R3-ip-pool-huawei1]interface GigabitEthernet 0/0/0`:

`[R3-GigabitEthernet0/0/0]ip address 192.168.1.1 24`: 配置网关

`[R3-GigabitEthernet0/0/0]dhcp select global`: Global 配置指的是路由器上整体的 DHCP 配置，适用于整个设备或特定的 DHCP 功能。这些配置通常定义了一些默认行为和策略，适用于所有接口或特定范围。

还有dhcp select int:是针对特定的网络接口（例如一个物理接口或子接口）上的 DHCP 配置。这种配置只影响该接口上的 DHCP 功能和行为。


### 配置 interface 模式
`dhcp enable`: 开启 dhcp 模式

`int g0/0/0`：进入路由器网口

`ip address 192.168.2.254 24`：配置网关

`dhcp select interface`: 设置端口模式