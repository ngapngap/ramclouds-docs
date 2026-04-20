# Aider

## 1) Mục đích

Dùng Aider với Ramclouds thông qua biến môi trường OpenAI-compatible.

## 2) Cấu hình nhanh

```bash
export OPENAI_API_BASE="https://ramclouds.me/v1"
export OPENAI_API_KEY="sk-your-api-key"
```

## 3) Ví dụ config hoàn chỉnh

```bash
export OPENAI_API_BASE="https://ramclouds.me/v1"
export OPENAI_API_KEY="sk-your-api-key"

# Ví dụ chạy với GPT model
aider --model gpt-5

# Ví dụ chạy với Claude qua OpenAI-compatible
aider --model claude-opus-4.6-CL
```

## 4) Lưu ý model/endpoint

- Aider trong flow này đi qua OpenAI-compatible endpoint (`/v1`).
- Với model Claude ở nhánh này, dùng hậu tố `-CL`.
- Không dùng model Claude không suffix trong nhánh OpenAI-compatible.

## 5) Troubleshooting ngắn

- API auth fail: kiểm tra `OPENAI_API_KEY` đã export trong shell hiện tại.
- Model invalid: xác nhận tên model đúng quy ước endpoint.
- Không nhận env vars: restart shell hoặc terminal session.
