# INTERVIEW GUIDE – NGUYEN THI DIEP

## Thông tin ứng viên

- 2 năm kinh nghiệm Android
- Digo IoT
- Smart Home
- Fire Safety
- MQTT
- BLE
- Firebase
- Coroutines
- Flow
- StateFlow
- MVVM
- Clean Architecture
- Google Play Console
- React Native (Midu Balance)

---

# PART 1 - OPENING & MINDSET

## Câu 1

Em hãy giới thiệu về bản thân và hành trình trở thành Android Developer.

### Kỳ vọng

Ứng viên trình bày được:

- Học Information Systems tại HaUI
- Bắt đầu Android khi nào
- Tại sao chọn Android
- Hiện tại đang làm gì

---

## Câu 2

Trong các dự án đã làm, em tự hào nhất dự án nào?

### Kỳ vọng

Ứng viên nên chọn:

```text
Digo Smart Home
```

hoặc

```text
Fire Safety
```

vì đây là những dự án có độ khó cao nhất.

---

## Câu 3

Theo em điều khó nhất khi làm IoT là gì?

### Đáp án tốt

```text
Realtime
Thiết bị không ổn định
Network không ổn định
Khó reproduce bug
```

---

## Câu 4

Nếu khách Nhật báo bug nhưng em chưa tìm được nguyên nhân.

Em xử lý thế nào?

### Đáp án tốt

```text
Thu thập thêm thông tin
Khoanh vùng nguyên nhân
Update tiến độ liên tục
Không im lặng
```

---

## Câu 5

Nếu có một task em chưa từng làm.

Em sẽ xử lý như thế nào?

### Đáp án tốt

```text
Đọc document
POC
Trao đổi team
Estimate sau khi hiểu vấn đề
```

### Red Flag

```text
Đợi leader hướng dẫn hết
```

---

# PART 2 - CV DEEP DIVE

# BLE

## Câu 6

Em mô tả toàn bộ flow BLE từ lúc tìm thiết bị tới lúc nhận dữ liệu.

### Đáp án

```text
Scan
↓
Connect
↓
Discover Services
↓
Discover Characteristics
↓
Read/Write
↓
Notify
```

---

## Sub Question

Service là gì?

### Đáp án

Service là nhóm chức năng của thiết bị.

Ví dụ:

```text
Heart Rate Service
Battery Service
Device Info Service
```

---

## Sub Question

Characteristic là gì?

### Đáp án

Nơi chứa dữ liệu thực tế.

Ví dụ:

```text
Battery Level
Heart Rate Value
Temperature Value
```

---

## Sub Question

Tại sao phải Discover Services?

### Đáp án

Android cần biết:

```text
Thiết bị hỗ trợ chức năng gì
Đọc dữ liệu ở đâu
Ghi dữ liệu ở đâu
```

---

## Sub Question

BLE Disconnect liên tục.

Em debug như thế nào?

### Đáp án tốt

Kiểm tra:

```text
RSSI
Distance
Battery thiết bị
Firmware
Android Version
Permission
Timeout
```

---

## Sub Question

BLE khác Bluetooth Classic thế nào?

### Đáp án

### BLE

```text
Tiết kiệm pin
Data nhỏ
Realtime
```

### Classic

```text
Data lớn
Audio
File Transfer
```

---

# MQTT

## Câu 7

MQTT là gì?

### Đáp án

MQTT là protocol realtime sử dụng mô hình:

```text
Publish
Subscribe
```

phù hợp cho IoT.

---

## Sub Question

MQTT hoạt động như thế nào?

### Đáp án

```text
Device
↓
Broker
↓
Mobile App
```

Ví dụ:

```text
Sensor gửi dữ liệu
↓
MQTT Broker
↓
Android nhận dữ liệu
```

---

## Sub Question

Broker là gì?

### Đáp án

Server trung gian.

Ví dụ:

```text
EMQX
Mosquitto
HiveMQ
```

---

## Sub Question

Publish là gì?

### Đáp án

```text
Gửi dữ liệu
```

Ví dụ:

```json
{
  "temperature": 35
}
```

---

## Sub Question

Subscribe là gì?

### Đáp án

```text
Lắng nghe dữ liệu
```

---

## Sub Question

Topic là gì?

### Đáp án

Địa chỉ dữ liệu MQTT.

Ví dụ:

```text
home/livingroom/temp
```

---

# QoS

## Câu 8

QoS là gì?

### Đáp án

Quality of Service.

---

### QoS 0

```text
At most once
```

Có thể mất dữ liệu.

Nhanh nhất.

---

### QoS 1

