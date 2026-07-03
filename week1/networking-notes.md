
# Networking Notes

## TCP
- Đảm bảo dữ liệu đến nơi
- Có gửi lại khi mất gói

## UDP
- Nhanh
- Không gửi lại

## Port
22: SSH
80: HTTP
443: HTTPS
53: DNS
3306: MySQL
## Port

22: SSH
53: DNS
80: HTTP
443: HTTPS
3306: MySQL

## Nmap

- nmap 127.0.0.1
- nmap -sV 127.0.0.1

Nmap dùng để quét host, port và xác định dịch vụ.


# Ngày 2 - Networking & Nmap

# 1. TCP và UDP

## TCP (Transmission Control Protocol)

Đặc điểm:
- Đảm bảo dữ liệu đến nơi.
- Đúng thứ tự.
- Nếu mất gói sẽ gửi lại.
- Tốc độ chậm hơn UDP.

Ví dụ:
- Chat (Messenger, Zalo)
- Đăng nhập website
- Tải file
- Gửi Email

=> Dùng khi dữ liệu phải chính xác.

---

## UDP (User Datagram Protocol)

Đặc điểm:
- Không đảm bảo dữ liệu đến nơi.
- Không gửi lại khi mất gói.
- Tốc độ nhanh.
- Độ trễ thấp.

Ví dụ:
- Gọi video
- Livestream
- Chơi game online
- VoIP

=> Dùng khi tốc độ quan trọng hơn độ chính xác.

---

# 2. Port

Port là cổng giao tiếp của một dịch vụ trên máy tính.

IP giống như địa chỉ ngôi nhà.

Port giống như số phòng trong ngôi nhà.

Ví dụ:

192.168.1.10:80

192.168.1.10 là máy tính.

80 là dịch vụ Website.

---

## Các Port quan trọng

22 : SSH (Đăng nhập Linux từ xa)

53 : DNS (Phân giải tên miền)

80 : HTTP (Website)

443 : HTTPS (Website có mã hóa)

3306 : MySQL (Cơ sở dữ liệu)

631 : CUPS (Dịch vụ in của Ubuntu)

---

# 3. HTTP và HTTPS

HTTP

- Port 80
- Không mã hóa dữ liệu

HTTPS

- Port 443
- Dữ liệu được mã hóa
- An toàn hơn HTTP

---

# 4. Localhost

127.0.0.1

Là địa chỉ của chính máy tính.

Ví dụ:

nmap 127.0.0.1

=> Quét chính máy Ubuntu.

---

# 5. 127.0.0.1 và 0.0.0.0

127.0.0.1

- Chỉ máy hiện tại truy cập được.

0.0.0.0

- Lắng nghe trên tất cả địa chỉ IP.
- Máy khác trong mạng có thể truy cập (nếu firewall cho phép).

=> 0.0.0.0 có bề mặt tấn công lớn hơn.

---

# 6. ss

Lệnh:

ss -tuln

Dùng để xem các port đang mở trên Linux.

Ý nghĩa:

tcp : Giao thức TCP

udp : Giao thức UDP

LISTEN : Đang chờ kết nối

127.0.0.1 : Chỉ localhost

0.0.0.0 : Tất cả IP

---

# 7. Nmap

Nmap là công cụ quét mạng được Pentester sử dụng để:

- Quét host
- Quét port
- Xác định dịch vụ
- Xác định phiên bản dịch vụ

---

## Các lệnh đã học

Kiểm tra phiên bản

nmap --version

Quét localhost

nmap 127.0.0.1

Quét và xác định phiên bản dịch vụ

nmap -sV 127.0.0.1

---

Ví dụ kết quả

631/tcp open ipp CUPS 2.4

631

=> Port

open

=> Port đang mở

ipp

=> Dịch vụ

CUPS 2.4

=> Phiên bản dịch vụ

---

# 8. Tư duy Pentester

Không chỉ nhìn thấy port.

Ví dụ:

22/tcp open ssh

80/tcp open http

443/tcp open https

Một Pentester sẽ suy nghĩ:

- Có Website không?
- Có lỗ hổng Web không?
- SSH có cấu hình yếu không?
- Phiên bản có lỗ hổng không?

---

# Kiến thức cần nhớ

TCP

✔ Chính xác

✔ Có gửi lại

✔ Chậm hơn

UDP

✔ Nhanh

✔ Không gửi lại

✔ Độ trễ thấp

HTTP Port 80

HTTPS Port 443

SSH Port 22

DNS Port 53

MySQL Port 3306

Localhost

127.0.0.1

Xem port

ss -tuln

Quét port

nmap

Xác định phiên bản

nmap -sV
Tại sao gửi file nên dùng TCP mà chơi game online thường dùng UDP?
->TCP sẽ gửi lại gói tin nếu bị mất, còn UDP không gửi lại nên nhanh hơn.

Port là gì? IP khác Port như thế nào?
->IP xác định máy tính trên mạng.
->Port xác định dịch vụ/chương trình đang chạy trên máy tính đó.

Tại sao 0.0.0.0:8080 thường rủi ro hơn 127.0.0.1:8080?
->0.0.0.0 nghĩa là dịch vụ lắng nghe trên tất cả các địa chỉ IP của máy.
Do đó:
Máy khác trong mạng có thể truy cập (nếu firewall cho phép).

ss -tuln dùng để làm gì?
->ss -tuln dùng để xem các socket TCP/UDP đang lắng nghe (LISTEN) hoặc đang hoạt động trên hệ thống Linux.

nmap -sV khác gì nmap?
->nmap -sV không xem phiên bản của port, mà xác định phiên bản của dịch vụ đang chạy trên port.
