# INTERVIEW GUIDE – NGUYEN DUC ANH

## Thông tin ứng viên

- Android Developer
- Khoảng 2-3 năm kinh nghiệm
- Rikkeisoft
- Thị trường Nhật Bản
- Dating / Social Network App
- Kotlin
- MVVM
- Clean Architecture
- Hilt
- Retrofit
- Firebase
- Socket
- Realtime Communication
- Có kinh nghiệm maintain production app

---

# MỤC TIÊU PHỎNG VẤN

Xác minh:

- Có thực sự làm Android production hay không
- Có khả năng tự chủ hay chỉ nhận task
- Hiểu Android framework tới đâu
- Có khả năng mentor fresher
- Có phù hợp môi trường làm việc với khách Nhật

---

# PART 1 - OPENING & MINDSET

## Câu 1

Em hãy giới thiệu bản thân trong khoảng 3 phút.

### Kỳ vọng

Ứng viên nên trình bày:

```text
- Quá trình học tập
- Quá trình đi làm
- Các dự án nổi bật
- Điểm mạnh
- Định hướng tương lai
```

---

## Câu 2

Tại sao em muốn chuyển công ty?

### Đáp án tốt

```text
- Tìm môi trường lớn hơn
- Muốn học thêm domain mới
- Muốn phát triển lên Senior
- Muốn tham gia dự án có quy mô lớn hơn
```

### Red Flag

```text
- Chán
- Lương thấp
- Team cũ không giỏi
```

---

## Câu 3

Điều gì làm em tự tin nhất ở bản thân?

### Đáp án tốt

```text
- Khả năng học nhanh
- Tinh thần trách nhiệm
- Khả năng tự nghiên cứu
```

---

## Câu 4

Nếu được đánh giá Android từ 1-10?

### Đáp án tốt

```text
6.5 - 8
```

### Red Flag

```text
9-10
```

---

# PART 2 - ANDROID FUNDAMENTAL

## Câu 5

Mô tả Activity Lifecycle.

### Đáp án

```text
onCreate()
↓
onStart()
↓
onResume()
↓
Running
↓
onPause()
↓
onStop()
↓
onDestroy()
```

---

## Sub Question

Khi xoay màn hình điều gì xảy ra?

### Đáp án

```text
Activity bị destroy
Activity được tạo lại
```

---

## Sub Question

ViewModel có bị mất không?

### Đáp án

```text
Không

ViewModel được giữ lại qua configuration change
```

---

## Sub Question

Nếu app bị kill bởi hệ điều hành?

### Đáp án

```text
ViewModel cũng mất
```

---

# Câu 6

Fragment Lifecycle khác Activity Lifecycle thế nào?

### Đáp án

Fragment có:

```text
onCreateView()
onViewCreated()
onDestroyView()
```

---

## Sub Question

Tại sao cần onDestroyView?

### Đáp án

Để tránh:

```text
Memory Leak
```

Ví dụ:

```kotlin
binding = null
```

---

# PART 3 - MVVM & CLEAN ARCHITECTURE

## Câu 7

Em mô tả MVVM Architecture đang dùng.

### Đáp án

```text
View
↓
ViewModel
↓
Repository
↓
Data Source
```

---

## Sub Question

Tại sao không gọi API trực tiếp từ Activity?

### Đáp án

```text
Khó maintain
Khó test
Vi phạm separation of concerns
```

---

## Sub Question

Repository có nhiệm vụ gì?

### Đáp án

```text
Quản lý nguồn dữ liệu

Remote
Local
Cache
```

---

## Sub Question

ViewModel nên biết Android Context không?

### Đáp án

```text
Không nên
```

Lý do:

```text
Dễ memory leak
Khó test
```

---

# PART 4 - COROUTINE

## Câu 8

Coroutine là gì?

### Đáp án

Coroutine giúp:

```text
Xử lý bất đồng bộ
Không block Main Thread
```

---

## Sub Question

launch khác async thế nào?

### Đáp án

### launch

```text
Không trả về kết quả
```

---

### async

```text
Có trả về kết quả qua await()
```

---

## Sub Question

Dispatchers.IO dùng khi nào?

### Đáp án

```text
API
Database
File
```

---

## Sub Question

Dispatchers.Main dùng khi nào?

### Đáp án

```text
Update UI
```

---

# PART 5 - HILT

## Câu 9

Hilt dùng để làm gì?

### Đáp án

```text
Dependency Injection
```

---

