---
name: cloudflare-tunnel-mobile-preview
description: |
  快速建立公開 URL 讓手機或遠端設備訪問本地開發伺服器。使用情境：(1) 手機無法連接 localhost，
  (2) 需要讓客戶/業主遠端預覽開發中的網站，(3) ngrok 需要登入但沒有帳號，
  (4) 需要 HTTPS 連線測試 PWA 或相機等功能。無需註冊、免費、一行指令搞定。
argument-hint: <port> [--background]
---

# Cloudflare Tunnel 手機預覽

> 一行指令，讓手機訪問 localhost — 無需註冊、免費、自帶 HTTPS

## Problem

開發前端專案時，想用手機測試但：
- `localhost:3000` 手機連不到
- 區域網路 IP 有時不通（防火牆、不同網段）
- ngrok 現在強制要登入
- 需要 HTTPS 才能測試 PWA、相機等功能

## Context / Trigger Conditions

- 「手機連不上」或「想用手機測試」
- 區域網路 IP 訪問失敗
- 需要讓非同網路的人預覽網站
- 需要 HTTPS 環境測試

## Solution

### 安裝

```bash
brew install cloudflared
```

### 一行指令啟動

```bash
# 假設本地伺服器在 port 3000
cloudflared tunnel --url http://localhost:3000
```

會產生類似這樣的 URL：
```
https://random-words.trycloudflare.com
```

把這個 URL 發給手機或任何人即可訪問！

### 背景執行

```bash
cloudflared tunnel --url http://localhost:3000 > /tmp/cf.log 2>&1 &
sleep 3
grep -o 'https://[^ ]*\.trycloudflare\.com' /tmp/cf.log
```

## Verification

1. 複製產生的 URL
2. 手機瀏覽器打開
3. 應該能看到本地開發中的網站

## Notes

### 優點
- **免註冊**：不需要 Cloudflare 帳號
- **免費**：Quick Tunnels 完全免費
- **HTTPS**：自動提供 SSL 憑證
- **全球可訪問**：不限同一網路

### 對比其他工具

| 工具 | 免註冊 | 免費 | HTTPS |
|------|--------|------|-------|
| **Cloudflare Tunnel** | ✅ | ✅ | ✅ |
| ngrok | ❌ | ⚠️ | ✅ |
| localtunnel | ✅ | ✅ | ✅ |

## Additional Resources

- For troubleshooting, see [references/troubleshooting.md](references/troubleshooting.md)

## References

- [Cloudflare Quick Tunnels](https://developers.cloudflare.com/cloudflare-one/connections/connect-networks/do-more-with-tunnels/trycloudflare/)

---

*Part of 🥋 AI Dojo Series by [Washin Village](https://washinmura.jp) 🐾*
