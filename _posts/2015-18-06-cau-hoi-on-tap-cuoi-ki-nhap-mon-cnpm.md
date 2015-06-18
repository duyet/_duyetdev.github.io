---
layout: post
title: Note 18/06/2015
---

# c. Trình bày các công nghệ nổi bật đã áp dụng khi thực hiện dự án.

Hệ thống quản lý thư viện (ULib) sử dụng công nghệ mới nhất của Nodejs theo mô hình Client-Server. 

- Điểm mạnh của mô hình Client-Server
 * Nhân viên dễ dàng sử dụng hệ thống, có thể đăng nhập bất kì đâu chỉ cần kết nối Internet mà không cần cài đặt phức tạp.
 * Có hệ thống phân quyền và bảo mật bằng mật khẩu riêng.
 * Cơ sở dữ liệu được lưu trữ tại 1 máy chủ duy nhất, giúp đồng bộ giữa các nhân viên, dễ dàng sao lưu phục hồi khi gặp sự cố.

- Điểm mạnh Nodejs 
 * RESTful API: ULib sử dụng công nghệ REST API, web client tương tác với server qua API, ngoài ra có thể dễ dàng mở rộng, thay đổi giao diện, mở rộng sang app mobile, ... mà không cần thiết kế lại Server. 
 * Single page Application: công nghệ SPA giúp tăng tốc độ hệ thống, tăng tốc độ dử dụng hệ thống so với WEB truyền thống. 
 * Nodejs có khả năng xử lý các luồng dữ liệu cực lớn 1 cách nhanh chóng.

# d. Trình bày kế hoạch thực hiện dự án và đánh giá mức độ hoàn thành của dự án.

* Họp nhóm và phân công 
* Khảo sát thư viện, xin các biểu mẫu, tìm hiểu mô hình nghiệp vụ, ....
* Xây dựng mô hình (ER, Model, ...) <-- list thêm 
* Xây dựng Web App, thiết kế giao diện, chức năng cho từng module 
* Kiểm tra, test thử 

Mức độ hoàn thành: một số chức năng chưa hoàn thiện 
 * Thống kê báo cáo chưa chi tiết 
 * Chưa kết nối được hệ thống quản lý thẻ ra vào của thư viện (chưa có đủ thông tin để xây dựng chức năng này)
 * Module phân quyền chưa tốt. 
 * ....

Tự đánh giá mức độ: 80%

# e. Trình bày những vấn đề gặp phải khi thực hiện dự án và nêu giải pháp để
giải quyết chúng.

* Phân công công việc chưa tốt, làm việc nhóm chưa hiệu quả 
* Chưa chia các mốc thời gian để thực hiện dự án chưa hợp lý.

Giải quyết: chém ... chém ...

# f. Nêu những bài học (Lesson Learned) sau khi thực hiện dự án.

