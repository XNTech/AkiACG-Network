# 静态ip
这一部分可以说是基础中的基础。

---

可能现在的孩子们已经习惯插根网线，或者连个WiFi就能直接获取IP地址的日子了。

当然，机房里的设备可不能乱设IP。

**那咋办捏？**
---
在三层交换机与路由器中，我们可以给每个端口分配静态的IP。
命令如下：

<details>
<summary>思科（Cisco）</summary>
给物理接口配 IP（常用于路由器）：
  
```
enable
configure terminal
interface gigabitethernet 0/0
ip address 192.168.1.1 255.255.255.0
no shutdown
exit
```

给三层交换机的 VLAN 接口（SVI）配 IP：

```
interface vlan (你的VLAN号)
ip address 192.168.10.1 255.255.255.0
no shutdown
exit
配完别忘了保存：
end
wr
```

</details>

<details>
<summary>华为&华三</summary>
物理接口：

```
system-view
interface gigabitethernet 0/0/0
ip address 192.168.1.1 24
quit
```

VLANIF 接口：

```
interface vlanif (你的VLAN号)
ip address 192.168.10.1 24
quit
```

保存：

```
save
```
</details>

---

当你设置好这些，你就可以按照你的IP范围、子网掩码与网关地址在对应的客户机上设置静态IP。本文不再赘述。
