# INTERVIEW GUIDE – NGUYEN THAI MINH

## Thông tin ứng viên

- Rikkeisoft
- 1 năm Android Developer
- 1 tháng Intern
- Social Network / Dating App
- 14 Android variants
- Kotlin
- MVVM
- Hilt
- Retrofit
- Socket.IO
- Twilio
- Firebase FCM
- GPU Pixel SDK
- Git

---

# MỤC TIÊU PHỎNG VẤN

Ứng viên này có điểm mạnh:

- Làm production app
- Realtime communication
- Twilio
- Socket
- Social Network

Điểm cần xác minh:

- Có thật sự làm Twilio không?
- Có thật sự làm Socket.IO không?
- Có ownership hay chỉ code task?
- Có khả năng làm việc độc lập không?
- Có tiềm năng mentor không?

---

# PART 1 - OPENING & MINDSET

## Câu 1

Em hãy giới thiệu ngắn gọn về bản thân.

### Kỳ vọng

Ứng viên nói được:

- Quá trình học
- Tại sao chọn Android
- Các dự án nổi bật

---

## Câu 2

Trong các dự án đã làm, em tự tin nhất phần nào?

### Follow-up

Tại sao?

### Điều muốn nghe

Ví dụ:

```text
Realtime Chat
Voice Call
Video Call
```

---

## Câu 3

Nếu tự đánh giá Android từ 1-10.

Em cho mình bao nhiêu điểm?

### Đáp án tốt

```text
6.5 - 7.5
```

### Red Flag

```text
9 - 10
```

---

## Câu 4

Theo em Senior khác Junior ở điểm gì?

### Đáp án tốt

Không phải code nhanh hơn.

Mà:

```text
Ownership
Estimate
Review Code
Mentor
Problem Solving
```

---

## Câu 5

Nếu estimate 3 ngày nhưng ngày thứ 2 phát hiện không kịp.

Em xử lý sao?

### Đáp án tốt

```text
Đánh giá lại
Thông báo sớm
Đề xuất giải pháp
```

### Red Flag

```text
Đợi tới deadline mới báo
```

---

# PART 2 - SOCIAL NETWORK APP

## Câu 6

Em hãy mô tả kiến trúc tổng thể của Social Network App.

### Đáp án tốt

```text
Presentation
↓
ViewModel
↓
Repository
↓
Remote API
↓
Socket
↓
Local Cache
```

---

## Sub Question

Tại sao dùng MVVM?

### Đáp án

```text
Tách UI
Dễ test
Dễ maintain
```

---

# SOCKET.IO

## Câu 7

Socket.IO hoạt động như thế nào?

### Đáp án tốt

```text
Client Connect
↓
Authenticate
↓
Join Room
↓
Emit Event
↓
Receive Event
```

---

## Sub Question

Socket.IO khác REST API thế nào?

### Đáp án

### REST

```text
Request
Response
```

Client phải chủ động gọi.

---

### Socket

```text
Realtime
Two-way Communication
```

Server chủ động push dữ liệu.

---

## Sub Question

Chat App tại sao không dùng Polling?

### Đáp án

Polling:

```text
Tốn network
Tốn pin
Delay cao
```

Socket:

```text
Realtime
```

---

## Sub Question

Mất mạng giữa lúc chat.

Socket xử lý thế nào?

### Đáp án tốt

```text
Reconnect
Retry
Sync lại dữ liệu
```

---

## Sub Question

Nếu user gửi tin nhắn nhưng chưa tới server?

### Đáp án

```text
Local Pending State
Retry Queue
```

Ví dụ:

```text
Sending
Sent
Delivered
Seen
```

---

# TWILIO

## Câu 8

Em mô tả flow Voice Call bằng Twilio.

### Đáp án

```text
User Call
↓
Backend tạo Token
↓
Client Connect Room
↓
Twilio Server
↓
Peer Join
↓
Audio Stream
```

---

## Sub Question

Twilio Token là gì?

### Đáp án

Token xác thực người dùng.

Cho phép:

```text
Join Room
Voice Call
Video Call
```

---

## Sub Question

Token hết hạn thì sao?

### Đáp án

Không join được room.

Cần lấy token mới.

---

## Sub Question

Call đang diễn ra.

Mạng bị mất.

Xử lý sao?

### Đáp án tốt

