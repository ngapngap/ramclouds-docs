# Claude Code

## 1) Mục đích

Cấu hình Claude Code để gọi Ramclouds theo luồng Claude-native, phù hợp khi bạn muốn dùng API tương thích Anthropic trực tiếp.

## 2) Cấu hình nhanh

```bash
export ANTHROPIC_BASE_URL="https://ramclouds.me"
export ANTHROPIC_API_KEY="sk-your-api-key"
```

Hoặc chạy trực tiếp bằng CLI flags:

```bash
claude --api-key "sk-your-api-key" --api-url "https://ramclouds.me"
```

## 3) Ví dụ config hoàn chỉnh

`~/.claude/settings.json`

```json
{
  "apiUrl": "https://ramclouds.me",
  "apiKey": "sk-your-api-key"
}
```

## 4) Lưu ý model/endpoint

- Với luồng Claude-native (`v1/messages`), dùng model Claude chuẩn **không có hậu tố `-CL`**.
- Ví dụ đúng: `claude-opus-4.6`
- Ví dụ sai cho luồng này: `claude-opus-4.6-CL`

## 5) Troubleshooting ngắn

- Nếu lỗi xác thực: kiểm tra lại `ANTHROPIC_API_KEY` và format `sk-...`.
- Nếu lỗi endpoint: xác nhận `ANTHROPIC_BASE_URL` là `https://ramclouds.me` (không thêm `/v1` cho flow Claude-native).
- Nếu lỗi model: bỏ hậu tố `-CL` khi đang dùng `v1/messages`.
