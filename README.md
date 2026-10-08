# Bài 3 Session 07

## 1. Tệp tin cấu hình `spring-app.service`

Tệp cấu hình Systemd được tạo tại:

```text
/etc/systemd/system/spring-app.service
```

Nội dung:

```ini
[Unit]
Description=Spring Boot Application
After=network.target mysql.service

[Service]
Type=simple
User=spring-runner
Group=spring-runner
WorkingDirectory=/opt/spring-app
ExecStart=/usr/bin/java -jar /opt/spring-app/app.jar
Restart=on-failure
RestartSec=10

[Install]
WantedBy=multi-user.target
```

Ảnh chụp tệp cấu hình:

(ảnh 1)
---

## 2. Kết quả lệnh `systemctl status`

Lệnh kiểm tra:

```bash
sudo systemctl status spring-app.service
```

Kết quả:

(ảnh 2)
Kết quả mong đợi:

```text
Active: active (running)
```

Service chạy với user:

```text
spring-runner
```

---

## 3. Kết quả lệnh `ss -tlnp`

Lệnh kiểm tra:

```bash
ss -tlnp | grep 8082
```

Kết quả:

(ảnh 3)
Kết quả mong đợi cho thấy Java đang lắng nghe trên port:

```text
8082
```

Ứng dụng Spring Boot hoạt động tại:

```text
http://<IP-VPS>:8082
```
