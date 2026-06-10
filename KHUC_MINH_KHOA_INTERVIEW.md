# INTERVIEW GUIDE – KHUC MINH KHOA

## Thông tin ứng viên

- 2 năm kinh nghiệm
- Zinza Technology
- Thị trường Nhật
- Dating App
- Android TV
- React Native MVP Blockchain
- Kotlin, MVVM, XML
- Firebase
- IAP
- S3 Upload
- Play Console
- SDK Migration
- Hilt
- Coroutines

---

# PART 1 - OPENING & MINDSET

## Câu 1

Em hãy giới thiệu ngắn gọn về bản thân và hành trình trở thành Android Developer.

### Kỳ vọng

Ứng viên nên trả lời:

- Học trường nào
- Bắt đầu Android từ khi nào
- Công việc hiện tại
- Các dự án nổi bật

### Câu trả lời tốt

"Tốt nghiệp Đại học Công nghệ Giao thông Vận tải, em bắt đầu Android từ năm 3. Sau khi thực tập em làm tại Zinza Technology, chủ yếu làm các dự án cho thị trường Nhật. Hiện tại em đã tham gia Dating App, Android TV App và một số dự án React Native. Công việc chính của em là phát triển tính năng mới, xử lý bug production, làm việc với PM và backend."

---

## Câu 2

Nếu tự đánh giá năng lực Android hiện tại từ 1-10 thì em cho bao nhiêu điểm?

### Câu trả lời tốt

```text
6.5 - 7.5 / 10
```

Lý do:

- Nắm vững Android cơ bản
- Làm production thực tế
- Vẫn còn nhiều thứ phải học như Architecture, Performance, Security

### Red Flag

```text
9/10
10/10
```

với 2 năm kinh nghiệm.

---

## Câu 3

Theo em một Junior và Senior khác nhau ở điểm gì?

### Câu trả lời tốt

Senior không chỉ code tốt hơn.

Senior còn phải:

- Estimate chính xác
- Hỗ trợ member khác
- Chủ động phát hiện vấn đề
- Đề xuất giải pháp
- Chịu trách nhiệm feature

---

## Câu 4

Nếu estimate 3 ngày nhưng làm đến ngày thứ 2 phát hiện không kịp, em làm gì?

### Câu trả lời tốt

```text
1. Xác định nguyên nhân
2. Đánh giá lại thời gian
3. Báo PM/Leader ngay
4. Đề xuất estimate mới
5. Đề xuất phương án giảm scope nếu cần
```

### Điều muốn nghe

Ứng viên biết báo sớm.

### Red Flag

```text
Cố làm đến deadline rồi mới báo.
```

---

## Câu 5

Leader nghỉ phép.
Khách Nhật báo bug production nghiêm trọng.

Em xử lý thế nào?

### Câu trả lời tốt

```text
1. Thu thập thông tin bug
2. Xác định mức độ ảnh hưởng
3. Reproduce
4. Tìm nguyên nhân
5. Đưa ra hướng fix
6. Update liên tục cho PM
```

### Điều muốn nghe

Ownership.

Không phụ thuộc hoàn toàn vào leader.

---

# PART 2 - CV DEEP DIVE

# DATING APP NHẬT

## Câu 6

Em hãy mô tả chi tiết flow upload video profile nữ mà em đã làm.

### Câu trả lời tốt

```text
User chọn video
↓
Validate duration
↓
Validate size
↓
Trim video nếu cần
↓
Compress video
↓
Upload lên S3
↓
Backend lưu metadata
↓
Trả URL
↓
Hiển thị profile
```

---

## Sub Question

Tại sao phải compress video?

### Đáp án

Giảm:

- Thời gian upload
- Băng thông
- Chi phí lưu trữ

Ví dụ:

```text
300MB -> 30MB
```

---

## Sub Question

Upload tới 80% thì mất mạng.

Làm sao xử lý?

### Đáp án tốt

Nếu upload đơn giản:

```text
Retry toàn bộ
```

Nếu upload lớn:

```text
Multipart Upload
Resume Upload
```

Android:

```text
WorkManager
Foreground Service
```

---

## Sub Question

Tại sao dùng WorkManager?

### Đáp án

WorkManager:

- Chạy background
- Tự retry
- App kill vẫn chạy tiếp

---

# IAP

## Câu 7

