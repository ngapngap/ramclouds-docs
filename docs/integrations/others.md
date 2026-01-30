# Other Integrations

Ramclouds API is compatible with any application that supports OpenAI's API format.

## AI as Workspace (AIAW)

Quick setup link:
```
https://aiaw.app/set-provider?provider={"type":"openai","settings":{"apiKey":"YOUR_KEY","baseURL":"https://ramclouds.me/v1","compatibility":"strict"}}
```

## OpenCat

For iOS/macOS users:
```
opencat://team/join?domain=ramclouds.me&token=YOUR_API_KEY
```

## AMA (Ask Me Anything)

```
ama://set-api-key?server=https://ramclouds.me&key=YOUR_API_KEY
```

## Fluent Read

Browser extension for AI-powered reading:
- Extension ID: `fluentread`
- Configure with Ramclouds API key

## BotGem / AMA

1. Open Settings
2. Add Custom Provider
3. Set API Base: `https://ramclouds.me/v1`
4. Enter your API key

## ChatBox

1. Go to Settings > AI Provider
2. Select "OpenAI API Compatible"
3. Configure:
   - API Host: `https://ramclouds.me`
   - API Path: `/v1/chat/completions`
   - API Key: Your key

## Cursor IDE

1. Open Cursor Settings
2. Go to "Models" section
3. Add custom model:
   - API Base: `https://ramclouds.me/v1`
   - API Key: Your Ramclouds key

## Continue (VS Code Extension)

Edit `~/.continue/config.json`:

```json
{
  "models": [
    {
      "title": "Ramclouds GPT-5",
      "provider": "openai",
      "model": "gpt-5",
      "apiBase": "https://ramclouds.me/v1",
      "apiKey": "YOUR_API_KEY"
    }
  ]
}
```

## Cline (Claude Dev)

1. Open Cline settings
2. Select "OpenAI Compatible" provider
3. Enter:
   - Base URL: `https://ramclouds.me/v1`
   - API Key: Your key
   - Model: `claude-opus-4-5` or others

## Generic OpenAI SDK

Any application using the OpenAI SDK can be configured:

### Python
```python
from openai import OpenAI

client = OpenAI(
    api_key="YOUR_KEY",
    base_url="https://ramclouds.me/v1"
)
```

### Node.js
```javascript
import OpenAI from 'openai';

const client = new OpenAI({
  apiKey: 'YOUR_KEY',
  baseURL: 'https://ramclouds.me/v1'
});
```

### Environment Variables

Many apps respect these environment variables:
```bash
export OPENAI_API_KEY="your-ramclouds-key"
export OPENAI_BASE_URL="https://ramclouds.me/v1"
```

## Need Help?

If your application isn't listed, it likely still works with Ramclouds. Look for:
- "OpenAI Compatible" option
- "Custom API endpoint" setting
- "API Base URL" configuration

Contact us on [Telegram](https://t.me/ramclouds_bot) for integration help.
