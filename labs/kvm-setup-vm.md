# Thiết lập máy ảo thông qua virt-manager
---
## Cấu hình
### Phần 1: Up images các OS dùng trong KVM
#### Bước 1: Up image OS về mấy cá nhân hoặc KVM node
> Sử dụng ftp up lên KVM node trong trường hợp bản cài OS đã có trong máy
#### Bước 2: Chuyển images tới thư mục
```
mv image_os.iso /var/lib/libvirt/images/
```
#### Bước 3: Thiết lập quyền truy cập image
```
chmod 777 /var/lib/libvirt/images/image_os
```
### Phần 2: Tạo mới máy ảo
#### Bước 1: Khởi động virt-manager
```
virt-manager
```
#### Bước 2: Chọn tạo mới VM
![](../images/install-kvm-2.png)
#### Bước 3: Cài từ images có sẵn
![](../images/install-kvm-3.png)
#### Bước 4: Chọn đĩa cài
![](../images/install-kvm-4.png)
#### Bước 5: Xác nhận loại đĩa
![](../images/install-kvm-5.png)
#### Bước 6: Cấu hình máy ảo
![](../images/install-kvm-6.png)
#### Bước 7: Chọn thiết lập boot
![](../images/install-kvm-7.png)
#### Bước 8: Kết quả
![](../images/install-kvm-8.png)

### Phần 3: Thiết lập thông số cho VM
> Các sửa đổi yêu cầu tắt máy ảo

#### Bước 1: Chọn VM cần sử đổi > Chọn Open
![](../images/setup-vm-1.png)
#### Bước 2: Chọn Show detail
![](../images/setup-vm-2.png)

> Tại đây ta có thể thêm sửa xóa các thành phần trong VM như CPU, RAM, HDD, NETWOK

#### Thêm card mạng mới
1. Chọn Add Hardware
2. Chọn Network
3. Chọn Network source cần
4. Chọn Finish

![](../images/setup-vm-3.png)