```text
Reconnect
Hiển thị trạng thái reconnecting
Retry
```

---

## Sub Question

Voice Call và Video Call khác nhau gì?

### Đáp án

Voice:

```text
Audio Track
```

Video:

```text
Audio Track
Video Track
```

Video tốn:

```text
CPU
Memory
Bandwidth
```

---

# VIDEO CALL

## Câu 9

Khi video call bị giật.

Em sẽ kiểm tra gì?

### Đáp án

```text
Network
Bitrate
FPS
CPU
Memory
```

---

## Follow-up

Nếu CPU máy quá cao?

### Đáp án

```text
Giảm resolution
Giảm FPS
Tắt beauty effect
```

---

# GPU PIXEL SDK

## Câu 10

CV ghi em làm:

```text
Background Blur
Face Smooth
Eye Enlargement
```

Các feature này hoạt động thế nào?

### Điều muốn nghe

Ứng viên phải hiểu:

```text
Camera Frame
↓
GPU Processing
↓
Apply Filter
↓
Render
```

---

## Sub Question

Tại sao các filter làm app lag?

### Đáp án

Do:

```text
GPU Load
Memory
Frame Processing
```

---

# FIREBASE CLOUD MESSAGING

## Câu 11

FCM dùng để làm gì trong dự án?

### Đáp án

```text
Push Notification
Incoming Call
User Activity
```

---

## Sub Question

Khi app đang kill.

FCM có nhận được không?

### Đáp án

Có.

Thông qua:

```text
Firebase Service
```

---

## Sub Question

Tại sao Incoming Call không chỉ dùng FCM?

### Đáp án

FCM chỉ để:

```text
Wakeup App
```

Call thực tế:

```text
Socket
Twilio
```

---

# PART 3 - PROBLEM SOLVING

## Câu 12

User báo:

```text
Tin nhắn gửi đi nhưng người nhận không nhận được.
```

Em debug thế nào?

### Đáp án tốt

```text
Kiểm tra Socket
Kiểm tra Room
Kiểm tra Backend
Kiểm tra ACK
```

---

## Follow-up

Làm sao biết lỗi app hay backend?

### Đáp án

```text
Log
Postman
Socket Event
Backend Log
```

---

## Câu 13

App bị lag khi mở màn hình Chat 5000 tin nhắn.

Em xử lý thế nào?

### Đáp án

```text
Paging
DiffUtil
RecyclerView Optimization
Image Cache
```

---

## Câu 14

App bị crash ngẫu nhiên.

Không reproduce được.

Em xử lý sao?

### Đáp án

```text
Crashlytics
Stacktrace
Device Info
OS Version
```

---

# PART 4 - OWNERSHIP & LEAD POTENTIAL

## Câu 15

Trong dự án em đã từng chủ động đề xuất cải tiến gì chưa?

### Điều muốn nghe

Ví dụ:

```text
Refactor
Performance
UX
Code Structure
```

---

## Câu 16

Nếu có một Fresher mới vào team.

Em sẽ hướng dẫn gì?

### Đáp án tốt

```text
Setup Project
Architecture
Git Flow
Coding Convention
```

---

## Câu 17

Nếu em phát hiện requirement của BA có vấn đề.

Em xử lý thế nào?

### Đáp án tốt

```text
Phân tích
Đưa ví dụ
Trao đổi lại BA
Đề xuất giải pháp
```

---

# CÂU HỎI CHỐT

## Câu 18

Theo em điều khó nhất khi làm Social Network App là gì?

### Đáp án tốt

```text
Realtime
Scalability
Message Sync
Call Stability
Notification
```

---

# THANG ĐIỂM

## Strong Hire

- Giải thích tốt Twilio
- Giải thích tốt Socket.IO
- Hiểu FCM
- Hiểu Realtime System
- Có ownership

## Hire

- Android tốt
- Socket cơ bản
- Twilio cơ bản

## No Hire

Không giải thích được:

- Socket.IO
- Twilio Token
- FCM Flow
- Message Sync

=> Khả năng cao chỉ implement UI hoặc code theo task.

---

# ĐIỂM QUAN TRỌNG NHẤT CẦN ĐÀO SÂU

1. Socket.IO
2. Twilio
3. Realtime Message Sync
4. Video Call
5. Ownership

Đây là 5 phần phân biệt người làm thật với người chỉ "integrate SDK theo tài liệu".
