# AmpCode

## 1) Mục đích

Cấu hình AmpCode qua proxy server (9Router) để dùng Ramclouds theo mô hình quản lý tập trung provider/model.

## 2) Cấu hình nhanh

AmpCode dùng proxy-only:

- `Base URL`: `http://localhost:20128/v1`
- `API Key`: theo policy của proxy/router
- `Model`: theo mapping đã định nghĩa trong 9Router

## 3) Ví dụ config hoàn chỉnh

Ví dụ cấu hình endpoint trong AmpCode:

```json
{
  "provider": "openai-compatible",
  "baseUrl": "http://localhost:20128/v1",
  "apiKey": "sk-your-api-key",
  "model": "claude-opus-4.6-CL"
}
```

## 4) Lưu ý model/endpoint

- AmpCode trong flow này đi qua OpenAI-compatible proxy (`/v1`).
- Nếu proxy map sang Claude qua adapter OpenAI-compatible, dùng model có `-CL`.
- Luôn kiểm tra mapping model thực tế tại proxy trước khi nhập vào client.

## 5) Troubleshooting ngắn

- Không kết nối được: xác nhận proxy local đang lắng nghe tại `localhost:20128`.
- 401 từ proxy: kiểm tra key/policy trong 9Router.
- Model mismatch: đối chiếu model mapping trong proxy và tên model ở AmpCode.
