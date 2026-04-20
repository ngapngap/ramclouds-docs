# OpenCode

## 1) Mục đích

Tích hợp OpenCode với Ramclouds theo hai nhánh: Claude-native hoặc OpenAI-compatible.

## 2) Cấu hình nhanh

Chọn đúng nhánh theo SDK bạn dùng:

- Claude-native: `@ai-sdk/anthropic`
- OpenAI-compatible: `@ai-sdk/openai-compatible`

## 3) Ví dụ config hoàn chỉnh

### Nhánh A — Claude-native (`@ai-sdk/anthropic`)

```ts
import { anthropic } from '@ai-sdk/anthropic';

const model = anthropic('claude-opus-4.6');
```

### Nhánh B — OpenAI-compatible (`@ai-sdk/openai-compatible`)

```ts
import { createOpenAICompatible } from '@ai-sdk/openai-compatible';

const ramclouds = createOpenAICompatible({
  name: 'ramclouds',
  baseURL: 'https://ramclouds.me/v1',
  apiKey: process.env.RAMCLOUDS_API_KEY,
});

const model = ramclouds('claude-opus-4.6-CL');
```

## 4) Lưu ý model/endpoint

- Claude-native (`v1/messages`): model Claude **không `-CL`**.
- OpenAI-compatible (`/v1`): model Claude **có `-CL`**.
- Không trộn model suffix giữa hai nhánh để tránh lỗi khó chẩn đoán.

## 5) Troubleshooting ngắn

- Model not found: kiểm tra lại suffix `-CL` theo đúng nhánh.
- 401: xác nhận biến môi trường `RAMCLOUDS_API_KEY` đã được load.
- Request fail ngẫu nhiên: kiểm tra base URL có đúng nhánh SDK đang dùng.
