# Bộ câu hỏi phỏng vấn Android Junior (1-3 năm kinh nghiệm)

## Mục tiêu tuyển dụng

- Android Developer Junior
- Có thể làm việc độc lập
- Phù hợp môi trường khách hàng Nhật
- Có tư duy ownership
- Có tiềm năng hướng dẫn fresher trong tương lai

**Thời gian:** 60 phút

---

# PHẦN 1 - KINH NGHIỆM DỰ ÁN & OWNERSHIP (20 điểm)

## Câu 1: Hãy giới thiệu dự án gần nhất của em

### Kỳ vọng

Ứng viên trình bày được:

- Domain dự án
- Team size
- Vai trò
- Công nghệ sử dụng

Ví dụ:

> Em tham gia dự án mạng xã hội khoảng 25 thành viên.
> Em phụ trách chat, notification và video call.
> Công nghệ: Kotlin, MVVM, Retrofit, Firebase, Twilio.

---

### Câu hỏi đào sâu 1

Feature nào em tự làm từ đầu đến cuối?

### Câu trả lời tốt

Ứng viên mô tả được:

- Requirement
- Thiết kế giải pháp
- API sử dụng
- Test
- Release

### Dấu hiệu fail

> Em chỉ fix bug.

---

### Câu hỏi đào sâu 2

Em estimate task như thế nào?

### Câu trả lời tốt

> Em chia task thành:
>
> - UI
> - API
> - Business logic
> - Test
>
> Sau đó estimate từng phần.

### Dấu hiệu fail

> Leader estimate sẵn.

---

### Câu hỏi đào sâu 3

Bug khó nhất em từng xử lý là gì?

### Kỳ vọng

Ứng viên trình bày được:

- Hiện tượng
- Cách điều tra
- Nguyên nhân gốc
- Giải pháp
- Bài học rút ra

### Dấu hiệu fail

Không xác định được root cause.

---

# PHẦN 2 - KIẾN THỨC ANDROID CƠ BẢN (20 điểm)

## Câu 2: MVVM là gì?

### Câu trả lời mong đợi

MVVM gồm:

- View
- ViewModel
- Repository
- Data Source

Flow:

```text
UI
↓
ViewModel
↓
Repository
↓
API / Database
```

---

### Câu hỏi đào sâu 1

Tại sao cần ViewModel?

### Câu trả lời tốt

- Tách UI và business logic
- Giữ state khi xoay màn hình
- Dễ test

---

### Câu hỏi đào sâu 2

ViewModel có nên gọi Retrofit trực tiếp không?

### Câu trả lời tốt

Không nên.

```text
ViewModel
↓
Repository
↓
API
```

Lý do:

- Dễ test
- Dễ maintain
- Tách trách nhiệm rõ ràng

---

### Câu hỏi đào sâu 3

Nếu vừa có API vừa có Room thì xử lý thế nào?

### Câu trả lời tốt

Repository quyết định nguồn dữ liệu.

Ví dụ:

```text
1. Load từ Room
2. Gọi API
3. Save vào Room
4. UI observe Room
```

---

### Câu hỏi đào sâu 4

Trong dự án của em có những Repository nào?

### Câu trả lời tốt

Ví dụ:

- AuthRepository
- UserRepository
- ProductRepository

Ứng viên phải trả lời theo dự án thực tế.

---

## Câu 3: Coroutine là gì?

### Câu trả lời mong đợi

Coroutine là giải pháp xử lý bất đồng bộ.

Ưu điểm:

- Không block UI
- Nhẹ hơn Thread
- Dễ đọc hơn callback

---

### Câu hỏi đào sâu 1

launch và async khác nhau thế nào?

### Câu trả lời tốt

launch:

```kotlin
viewModelScope.launch {}
```

Trả về:

```kotlin
Job
```

async:

```kotlin
viewModelScope.async {}
```

Trả về:

```kotlin
Deferred<T>
```

---

### Câu hỏi đào sâu 2

Khi nào dùng async?

### Câu trả lời tốt

Khi cần return dữ liệu.

Ví dụ:

