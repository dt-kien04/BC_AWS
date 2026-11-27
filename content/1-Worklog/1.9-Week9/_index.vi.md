---
title: "Worklog Tuần 9"
date: 2026-09-26
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---



### Mục tiêu tuần 9:

* Thiết kế kiến trúc có tính sẵn sàng cao (High Availability) và khả năng tự động mở rộng.
* Loại bỏ điểm lỗi đơn lẻ của mô hình máy chủ truyền thống.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 7   | - Đóng gói máy chủ Web-travel-sv thành khuôn mẫu chuẩn Web-Travel-AMI. <br> - Tạo Target Group (Travel-target) và kích hoạt tính năng giữ phiên đăng nhập (Sticky Sessions). <br> - Tạo Launch Template (Travel-template) sử dụng khuôn mẫu vừa đóng gói. <br> - Thiết lập Auto Scaling Group (Travel-auto-scaling-group) trải dài trên 2 Public Subnets. <br> | 26/09/2026   | 26/09/2026      | <https://aws.amazon.com/> |

### Kết quả đạt được tuần 9:

* Hoàn thiện kiến trúc tự động mở rộng linh hoạt từ 0 đến 3 máy chủ dựa trên nhu cầu tải thực tế.

* Đảm bảo trải nghiệm người dùng không bị gián đoạn phiên đăng nhập khi hệ thống điều phối lưu lượng qua nhiều máy chủ.
