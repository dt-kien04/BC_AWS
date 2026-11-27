---
title: "Worklog Tuần 6"
date: 2026-09-05
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---



### Mục tiêu tuần 6:

* Hiểu rõ lợi ích của dịch vụ cơ sở dữ liệu quản trị (Managed Database) so với cài đặt thủ công.
* Khởi tạo và bảo mật cơ sở dữ liệu MySQL trong khu vực mạng riêng tư.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 7   | - Tìm hiểu dịch vụ Amazon RDS và các tùy chọn cấu hình lưu trữ, sao lưu. <br> - Tạo DB Subnet Group gồm 2 Private Subnets của travel-vpc. <br> - Khởi tạo cơ sở dữ liệu MySQL (travel-database, cấu hình db.t4g.micro) ở chế độ không công khai (Public access = No). <br> - Gắn tường lửa TL-Database và trích xuất địa chỉ kết nối (Endpoint). <br> | 05/09/2026   | 05/09/2026      | <https://aws.amazon.com/> |

### Kết quả đạt được tuần 6:
* Khởi tạo thành công cơ sở dữ liệu travel-database ở trạng thái hoạt động ổn định (Available) trong Private Subnet.

* Thu được chuỗi Endpoint nội bộ và hoàn tất việc khởi tạo database rỗng travel_test sẵn sàng tiếp nhận dữ liệu.
