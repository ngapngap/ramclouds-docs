# Cursor

## 1) Mục đích

Cấu hình Cursor để gọi Ramclouds qua OpenAI-compatible API.

## 2) Cấu hình nhanh

Trong Cursor:

1. Vào **Settings** → **Models**.
2. Nhập **OpenAI API Key**: `sk-your-api-key`.
3. Bật **Override OpenAI Base URL**: `https://ramclouds.me/v1`.

## 3) Ví dụ config hoàn chỉnh

```text
OpenAI API Key: sk-your-api-key
Override OpenAI Base URL: https://ramclouds.me/v1
Model: claude-opus-4.6-CL (hoặc gpt-5)
```

## 4) Lưu ý model/endpoint

- Cursor trong flow này dùng OpenAI-compatible endpoint (`/v1`).
- Model Claude trên endpoint này nên dùng hậu tố `-CL`.
- Với GPT model, dùng tên model chuẩn (ví dụ `gpt-5`).

## 5) Troubleshooting ngắn

- Lỗi xác thực: dán lại API key và lưu settings.
- Lỗi model unavailable: đổi sang model có sẵn trong tài khoản/route hiện tại.
- Request không đi đúng host: kiểm tra lại `Override OpenAI Base URL`.
