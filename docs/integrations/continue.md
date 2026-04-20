# Continue (VS Code)

## 1) Mục đích

Tích hợp Continue với Ramclouds để dùng model qua OpenAI-compatible endpoint.

## 2) Cấu hình nhanh

Sửa `~/.continue/config.json` với:

- `provider`: `openai`
- `apiBase`: `https://ramclouds.me/v1`
- `apiKey`: `sk-your-api-key`

## 3) Ví dụ config hoàn chỉnh

```json
{
  "models": [
    {
      "title": "Ramclouds",
      "provider": "openai",
      "model": "gpt-5",
      "apiBase": "https://ramclouds.me/v1",
      "apiKey": "sk-your-api-key"
    }
  ]
}
```

## 4) Lưu ý model/endpoint

- Continue ở cấu hình này dùng OpenAI-compatible endpoint (`/v1`).
- Nếu chọn model Claude trong nhánh này, dùng tên có hậu tố `-CL`.
- Nếu chọn GPT-family (`gpt-5`), giữ nguyên tên model.

## 5) Troubleshooting ngắn

- 401: kiểm tra API key trong file config.
- Model not found: xác nhận tên model đúng quy ước của endpoint `/v1`.
- Không thấy model trong UI: reload cửa sổ VS Code sau khi đổi config.
