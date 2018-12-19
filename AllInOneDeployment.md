
##  Cách triển khai mô hình (1-1-n+)

### Mục tiêu
> tập trung ở 1 nơi duy nhất, trên 1 domain

- phù hợp cho các hệ thống cần triển khai nhanh, tôi ưu thời gian triển khai

### Thành phần

#### 1 UserFront: website | mobileApps
- website `easyweb`:   HTML, CSS, JS
  - `/easyweb(/index.html)`: đường dẫn truy cập
  - phát triển bởi EasyBuilder

- apps `easyapp`: demo nhanh trải nghiệm mobileapps
  - `/easyapp(/index.html)`: đường dẫn truy cập
  - demo mobileapps bằng Framework7 + VueJS

- 1 StaffAdmin:  `easyadmin`: webapp dạng SPA
  - `/(index.html)`: domain chính hoặc sub-domain
  -

- n+ API backend
  - `/explorer`: explorer API của loopback

- dùng chung hình ảnh:
  - `/images` đường dẫn truy cập, ví dụ `/images/one-place.png`

  - easyAdmin sẽ upload lên và lưu trữ trong apibackend


### Thiết lập
- sử dụng static file của loopback
```
//server/middleware.json
"loopback#static": [
      {
        "paths": [
          "/"
        ],
        "params": "$!../easyadmin"
      },
      {
        "paths": [
          "/easyweb"
        ],
        "params": "$!../easyweb"
      },
      {
        "paths": [
          "/easyapp"
        ],
        "params": "$!../easyapp"
      },
      {
        "paths": [
          "/images"
        ],
        "params": "server/storage/images"
      }
    ]
```

#### Minh họa
- xem hình ![one-place](/one-place.png)


