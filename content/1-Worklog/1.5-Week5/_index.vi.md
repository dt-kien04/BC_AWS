---
title: "Worklog Tuần 5"
date: 2026-08-29
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---



### Mục tiêu tuần 5:

* Nắm vững cơ chế tường lửa trạng thái (Stateful Firewall) trên AWS.
* Thiết lập quy tắc kiểm soát lưu lượng vào/ra chặt chẽ cho từng tầng ứng dụng.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 7   | - Tìm hiểu nguyên lý hoạt động của Inbound Rules và Outbound Rules trong Security Groups. <br> - Tạo nhóm bảo mật cho Web Server (TL-Web): mở cổng HTTP (80), HTTPS (443) cho người dùng và giới hạn cổng SSH (22) theo địa chỉ IP cá nhân. <br> - Tạo nhóm bảo mật cho Database (TL-Database): chỉ mở cổng MySQL (3306) cho duy nhất luồng kết nối nội bộ từ TL-Web. <br> | 29/08/2026 | 29/08/2026      | <https://aws.amazon.com/> |

### Kết quả đạt được tuần 5:

* Hoàn thiện hệ thống phòng thủ hai lớp thông qua TL-Web và TL-Database.

* Đảm bảo nguyên tắc đặc quyền tối thiểu, ngăn chặn hoàn toàn mọi truy cập trái phép từ bên ngoài Internet vào tầng cơ sở dữ liệu.