Mô tả flow thanh toán Google Play Billing.

### Câu trả lời tốt

```text
User bấm mua
↓
Google Billing
↓
Google trả Purchase Token
↓
Client gửi token lên Backend
↓
Backend verify với Google
↓
Backend cấp quyền
↓
Client acknowledge purchase
```

---

## Sub Question

Purchase Token là gì?

### Đáp án

Chuỗi định danh giao dịch do Google tạo.

Ví dụ:

```text
abcd123456xyz
```

---

## Sub Question

Tại sao backend phải verify?

### Đáp án

Không trust client.

Client có thể:

- Root
- Hook
- Fake response

---

## Sub Question

Nếu backend cấp item trước khi verify thì sao?

### Đáp án

Có thể bị fraud.

User nhận item miễn phí.

---

# PLAY CONSOLE

## Câu 8

Em từng gặp reject app chưa?

### Câu trả lời tốt

Ví dụ:

```text
Dating Policy
UGC Policy
Privacy Policy
Target API
```

---

## Sub Question

Dating App cần những chức năng gì để pass policy?

### Đáp án

```text
Report User
Block User
Terms
Privacy Policy
Age Restriction
```

---

## Sub Question

Nếu Google suspend app?

### Đáp án

```text
Đọc policy
Fix issue
Appeal
Resubmit
```

---

# PART 3 - ANDROID TECHNICAL

## Câu 9

MVVM gồm những thành phần nào?

### Đáp án

```text
View
ViewModel
Model
```

---

### Vai trò

#### View

```text
Hiển thị UI
```

#### ViewModel

```text
Xử lý state
```

#### Model

```text
Data
Repository
API
DB
```

---

## Sub Question

Tại sao không gọi API trực tiếp trong Activity?

### Đáp án

Vi phạm:

```text
Single Responsibility
```

Khó test.

Khó maintain.

---

# COROUTINE

## Câu 10

launch và async khác nhau thế nào?

### Đáp án

### launch

```kotlin
launch {
}
```

Trả:

```text
Job
```

Không có kết quả.

---

### async

```kotlin
async {
}
```

Trả:

```text
Deferred<T>
```

Có kết quả.

---

## Sub Question

Khi nào dùng async?

### Đáp án

Chạy song song.

Ví dụ:

```kotlin
API User
API Product
```

---

# HILT

## Câu 11

Dependency Injection là gì?

### Đáp án

Không tự tạo dependency.

Được inject từ bên ngoài.

Ví dụ:

Sai:

```kotlin
val repo = UserRepository()
```

Đúng:

```kotlin
@Inject
lateinit var repo: UserRepository
```

---

## Sub Question

Lợi ích?

### Đáp án

```text
Dễ test
Dễ maintain
Dễ replace implementation
```

---

# PART 4 - PROBLEM SOLVING

## Câu 12

Android 14 crash.
Android 13 bình thường.

Em làm gì đầu tiên?

### Đáp án tốt

```text
Crashlytics
↓
Stacktrace
↓
Reproduce
↓
Fix
```

---

## Sub Question

Nếu không reproduce được?

### Đáp án

Thu thập thêm:

```text
Device
OS
Log
User Flow
```

---

## Câu 13

App bị lag khi scroll RecyclerView.

Em kiểm tra gì?

### Đáp án

```text
DiffUtil
Image Loading
Nested RecyclerView
Main Thread
notifyDataSetChanged
```

---

# PART 5 - LEAD POTENTIAL

## Câu 14

Nếu có 1 fresher mới vào team.

Tuần đầu em sẽ hỗ trợ gì?

### Đáp án tốt

```text
Setup project
Git workflow
Coding convention
Architecture
Task nhỏ
Review code
```

---

## Câu 15

Theo em một developer giỏi nhất là người như thế nào?

### Câu trả lời tốt

Không phải code nhanh nhất.

Mà là:

- Giải quyết vấn đề
- Chịu trách nhiệm
- Chủ động
- Hỗ trợ team

---

# ĐÁNH GIÁ

## Strong Hire

Ứng viên trả lời tốt:

- Upload video
- S3
- IAP
- Play Policy
- Crash Production
- Ownership

## Hire

Android tốt nhưng ownership trung bình.

## No Hire

Không giải thích được:

- Feature trong CV
- IAP
- Upload flow
- Play Policy
- Production Issue
