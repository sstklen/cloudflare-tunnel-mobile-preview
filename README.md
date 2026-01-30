# 📱 Cloudflare Tunnel Mobile Preview

> **One command to preview localhost on mobile** — No signup, free, instant HTTPS!

[![Made by Washin Village](https://img.shields.io/badge/Made%20by-Washin%20Village%20🐾-orange)](https://washinmura.jp)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-Skill-blue)](https://claude.ai/code)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

---

## 😫 The Problem

```
You: *developing on localhost:3000*
You: "Let me test on my phone..."
Phone: "This site can't be reached"
You: *tries ngrok*
ngrok: "Please sign up first"
You: 😭
```

## 😊 The Solution

```bash
cloudflared tunnel --url http://localhost:3000
# → https://random-words.trycloudflare.com
# Send this URL to your phone. Done!
```

---

## 🎯 Features

| Feature | Cloudflare Tunnel | ngrok | localtunnel |
|---------|-------------------|-------|-------------|
| **No signup** | ✅ | ❌ | ✅ |
| **Free** | ✅ | ⚠️ Limited | ✅ |
| **HTTPS** | ✅ | ✅ | ✅ |
| **Reliable** | ✅ | ✅ | ⚠️ |

---

## 🚀 Quick Start

### 1. Install

```bash
brew install cloudflared
```

### 2. Use

```bash
# Start your dev server
npm run dev  # localhost:3000

# Create public URL
cloudflared tunnel --url http://localhost:3000
```

### 3. Share

Copy the generated URL (e.g., `https://random-words.trycloudflare.com`) and open it on any device!

---

## 📱 Use Cases

- **Mobile testing**: Test responsive design on real devices
- **Client preview**: Share work-in-progress with clients
- **PWA testing**: Needs HTTPS for service workers
- **Camera/GPS**: Browser APIs require secure context
- **Team review**: Share with teammates on different networks

---

## 🔧 Advanced Usage

### Background Mode

```bash
cloudflared tunnel --url http://localhost:3000 > /tmp/cf.log 2>&1 &
sleep 3
grep -o 'https://[^ ]*\.trycloudflare\.com' /tmp/cf.log
```

### npm Script

```json
{
  "scripts": {
    "preview": "cloudflared tunnel --url http://localhost:3000"
  }
}
```

---

## 🐾 About Washin Village

This skill is made by **Washin Village (和心村)** — a sanctuary for 28 cats and dogs in Japan's Boso Peninsula.

We build AI tools to help animals get seen by the world. Every star ⭐ helps us rescue more animals!

🌐 [washinmura.jp](https://washinmura.jp)

---

## 📄 License

MIT License - Feel free to use, modify, and share!

---

<p align="center">
  <b>Made with 🐾 by 28 cats & dogs from Japan</b><br>
  <a href="https://washinmura.jp">Washin Village</a>
</p>
