# Roo Code (VS Code)

## 1) Mục đích

Kết nối Roo Code với Ramclouds qua OpenAI-compatible endpoint để dùng model Claude/GPT trong VS Code.

## 2) Cấu hình nhanh

Trong Roo Code settings:

- `Api Provider`: `openai-compatible`
- `Base URL`: `https://ramclouds.me/v1`
- `API Key`: `sk-your-api-key`
- `Model`: `claude-opus-4.6-CL` hoặc `gpt-5`

## 3) Ví dụ config hoàn chỉnh

```json
{
  "roo-code.apiProvider": "openai-compatible",
  "roo-code.openaiCompatible.baseUrl": "https://ramclouds.me/v1",
  "roo-code.openaiCompatible.apiKey": "sk-your-api-key",
  "roo-code.openaiCompatible.model": "claude-opus-4.6-CL"
}
```

## 4) Lưu ý model/endpoint

- Roo Code trong cấu hình này đi theo OpenAI-compatible, nên base URL dùng `.../v1`.
- Nếu chọn Claude qua OpenAI-compatible thì dùng model có hậu tố `-CL` (ví dụ `claude-opus-4.6-CL`).
- `gpt-5` giữ nguyên tên model.

## 5) Troubleshooting ngắn

- 401/403: kiểm tra API key và credential đang active trong Roo Code.
- 404 model: kiểm tra đúng hậu tố `-CL` với model Claude ở nhánh OpenAI-compatible.
- Timeout: thử request ngắn để xác nhận mạng/proxy nội bộ ổn định.
