---
title: "Worklog Tuần 8"
date: 2026-09-19
weight: 1
chapter: false
pre: " <b> 1.8. </b> "
---
{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}


### Mục tiêu tuần 8:

* Xây dựng hoàn chỉnh môi trường chạy web (LAMP stack) trên máy chủ Ubuntu.
* Kết nối thông suốt ứng dụng PHP trên EC2 với cơ sở dữ liệu Amazon RDS.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 7   | - Cài đặt gói phần mềm Apache2, PHP, MySQL Client và Git trên EC2. <br> - Kéo mã nguồn từ GitHub về thư mục /var/www/html/ và phân quyền thư mục lưu trữ ảnh (www-data). <br> - Nạp dữ liệu từ tệp travel_test.sql lên Amazon RDS qua dòng lệnh. <br> - Cấu hình tệp php/ket_noi.php trỏ tới Endpoint của RDS và kiểm thử website trên trình duyệt. <br> | 19/09/2026   | 19/09/2026      | <ubuntu.com> |

### Kết quả đạt được tuần 8:

* Ứng dụng Web Travel chính thức vận hành trực tuyến trên nền tảng AWS qua địa chỉ IPv4 công cộng

* Toàn bộ chức năng nghiệp vụ (hiển thị tour, đăng ký, đăng nhập, đặt tour và quản trị hệ thống) hoạt động đồng bộ dữ liệu chính xác với Amazon RDS.