```text
At least once
```

Có thể nhận trùng.

---

### QoS 2

```text
Exactly once
```

Chậm nhất.

An toàn nhất.

---

## Sub Question

Fire Alarm nên dùng QoS nào?

### Đáp án

QoS 1 hoặc QoS 2.

Không được mất dữ liệu.

---

## Sub Question

Tại sao không dùng QoS 0?

### Đáp án

Có thể mất cảnh báo cháy.

---

# SMART HOME

## Câu 9

Nếu user bật đèn trên app nhưng đèn không sáng.

Em debug thế nào?

### Đáp án tốt

```text
Kiểm tra MQTT message
↓
Kiểm tra Broker
↓
Kiểm tra Device
↓
Kiểm tra ACK
```

---

## Follow-up

Làm sao biết lỗi ở app hay thiết bị?

### Đáp án

Dùng:

```text
MQTT Explorer
MQTTX
Backend Log
```

---

# COROUTINE / FLOW

## Câu 10

Tại sao dự án IoT lại dùng Flow hoặc StateFlow?

### Đáp án

Vì dữ liệu realtime.

Ví dụ:

```text
Nhiệt độ
Trạng thái thiết bị
Cảnh báo
```

liên tục thay đổi.

---

## Sub Question

Flow khác LiveData thế nào?

### Đáp án

### LiveData

```text
Lifecycle Aware
Android Only
```

### Flow

```text
Coroutine Based
Linh hoạt hơn
```

---

## Sub Question

StateFlow khác SharedFlow thế nào?

### Đáp án

### StateFlow

Luôn có:

```text
Current State
```

Ví dụ:

```text
Connected
Disconnected
```

---

### SharedFlow

Dùng cho Event.

Ví dụ:

```text
Show Toast
Navigate
```

---

# FIREBASE

## Câu 11

Firebase Crashlytics dùng để làm gì?

### Đáp án

Thu thập:

```text
Crash
Stacktrace
Device Info
OS Version
```

---

## Sub Question

Một crash xuất hiện trên 2 máy trong 10.000 user.

Có fix không?

### Đáp án

Có.

Đặc biệt:

```text
Crash production
Payment
Login
Fire Alarm
```

---

# GOOGLE PLAY CONSOLE

## Câu 12

Em từng release app lên Play Store.

Cho anh mô tả quy trình release.

### Đáp án

```text
Build Release
↓
Upload AAB
↓
Internal Testing
↓
Closed Testing
↓
Production
```

---

## Sub Question

Tại sao phải dùng Closed Testing?

### Đáp án

Kiểm tra trước khi phát hành thật.

Giảm rủi ro.

---

# PART 3 - PROBLEM SOLVING

## Câu 13

1000 thiết bị gửi dữ liệu liên tục.

App bắt đầu lag.

Em xử lý thế nào?

### Đáp án tốt

```text
Background Thread
Flow
Buffer
Throttle
Debounce
```

---

## Follow-up

Nếu UI update 100 lần/giây thì sao?

### Đáp án

Không render tất cả.

Ví dụ:

```text
Render mỗi 500ms
```

---

## Câu 14

App bị memory leak.

Em điều tra thế nào?

### Đáp án

```text
LeakCanary
Memory Profiler
Heap Dump
```

---

# PART 4 - LEAD POTENTIAL

## Câu 15

Nếu một Fresher mới vào team.

Em sẽ hướng dẫn gì đầu tiên?

### Đáp án tốt

```text
Architecture
Git Flow
Coding Convention
Project Structure
```

---

## Câu 16

Theo em developer giỏi nhất là người như thế nào?

### Đáp án tốt

Không phải code nhanh nhất.

Mà là:

```text
Giải quyết vấn đề
Ownership
Tự học
Hỗ trợ team
```

---

# CÂU HỎI CHỐT

## Câu 17

Nếu hôm nay em được giao làm Team Lead của dự án Smart Home.

Điều đầu tiên em sẽ làm là gì?

### Đáp án tốt

```text
Hiểu hệ thống
Hiểu member
Hiểu deadline
Chia task
Quản lý rủi ro
```

---

# THANG ĐIỂM

## Strong Hire

- BLE thật
- MQTT thật
- Hiểu QoS
- Hiểu Broker
- Có ownership khi debug thiết bị

## Hire

- Android tốt
- BLE cơ bản
- MQTT cơ bản

## No Hire

- Không giải thích được:
  - Service/Characteristic
  - MQTT Broker
  - QoS
  - Flow/StateFlow

=> Rất có thể chỉ làm UI hoặc CRUD.
