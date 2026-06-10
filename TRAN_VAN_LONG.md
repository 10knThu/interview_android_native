# INTERVIEW GUIDE – TRAN VAN LONG

## Thông tin ứng viên

- 2+ năm kinh nghiệm Android
- FPT Software
- iPos23 - RefApp
- STERAPOS
- Kotlin
- MVVM
- Coroutines
- Room DB
- Jetpack Compose
- Android Test 80% Coverage
- Code Review
- Support Member
- Documentation

---

# PART 1 - OPENING & MINDSET

## Câu 1

Em hãy giới thiệu ngắn gọn về bản thân và hành trình trở thành Android Developer.

### Kỳ vọng

Ứng viên trình bày:

- Học Automation tại HUST
- Chuyển sang Android
- Kinh nghiệm FPT
- Các dự án chính

### Điều muốn đánh giá

- Kỹ năng giao tiếp
- Khả năng trình bày
- Mức độ tự tin

---

## Câu 2

Trong các dự án đã làm, em tự hào nhất dự án nào?

### Follow-up

Tại sao?

### Đáp án tốt

Ứng viên chọn:

```text
STERAPOS
```

Vì:

- Dự án lớn hơn
- Có migrate code
- Có Android Test
- Có review code
- Có support member

---

## Câu 3

Theo em điểm mạnh nhất của em là gì?

### Đáp án tốt

Ví dụ:

```text
Khả năng học nhanh
Khả năng hỗ trợ team
Khả năng maintain hệ thống lớn
```

### Red Flag

```text
Em code nhanh.
```

---

## Câu 4

Nếu estimate 5 ngày nhưng sau 2 ngày phát hiện không kịp.

Em làm gì?

### Đáp án tốt

```text
Xác định nguyên nhân
Đánh giá lại estimate
Thông báo sớm cho PM
Đề xuất phương án
```

### Red Flag

```text
Đợi tới deadline rồi mới báo.
```

---

## Câu 5

Theo em một Senior khác Junior ở điểm nào?

### Đáp án tốt

Không phải code nhanh hơn.

Mà là:

```text
Ownership
Estimate
Review Code
Support Team
Design Solution
```

---

# PART 2 - CV DEEP DIVE

# STERAPOS

## Câu 6

Em mô tả kiến trúc tổng thể của dự án STERAPOS.

### Kỳ vọng

Ứng viên mô tả được:

```text
Presentation
↓
ViewModel
↓
Repository
↓
Remote / Local
```

---

## Sub Question

Tại sao dùng MVVM?

### Đáp án

```text
Tách UI và Business Logic
Dễ maintain
Dễ test
```

---

## Sub Question

Nếu ViewModel dài 2000 dòng.

Em xử lý thế nào?

### Đáp án

Tách:

```text
UseCase
Manager
Repository
```

---

# JAVA -> KOTLIN MIGRATION

## Câu 7

CV ghi migrate Java sang Kotlin.

Em mô tả quá trình migrate.

### Đáp án tốt

```text
Convert bằng Android Studio
↓
Review code
↓
Refactor Kotlin Style
↓
Test lại
```

---

## Sub Question

Android Studio convert có hoàn hảo không?

### Đáp án

Không.

Thường gặp:

```text
Nullable sai
Code xấu
Nhiều !!
```

---

## Sub Question

Ví dụ lỗi thường gặp nhất khi migrate?

### Đáp án

```kotlin
String?
```

và

```kotlin
String
```

Dễ gây:

```text
NullPointerException
```

---

# COMPOSE

## Câu 8

Compose Recomposition là gì?

### Đáp án

Compose sẽ render lại UI khi state thay đổi.

Ví dụ:

```kotlin
mutableStateOf()
```

thay đổi

↓

Compose redraw UI.

---

## Sub Question

Recomposition quá nhiều gây vấn đề gì?

### Đáp án

```text
Lag
Giật
Tốn CPU
Tốn pin
```

---

## Sub Question

Làm sao giảm Recomposition?

### Đáp án

```kotlin
remember()
rememberSaveable()
derivedStateOf()
```

---

## Sub Question

Khi nào dùng rememberSaveable?

### Đáp án

Khi:

```text
Rotate Screen
Process Recreation
```

vẫn muốn giữ dữ liệu.

---

# ROOM DATABASE

## Câu 9

