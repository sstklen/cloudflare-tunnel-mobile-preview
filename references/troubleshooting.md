# Troubleshooting Guide

## 常見問題

### Q: cloudflared 指令找不到？

```bash
# 安裝
brew install cloudflared

# 確認安裝
which cloudflared
```

### Q: URL 每次都不一樣？

這是 Quick Tunnel 的特性。每次啟動會產生新的隨機 URL。

如需固定 URL，需要：
1. 註冊 Cloudflare 帳號
2. 設定 Named Tunnel

### Q: 手機還是連不上？

確認：
1. 手機有網路連線
2. URL 複製正確（包含 https://）
3. cloudflared 程序還在運行

### Q: 怎麼停止 tunnel？

```bash
# 如果在前台運行
Ctrl + C

# 如果在背景運行
pkill cloudflared
```

### Q: 可以同時開多個 tunnel 嗎？

可以，指定不同的 port：

```bash
cloudflared tunnel --url http://localhost:3000 &
cloudflared tunnel --url http://localhost:8080 &
```

## 進階用法

### 腳本化

```bash
#!/bin/bash
# start-preview.sh

PORT=${1:-3000}
LOG="/tmp/cloudflared-$PORT.log"

cloudflared tunnel --url "http://localhost:$PORT" > "$LOG" 2>&1 &
sleep 3

URL=$(grep -o 'https://[^ ]*\.trycloudflare\.com' "$LOG")
echo "🌐 Preview URL: $URL"
echo "$URL" | pbcopy
echo "📋 URL copied to clipboard!"
```

使用：
```bash
./start-preview.sh 3000
```

### 搭配 npm scripts

```json
{
  "scripts": {
    "dev": "next dev",
    "preview": "cloudflared tunnel --url http://localhost:3000"
  }
}
```

```bash
npm run dev &
npm run preview
```
