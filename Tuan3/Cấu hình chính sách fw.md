## Cấu hình chính sách fw:RDP, SMB, FTP, HTTP, DNS,SSH, HTTPS, HCP, NTP
### 1. Cấu hình FW
- Sơ đồ: 

  ![alt](image/sodo.png)

- Cấu hình trên FW
  - Cắm dây console trên FW và đặt địa chỉ cho cổng mgt
  
  ![alt](image/mgt.png)

  ![alt](image/mgt1.jpg)

  ![alt](image/mgt2.jpg)

  - Đổi địa chỉ IPv4
  
  ![alt](image/ipv4.jpg)

  - Truy cập vào quản lý FW
  > https://192.168.10.5

  ![alt](image/fw1.jpg)

  - Tạo sub-interface trên FW
  
  ![alt](image/si.jpg)

  ![alt](image/si1.jpg)

- Tắt kết nối Wifi và tắt firewall trên cả 2 máy pc và thực hiện ping để kiểm tra xem 2 pc đã thông với nhau chưa
  
  ![alt](image/ping.jpg)

### 2. Cấu hình chính sách fw: RDP
- Mục đích: Kiểm thử tính năng kiểm soát RDP truy cập trên hillstone firewall cho các thiết bị trong hệ thống

- Kịch bản:
  - Bật chế độ RDP trên 2 pc
  - Tạo policy trên Firewall thực hiện block service RDP từ PC 192.168.16.15 truy cập RDP đến PC 192.168.15.20
- Các bước thực hiện :
  - B1: Tạo policy any any
  
    ![alt](image/any-any.png)

  - B2: Kiểm tra kết nối RDP từ PC 192.168.16.15 truy cập RDP đến PC 192.168.15.20
    - PC 192.168.16.15 có thể truy cập RDP đến PC 192.168.15.20

    ![alt](image/rdp1.png)

    ![alt](image/rdp2.png)

  - B3: Tạo policy deny RDP từ PC 192.168.16.15 truy cập RDP đến PC 192.168.15.20
  
    ![alt](image/rdp3.png)

    ![alt](image/rdp4.png)

    - Policy sẽ thực hiện lần lượt từ trên xuống nên cần đẩy policy deny RDP lên Top
  
    ![alt](image/rdp5.png)

  - B4: Kiểm tra kết nối RDP sau khi cấu hình policy từ PC 192.168.16.15 truy cập RDP đến PC 192.168.15.20
    - Truy cập RDP từ PC 192.168.16.15 truy cập RDP đến PC 192.168.15.20 đã bị chặn
  
    ![alt](image/rdp6.png)



### 3. Cấu hình chính sách fw: SMB
- Kịch bản :
  - Tạo policy trên Firewall thực hiện block service SMB từ PC 192.168.12.15 đến PC 192.168.13.15
- - Các bước thực hiện :
  - B1: Tạo policy any any
  
    ![alt](image/any-any.png)

  - B2: Kiểm tra kết nối 
   ctrl + r --> \\\192.168.13.15
    
    ![alt](image/smb_rdp1.png)

    ![alt](image/smb_any.png)

  - B3: Tạo policy deny SMB 
  
    ![alt](image/smb_deny.png)

  - B4: Kiểm tra kết nối SMB sau khi cấu hình policy từ PC 192.168.12.15 truy cập đến PC 192.168.13.50. 
    - Truy cập SMB từ PC 192.168.12.15 truy cập đến PC 192.168.13.50 đã bị chặn, không thể kết nối \\\192.168.12.15

### 4. Cấu hình chính sách fw: FTP
### 5. Cấu hình chính sách fw: HTTP, HTTPS
- Kịch bản :
  - Tạo policy trên Firewall thực hiện block service HTTP từ PC 192.168.12.15 truy cập đến PC 192.168.13.50
- Các bước thực hiện :
  - Tạo policy any any
  
    ![alt](image/any-any.png)

  - Kiểm tra kết nối HTTP, HTTPS 
  
    ![alt](image/http.png)

  - Tạo policy deny HTTP, HTTPS 
  
    ![alt](image/http1.png)

  - Kiểm tra kết nối HTTP, HTTPS sau khi cấu hình policy 
  
    ![alt](image/http3.png)

### 6. Cấu hình chính sách fw: DNS
### 7. Cấu hình chính sách fw: SSH
### 8. Cấu hình chính sách fw: DHCP
### 9. Cấu hình chính sách fw: NTP
