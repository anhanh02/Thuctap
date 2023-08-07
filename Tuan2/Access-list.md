### Access Control List
- *Access Control List (ACL)* – kiểm soát truy cập
  - ACL còn được gọi là Packet Filtering Firewall, là việc triển khai những luật cho phép đồng ý hoặc không đồng ý những kết nối cụ thể giữa các thiết bị định tuyến
  - ACL cho phép quản lý và kiểm soát quyền truy cập vào các tài nguyên trên mạng. Các tài nguyên này bao gồm máy chủ, thiết bị mạng, cơ sở dữ liệu, tệp tin và ứng dụng
  - Đó là sự bảo mật cho các thiết bị ở tầng 3 (layer 3) mà nó kiểm soát khả năng kết nối từ thiết bị định tuyến đến các thiết bị khác
  
- Các dạng Access-list

| Standard Access List  | Extended Access List  |
|---|---|
| Dải số cho Standard Access List từ 1 – 99  | Dải số cho Extended Access List từ 100 – 199  |
| Có thể chặn được Network, Host và Subnet  | Người quản trị có thể đồng ý hoặc chặn bất cứ một Network, Host, Subnet và cả dịch vụ  |
| Chặn toàn bộ các dịch vụ  | Được lựa chọn các dịch vụ muốn chặn  |
| Kiểm tra thông tin trong tiêu đề của gói tin như địa chỉ IP nguồn  | Kiểm tra thông tin trong cả tiêu đề và phần dữ liệu của gói tin như địa chỉ IP nguồn, địa chỉ IP đích, giao thức, cổng  |

- Cách thức hoạt động của Access Control List:
  - Người dùng yêu cầu truy cập tài nguyên trên mạng. Yêu cầu này sẽ được chuyển đến hệ thống máy chủ
  - Hệ thống máy chủ sẽ kiểm tra yêu cầu truy cập và so sánh nó với các quy tắc trong danh sách ACL tương ứng với tài nguyên được yêu cầu
  - Nếu yêu cầu truy cập khớp với một quy tắc trong danh sách ACL, hệ thống sẽ thực hiện hành động được quy định trong quy tắc đó. Nếu quy tắc cho phép truy cập vào tài nguyên đó, yêu cầu truy cập sẽ được chấp nhận và người dùng sẽ có quyền truy cập vào tài nguyên đó. Nếu quy tắc từ chối truy cập, yêu cầu truy cập sẽ bị từ chối
  - Nếu yêu cầu truy cập không khớp với bất kỳ quy tắc nào trong danh sách ACL, hệ thống sẽ áp dụng mặc định một quy tắc như từ chối truy cập
  - Sau khi yêu cầu truy cập được xử lý, hệ thống máy chủ sẽ phản hồi kết quả truy cập cho người dùng
- Các hành động thường có thể thực hiện bởi ACL bao gồm:
  - Permit (Cho phép): Gói tin phù hợp với quy tắc sẽ được chấp nhận và tiếp tục truyền đi
  - Deny (Từ chối): Gói tin phù hợp với quy tắc sẽ bị từ chối và không được truyền đi
  - Redirect (Chuyển hướng): Gói tin phù hợp với quy tắc sẽ được chuyển hướng đến một đích định trước khác
  - Log (Ghi nhật ký): Gói tin phù hợp với quy tắc sẽ được ghi lại vào bộ nhớ ghi nhật ký
- Ưu điểm của ACL
  - ACL cho phép quản trị viên kiểm soát truy cập vào tài nguyên mạng bằng cách cho phép hoặc từ chối các gói tin truy cập dựa trên các quy tắc được thiết lập
  - ACL giúp tăng tính bảo mật cho hệ thống mạng bằng cách hạn chế truy cập của người dùng không được ủy quyền và bảo vệ tài nguyên mạng quan trọng khỏi các mối đe dọa bên ngoài
  - ACL có thể triển khai trên nhiều loại thiết bị mạng, bao gồm router, switch, firewall, server hoặc các thiết bị trung gian khác. Ngoài ra, các quy tắc ACL có thể được thay đổi và cập nhật theo nhu cầu của tổ chức
  - ACLs giúp tăng tính khả dụng của hệ thống mạng bằng cách ngăn chặn các cuộc tấn công mạng và giúp giữ cho hệ thống hoạt động tốt hơn
- Nhược điểm của ACL
  - ACL có thể khá phức tạp và cần phải được cấu hình và quản lý một cách chính xác để đảm bảo tính bảo mật và hiệu quả
  - Nếu quản trị viên cấu hình ACL sai, có thể gây ra sự cố bảo mật hoặc ảnh hưởng đến tính khả dụng của hệ thống mạng
  - ACLs có thể gây ra độ trễ trong việc truy cập tài nguyên mạng, đặc biệt là khi có nhiều quy tắc ACL cần được áp dụng
  - Khi hệ thống mạng phát triển và phức tạp hơn, việc quản lý các quy tắc ACL cũng trở nên khó khăn hơn



