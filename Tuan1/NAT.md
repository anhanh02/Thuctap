### 5. Công nghệ NAT
**5.1: Công nghệ NAT**
- *NAT (Network Address Translation)* là một kỹ thuật cho phép một hoặc nhiều địa chỉ IP nội miền chuyển đổi sang một hoặc nhiều địa chỉ IP ngoại miền
- NAT giúp địa chỉ mạng cục bộ (Private) truy cập được đến mạng công cộng (Internet). Vị trí thực hiện kỹ thuật NAT là router biên, nơi kết nối 2 loại mạng này
- Chức năng của NAT
  - NAT truyền gói tin từ lớp mạng này sang lớp mạng khác trong cùng một hệ thống. NAT sẽ thực hiện thay đổi địa chỉ IP bên trong gói tin. Sau đó chuyển qua router và các thiết bị mạng
  - Khi gói tin được truyền từ mạng Internet quay trở lại NAT, NAT sẽ thực hiện nhiệm vụ thay đổi địa chỉ đích đến thành địa chỉ IP bên trong hệ thống mạng cục bộ và chuyển đi
  - NAT có thể là tường lửa, giúp người dùng bảo mật được thông tin IP máy tính. Nếu máy tính gặp sự cố khi đang kết nối Internet thì địa chỉ IP public đã cấu hình trước đó sẽ được hiển thị thay thế cho IP mạng cục bộ 
- Ưu, nhược điểm của NAT
  - Ưu điểm
    - Tiết kiệm địa chỉ IPv4
    - Giúp che giấu IP bên trong mạng LAN
    - NAT có thể chia sẻ kết nối internet cho nhiều máy tính, thiết bị di động khác nhau trong mạng LAN chỉ với một địa chỉ IP public duy nhất
    - NAT giúp nhà quản trị mạng lọc được các gói tin đến và xét duyệt quyền truy cập của IP public đến 1 port bất kỳ
  - Nhược điểm
    - Khi dùng kỹ thuật NAT, CPU sẽ phải kiểm tra và tốn thời gian để thay đổi địa chỉ IP. Điều này làm tăng độ trễ trong quá trình switching. Làm ảnh hưởng đến tốc độ đường truyền của mạng Internet
    - Kỹ thuật viên gặp khó khi cần kiểm tra nguồn gốc IP hoặc truy tìm dấu vết của gói tin do NAT có khả năng che giấu địa chỉ IP trong mạng LAN
    - NAT giấu địa chỉ IP nên khiến cho 1 vài ứng dụng cần sử dụng IP không thể hoạt động được
- Địa chỉ Private và Địa chỉ Public được sử dụng để xác định duy nhất một máy trên Internet

| Địa chỉ Private  | Địa chỉ Public  |
|---|---|
| Được sử dụng trong nội bộ  | Được sử dụng toàn cầu  |
| Sử dụng để giao tiếp trong mạng  | Sử dụng để giao tiếp bên ngoài mạng  |
| Được chỉ định cho thiết bị cụ thể trong 1 private network  | Được chỉ định và kiểm soát bởi nhà cung cấp dịch vụ internet  |
| Có sẵn và miễn phí  | Không miễn phí  |
| Được bảo mật  | Không có bảo mật và dễ bị tấn công  |
| Yêu cầu NAT để giao tiếp với các thiết bị  | Không yêu cầu NAT  |
| Có thể được sử dụng lại bởi các thiết bị khác trong Private Network  | Không thể lặp bởi các thiết bị khác  |

**5.2: Các kỹ thuật NAT**
- NAT one-to-one
  - Thực hiện NAT một địa chỉ bên trong thành 1 địa chỉ bên ngoài
  - Có 2 loại:
    - `Static NAT` 
      - Phải cấu hình chỉ rõ IP Private nào được liên kết với IP Public nào. Các cặp địa chỉ được liên kết với nhau sẽ được lưu lại trong *Static NAT*
      - Được sử dụng để chuyển đổi từ địa chỉ IP này sang địa chỉ IP khác một cách cố định (thường là từ một địa chỉ Private sang Public)
      - Cấu hình *Static NAT*:
        - Thiết lập liên kết giữa địa chỉ Private và Public
        > Router (config) # ip nat inside source static [local ip] [global ip]
        - Xác định cổng kết nối với mạng nội bộ
        > Router (config-if) # ip nat inside
        - Xác định cổng kết nối với mạng bên ngoài
        > Router (config-if) # ip nat outside
    - `Dynamic NAT`
      - Dùng để ánh xạ một địa chỉ IP này sang một địa chỉ IP khác 1 cách tự động (thông thường sẽ chuyển từ IP Private sang IP được đăng ký hợp lệ)
      - Cấu hình *Dynamic NAT*:
        - Xác định địa chỉ IP mạng bên ngoài
        > Router (config) # ip nat pool [name start ip] [name end ip] netmask [netmask]/prefix-lenght [prefix-lenght]
        - Thiết lập ACL tạo danh sách các địa chỉ Private được phép chuyển đổi IP
        > Router (config) # access-list [access-list-number-permit] source [source-wildcard]
        - Thiết lập mối quan hệ giữa địa chỉ nguồn và địa chỉ IP hợp lệ bên ngoài
        > Router (config) # ip nat inside source list <acl-number> pool <name>
        - Xác định cổng kết nối với mạng nội bộ
        > Router (config-if) # ip nat inside
        - Xác định cổng kết nối với mạng bên ngoài:
        > Router (config-if) # ip nat outside
- NAT many-to-one 
  - Còn gọi là `NAT Overload` hay `PAT (Port Address Translation)`
  - Cho phép NAT cùng lúc nhiều địa chỉ Private bên trong thành 1 địa chỉ Public bên ngoài
  - Cấu hình *NAT Overload*
    - Xác định các địa chỉ IP mạng nội bộ cần ánh xạ ra ngoài
    > Router (config) # access-list <ACL-number> permit <source> <wildcard>
    - Cấu hình để chuyển địa chỉ IP đến cổng kết nối với mạng bên ngoài:
    > Router (config) # ip nat inside source list <ACL-number> interface <interface> overload
    - Xác định cổng kết nối với mạng nội bộ
    > Router (config-if) # ip nat inside
    - Xác định cổng kết nối với mạng bên ngoài:
    > Router (config-if) # ip nat outside