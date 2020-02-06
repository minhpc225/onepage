
## Vehicle(phương tiện)

   ### Lựa chọn phương tiện di chuyển
   
   Sử dụng `graph.flag_encoders`

   Các tùy chọn:
    
   - car: đường di chuyển cho ô tô
   - bike: đường di chuyển cho xe 2 bánh
   - bike 2: đường di chuyển cho xe 2 bánh có sử dụng độ cao ( Cần phải [thêm dữ liệu độ cao][1] vào đồ thị)
   - mtb: xe leo núi
   - racingbike
   - motocycle: xe gắn máy
   - turn_costs: thêm giá trị cho mỗi lần rẽ cho car hoặc motocycle
        vd: `graph.flag_encoders: car|turn_cost=true`
    
   ### Thêm thông tin cho đường phục vụ việc tính toán 
   
   Sửu dụng `graph.encoded_values`
    
   [Mặc định](https://github.com/graphhopper/graphhopper/pull/1548) : road_class,road_class_link,road_environment,max_speed,road_access 
    
   Các thông tin có thể thêm:
    
   - Để nội suy hầm, cầu, xem [tại đây](https://github.com/graphhopper/graphhopper/pull/798)
    
   - surface,max_width,max_height,max_weight,max_axle_load,max_length,hazmat,hazmat_tunnel,hazmat_water,toll,track_type.

   ### Nếu nhiều `graph.flag_encoders` và `graph.encoded_values` được sử dụng `graph.bytes_for_flags` nên được đặt là 8 hoặc hơn( bội của 4)
    
    `graph.bytes_for_flags: 8`

    
## Độ cao(Elevation)

   ### Thêm dữ liệu độ cao vào đồ thị:
    
   [1]: graph.elevation.provider: srtm( mặc định là `graph.elevation.provider: noop`:không sử dụng dữ liệu độ cao)
    
   ### Đặt đường dẫn cho bộ đệm.
   
   Mặc định là `graph.elevation.cache_dir: /tmp/srtm`
    
   ### Nếu ổ cứng tốc độ chậm hoặc có thể sử dụng được nhiều ram
    
   Thay đổi từ mặc định là `graph.elevation.dataaccess: MMAP` thành `graph.elevation.dataaccess: RAM_STORE`
    
## Speed, hybrid and flexible mode

   ### speed mode sử dụng  [Contraction Hierarchies](https://en.wikipedia.org/wiki/Contraction_hierarchies) và trọng số mặc định là fastest 
    
   kích hoạt:
    
    `prepare.ch.weightings: fastest`
    
   để kích hoạt sử dụng turn cost:
    
    `prepare.ch.weightings: fastest|u_turn_cost=30` 
    
   trong đó 30 là turn_cost trong 1s
    
    ..........
    
   tắt speed mode:
    
    `prepare.ch.weightings: no`
    
    `prepare.ch.threads: 1` ????
    
   ### hybird mode
    
   kích hoạt:
    
    `prepare.lm.weightings: fastest`
    
   điều chỉnh hiệu suất và bộ nhớ:
    
    `prepare.lm.landmarks: [int]`
    
    `prepare.lm.threads: 1`??
    
   set min network size và min one way network size
    
    `prepare.min_network_size: 200`
    
    `prepare.min_one_way_network_size: 200`

## Routing
   
   ### chọn số nút được duyệt tối đa:
        `routing.max_visited_nodes:100000`( mặc định là Interger.MAX_VALUE)
   Nếu giá trị `routing.max_visited_nodes:100000` được khởi tạo, flexible mode có thể được chạy ngay cả khi speed mode hoặc hybird mode được bật nếu ch.disable=true
   Thêm `routing.ch.disabling_allowed: true` để cho phép disable speed mode
   Thêm `routing.lm.disabling_allowed: true` để cho phép disable hybird mode
   ### giới hạn khoảng cách tối đa giữa 2 điểm tham chiếu sử dụng flexible request 
        `routing.non_ch.max_waypoint_distance: 1000000` (đơn vị là m, mặc định 1000km)

## Storage 
    
   ## cấu hình quyền truy cập bộ nhớ, mặc định và nên sử dụng là:
        `graph.dataaccess: RAM_STORE`
   ## chọn ngôn ngữ cho tên đường, mã ngôn ngữ theo tiêu chuẩn ISO 639-1 hoặc ISO 639-2
        `datareader.preferred_language: vi`
   ## sắp xếp lại đồ thị sau khi import sẽ làm tăng tốc độ truy vấn khaongr 10% và sẽ sử dụng nhiều ram hơn
        `graph.do_sort: true`

## Spatial Rules

   ### dữ liệu không gian yêu cầu 1 số cấu hình và cung cấp polygon với 1 số quy tắc được đặt mặc định tại:
        `spatial_rules.location: core/files/spatialrules/countries.geo.json`
   ### giới hạn độ lớn của bbox
        `spatial_rules.max_bbox: -180,180, -90,90`
    
