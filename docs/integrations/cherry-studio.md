# Cherry Studio Integration

[Cherry Studio](https://cherry-ai.com) is a powerful AI chat client that supports multiple providers.

## Quick Setup

Click the link below to auto-configure Cherry Studio with Ramclouds:

```
cherrystudio://providers/api-keys?v=1&data={YOUR_CHERRY_CONFIG}
```

## Manual Setup

### Step 1: Open Settings

1. Open Cherry Studio
2. Go to **Settings** > **Providers**

### Step 2: Add Custom Provider

1. Click **Add Provider**
2. Choose **Custom OpenAI Compatible**

### Step 3: Configure

| Field | Value |
|-------|-------|
| Name | Ramclouds |
| API Base URL | `https://ramclouds.me/v1` |
| API Key | Your Ramclouds API key |

### Step 4: Add Models

Add the models you want to use:

- `gpt-5`
- `claude-opus-4-5`
- `gemini-2.5-pro`
- etc.

### Step 5: Save & Test

Click **Save** and test with a simple message.

## Screenshot Guide

1. **Provider Settings**
   - Navigate to Settings > Providers
   - Click "Add Provider"

2. **Configuration**
   - Enter the details as shown above
   - Make sure the URL ends with `/v1`

3. **Model Selection**
   - Add models manually or fetch from API
   - Select default model for new chats

## Troubleshooting

### Connection Failed

- Check your API key is correct
- Ensure URL is `https://ramclouds.me/v1`
- Verify your internet connection

### Model Not Found

- Check the model ID is exactly correct
- Some models may not be available for your tier
- Try using `/v1/models` to list available models

## Tips

- Use `claude-opus-4-5` for complex reasoning tasks
- Use `gpt-5` for general conversations
- Use `gemini-2.5-flash` for fast responses
