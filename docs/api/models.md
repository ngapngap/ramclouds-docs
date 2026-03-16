# Models

## Endpoint
```
GET https://ramclouds.me/v1/models
```

## Available Models

### OpenAI
| Model | Description |
|-------|-------------|
| gpt-5 | GPT-5 base |
| gpt-5.1 | GPT-5.1 |
| gpt-5.2 | GPT-5.2 |
| gpt-5-codex | Code optimized |

### Anthropic
| Model | Description |
|-------|-------------|
| claude-opus-4.6 | Most capable |
| claude-sonnet-4.6 | Balanced |
| claude-haiku-4.6 | Fast |

### Google
| Model | Description |
|-------|-------------|
| gemini-2.5-pro | Pro model |
| gemini-2.5-flash | Fast |
| gemini-3-pro-preview | Preview |

### Others
| Model | Description |
|-------|-------------|
| deepseek-v3.2 | DeepSeek |
| qwen3-max | Alibaba Qwen |
| kimi-k2-thinking | Moonshot |
| glm-4.7 | Zhipu |

## Claude Model ID Rules by Endpoint

- Với endpoint `v1/messages` theo chuẩn Claude (Claude-native), model phải dùng **model ID không có hậu tố `-CL`**.
- Với adapter tương thích OpenAI (`@ai-sdk/openai-compatible`), model Claude dùng **hậu tố `-CL`**.
- Quy tắc trên cần áp dụng nhất quán theo đúng nhánh SDK/endpoint để tránh mismatch.

**Ví dụ chuẩn hóa:**

- Correct Claude-native (`v1/messages`): `claude-opus-4.6`
- Incorrect Claude-native (`v1/messages`): `claude-opus-4.6-CL`
- Correct OpenAI-compatible (`@ai-sdk/openai-compatible`): `claude-opus-4.6-CL`

> Security note (docs-level): Không commit API key vào repo. Chỉ dùng endpoint localhost từ nguồn tin cậy (tránh endpoint giả mạo). Đồng thời kiểm tra đúng quy tắc hậu tố `-CL` giữa Claude-native và OpenAI-compatible để tránh request fail hoặc lỗi khó chẩn đoán.

## Example
```bash
curl https://ramclouds.me/v1/models -H "Authorization: Bearer YOUR_API_KEY"
```
