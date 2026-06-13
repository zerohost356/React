# TempMail

<div align="center">

![Next.js](https://img.shields.io/badge/Next.js-15-black?style=flat-square&logo=next.js&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6?style=flat-square&logo=typescript&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-v4-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white)
![License](https://img.shields.io/badge/license-MIT-22c55e?style=flat-square)
![Build](https://img.shields.io/badge/build-passing-22c55e?style=flat-square)

**Free disposable email — generate random or custom addresses and receive mail instantly, no signup required.**

🌐 **Live:** [tempmail-gpt.onrender.com](https://tempmail-gpt.onrender.com)

</div>

---

## Features

- Generate random or custom temporary email addresses
- **Real-time** inbox via Server-Sent Events (SSE) with auto-polling fallback
- Desktop push notifications for new emails
- View emails in HTML or plain text
- Address history saved in browser (up to 8 recent addresses)
- Live global statistics (emails in last 24h, active domains)
- One-click inbox clear
- 1,200+ available domains

## Tech Stack

| Technology | Version |
|---|---|
| [Next.js](https://nextjs.org/) | 15 (Pages Router) |
| [TypeScript](https://www.typescriptlang.org/) | 5 |
| [Tailwind CSS](https://tailwindcss.com/) | v4 |
| [Axios](https://axios-http.com/) | 1.x |

---

## Getting Started

### Prerequisites

- **Node.js** >= 18
- **npm** >= 9

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/zerohost356/TempMail.git
cd TempMail

# 2. Install dependencies
npm install

# 3. Start the development server
npm run dev
```

Open [http://localhost:5000](http://localhost:5000) in your browser.

### Scripts

| Command | Description |
|---------|-------------|
| `npm run dev` | Development server on port 5000 |
| `npm run build` | Production build |
| `npm run start` | Production server on port 5000 |
| `npm run lint` | Run ESLint |

---

## Deployment

### Deploy to Render

1. Fork or push this repo to GitHub
2. Go to [render.com](https://render.com) → **New Web Service**
3. Connect your GitHub repo (`zerohost356/React`)
4. Use these settings:

| Setting | Value |
|---------|-------|
| **Build Command** | `npm install && npm run build` |
| **Start Command** | `npm run start` |
| **Environment** | `NODE_ENV=production` |

Render will auto-detect `render.yaml` and apply the correct configuration.

### render.yaml

```yaml
services:
  - type: web
    name: tempmail
    runtime: node
    buildCommand: npm install && npm run build
    startCommand: npm run start
    envVars:
      - key: NODE_ENV
        value: production
```

> No API keys required — the app auto-manages upstream sessions.

---

## API Reference

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/domains` | List available email domains |
| `GET` | `/api/generator-email` | Generate a random email address |
| `GET` | `/api/custom-email?username=&domain=` | Generate a custom email address |
| `GET` | `/api/inbox?inbox=` | Fetch emails for an inbox |
| `GET` | `/api/email/[id]?inbox=` | Get a specific email's full content |
| `DELETE` | `/api/clear?inbox=` | Delete all emails in an inbox |
| `GET` | `/api/stats` | Global usage statistics |
| `GET` | `/api/stream?inbox=` | SSE stream for real-time updates |

---

## Project Structure

```
├── components/
│   └── Layout.tsx          # Shared layout (header, navigation)
├── lib/
│   ├── tempmail.ts         # Upstream service integration & auth
│   └── cookies.ts          # Cookie helpers
├── pages/
│   ├── index.tsx           # Inbox & email generator
│   ├── docs.tsx            # API documentation
│   ├── statistics.tsx      # Live statistics
│   ├── domains.tsx         # Available domains
│   └── api/                # API route handlers
├── public/                 # Static assets (icons, manifest)
├── styles/                 # Global CSS (Tailwind v4)
├── render.yaml             # Render deployment config
└── cache/                  # Next.js telemetry config
```

---

## License

MIT