```kotlin
val user = async { api.getUser() }
val products = async { api.getProducts() }

await()
```

---

### Câu hỏi đào sâu 3

viewModelScope là gì?

### Câu trả lời tốt

Coroutine scope gắn với ViewModel.

Khi ViewModel bị clear:

```text
Coroutine tự cancel
```

---

### Câu hỏi đào sâu 4

viewModelScope và lifecycleScope khác nhau thế nào?

### Câu trả lời tốt

viewModelScope

- Sống theo ViewModel

lifecycleScope

- Sống theo Activity hoặc Fragment

---

## Câu 4: StateFlow là gì?

### Câu trả lời mong đợi

StateFlow là nơi lưu trữ state hiện tại.

Ví dụ:

```kotlin
private val _state =
    MutableStateFlow(UiState())
```

---

### Câu hỏi đào sâu 1

Tại sao StateFlow phải có initial value?

### Câu trả lời tốt

Vì StateFlow luôn có state hiện tại.

---

### Câu hỏi đào sâu 2

StateFlow và SharedFlow khác nhau thế nào?

### Câu trả lời tốt

StateFlow

- Có giá trị hiện tại
- Bắt buộc initial value

SharedFlow

- Dùng cho event
- Không bắt buộc initial value

---

### Câu hỏi đào sâu 3

Snackbar nên dùng gì?

### Câu trả lời tốt

SharedFlow

Vì Snackbar là event.

---

### Câu hỏi đào sâu 4

Loading nên dùng gì?

### Câu trả lời tốt

StateFlow

Vì Loading là state.

---

### Câu hỏi đào sâu 5

StateFlow khác LiveData thế nào?

### Câu trả lời tốt

StateFlow

- Kotlin native
- Hỗ trợ Compose tốt hơn

LiveData

- Lifecycle aware
- Android specific

---

# PHẦN 3 - THỰC CHIẾN ANDROID (20 điểm)

## Câu 5: Thiết kế màn hình Product List

API:

```json
[
  {
    "id": 1,
    "name": "Iphone",
    "price": 1000
  }
]
```

---

### Kỳ vọng

```text
data/
domain/
presentation/
```

Hoặc Clean Architecture.

---

### Câu hỏi đào sâu 1

Model đặt ở đâu?

### Câu trả lời tốt

- domain/model
hoặc
- data/model

Tuỳ kiến trúc.

---

### Câu hỏi đào sâu 2

Loading xử lý thế nào?

### Câu trả lời tốt

```kotlin
sealed class UiState {
    object Loading
    data class Success(...)
    data class Error(...)
}
```

---

### Câu hỏi đào sâu 3

Error xử lý thế nào?

### Câu trả lời tốt

- Hiển thị message
- Retry
- Log lỗi nếu cần

---

### Câu hỏi đào sâu 4

Pull To Refresh làm thế nào?

### Câu trả lời tốt

- Gọi lại API
- Update state
- Hiển thị loading

---

## Câu 6: Production bị crash

Khách hàng báo app crash.

Em xử lý thế nào?

### Câu trả lời tốt

```text
1. Xem Crashlytics
2. Đọc Stacktrace
3. Reproduce
4. Fix
5. Regression Test
```

---

### Câu hỏi đào sâu 1

Thông tin nào quan trọng?

### Câu trả lời tốt

- Device
- Android version
- App version
- Stacktrace

---

### Câu hỏi đào sâu 2

Không reproduce được thì sao?

### Câu trả lời tốt

- Thêm log
- Kiểm tra code path
- Phân tích Crashlytics

---

### Câu hỏi đào sâu 3

Crashlytics là gì?

### Câu trả lời tốt

Công cụ theo dõi crash của Firebase.

Cung cấp:

- Stacktrace
- Device info
- Tần suất crash

---

## Câu 7: App bị lag

App lag khi scroll 500 item.

Em kiểm tra gì?

### Câu trả lời tốt

- RecyclerView
- Image loading
- Main Thread
- Memory

---

### Câu hỏi đào sâu 1

DiffUtil là gì?

### Câu trả lời tốt

Tính toán sự khác biệt của list.

