# Embeddings

Create text embeddings for semantic search and similarity.

## Endpoint

```
POST https://ramclouds.me/v1/embeddings
```

## Request Body

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `model` | string | Yes | Embedding model ID |
| `input` | string/array | Yes | Text to embed |
| `encoding_format` | string | No | `float` or `base64` |

## Example Request

### cURL

```bash
curl https://ramclouds.me/v1/embeddings \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -d '{
    "model": "text-embedding-3-small",
    "input": "Hello world"
  }'
```

### Python

```python
from openai import OpenAI

client = OpenAI(
    api_key="YOUR_API_KEY",
    base_url="https://ramclouds.me/v1"
)

response = client.embeddings.create(
    model="text-embedding-3-small",
    input="The quick brown fox jumps over the lazy dog"
)

embedding = response.data[0].embedding
print(f"Embedding dimension: {len(embedding)}")
```

### Multiple Inputs

```python
response = client.embeddings.create(
    model="text-embedding-3-small",
    input=[
        "First sentence to embed",
        "Second sentence to embed",
        "Third sentence to embed"
    ]
)

for i, data in enumerate(response.data):
    print(f"Text {i}: {len(data.embedding)} dimensions")
```

## Response

```json
{
  "object": "list",
  "data": [
    {
      "object": "embedding",
      "index": 0,
      "embedding": [0.0023064255, -0.009327292, ...]
    }
  ],
  "model": "text-embedding-3-small",
  "usage": {
    "prompt_tokens": 5,
    "total_tokens": 5
  }
}
```

## Available Models

| Model | Dimensions | Description |
|-------|------------|-------------|
| `text-embedding-3-small` | 1536 | Fast, cost-effective |
| `text-embedding-3-large` | 3072 | Higher quality |
| `text-embedding-ada-002` | 1536 | Legacy model |

## Use Cases

### Semantic Search

```python
import numpy as np
from openai import OpenAI

client = OpenAI(
    api_key="YOUR_API_KEY",
    base_url="https://ramclouds.me/v1"
)

def get_embedding(text):
    response = client.embeddings.create(
        model="text-embedding-3-small",
        input=text
    )
    return response.data[0].embedding

def cosine_similarity(a, b):
    return np.dot(a, b) / (np.linalg.norm(a) * np.linalg.norm(b))

# Example
query = get_embedding("How to make coffee?")
docs = [
    get_embedding("Coffee brewing guide"),
    get_embedding("Tea preparation methods"),
    get_embedding("Making espresso at home")
]

for i, doc in enumerate(docs):
    similarity = cosine_similarity(query, doc)
    print(f"Document {i}: {similarity:.4f}")
```

### Text Classification

Embeddings can be used to classify text by comparing to labeled examples or using machine learning models.
