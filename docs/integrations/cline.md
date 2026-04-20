# Cline

## 1) Mục đích

Kết nối Cline (Claude Dev) với Ramclouds bằng OpenAI-compatible cấu hình.

## 2) Cấu hình nhanh

Trong Cline settings:

- Provider: `OpenAI Compatible`
- Base URL: `https://ramclouds.me/v1`
- API Key: `sk-your-api-key`
- Model: `claude-opus-4.6-CL`

## 3) Ví dụ config hoàn chỉnh

```json
{
  "provider": "openai-compatible",
  "baseUrl": "https://ramclouds.me/v1",
  "apiKey": "sk-your-api-key",
  "model": "claude-opus-4.6-CL"
}
```

## 4) Lưu ý model/endpoint

- Đây là nhánh OpenAI-compatible, nên endpoint dùng `.../v1`.
- Nếu dùng model Claude, áp dụng tên model có hậu tố `-CL`.

## 5) Troubleshooting ngắn

- 404 endpoint: kiểm tra có đang trỏ đúng `https://ramclouds.me/v1`.
- 401/403: kiểm tra key và quyền truy cập route.
- Lỗi model: thử model fallback như `gpt-5` để xác nhận đường truyền.
