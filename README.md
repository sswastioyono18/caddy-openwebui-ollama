# Why

Modification based on this repo (Huge thanks btw)
https://github.com/bartolli/ollama-bearer-auth-caddy

The reason was that I want to use ollama natively inside the OS.
Therefore, Open Web UI -> Caddy (+validation api key) -> Ollama 

The objective is that I want to make Open Web UI as an API for accessing Ollama with different API Keys

# How to
first time
```
docker compose build --no-cache
```
afterwards 
```
docker compose up -d
```

In OpenWeb UI, configure 
For url, use `http://ollama-reverse-proxy:8081`
Api key in `Caddy/valid_keys.conf`

Save, all done!

# Example how to call API
```
curl -X POST http://host:port/api/chat/completions -H "Authorization: Bearer <bearer from OpenWebUI" \
-H "Content-Type: application/json" \
-d '{
      "model": "gemma3:4b",
      "messages": [
        {
          "role": "user",
          "content": "Tell me about Google"
        }
      ]
    }'
```
