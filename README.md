# Android Junior Interview Guide (Phiên bản chi tiết)

## Câu 1: MVVM là gì?

### Đáp án mong đợi

MVVM là một kiến trúc giúp tách giao diện người dùng khỏi phần xử lý logic và dữ liệu.

Bao gồm:

### View

Là Activity, Fragment hoặc Compose UI.

Nhiệm vụ:

* Hiển thị dữ liệu
* Nhận thao tác từ người dùng

Không nên chứa business logic.

---

### ViewModel

Là nơi xử lý logic liên quan đến giao diện.

Ví dụ:

* Gọi repository
* Xử lý dữ liệu trước khi hiển thị
* Quản lý state của màn hình

ViewModel có thể tồn tại khi xoay màn hình nên dữ liệu không bị mất.

---

### Repository

Là tầng trung gian giữa ViewModel và Data Source.

Nhiệm vụ:

* Gọi API
* Gọi Room Database
* Quyết định lấy dữ liệu từ local hay remote

---

### Data Source

Nguồn dữ liệu thực tế.

Ví dụ:

* REST API
* Room Database
* SharedPreferences

---

### Câu hỏi đào sâu

#### Tại sao không gọi API trực tiếp trong Activity?

Đáp án:

Nếu gọi API trong Activity:

* Code khó bảo trì
* Khó test
* Activity chứa quá nhiều logic

Ví dụ:

```kotlin
button.setOnClickListener {
    api.getUser()
}
```

Khi màn hình lớn lên:

* API
* Validation
* Business logic

đều nằm trong Activity.

Đây là anti-pattern.

---

#### Tại sao Repository lại cần thiết?

Đáp án:

Giả sử hôm nay dữ liệu lấy từ API.

Ngày mai yêu cầu:

* Cache dữ liệu
* Offline mode

Nếu không có Repository:

Toàn bộ ViewModel phải sửa.

Nếu có Repository:

Chỉ cần sửa Repository.

ViewModel không cần biết dữ liệu đến từ đâu.

---

## Câu 2: Coroutine là gì?

### Đáp án mong đợi

Coroutine là cơ chế xử lý bất đồng bộ của Kotlin.

Mục đích:

* Tránh block UI Thread
* Thực hiện tác vụ dài như API hoặc Database

Ví dụ:

```kotlin
viewModelScope.launch {
    val users = repository.getUsers()
}
```

Trong lúc API chạy:

* UI vẫn hoạt động
* Người dùng vẫn bấm được

---

### Tại sao không dùng Thread?

Đáp án:

Thread:

* Tốn bộ nhớ
* Quản lý khó
* Dễ leak

Coroutine:

* Nhẹ hơn
* Dễ đọc
* Dễ cancel

---

### launch và async khác nhau thế nào?

launch:

```kotlin
viewModelScope.launch {
}
```

Dùng khi không cần trả về kết quả.

Trả về:

```kotlin
Job
```

---

async:

```kotlin
viewModelScope.async {
}
```

Dùng khi cần nhận kết quả.

Trả về:

```kotlin
Deferred<T>
```

Ví dụ:

```kotlin
val user = async {
    api.getUser()
}

val result = user.await()
```

---

### Khi nào dùng async?

Ví dụ:

Màn hình Home cần:

* User Info
* Notification
* Banner

Có thể gọi song song:

```kotlin
val user = async { getUser() }
val banner = async { getBanner() }
val notify = async { getNotify() }
```

Giúp giảm thời gian chờ.

---

## Câu 3: StateFlow là gì?

### Đáp án mong đợi

StateFlow là nơi lưu trữ trạng thái hiện tại của màn hình.

Ví dụ:

```kotlin
data class HomeUiState(
    val loading: Boolean = false,
    val users: List<User> = emptyList()
)
```

```kotlin
private val _state =
    MutableStateFlow(HomeUiState())
```

UI sẽ observe StateFlow.

Khi state thay đổi:

UI tự động cập nhật.

---

### Tại sao StateFlow phải có giá trị khởi tạo?

Đáp án:

Vì StateFlow luôn đại diện cho trạng thái hiện tại.

Nó không bao giờ được phép rỗng.

Ví dụ:

```kotlin
MutableStateFlow(HomeUiState())
```

Luôn có state đầu tiên.

---

### StateFlow và SharedFlow khác nhau thế nào?

StateFlow:

Dùng cho state.

Ví dụ:

* Loading
* User Info
* Product List

---

SharedFlow:

Dùng cho event.

Ví dụ:

* Toast
* Snackbar
* Navigate

---

### Tại sao Snackbar không nên dùng StateFlow?

Ví dụ:

```kotlin
state.message = "Login Success"
```

Khi xoay màn hình:

State vẫn tồn tại.

Snackbar có thể hiện lại lần nữa.

Đây là bug.

Snackbar là event.

Nên dùng SharedFlow.

---

## Câu 4: Crash trên Production

### Khách hàng báo app crash.

Em làm gì?

### Đáp án mong đợi

Bước 1:

Xem Crashlytics.

Thu thập:

* Device
* Android Version
* Stacktrace
* App Version

---

Bước 2:

Đọc Stacktrace.

Ví dụ:

```text
NullPointerException
User.name
```

=> Có thể User bị null.

---

Bước 3:

Reproduce.

Tìm cách tái hiện bug.

Ví dụ:

* Android 14
* Login bằng tài khoản mới

---

Bước 4:

Fix.

---

Bước 5:

Regression Test.

Kiểm tra các màn hình liên quan.

---

### Nếu không reproduce được?

Đáp án:

* Thêm log
* Review code
* So sánh các device bị crash
* Theo dõi Crashlytics tiếp

Không được fix đoán mò.

---

## Câu 5: Estimate bị trễ

Estimate:

2 ngày

Ngày thứ 2 vẫn chưa xong.

Em làm gì?

### Đáp án mong đợi

Không được im lặng.

Cần:

1. Báo leader ngay

2. Nêu phần đã hoàn thành

Ví dụ:

```text
UI: 100%
API: 80%
Testing: chưa làm
```

3. Giải thích nguyên nhân

Ví dụ:

```text
API thay đổi
Requirement chưa rõ
```

4. Đề xuất estimate mới

Ví dụ:

```text
Cần thêm 1 ngày
```

---

### Tại sao đây là đáp án đúng?

Trong môi trường Nhật:

Điều quan trọng nhất không phải là trễ.

Điều quan trọng nhất là:

* Minh bạch
* Báo sớm
* Chủ động

Nếu đợi tới deadline mới báo:

Đó là dấu hiệu quản lý công việc kém.