## Sub Question

Lợi ích của Hilt?

### Đáp án

```text
Giảm boilerplate
Dễ test
Dễ maintain
```

---

## Sub Question

Nếu không dùng Hilt?

### Đáp án

Phải:

```text
Tự khởi tạo object
Manual injection
```

---

## Sub Question

Singleton là gì?

### Đáp án

```text
Một instance duy nhất
```

Ví dụ:

```text
Retrofit
Database
```

---

# PART 6 - NETWORK

## Câu 10

Retrofit hoạt động thế nào?

### Đáp án

```text
Interface
↓
Annotation
↓
HTTP Request
↓
Response
```

---

## Sub Question

Interceptor dùng để làm gì?

### Đáp án

```text
Add Header
Logging
Refresh Token
```

---

## Sub Question

Nếu API trả về 401?

### Đáp án

```text
Refresh Token
Retry Request
```

---

# PART 7 - FIREBASE

## Câu 11

Em đã dùng Firebase nào?

### Kỳ vọng

Ứng viên trả lời:

```text
FCM
Crashlytics
Analytics
```

---

## Sub Question

FCM hoạt động thế nào?

### Đáp án

```text
Server
↓
Firebase
↓
Device
```

---

## Sub Question

FCM token là gì?

### Đáp án

```text
Định danh thiết bị nhận push
```

---

## Sub Question

Khi token thay đổi thì sao?

### Đáp án

```text
Update token lên server
```

---

# PART 8 - REALTIME / SOCKET

## Câu 12

Socket khác REST API thế nào?

### Đáp án

### REST

```text
Request → Response
```

---

### Socket

```text
Realtime
2 chiều
```

---

## Sub Question

Chat App nên dùng gì?

### Đáp án

```text
Socket
```

---

## Sub Question

Mất mạng trong lúc chat?

### Đáp án

```text
Reconnect
Retry
Sync dữ liệu
```

---

# PART 9 - DEBUG & PROBLEM SOLVING

## Câu 13

User báo app crash nhưng em không reproduce được.

Em xử lý thế nào?

### Đáp án

```text
Crashlytics
Logcat
Stacktrace
Thiết bị
Android Version
```

---

## Sub Question

Bug production ưu tiên xử lý theo gì?

### Đáp án

```text
Mức độ ảnh hưởng
Số lượng user
Doanh thu
```

---

## Câu 14

App bị lag khi load danh sách 10.000 item.

Em xử lý thế nào?

### Đáp án

```text
Paging
RecyclerView Optimization
Image Cache
DiffUtil
```

---

# PART 10 - MINDSET & TEAMWORK

## Câu 15

Nếu BA yêu cầu một tính năng em thấy không hợp lý.

Em xử lý thế nào?

### Đáp án tốt

```text
Phân tích
Đưa ví dụ
Trao đổi
Đề xuất giải pháp
```

---

## Câu 16

Nếu có một Fresher mới vào team.

Em sẽ hướng dẫn gì đầu tiên?

### Đáp án tốt

```text
Project Structure
Git Flow
Coding Convention
Architecture
```

---

## Câu 17

Code Review quan trọng ở điểm nào?

### Đáp án

```text
Phát hiện bug
Đảm bảo coding standard
Chia sẻ kiến thức
```

---

## Câu 18

Theo em một developer giỏi là người như thế nào?

### Đáp án tốt

```text
Có ownership
Giải quyết vấn đề
Tự học
Hỗ trợ team
```

---

# CÂU HỎI CHỐT

## Câu 19

Nếu ngày mai anh giao em một task hoàn toàn mới:

```text
Chưa biết domain
Chưa biết API
Chưa biết luồng nghiệp vụ
```

Em sẽ bắt đầu từ đâu?

### Đáp án tốt

```text
Tìm hiểu requirement
Đọc tài liệu
Trao đổi BA
Phân tích API
POC nếu cần
Estimate sau khi hiểu rõ
```

---

# THANG ĐIỂM

## Strong Hire

- Android Core vững
- MVVM tốt
- Coroutine tốt
- Hilt tốt
- Có ownership
- Có tư duy mentor

## Hire

- Android khá
- Làm việc độc lập được
- Có tiềm năng phát triển

## No Hire

Không trả lời được:

```text
Activity Lifecycle
MVVM
Coroutine
Hilt
Repository
FCM
Socket
```

=> Chưa đủ năng lực cho Junior Android làm việc trực tiếp với khách Nhật.
