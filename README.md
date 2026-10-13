# Bài 1 — CI Matrix với JDK 17 và JDK 21

Dự án Spring Boot + Gradle minh họa kiểm thử tự động trên hai phiên bản Java.

- Workflow: [ci-matrix.yml](.github/workflows/ci-matrix.yml)
- Kích hoạt: mỗi lần push vào `main`.
- Hai job: `test-matrix (17)` và `test-matrix (21)` chạy song song khi runner sẵn sàng.
- `actions/checkout@v5` và `actions/setup-java@v5`, Temurin, `cache: gradle`.
- Lệnh kiểm thử: `./gradlew test` (Windows: `gradlew.bat test`).
- Không khóa Gradle toolchain ở JDK 17: test thực sự chạy bằng JDK được chọn trong ma trận.
- Bài kiểm thử khởi động Spring context và xác nhận application bean tồn tại.

## Chạy tại máy

Cài JDK 17 hoặc JDK 21, sau đó chạy:

```sh
chmod +x gradlew
./gradlew test
```

Gradle Wrapper tự tải Gradle 8.14.3. Báo cáo test nằm ở `build/reports/tests/test/index.html`.

## Bài nộp

Xem [homework/session_12/ex1](homework/session_12/ex1/README.md).
Workflow phải đặt tại `.github/workflows/ci-matrix.yml` ở gốc repository để GitHub Actions nhận diện.
