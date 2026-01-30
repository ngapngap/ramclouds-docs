# Authentication

All API requests require authentication using an API key.

## Getting Your API Key

1. Log in to your account at [ramclouds.me](https://ramclouds.me)
2. Navigate to the **API Keys** section in your dashboard
3. Click **Create New Key**
4. Copy and securely store your API key

> **Important**: Keep your API key secret. Never share it publicly or commit it to version control.

## Using Your API Key

Include your API key in the `Authorization` header of every request:

```
Authorization: Bearer YOUR_API_KEY
```

### Example

```bash
curl https://ramclouds.me/v1/models \
  -H "Authorization: Bearer sk-xxxxxxxxxxxxxxxxxxxxx"
```

## API Key Format

Ramclouds API keys follow this format:
```
sk-[random alphanumeric string]
```

Example: `sk-bo90aT6mhj73A9ledgahoyLw5bqnxXyk7TGiwD26Rzu56pVo`

## Security Best Practices

### Do

- Store API keys in environment variables
- Use different keys for development and production
- Rotate keys periodically
- Monitor your usage for unusual activity

### Don't

- Hardcode API keys in your source code
- Share keys via email or chat
- Commit keys to Git repositories
- Use the same key across multiple applications

## Environment Variables

### Bash/Zsh

```bash
export RAMCLOUDS_API_KEY="sk-your-api-key"
```

### Python

```python
import os
from openai import OpenAI

client = OpenAI(
    api_key=os.environ.get("RAMCLOUDS_API_KEY"),
    base_url="https://ramclouds.me/v1"
)
```

### Node.js

```javascript
const client = new OpenAI({
  apiKey: process.env.RAMCLOUDS_API_KEY,
  baseURL: 'https://ramclouds.me/v1'
});
```

## Rate Limits

Rate limits depend on your account tier. Check your dashboard for current limits.

## Troubleshooting

### 401 Unauthorized

- Check that your API key is correct
- Ensure you're using `Bearer` prefix
- Verify your account is active

### 403 Forbidden

- Your account may have insufficient credits
- The requested model may not be available for your tier
