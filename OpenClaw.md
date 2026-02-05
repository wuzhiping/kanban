```code
curl -N http://127.0.0.1:18789/v1/chat/completions   -H 'Authorization: Bearer 9fb789b9632eb69cee22aa99501d169f051777d7e47ce6cb'   -H 'Content-Type: application/json'   -d '{
    "model": "openclaw",
    "stream": true, "user": "jinbe-session-001",
    "messages": [{"role":"user","content":"nice to see u, always reply with zh-cn"}]
  }'

curl -sS http://127.0.0.1:18789/tools/invoke   -H 'Authorization: Bearer 9fb789b9632eb69cee22aa99501d169f051777d7e47ce6cb'   -H 'Content-Type: application/json'   -d '{ "tool": "sessions_list", "args": {} }'

curl -sS http://127.0.0.1:18789/tools/invoke   -H 'Authorization: Bearer 9fb789b9632eb69cee22aa99501d169f051777d7e47ce6cb'   -H 'Content-Type: application/json'   -d '{
    "tool": "sessions_history",
    "args": {
      "sessionKey": "agent:main:openai-user:jinbe-session-001",
      "limit": 20
    }
  }'
```

```json 
  "auth": {
    "profiles": {
      "feg:default": {
        "provider": "feg",
        "mode": "api_key"
      }
    }
  },
  "models": {
    "providers": {
      "feg": {
        "baseUrl": "http://litellm.feg.cn/v1",
        "apiKey": "sk-k5UlvstW5kP4G0jd7rK1cAx",
        "api": "openai-completions",
        "models": [
          {
            "id": "kimi-k2.5",
            "name": "kimi2.5",
            "reasoning": true,
            "input": [
              "text"
            ],
            "cost": {
              "input": 0,
              "output": 0,
              "cacheRead": 0,
              "cacheWrite": 0
            },
            "contextWindow": 128000,
            "maxTokens": 8192
          }
        ]
      }
    }
  },
  "agents": {
    "defaults": {
      "model": {
        "primary": "feg/kimi-k2.5"
      },
      "models": {
        "feg/kimi-k2.5": {
          "alias": "kimi",
          "params": {
            "temperature": 1
          }
        }
      },
      "workspace": "/home/gem/.openclaw/workspace",
      "compaction": {
        "mode": "safeguard"
      },
      "maxConcurrent": 4,
      "subagents": {
        "maxConcurrent": 8
      }
    }
  },
  
```
```json  
  
  "gateway": {
    "port": 18789,
    "controlUi": {
       "allowedOrigins": [
        "http://10.17.1.26:3888"
      ],
      "allowInsecureAuth": true
    },
    "http": {
      "endpoints": {
        "chatCompletions": {
          "enabled": true
        },
        "responses": {
          "enabled": true
        }
      }
    }
  },
  
```
  
  
  

  


