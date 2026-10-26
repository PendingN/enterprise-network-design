# Enterprise Network Design

**Thiết kế hệ thống mạng doanh nghiệp kết nối trụ sở TP.HCM và chi nhánh Đắk Lắk.**

Đồ án môn Mạng máy tính và Truyền thông dữ liệu tại Trường Đại học Tôn Đức Thắng, xây dựng phương án hạ tầng mạng cho doanh nghiệp phân phối hàng tiêu dùng. Dự án gồm báo cáo thiết kế, sơ đồ logic và vật lý, slide thuyết trình cùng mô hình Cisco Packet Tracer.

[Báo cáo](52400079_52400066.docx) · [Slide thuyết trình](52400079_52400066.pptx) · [Mô hình Packet Tracer](Network.pkt)

## Bài toán và mục tiêu

Doanh nghiệp cần kết nối các phòng ban tại hai địa điểm, cung cấp dịch vụ mạng dùng chung và kiểm soát truy cập giữa các vùng mạng. Phương án thiết kế hướng đến:

- Phân đoạn mạng theo phòng ban để thuận tiện quản lý và áp dụng chính sách truy cập.
- Kết nối trụ sở và chi nhánh, hỗ trợ trao đổi dữ liệu giữa hai địa điểm.
- Bố trí thiết bị và liên kết dự phòng nhằm giảm gián đoạn khi có sự cố.
- Cân đối hiệu năng, khả năng mở rộng, bảo mật và chi phí triển khai.

## Phạm vi hệ thống

| Địa điểm | Tổ chức |
| --- | --- |
| Trụ sở TP.HCM — tầng 1 | Sales, Marketing, Nhân sự (HR) |
| Trụ sở TP.HCM — tầng 2 | Tài chính (Finance), Nghiên cứu và phát triển (R&D) |
| Trụ sở TP.HCM — tầng 3 | IT và khu vực máy chủ nội bộ |
| Chi nhánh Đắk Lắk | Sales, Marketing và Finance trên cùng một tầng |

Các dịch vụ trong phương án thiết kế gồm cấp phát IP tự động, truyền tệp, Web, DNS, Email, Wi-Fi và điện thoại IP.

## Kiến trúc mạng

Tại trụ sở, các switch truy cập phục vụ từng phòng ban được kết nối đến hai switch lớp 3 trung tâm. Mạng được phân chia thành các VLAN cho phòng ban, quản trị, máy chủ, thoại và Wi-Fi. Hai tường lửa kết nối mạng nội bộ với các tuyến ra nhà cung cấp dịch vụ; khu vực máy chủ Web, DNS và Email được bố trí riêng.

Chi nhánh sử dụng switch lớp 3 để kết nối các VLAN phòng ban, kết hợp tường lửa và router cho kết nối ra ngoài. Báo cáo trình bày phương án VPN site-to-site cho việc trao đổi dữ liệu giữa hai địa điểm.

### Sơ đồ logic

Thể hiện các vùng mạng, thiết bị và liên kết giữa trụ sở, nhà cung cấp dịch vụ và chi nhánh.

![Sơ đồ logic của hệ thống mạng doanh nghiệp](Logical.jpg)

### Sơ đồ vật lý

Thể hiện cách bố trí thiết bị theo địa điểm và các tầng của trụ sở.

![Sơ đồ vật lý của hệ thống mạng doanh nghiệp](Physical.jpg)

## Công nghệ trong thiết kế

| Nhóm | Công nghệ | Vai trò |
| --- | --- | --- |
| Phân đoạn và chuyển mạch | VLAN, trunk 802.1Q | Phân chia mạng và truyền lưu lượng nhiều VLAN qua liên kết giữa các switch |
| Định tuyến | Inter-VLAN routing qua SVI, OSPF | Kết nối các mạng con và trao đổi thông tin định tuyến |
| Dự phòng | HSRP, EtherChannel | Dự phòng cổng mặc định và gộp liên kết |
| Kiểm soát vòng lặp | STP, PortFast, BPDU Guard | Kiểm soát vòng lặp tầng 2 và bảo vệ cổng truy cập |
| Bảo mật | ACL, SSH, Port Security, Cisco ASA, NAT, VPN site-to-site | Kiểm soát truy cập, quản trị từ xa và bảo vệ kết nối giữa các vùng mạng |
| Mạng không dây | Access Point, Wireless LAN Controller | Cung cấp Wi-Fi và quản lý điểm truy cập tập trung |
| Dịch vụ | DHCPv4, FTP, HTTP/HTTPS, DNS, Email, VoIP | Cung cấp các dịch vụ mạng cho người dùng |

Danh sách trên tổng hợp nội dung thiết kế trong báo cáo; không thay thế kết quả kiểm thử cấu hình trong tệp mô phỏng.

## Tài liệu và tệp dự án

| Tệp | Nội dung |
| --- | --- |
| [52400079_52400066.docx](52400079_52400066.docx) | Báo cáo: yêu cầu, cơ sở lý thuyết, lựa chọn thiết bị, kết nối cổng, VLAN và quy hoạch IP |
| [52400079_52400066.pptx](52400079_52400066.pptx) | Slide trình bày đồ án |
| [Network.pkt](Network.pkt) | Mô hình mạng Cisco Packet Tracer |
| [Logical.jpg](Logical.jpg) | Sơ đồ mạng logic |
| [Physical.jpg](Physical.jpg) | Sơ đồ mạng vật lý |

## Cách mở dự án

1. Tải kho bằng **Code → Download ZIP**, sau đó giải nén; hoặc sao chép bằng Git:

   ```bash
   git clone https://github.com/PendingN/enterprise-network-design.git
   ```

2. Mở `Network.pkt` bằng **Cisco Packet Tracer** để xem mô hình và cấu hình thiết bị.
3. Đối chiếu mô hình với bảng kết nối cổng, VLAN và địa chỉ IP trong báo cáo Word.
4. Mở báo cáo và slide bằng Microsoft Office hoặc phần mềm tương thích.

Kho chưa ghi nhận phiên bản Packet Tracer dùng để tạo mô hình. Nếu phần mềm báo không tương thích, cần kiểm tra phiên bản trước khi mở và lưu lại tệp.

## Kiểm chứng mô hình

Kho hiện chưa kèm nhật ký hoặc bảng kết quả kiểm thử riêng. Khi đánh giá mô hình, cần kiểm tra các tình huống sau và đối chiếu với chính sách thiết kế:

- Máy trạm nhận đúng địa chỉ IP, subnet mask và default gateway.
- Kết nối trong VLAN, giữa các VLAN và giữa hai địa điểm hoạt động đúng quyền truy cập.
- Các dịch vụ máy chủ, Wi-Fi và điện thoại IP hoạt động theo cấu hình.
- ACL và quyền quản trị SSH cho phép hoặc từ chối đúng đối tượng.
- Hệ thống chuyển sang đường hoặc thiết bị dự phòng khi ngắt một thành phần thuộc phương án dự phòng.

## Nhóm thực hiện

- **Hà Tuấn Anh** — 52400066
- **Vũ Thùy Linh** — 52400079

Đồ án học phần, năm 2025. Các sơ đồ và phương án trong kho phục vụ học tập, mô phỏng và trình bày thiết kế mạng.