Room hoạt động như thế nào?

### Đáp án

Gồm:

```text
Entity
DAO
Database
```

---

### Entity

```kotlin
@Table
```

Đại diện dữ liệu.

---

### DAO

```kotlin
@Query
@Insert
```

Thao tác dữ liệu.

---

### Database

```kotlin
RoomDatabase
```

Quản lý database.

---

## Sub Question

Tại sao dùng Room thay vì SQLite thuần?

### Đáp án

```text
Ít code hơn
Type-safe
Compile-time check
```

---

# PART 3 - UNIT TEST & QUALITY

# Đây là phần quan trọng nhất với ứng viên này

## Câu 10

CV ghi Android Test Coverage 80%.

80% được tính như thế nào?

### Đáp án

Coverage:

```text
Executed Lines
/
Total Lines
```

Thường đo bằng:

```text
Jacoco
```

---

## Sub Question

Coverage 80% nhưng vẫn có bug.

Tại sao?

### Đáp án

Coverage cao không đồng nghĩa test tốt.

Ví dụ:

```text
Business Logic chưa cover
Case đặc biệt chưa cover
```

---

## Sub Question

Những gì em thường test?

### Đáp án

```text
ViewModel
UseCase
Repository
Mapper
```

---

## Sub Question

Những gì KHÔNG nên test?

### Đáp án

```text
Android Framework
Retrofit
Room internal
```

---

# CODE REVIEW

## Câu 11

CV ghi support member và review code.

Khi review code em thường nhìn gì đầu tiên?

### Đáp án tốt

```text
Logic
Crash
Memory Leak
Performance
Coding Convention
```

---

## Sub Question

Một Fresher viết code như sau:

```kotlin
GlobalScope.launch {
}
```

Em review thế nào?

### Đáp án

Không nên dùng.

Lý do:

```text
Không lifecycle-aware
Dễ leak
Khó quản lý
```

Nên dùng:

```kotlin
viewModelScope
lifecycleScope
```

---

## Sub Question

Nếu Fresher liên tục lặp lại lỗi.

Em xử lý sao?

### Đáp án tốt

```text
Pair Programming
Training
Document
Guideline
```

---

# PART 4 - PROBLEM SOLVING

## Câu 12

Khách hàng báo:

```text
POS app bị lag khi thanh toán.
```

Em xử lý thế nào?

### Đáp án tốt

```text
Thu thập log
Reproduce
Profiler
Thread Analysis
```

---

## Follow-up

Nếu API nhanh nhưng UI vẫn lag?

### Đáp án

Kiểm tra:

```text
Main Thread Block
Compose Recomposition
RecyclerView
Animation
```

---

## Câu 13

App crash ngẫu nhiên.

Không reproduce được.

Em làm gì?

### Đáp án tốt

```text
Crashlytics
Stacktrace
Device Info
OS Version
User Flow
```

---

# PART 5 - LEAD POTENTIAL

## Câu 14

Nếu ngày mai em được giao dẫn dắt 1 fresher.

Tuần đầu em sẽ làm gì?

### Đáp án tốt

```text
Setup môi trường
Giới thiệu Architecture
Coding Convention
Git Workflow
Task nhỏ
Review Code
```

---

## Câu 15

Theo em một Lead tốt cần gì?

### Đáp án tốt

Không phải người code giỏi nhất.

Mà là:

```text
Phân chia công việc
Estimate
Mentor
Giải quyết vấn đề
Giao tiếp
```

---

# CÂU HỎI CHỐT

## Câu 16

Trong tất cả những việc em từng làm.

Điều gì khiến em nghĩ mình phù hợp với vị trí Android Developer hơn người khác?

### Điều muốn nghe

Ứng viên nói về:

```text
Tinh thần trách nhiệm
Khả năng học hỏi
Ownership
Khả năng hỗ trợ team
```

Không phải:

```text
Em code nhanh.
```

---

# THANG ĐIỂM

## Strong Hire

- Hiểu Compose sâu
- Hiểu Test thật
- Có tư duy review code
- Có ví dụ mentor thực tế
- Trả lời tốt Ownership

## Hire

- Android tốt
- Compose tốt
- Test cơ bản

## No Hire

- Không giải thích được Coverage 80%
- Không giải thích được Recomposition
- Không có ví dụ support member
- Chỉ trả lời lý thuyết MVVM
