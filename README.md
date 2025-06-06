# RPA_FaceBook_AutoCommentBot_PAD
🧠 RPA Facebook Auto Comment - Power Automate Desktop
Tự động đăng nhập nhiều tài khoản Facebook từ file Excel và bình luận vào bài viết mới nhất trên một fanpage cụ thể (ví dụ: MTP Fanpage) bằng Power Automate Desktop.

📁 Cấu trúc dữ liệu đầu vào
File Excel facebook_accounts1.xlsx gồm các cột:

tên acc: Email hoặc tên tài khoản Facebook

pass: Mật khẩu Facebook

nội dung comment: Nội dung cần comment trên bài viết mới nhất

🔄 Quy trình hoạt động
Mở Excel và đọc dữ liệu

Mở file Excel với PAD

Đọc tất cả dữ liệu và lưu vào biến fbData

Lặp qua từng tài khoản (LOOP FOREACH fbRow IN fbData)

Mở trình duyệt Chrome ở chế độ ẩn danh tới link fanpage Facebook

Đợi trình duyệt tải (WAIT 10)

Đăng nhập tài khoản Facebook:

Nhập tên acc

Nhấn {Tab} chuyển sang ô mật khẩu

Nhập pass

Nhấn {Enter} để đăng nhập

Đợi giao diện Facebook tải (WAIT 10)

Tìm và click ô "Viết bình luận"

Dùng UI Automation để hover và click nút "Viết bình luận"

Gửi bình luận

Nhập nội dung từ fbRow['nội dung comment']

Nhấn {Enter} để gửi

Đóng Chrome

Gọi PowerShell: Stop-Process -Name chrome -Force

Kết thúc

Sau khi duyệt hết các tài khoản, đóng file Excel

🧰 Công nghệ sử dụng
Power Automate Desktop: Để xây dựng RPA

UI Automation: Tương tác với trình duyệt Chrome

PowerShell: Đóng trình duyệt Chrome sau mỗi lượt

Excel Automation: Đọc dữ liệu đăng nhập từ file

📌 Ghi chú
Flow hoạt động tốt nhất khi trình duyệt không bị yêu cầu xác minh bất thường (ví dụ: mã bảo mật, captcha…)

Bạn có thể tùy chỉnh nội dung comment hoặc page đích bằng cách sửa dòng URL trong command --incognito https://www.facebook.com/MTP.Fan?...
