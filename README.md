# IELTS Visual Vocabulary Trainer — 1.000 từ

Ứng dụng PWA cho iPhone, dùng GitHub Pages, 1.000 mục từ: A1–A2 (350), B1–B2 (400), C1–C2 (250), chia 18 chủ đề. Mỗi mục có nghĩa tiếng Việt, biểu tượng minh họa, câu ví dụ đơn giản, IPA (nếu có trong từ điển), giọng đọc thiết bị. Có quiz ngẫu nhiên 10 câu, luyện đọc bằng nhận dạng giọng nói khi được hỗ trợ và lưu tiến độ trên thiết bị. Các câu ví dụ của từ bổ sung là câu giới thiệu từ vựng đơn giản, không phải ví dụ ngữ cảnh nâng cao.

## Đăng lên GitHub Pages
1. Giải nén ZIP, upload **toàn bộ file bên trong** vào thư mục gốc của repository GitHub (ghi đè file cũ), Commit changes.
2. Settings → Pages → Deploy from a branch → main → /(root) → Save.
3. Trên iPhone mở link GitHub Pages trong Safari, Share → Add to Home Screen.
4. Nếu thấy bản cũ, đóng app và mở lại khi có mạng để service worker cập nhật.

## Giới hạn
- Hình là emoji minh họa theo chủ đề, **không phải 1.000 tranh minh họa riêng**.
- Phần luyện đọc chỉ so khớp văn bản nhận dạng, **không phải AI chấm phát âm chuyên dụng**. Dịch vụ AI chấm phát âm thực sự cần backend bảo mật và API; không nên đặt API key trong GitHub Pages.
- Từ điển được biên soạn theo độ khó tham khảo, không phải danh sách CEFR được chứng nhận.
- Hoạt động offline cho nội dung và quiz sau lần tải đầu; giọng nói phụ thuộc trình duyệt, thiết bị và mạng.
- Tiến độ lưu localStorage, không đồng bộ giữa các thiết bị.


## Luyện đọc 5 cấp độ (bản nâng cấp)
- 1 từ → cụm ngắn → 1 câu → 3 câu → đoạn 5 câu.
- Điểm khớp nhận dạng 0–100%: xanh lá 90–100, xanh nhạt 70–89, vàng 50–69, cam 30–49, đỏ 0–29.
- Từng từ được đánh dấu xanh (khớp) hoặc đỏ (chưa khớp).
- Có thể nghe mẫu, đọc lại, chuyển cấp độ và lưu lịch sử.
- Đây là **độ khớp bản ghi nhận dạng giọng nói**, không phải điểm phát âm AI chuyên sâu. GitHub Pages tĩnh không có backend để bảo vệ khóa API chấm phát âm.
