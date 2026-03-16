# IDE Integrations

Cấu hình Ramclouds API cho các IDE coding assistants.

## Lưu ý khi chọn endpoint `v1/messages` (Claude)

Khi IDE hoặc extension của bạn gọi endpoint `v1/messages`, model Claude phải dùng **model ID chuẩn không có hậu tố `-CL`**.

- Đúng (cho `v1/messages`): `claude-opus-4.6`
- Sai (cho `v1/messages`): `claude-opus-4.6-CL`

Phạm vi áp dụng: quy tắc này chỉ dành cho `v1/messages`. Với endpoint khác, dùng đúng quy ước của endpoint đó.

### Thao tác cấu hình để tránh nhập nhầm `-CL`

1. Chọn endpoint/base URL tương ứng luồng `v1/messages` trong IDE/tool.
2. Dán model Claude chuẩn (không `-CL`) vào trường `model`.
3. Kiểm tra lại preset/template cũ, xóa mọi hậu tố `-CL` nếu còn sót.
4. Lưu cấu hình và test nhanh 1 request trước khi dùng cho môi trường production.

> Security note (docs-level): cấu hình mismatch endpoint/model có thể làm request fail hoặc phát sinh lỗi khó chẩn đoán. Không commit API key vào repo, kiểm tra endpoint localhost đúng nguồn trước khi lưu, và luôn đối chiếu đúng hậu tố `-CL` giữa Claude-native và OpenAI-compatible.

## OpenCode

### Nhánh 1 — Claude-native (`@ai-sdk/anthropic`)

Dùng khi bạn muốn gọi theo chuẩn Claude-native, model **không có** hậu tố `-CL`.

```ts
import { anthropic } from '@ai-sdk/anthropic';

const model = anthropic('claude-opus-4.6');
```

- SDK: `@ai-sdk/anthropic`
- Model đúng: `claude-opus-4.6`
- Model sai cho nhánh này: `claude-opus-4.6-CL`

### Nhánh 2 — OpenAI-compatible (`@ai-sdk/openai-compatible`)

Dùng khi ứng dụng/framework đang đi qua adapter tương thích OpenAI, model Claude **có** hậu tố `-CL`.

```ts
import { createOpenAICompatible } from '@ai-sdk/openai-compatible';

const ramclouds = createOpenAICompatible({
  name: 'ramclouds',
  baseURL: 'https://ramclouds.me/v1',
  apiKey: process.env.RAMCLOUDS_API_KEY,
});

const model = ramclouds('claude-opus-4.6-CL');
```

- SDK: `@ai-sdk/openai-compatible`
- Model đúng: `claude-opus-4.6-CL`
- Model sai cho nhánh này: `claude-opus-4.6`

> Security note (docs-level): không commit API key; ưu tiên biến môi trường. Nếu dùng endpoint localhost để proxy/router, chỉ trỏ tới endpoint tự quản trị và xác minh nguồn rõ ràng để tránh endpoint giả mạo.

## AmpCode

AmpCode **bắt buộc** đi qua proxy server; không có luồng cấu hình direct-provider hợp lệ. Repo proxy tham chiếu: `https://github.com/fdkgenie/9router`.

Điểm mạnh thực tế của mô hình proxy-only là chỉ cần trỏ **một lần** vào `http://localhost:20128/v1`, sau đó quản lý provider/model tập trung tại 9Router thay vì sửa nhiều nơi trong IDE.

### So sánh thực tế: không proxy-only vs proxy-only qua 9Router

| Tiêu chí | Không đi qua proxy (không áp dụng cho AmpCode) | Proxy-only qua 9Router (AmpCode thực tế) |
|---|---|---|
| Tính hợp lệ với AmpCode | Không hợp lệ | Bắt buộc/được hỗ trợ |
| Endpoint trong AmpCode | N/A | Một endpoint thống nhất: `http://localhost:20128/v1` |
| Quản lý provider/model | N/A | Quản lý tập trung tại proxy |
| Độ phức tạp khi đổi provider | N/A | Chủ yếu đổi tại proxy, client giữ nguyên |
| Mở rộng đa provider | N/A | Dễ mở rộng và quản lý tập trung |
| Trạng thái RamClouds | N/A | Đã thêm RamClouds làm provider (qua proxy layer) |

