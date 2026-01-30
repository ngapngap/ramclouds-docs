# Authentication

## API Key Format
```
sk-xxxxxxxxxxxxxxxxxxxxx
```

## Sử dụng
```
Authorization: Bearer sk-your-api-key
```

## Environment Variables
```bash
export OPENAI_API_KEY="sk-your-api-key"
export OPENAI_BASE_URL="https://ramclouds.me/v1"
```

## Python
```python
import os
from openai import OpenAI

client = OpenAI(
    api_key=os.environ.get("OPENAI_API_KEY"),
    base_url="https://ramclouds.me/v1"
)
```

## Lưu ý

- Không chia sẻ API key
- Không commit vào git
- Sử dụng environment variables
