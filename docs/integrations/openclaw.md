# OpenClaw / ClawdBot

## 1) Mục đích

Cấu hình OpenClaw để gọi Ramclouds qua provider OpenAI-compatible.

## 2) Cấu hình nhanh

1. Chạy onboarding:

```bash
openclaw onboard
```

2. Mở file `~/.openclaw/agents/<agentId>/models.json` và thêm provider Ramclouds.

## 3) Ví dụ config hoàn chỉnh

```json
{
  "ramclouds": {
    "provider": "openai",
    "baseUrl": "https://ramclouds.me/v1",
    "apiKey": "sk-your-api-key",
    "model": "gpt-5"
  }
}
```

Dùng với agent:

```bash
openclaw agent --message "Hello" --model ramclouds
```

## 4) Lưu ý model/endpoint

- Flow hiện tại chỉ cần `provider`, `baseUrl`, `apiKey`, `model`.
- Không cần thêm `headers.User-Agent` trong cấu hình OpenClaw.
- Nếu dùng Claude qua OpenAI-compatible, dùng model có hậu tố `-CL`.

## 5) Troubleshooting ngắn

- OpenClaw không nhận model: kiểm tra đúng tên key provider (`ramclouds`) trong `models.json`.
- 401: xác nhận API key hợp lệ.
- Request fail: kiểm tra `baseUrl` trỏ đúng `https://ramclouds.me/v1`.
