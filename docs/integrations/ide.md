# IDE Integrations

Cấu hình Ramclouds API cho các IDE coding assistants.

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
| Model | `claude-sonnet-4-5` hoặc `gpt-5` |

**Hoặc settings.json:**
```json
{
  "roo-code.apiProvider": "openai-compatible",
  "roo-code.openaiCompatible.baseUrl": "https://ramclouds.me/v1",
  "roo-code.openaiCompatible.apiKey": "sk-your-api-key",
  "roo-code.openaiCompatible.model": "claude-sonnet-4-5"
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
   - Model: `claude-opus-4-5`

## Aider

```bash
export OPENAI_API_BASE="https://ramclouds.me/v1"
export OPENAI_API_KEY="sk-your-api-key"

aider --model gpt-5
```

## Environment Variables (Universal)

```bash
export OPENAI_API_KEY="sk-your-api-key"
export OPENAI_BASE_URL="https://ramclouds.me/v1"
```

Hầu hết các tools sử dụng OpenAI SDK sẽ tự động nhận các biến này.
