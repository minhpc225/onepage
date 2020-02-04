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

### 3. File web config

https://raw.githubusercontent.com/graphhopper/graphhopper/master/config-example.yml

### 4. File jar

Vào đường link https://oss.sonatype.org/content/groups/public/com/graphhopper/graphhopper-web/1.0-SNAPSHOT/ và tải bản jar mới nhất

### 5. OSM data

Truy cập http://download.geofabrik.de/asia/vietnam.html và download file pbf của khu vực sử dụng

### File config, jar, osm data copy vào thư mục root của graphhopper

## Tiến hành xây dựng web server

Clone source code: 
```bash git clone git://github.com/graphhopper/graphhopper.gitgraphhopper-web-1.0-20200130.134108-163
cd graphhopper; git checkout 0.13
```

Khởi tạo server ví dụ với osm data là `vietnam-lastest.osm.pbf` và jar `graphhopper-web-1.0-20200130.134108-163.jar`:
```bash
java-Dgraphhopper.datareader.file=vietnam-lastest.osm.pbf -jar graphhopper-web-1.0-20200130.134108-163.jar server config-example.yml
```

Server đã được khởi tạo, truy cập http://localhost:8989/maps/ 
