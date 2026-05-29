================================================================================
          HƯỚNG DẪN SỬ DỤNG ZERG BOT (STABLE + LICENSE + AUTO PROXY)
================================================================================

1. CÀI ĐẶT MÔI TRƯỜNG (CÀI THƯ VIỆN)
Mở Terminal/CMD tại thư mục tool và chạy lệnh duy nhất sau:
--------------------------------------------------------------------------------
npm install axios https-proxy-agent colors chalk@4.1.2 node-machine-id bs58 tweetnacl uuid
--------------------------------------------------------------------------------

2. CẤU HÌNH FILE ĐẦU VÀO (INPUT)
Bạn cần chuẩn bị 4 file sau trong cùng thư mục chạy tool:

- privatekey.txt: 
    Mỗi dòng 1 Private Key (Định dạng BS58 của mạng Solana/Phantom).

- proxy.txt: 
    Mỗi dòng 1 Proxy định dạng: http://user:pass@ip:port hoặc http://ip:port
    *LƯU Ý: Tool sẽ tự động XÓA Proxy trong file này nếu gặp lỗi 403/429.

- user_agents.txt: 
    Mỗi dòng 1 User-Agent trình duyệt để giả lập thiết bị.

- config.json: 
    Tạo file với nội dung mẫu sau:
    {
      "threads": 10,
      "thread_start_delay": 2,
      "action_delay": [5, 10],
      "account_delay": [10, 20]
    }

3. CHI TIẾT ĐẦU RA (OUTPUT)
Sau khi tool vận hành, các dữ liệu sau sẽ được sinh ra:

- checkpint.txt: 
    Đây là file kết quả quan trọng nhất. 
    Định dạng: [Địa chỉ ví] | [Số XP] | [Rank hiện tại]
    Dùng file này để kiểm tra tổng tài sản của tất cả các ví.

- profiles.json: 
    Lưu trữ Token (Cookie) và UUID của từng ví. 
    Lần sau chạy lại tool sẽ dùng luôn Token này để không phải Login lại (Chống 403).

- last_index_zerg.txt: 
    Lưu vị trí ví cuối cùng đang chạy. Tắt tool bật lại sẽ chạy tiếp, không chạy lại từ đầu.

4. CƠ CHẾ HOẠT ĐỘNG
- Bước 1 (License): Tool kiểm tra HWID máy. Nếu chưa có key, tool yêu cầu nhập License Key.
- Bước 2 (Stealth): Tool dùng Cookie cũ nếu còn hạn để vượt Cloudflare.
- Bước 3 (Auto-Filter): Nếu Proxy bị chặn (403), tool tự xóa Proxy đó khỏi proxy.txt và đổi IP khác.
- Bước 4 (Interface): Ẩn toàn bộ log lỗi rác. Chỉ hiện log thành công. 
  Dưới cùng luôn có Spinner "Tool đang hoạt động..." nhấp nháy báo hiệu tool vẫn đang chạy.

5. CÁCH CHẠY TOOL
Dùng lệnh sau:
--------------------------------------------------------------------------------
node main.js
--------------------------------------------------------------------------------
================================================================================