Tránh notifyDataSetChanged toàn bộ.

---

### Câu hỏi đào sâu 2

Paging là gì?

### Câu trả lời tốt

Load dữ liệu từng phần.

Không load toàn bộ cùng lúc.

---

### Câu hỏi đào sâu 3

Kiểm tra Main Thread block thế nào?

### Câu trả lời tốt

- Android Profiler
- StrictMode
- Log

---

# PHẦN 4 - LIVE CODING (15 điểm)

## Câu 8

Cho:

```kotlin
data class User(
    val id: Int,
    val name: String,
    val age: Int
)
```

```kotlin
val users = listOf(
    User(1, "A", 18),
    User(2, "B", 22),
    User(3, "C", 25),
    User(4, "D", 17)
)
```

---

### Yêu cầu 1

Lấy danh sách user >= 18 tuổi

### Đáp án

```kotlin
val result =
    users.filter {
        it.age >= 18
    }
```

---

### Yêu cầu 2

Sort giảm dần theo tuổi

### Đáp án

```kotlin
val result =
    users.sortedByDescending {
        it.age
    }
```

---

### Yêu cầu 3

Trả về danh sách tên

### Đáp án

```kotlin
val names =
    users.map {
        it.name
    }
```

---

### Câu hỏi đào sâu 1

filter và map khác nhau thế nào?

### Câu trả lời tốt

filter

- Lọc dữ liệu

map

- Chuyển đổi dữ liệu

---

### Câu hỏi đào sâu 2

map và forEach khác nhau thế nào?

### Câu trả lời tốt

map

- Trả về list mới

forEach

- Chỉ duyệt

---

# PHẦN 5 - MINDSET & KHÁCH HÀNG NHẬT (25 điểm)

## Câu 9

Estimate 2 ngày.

Ngày thứ 2 vẫn chưa xong.

Em làm gì?

### PASS

- Báo leader sớm
- Nêu rõ blocker
- Đề xuất estimate mới

### FAIL

> Em cố làm thêm vài ngày rồi báo.

---

### Câu hỏi đào sâu

Khi nào nên báo risk?

### Câu trả lời tốt

Ngay khi phát hiện risk.

Không đợi tới deadline.

---

## Câu 10

Nhận task nhưng không hiểu requirement.

Em làm gì?

### PASS

1. Đọc tài liệu
2. Tìm hiểu code cũ
3. Tự điều tra
4. Tổng hợp câu hỏi
5. Hỏi BA hoặc Leader

### FAIL

> Code trước rồi sửa sau.

---

## Câu 11

Fresher hỏi em một bug mà em không biết.

Em xử lý sao?

### PASS

- Cùng phân tích
- Hướng dẫn debug
- Escalate nếu cần

### FAIL

> Em sửa hộ luôn.

---

### Câu hỏi đào sâu

Em mentor fresher như thế nào?

### Câu trả lời tốt

- Dạy cách tư duy
- Dạy cách debug
- Không đưa đáp án ngay

---

## Câu 12

Leader nghỉ phép.

Production bug xuất hiện.

Em làm gì?

### PASS

1. Thu thập thông tin
2. Đánh giá ảnh hưởng
3. Báo team
4. Đề xuất hướng xử lý
5. Theo dõi tới khi fix xong

---

### Câu hỏi đào sâu

Khách hàng hỏi tiến độ xử lý bug.

Em trả lời sao?

### Câu trả lời tốt

> Đã xác định phạm vi ảnh hưởng.
>
> Đang điều tra nguyên nhân.
>
> Sẽ cập nhật tiến độ tiếp theo sau X giờ.

### FAIL

> Đang kiểm tra.

---

# THANG ĐIỂM

| Mục | Điểm |
|------|------:|
| Kinh nghiệm dự án | 20 |
| Android Foundation | 20 |
| Android Practical | 20 |
| Live Coding | 15 |
| Mindset & Communication | 25 |
| Tổng | 100 |

# ĐÁNH GIÁ

- 85+ : Strong Hire
- 75-84 : Hire
- 65-74 : Consider
- <65 : Reject
