# Hướng dẫn cài đặt Graphhopper
## Yêu cầu:
### 1. jdk 8 trở lên:

Sử dụng lệnh `java -vesion` để kiểm tra.

Nếu đã cài đặt thì kết quả sẽ có dạng:
```bash
openjdk 10.0.2 2018-07-17
OpenJDK Runtime Environment (build 10.0.2+13-Ubuntu-1ubuntu0.18.04.4)
OpenJDK 64-Bit Server VM (build 10.0.2+13-Ubuntu-1ubuntu0.18.04.4, mixed mode)
````
Nếu chưa cài đặt, dùng lệnh sau để cài đặt openjdk-8-jre trong ubuntu:
```bash
sudo apt install openjdk-8-jre-headless
```

Kiểm tra lại với `java -vesion`

### 2. Git

Sử dụng lệnh `git --version` để kiểm tra **git** đã được cài đặt hay chưa.

Nếu **git** đã được cài đặt kết quả sẽ như sau:
```bash
git version 2.17.1
```

Nếu chưa được cài đặt đầu tiên, sử dụng các công cụ quản lý gói apt để cập nhật chỉ mục gói nội bộ của bạn. Với bản cập nhật hoàn tất, bạn có thể tải xuống và cài đặt Git:

```bash
sudo apt update
sudo apt install git
```

Kiểm tra lại với `git --version` để chắc chắn bạn đã cài đặt thành công
