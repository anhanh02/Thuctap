### 1. Mô hình OSI và TCP/IP
**1.1: Mô hình OSI**
  - **OSI (Open systems interconnection reference model)** là một hệ thống mở, phải có khả năng kết nối với các hệ thống khác nhau, tương thích với các chuẩn OSI
  - Có 2 loại giao thức trong mô hình OSI:
    - Giao thức hướng kết nối
      - Trước khi truyền dữ liệu, các thực thể đồng tầng trong 2 hệ thống cần thiết lập kết nối logic
      - Thỏa thuận về tập các tham số sẽ sử dụng trong giai đoạn truyền dữ liệu
      - Dữ liệu được truyền với các cơ chế kiểm soát lỗi, kiểm soát luồng dữ liệu, phân mảnh, hợp nhất dữ liệu
      - Sau khi trao đổi dữ liệu, kết nối được hủy bỏ
    - Giao thức không kết nối
      - Chỉ có giai đoạn duy nhất là giai đoạn truyền dữ liệu
      - Không có giai đoạn thiết lập hay hủy bỏ kết nối 
  - Gồm 7 tầng: 
    - Application
      - Cung cấp các dịch vụ mạng
      - Cung cấp xác thực người dùng
    - Presentation
      - Cung cấp mã hóa 
      - Biểu diễn thông tin người dùng phù hợp với thông tin làm việc của mạng và ngược lại
    - Session
      - Giao tiếp giữa các máy chủ
      - Thiết lập, quản lý, kết thúc các phiên làm việc giữa các ứng dụng
    - Transport 
      - Kết nối đầu cuối
      - Chia nhỏ các gói tin lớn thành các gói tin nhỏ hơn trước khi gửi đi và đánh số thứ tự đảm bảo chuyển đi đúng thứ tự
      - Thiết lập, duy trì, kết nối các mạch ảo
      - Phát hiện lỗi, phục hồi thông tin và điều khiển luồng
      - Vận chuyển tin cậy
    - Network
      - Cung cấp dữ liệu
      - Định tuyến gói dữ liệu 
      - Điều khiển tắc nghẽn, lựa chọn đường dẫn
    - Datalink
      - Truy cập phương tiện
      - Thiết lập các liên kết, duy trì và hủy bỏ các liên kết dữ liệu
      - Kiểm soát lỗi và kiếm soát lưu lượng
    - Physical
      - Truyền nhị phân
      - Xác định các chức năng, thủ tục về điện, cơ, quang để kích hoạt, duy trì và giải phóng các kết nối vật lý giữa các hệ thống mạng

**1.2: Mô hình TCP/IP**
  - **TCP/IP (Transmission control protocol/ Internet protocol)** là giao thức cơ bản được sử dụng giữa các máy vi tính và các thiết bị mạng truyền thông với nhau   
  - Gồm 4 tầng
    - Application
      - Kiếm soát các giao thức lớp cao
      - Đặc tả cho các ứng dụng phổ biến
    - Transport
      - Cung cấp dịch vụ vận chuyển từ host nguồn đến đích
      - Thiết lập cầu nối logic giữa các host
    - Internet
      - Cung cấp 1 địa chỉ logic cho giao diện vật lý mạng 
    - Network Access
      - Cung cấp các phương tiện kết nối vật lý cáp, bộ chuyển đổi, card mạng

**1.2: So sánh mô hình OSI và TCP/IP**
  - Giống nhau:
    - Đều có kiến trúc phân lớp 
    - Đều có lớp Network và Transport
    - Sử dụng kỹ thuật chuyển gói
    - Đều là mô hình logic 
  - Khác nhau:
  
|   #|  OSI | TCP/IP |
|---|---|---|
| Độ tin cậy và phổ biến | Nhiều người cho rằng là mô hình cũ, số người sử dụng hạn chế  | Được chuẩn hóa, được tin cậy và sử dụng phổ biến  |
| Tiếp cận | Theo chiều dọc  | Theo chiều ngang  |
| Số lớp ( tầng )  | 7  |  4 |
| Truyền thông  | Hỗ trợ cả định tuyến và không dây  | Hỗ trợ truyền thông không kết nối từ tầng mạng  |
| Tính phụ thuộc  | Giao thức độc lập  |  Phục thuộc vào giao thức |
| Mục đích  | Được sử dụng cho hệ thống máy tính  |  Được dùng để truyền dữ liệu qua internet |



 