### Gợi ý cấu hình AmpCode qua 9Router (proxy-only)

- Base URL: `http://localhost:20128/v1`
- API key: key do proxy/router cấp hoặc quản lý theo policy nội bộ
- Model: theo mapping đã định nghĩa ở 9Router (đúng quy tắc suffix theo nhánh)

> Security note (docs-level): chỉ tin cậy endpoint proxy nội bộ mà bạn kiểm soát. API key/provider secret cần được quản lý tại proxy layer và không để lộ secret phía client AmpCode. Luôn xác minh tiến trình lắng nghe `localhost:20128` là proxy tin cậy trước khi nhập credential.

## Claude Code

```bash
# Set environment variables
export ANTHROPIC_BASE_URL="https://ramclouds.me"
export ANTHROPIC_API_KEY="sk-your-api-key"

# Hoặc chạy với flags
claude --api-key "sk-your-api-key" --api-url "https://ramclouds.me"
```

**Settings file** (`~/.claude/settings.json`):
```json
{
  "apiUrl": "https://ramclouds.me",
  "apiKey": "sk-your-api-key"
}
```

## Roo Code (VS Code)

1. Mở **Settings** → Tìm "Roo Code"
2. Cấu hình:

| Setting | Value |
|---------|-------|
| Api Provider | `openai-compatible` |
| Base URL | `https://ramclouds.me/v1` |
| API Key | `sk-your-api-key` |
| Model | `claude-opus-4.6-CL` hoặc `gpt-5` |

**Hoặc settings.json:**
```json
{
  "roo-code.apiProvider": "openai-compatible",
  "roo-code.openaiCompatible.baseUrl": "https://ramclouds.me/v1",
  "roo-code.openaiCompatible.apiKey": "sk-your-api-key",
  "roo-code.openaiCompatible.model": "claude-opus-4.6-CL"
}
```

## Continue (VS Code)

Edit `~/.continue/config.json`:
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

## Cursor

1. **Settings** → **Models** → **OpenAI API Key**
2. Nhập API key: `sk-your-api-key`
3. **Override OpenAI Base URL**: `https://ramclouds.me/v1`

## Cline / Claude Dev

1. Mở Cline settings
2. Chọn **OpenAI Compatible**
3. Cấu hình:
   - Base URL: `https://ramclouds.me/v1`
   - API Key: `sk-your-api-key`
   - Model: `claude-opus-4.6-CL`

## Aider

```bash
export OPENAI_API_BASE="https://ramclouds.me/v1"
export OPENAI_API_KEY="sk-your-api-key"

aider --model gpt-5
```

## OpenClaw / ClawdBot

1. Chạy onboard wizard:
```bash
openclaw onboard
```

2. Cấu hình model trong `~/.openclaw/agents/<agentId>/models.json`:
```json
{
  "ramclouds": {
    "provider": "openai",
    "baseUrl": "https://ramclouds.me/v1",
    "apiKey": "sk-your-api-key",
    "model": "gpt-5",
    "headers": {
      "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36"
    }
  }
}
```

3. Sử dụng với agent:
```bash
openclaw agent --message "Hello" --model ramclouds
```

## n8n

> **Lưu ý:** Bắt buộc phải thêm header `User-Agent`, nếu không sẽ lỗi 403.

### OpenAI Node

1. Tạo **Credentials** → **OpenAI API**:
   - API Key: `sk-your-api-key`
   - Base URL: `https://ramclouds.me/v1`
2. Trong node, thêm **Header**:
   - Name: `User-Agent`
   - Value: `Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36`
3. Chọn Model: `gpt-5` hoặc model khác

### HTTP Request Node

1. Method: `POST`
2. URL: `https://ramclouds.me/v1/chat/completions`
3. Headers:
   - `Authorization`: `Bearer sk-your-api-key`
   - `Content-Type`: `application/json`
   - `User-Agent`: `Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36`
4. Body (JSON):
```json
{
  "model": "gpt-5",
  "messages": [{"role": "user", "content": "Hello"}]
}
```

## Environment Variables (Universal)

```bash
export OPENAI_API_KEY="sk-your-api-key"
export OPENAI_BASE_URL="https://ramclouds.me/v1"
```

Hầu hết các tools sử dụng OpenAI SDK sẽ tự động nhận các biến này.
