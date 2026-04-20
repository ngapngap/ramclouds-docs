# n8n

## 1) Mục đích

Tích hợp n8n với Ramclouds cho workflow automation qua OpenAI-compatible endpoint.

## 2) Cấu hình nhanh

- Base URL: `https://ramclouds.me/v1`
- API Key: `sk-your-api-key`
- Bắt buộc thêm header `User-Agent` để tránh lỗi 403 trong n8n flow.

## 3) Ví dụ config hoàn chỉnh

### OpenAI Node

1. Tạo Credentials → **OpenAI API**:
   - API Key: `sk-your-api-key`
   - Base URL: `https://ramclouds.me/v1`
2. Trong node, thêm Header:
   - Name: `User-Agent`
   - Value: `Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36`
3. Chọn model: `gpt-5` hoặc model khác.

### HTTP Request Node

- Method: `POST`
- URL: `https://ramclouds.me/v1/chat/completions`
- Headers:
  - `Authorization`: `Bearer sk-your-api-key`
  - `Content-Type`: `application/json`
  - `User-Agent`: `Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36`

Body JSON:

```json
{
  "model": "gpt-5",
  "messages": [
    {
      "role": "user",
      "content": "Hello"
    }
  ]
}
```

## 4) Lưu ý model/endpoint

- n8n trong hướng dẫn này đi theo OpenAI-compatible (`/v1`).
- Nếu dùng model Claude trong endpoint này, dùng hậu tố `-CL`.
- Với GPT-family, dùng tên model chuẩn.

## 5) Troubleshooting ngắn

- 403: kiểm tra đã thêm header `User-Agent` ở node tương ứng.
- 401: kiểm tra API key trong credential hoặc header `Authorization`.
- 404 route/model: xác nhận URL `/v1` và model name đúng quy ước.
