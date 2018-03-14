# Network brigde trong KVM
## Tổng quan
Bridged network sử dụng để chia sẻ mạng của thiết bị thật tới các Vm (VMs). Mỗi VM được cung cấp địa chỉ có sẵn của router tại dải mạng thực cung cấp cho host. Bridged networking cho phép VMs kết nối với mạng bên ngoài thông qua card mạng vật lý máy chủ.

## Kiến trúc
![](../images/KVM-bridge-1.jpg)

## Các bước cơ bản để tạo bridge:
1. Cấu hình card mạng chia sẻ không có ip (ens33)
2. Tạo mới interface bridge (br0)
3. Có thể gán ip tĩnh cho card bridge nhưng không được gán cho card mạng vật lý gán tới bridge (Tùy chọn)

## Cấu hình
### Bước 1: Cấu hình card mạng thật tại KVM node
```
cd /etc/sysconfig/network-scripts
vi ifcfg-ens33
```
Nội dung
```
DEVICE=ens33
TYPE=Ethernet
ONBOOT=yes
BRIDGE=br0
BOOTPROTO=static
```
### Bước 2: Cấu hình card mạng brigde
```
cd /etc/sysconfig/network-scripts
vi ifcfg-br0
```
Nội dung
```
TYPE=Bridge
BOOTPROTO=none
IPADDR=192.168.2.133
GATEWAY=192.168.2.2
NETMASK=255.255.255.0
DNS1=192.168.2.2

NAME="br0"
DEVICE="br0"
ONBOOT="yes"
BRIGDE=br0

```
### Bước 3: Khởi động lại card mạng
```
service network restart
```

### Kiểm tra card bridge đã có
```
brctl show
```
![](../images/KVM-bridge-2.PNG)
