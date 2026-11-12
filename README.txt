HÔM NAY ĂN GÌ? — WEBSITE VÒNG QUAY CHUNG 4 NGƯỜI
=================================================

BỘ FILE NÀY LÀ MÃ NGUỒN WEBSITE. Để có một link công khai và đồng bộ giữa 4 điện thoại,
bạn cần cấu hình Firebase và đưa website lên dịch vụ hosting. Chỉ mở file HTML trên máy
thì không thể đồng bộ giữa nhiều điện thoại.

PHẦN 1 — TẠO CƠ SỞ DỮ LIỆU FIREBASE (miễn phí ở mức sử dụng nhỏ)
1. Mở https://console.firebase.google.com/ và đăng nhập Google.
2. Chọn Add project / Tạo dự án, đặt tên tùy ý, ví dụ hom-nay-an-gi.
3. Trong dự án, vào Build > Realtime Database > Create Database.
4. Chọn khu vực gần Việt Nam (nếu có asia-southeast1), tạo database.
5. Mở tab Rules và đặt quy tắc thử nghiệm dưới đây, sau đó bấm Publish:

{
  "rules": {
    "rooms": {
      "$room": {
        ".read": true,
        ".write": true
      }
    }
  }
}

LƯU Ý BẢO MẬT: Quy tắc này cho phép người biết đường dẫn phòng đọc/ghi dữ liệu.
Chỉ dùng cho trò chơi thử nghiệm, không lưu thông tin cá nhân. Mã phòng không phải mật khẩu.
Có thể tắt/xóa database sau khi chơi. Không dùng cấu hình này cho ứng dụng quan trọng.

6. Vào Project settings (biểu tượng bánh răng) > General > Your apps > biểu tượng Web </>.
7. Đăng ký ứng dụng web. Firebase sẽ hiện đoạn firebaseConfig. Sao chép các giá trị
   apiKey, authDomain, databaseURL, projectId, appId.
8. Mở index.html bằng trình soạn thảo văn bản. Tìm đoạn:
   const firebaseConfig = { ... };
   Thay YOUR_API_KEY, YOUR_PROJECT_ID, YOUR_APP_ID bằng giá trị thật.
   Đặc biệt databaseURL phải đúng URL Realtime Database mà Firebase cung cấp.

PHẦN 2 — ĐƯA WEBSITE LÊN MẠNG ĐỂ LẤY LINK
Cách dễ dùng: GitHub Pages
1. Tạo tài khoản tại https://github.com/ nếu chưa có.
2. Tạo repository mới, ví dụ hom-nay-an-gi.
3. Tải index.html lên repository ở thư mục gốc.
4. Vào Settings > Pages.
5. Ở Build and deployment, chọn Deploy from a branch; chọn branch main và folder /(root),
   rồi Save.
6. Đợi GitHub Pages xuất bản. Link sẽ có dạng:
   https://TEN-TK-GITHUB.github.io/hom-nay-an-gi/
   Đây chỉ là dạng ví dụ; link thật phụ thuộc tên tài khoản và repository.

CÁCH CHƠI
- Một người mở link, nhập tên rồi bấm “Tạo phòng mới”.
- Gửi mã phòng 6 ký tự cho 3 người còn lại.
- Ba người kia mở cùng link, nhập tên và mã phòng, bấm “Vào phòng”.
- Mỗi người bấm quay đúng một lần. Món đã được chọn sẽ không lặp lại.
- Cả nhóm nhìn thấy kết quả cập nhật trên màn hình.

GHI CHÚ
- Đây là bản mẫu cơ bản, chưa có tài khoản đăng nhập, xác minh người chơi hay chống phá phòng.
- Ai biết mã phòng có thể tham gia nếu phòng còn chỗ. Không nhập tên thật hoặc thông tin riêng tư.
- Nếu muốn phát hành rộng rãi, cần bổ sung xác thực và quy tắc bảo mật Firebase.
