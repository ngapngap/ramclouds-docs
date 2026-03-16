# API Overview

## Base URL
```
https://ramclouds.me/v1
```

## Endpoints

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/v1/chat/completions` | POST | Chat completions |
| `/v1/messages` | POST | Claude Messages API-compatible endpoint |
| `/v1/models` | GET | List models |
| `/v1/embeddings` | POST | Embeddings |

## Request Example

```bash
curl https://ramclouds.me/v1/chat/completions \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "gpt-5",
    "messages": [{"role": "user", "content": "Hello!"}]
  }'
```

## Response

```json
{
  "id": "chatcmpl-xxx",
  "model": "gpt-5",
  "choices": [{
    "message": {"role": "assistant", "content": "Hello!"},
    "finish_reason": "stop"
  }],
  "usage": {"prompt_tokens": 10, "completion_tokens": 5, "total_tokens": 15}
}
```

## Endpoint-specific Model ID Rule (Claude)

Với endpoint `v1/messages` theo chuẩn Claude (Claude-native), model Claude phải là **model ID chuẩn không có hậu tố `-CL`**. Ngược lại, nếu dùng adapter tương thích OpenAI (`@ai-sdk/openai-compatible`), model Claude cần có hậu tố `-CL`.

- Correct Claude-native (`v1/messages`): `claude-opus-4.6`
- Incorrect Claude-native (`v1/messages`): `claude-opus-4.6-CL`
- Correct OpenAI-compatible (`@ai-sdk/openai-compatible`): `claude-opus-4.6-CL`

Lưu ý phạm vi: quy tắc trên áp dụng theo đúng nhánh SDK/endpoint. Tránh trộn quy ước model giữa Claude-native và OpenAI-compatible để không gây nhầm lẫn vận hành.

> Security note (docs-level): Không commit API key vào repo. Khi dùng endpoint localhost, cần xác minh đúng nguồn endpoint để tránh endpoint giả mạo. Đồng thời kiểm tra đúng hậu tố `-CL` theo từng nhánh (Claude-native vs OpenAI-compatible) để giảm lỗi request khó chẩn đoán.

## Errors

| Status | Description |
|--------|-------------|
| 400 | Invalid request format or endpoint/model mismatch |
| 401 | Invalid API key |
| 403 | Insufficient credits |
| 429 | Rate limited |
