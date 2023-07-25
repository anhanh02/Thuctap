### 4. Công nghệ Ethernet, PPPoE
**4.1: Ethernet**
- Ethernet là công nghệ để kết nối các thiết bị trong mạng cục bộ có dây (LAN) hoặc mạng diện rộng (WAN). Nó cho phép các thiết bị giao tiếp với nhau thông qua một giao thức. Giao thức này là một tập hợp các quy tắc hoặc ngôn ngữ mạng chung
- Ethernet thường ít bị gián đoạn. Nó cũng có thể cung cấp mức độ kiểm soát và bảo mật mạng cao hơn so với công nghệ không dây vì các thiết bị phải được kết nối vật lý bằng hệ thống cáp. Điều này khiến cho người ngoài khó truy cập dữ liệu mạng hoặc chiếm đoạt băng thông cho cá thiết bị không hoạt động
- Cách thức hoạt động:
  - Giao thức Ethernet sử dụng Physical Layer và Datalink Layer trên mô hình OSI.
  - Ethernet xác định 2 đơn vị truyền: packet và framework. Framework không chỉ có nội dung của dữ liệu được truyền mà còn bao gồm:
    - Địa chỉ truy cập vật lý (MAC) của người gửi và người nhận
    - Gắn thẻ Vlan và thông tin liên quan khác
    - Thông tin sửa lỗi để phát hiện sự cố
  - Mỗi frame sẽ nằm trong một gói chứa một vài byte thông tin để thiết lập kết nối và đánh dấu vị trí framework bắt đầu
- Ưu, nhược điểm của Ethernet
  - Ưu điểm:
    - Chi phí tương đối thấp
    - Khả năng tương thích ngược
    - Chất lượng truyền dữ liệu tốt
    - Tốc độ truyền dữ liệu cao
    - Đáng tin cậy và bảo mật dữ liệu vì có thể sử dụng tường lửa thông thường
  - Nhược điểm:
    - Chỉ dành cho các mạng nhỏ với khoảng cách ngắn
    - Khó di chuyển
    - Sử dụng cáp dài hơn có thể tạo ra nhiễu xuyên âm
    - Khó khăn trong việc bảo trì và khắc phục sự cố
    - Tốn kém chi phí lắp đặt với các doanh nghiệp lớn vì hệ thống lúc này sẽ cần modern, tường lửa, máy chủ, switch chuyển mạch và các thiết bị nâng cao khác

**4.2: PPPoE**
- *PPPoE (Point-to-Point Protocol over Ethernet)* là giao thức được thiết kế để quản lý cách truyền dữ liệu qua mạng Ethernet(mạng cáp) và cho phép kết nối một máy chủ duy nhất được phân chia giữa nhiều máy khách, sử dụng Ethernet
- PPPoE cũng có thể cung cấp các tính năng mạng cần thiết như xác thực, mã hóa và nén dữ liệu 
- PPPoE chủ yếu được sử dụng bởi những nhà cung cấp dịch vụ Internet để cung cấp kết nối cho các thuê bao
- Quy trình làm việc của PPPoE bao gồm hai giai đoạn chính:
  - Giai đoạn Discovery (Khám phá) - Trong giai đoạn này, PPPoE client xác định địa chỉ MAC Ethernet cục bộ và thiết lập ID phiên. Và các host định vị nhiều PPPoE server, sau đó cho phép người dùng chọn một máy chủ.
  - Giai đoạn Session (Phiên) - Khi giai đoạn khám phá hoàn tất thành công, cả host và server được chọn đều có thông tin về kết nối PPP qua Ethernet. Sau đó, PPPoE cho phép dữ liệu được truyền qua liên kết PPP trong các PPPoE header. Do đó, một phiên được thiết lập giữa một người dùng cá nhân và trang web từ xa, có thể được giám sát. Trong khi đó, việc thanh toán của người dùng do PPPoE lập và ghi lại.
- Sự khác biệt giữa PPPoE và DHCP có thể được tóm tắt như sau:
  - PPPoE cần được cấu hình chính xác trước khi người dùng thực sự có thể kết nối Internet, tuy nhiên, DHCP không cần phải được cấu hình và về cơ bản là kiểu “plug and play”. Vì vậy, việc sử dụng DHCP để kết nối với ISP sẽ loại bỏ các vấn đề liên quan đến PPPoE. Cũng giống như các máy tính trong mạng, bạn không cần phải cấu hình máy tính của mình trước. Bạn chỉ cần để mọi thứ tự động và cấu hình cho các máy chủ ISP.
  - DHCP không cần xác thực và bạn sẽ không biết IP khi bật mạng. Những gì bạn sẽ làm là đợi máy chủ DHCP gán một IP ngẫu nhiên cho bạn từ tất cả các địa chỉ IP Internet. Ngược lại, PPPOE cần xác thực trước. Chỉ khi mật khẩu tài khoản của bạn chính xác, nó mới gán một IP hợp lệ cho bạn.
  - Vì PPPoE cho phép một số lượng lớn host tạo thành một đơn vị mạng và kiểm soát, lập bill cho mỗi host, nên nó được sử dụng rộng rãi trong cộng đồng, tòa nhà và khuôn viên. Và cách truy cập băng thông rộng ADSL thịnh hành đã áp dụng giao thức PPPoE. Đối với DHCP, nó thường được sử dụng để chỉ định động địa chỉ IP cho mạng LAN của công ty hoặc Internet.
- Ưu điểm PPPoE
  - Tốc độ nhanh và ổn định: Ngay sau khi đã nhận được tín hiệu thông báo, hệ thống thuật toán của giao thức PPPoE sẽ ngay lập tức nhận diện vấn đề, rồi từ đó phát sóng tín hiệu đi chỉ trong vòng vài giây.
  - Tính bảo mật cao: Những thiết bị truyền tín hiệu đến PPPoE đều được dùng để phân tích và nhận thức một cách bí mật
  - Hạn chế tối đa sự cố rò rỉ thoát ra khỏi khu vực làm việc. Khiến cho PPPoE được đánh giá rất cao so với những giao thức khác. 
