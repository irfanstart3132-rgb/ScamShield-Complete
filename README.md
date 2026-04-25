# 🛡️ ScamShield — AI Trust Layer for Digital Communications

<div align="center">

**"Protecting every digital interaction with enterprise-grade AI"**

![License](https://img.shields.io/badge/license-MIT-blue)
![Node](https://img.shields.io/badge/node-%3E%3D18.0-green)
![Status](https://img.shields.io/badge/status-active%20development-success)
![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen)
![Version](https://img.shields.io/badge/version-1.0.0-blue)

[🌐 Live Demo](#) · [📚 API Docs](#) · [🐛 Report Bug](../../issues) · [💡 Request Feature](../../issues)

</div>

---

## 📌 What is ScamShield?

ScamShield is a **production-ready, AI-powered scam detection platform** that protects users from phishing, fraud, and social engineering attacks in real-time. Built with transformer models, vector search, and multi-layered threat intelligence — it works across every channel scammers use.

> Built because 1 in 4 adults get scammed, and no comprehensive solution exists for everyday consumers.

---

## 🔥 The Problem We're Solving

| Stat | Source |
|------|--------|
| **$8.8 Billion** lost to scams annually | FTC 2022 |
| **1 in 4 adults** will be targeted by a scam | AARP |
| **70% YoY increase** in AI-powered scam attacks | Cybersecurity Ventures |
| **$3,000 average** loss per victim | FTC |

Existing tools are fragmented — antivirus protects your device, but nothing protects your *conversations*, *links*, or *calls* in real time.

---

## ✨ What ScamShield Does

### For Consumers
| Feature | Description |
|---------|-------------|
| 📧 **Message Scanning** | Analyze SMS, email, and chat messages in <200ms |
| 🔗 **URL Safety Check** | Verify any link before clicking |
| 📱 **WhatsApp Protection** | Guard family group chats automatically |
| 📞 **Voice Call Analysis** | Detect phone scam patterns in real time |
| 🌐 **Browser Extension** | Chrome & Firefox real-time page protection |
| 👥 **Community Database** | Crowd-sourced scam reporting and alerts |

### For Developers & Businesses
| Feature | Description |
|---------|-------------|
| 🔌 **RESTful API** | Integrate scam detection into any product |
| ⚡ **WebSocket Support** | Real-time streaming analysis |
| 📦 **SDK (JS/Python)** | Drop-in library for quick implementation |
| 🐳 **Docker Ready** | Single-command deployment |
| 📊 **Analytics Dashboard** | Threat intelligence and reporting |
| 🏢 **White-label Option** | Enterprise branding support |

---

## 🏗️ System Architecture

```
┌──────────────────────────────────────────────────────────────┐
│                      DISTRIBUTION LAYER                      │
│   Browser Extension  │  WhatsApp Bot  │  API  │  Mobile App  │
└──────────────────────┬───────────────────────────────────────┘
                       │
┌──────────────────────▼───────────────────────────────────────┐
│                       API GATEWAY                            │
│         Auth  •  Rate Limiting  •  Caching  •  Queue         │
└──────────────────────┬───────────────────────────────────────┘
                       │
┌──────────────────────▼───────────────────────────────────────┐
│                    DETECTION ENGINE                          │
│                                                              │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────────────┐  │
│  │ Transformer │  │   Vector    │  │   Threat Intel      │  │
│  │  (Text ML)  │  │   Search    │  │   (Live Feeds)      │  │
│  └─────────────┘  └─────────────┘  └─────────────────────┘  │
│                                                              │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────────────┐  │
│  │    URL      │  │ Behavioral  │  │   Reputation        │  │
│  │  Analysis   │  │  Analysis   │  │   Scoring           │  │
│  └─────────────┘  └─────────────┘  └─────────────────────┘  │
└──────────────────────────────────────────────────────────────┘
                       │
┌──────────────────────▼───────────────────────────────────────┐
│                       DATA LAYER                             │
│      PostgreSQL  •  Redis Cache  •  Pinecone Vectors         │
└──────────────────────────────────────────────────────────────┘
```

---

## 🚀 Quick Start

### Prerequisites
- Node.js >= 18.0
- npm or yarn
- Git
- Docker (optional but recommended)

### 1. Clone & Install

```bash
git clone https://github.com/YOUR_USERNAME/scamshield.git
cd scamshield

# Install backend
cd backend/api-gateway
npm install

# Copy environment file
cp .env.example .env
```

### 2. Configure Environment

Edit `.env` with your API keys (see [Configuration](#-configuration) below):

```bash
# Minimum required for local dev
OPENAI_API_KEY=sk-your-key-here
JWT_SECRET=any-random-secret-string
PORT=3000
```

### 3. Start Development Server

```bash
npm run dev
# Server starts at http://localhost:3000
```

### 4. Test the API

```bash
curl -X POST http://localhost:3000/api/scan/message \
  -H "Content-Type: application/json" \
  -d '{"message": "Congratulations! You won $1,000. Click here to claim."}'
```

### Docker Alternative

```bash
docker-compose up -d
docker-compose logs -f
```

---

## 📦 Project Structure

```
scamshield/
├── frontend/
│   ├── extension/              # Chrome/Firefox browser extension
│   │   ├── manifest.json
│   │   ├── popup.html
│   │   └── background.js
│   └── dashboard/              # Analytics & user dashboard
│
├── backend/
│   ├── api-gateway/            # Main API server (Express)
│   │   ├── server.js
│   │   ├── package.json
│   │   ├── middleware/
│   │   │   ├── auth.js         # JWT authentication
│   │   │   └── rateLimiter.js  # Per-plan rate limiting
│   │   └── routes/
│   │       ├── scan.js         # Core analysis endpoints
│   │       └── report.js       # Community reporting
│   │
│   ├── detection-engine/       # Core AI & ML analysis
│   │   ├── index.js
│   │   ├── classifiers/
│   │   │   ├── url-analyzer.js
│   │   │   ├── text-analyzer.js
│   │   │   └── voice-analyzer.js
│   │   ├── models/
│   │   │   ├── phishing-detector.js
│   │   │   └── threat-scorer.js
│   │   ├── embeddings/
│   │   │   └── semantic-search.js
│   │   └── intelligence/
│   │       ├── threat-feeds.js
│   │       └── reputation.js
│   │
│   └── workers/                # Background async jobs
│       ├── url-scanner.js
│       └── email-analyzer.js
│
├── docs/
│   ├── API.md
│   ├── DEPLOYMENT.md
│   └── ARCHITECTURE.md
│
├── docker-compose.yml
├── .env.example
├── .gitignore
├── LICENSE
└── README.md
```

---

## 🔧 Configuration

### Required API Keys

| Service | Purpose | Free Tier | Get Key |
|---------|---------|-----------|---------|
| OpenAI | Text & NLP analysis | $5 credit | [openai.com](https://openai.com) |
| Pinecone | Vector similarity search | 1 index free | [pinecone.io](https://pinecone.io) |
| Upstash Redis | Response caching | 256MB free | [upstash.com](https://upstash.com) |
| VirusTotal | URL reputation | 500 req/day free | [virustotal.com](https://virustotal.com) |

### Full `.env` Reference

```bash
# Server
PORT=3000
NODE_ENV=development
JWT_SECRET=your-256-bit-secret

# AI Provider
OPENAI_API_KEY=sk-your-key-here
OPENAI_MODEL=gpt-4-turbo

# Vector Database (Semantic Search)
PINECONE_API_KEY=your-pinecone-key
PINECONE_ENVIRONMENT=us-east-1-aws
PINECONE_INDEX_NAME=scamshield

# Cache
REDIS_URL=redis://localhost:6379

# URL Threat Intelligence
VIRUSTOTAL_API_KEY=your-virustotal-key

# Optional: SMS scanning
TWILIO_ACCOUNT_SID=your-twilio-sid
TWILIO_AUTH_TOKEN=your-twilio-token
```

---

## 📚 API Reference

### Base URL
```
https://api.scamshield.io/v1
```

### Endpoints

#### Scan a Message
```http
POST /api/scan/message
Authorization: Bearer <jwt_token>
Content-Type: application/json

{
  "message": "string (required)",
  "language": "en (optional)",
  "context": "sms|email|whatsapp (optional)"
}
```

**Response:**
```json
{
  "risk_score": 0.92,
  "verdict": "HIGH_RISK",
  "category": "phishing",
  "confidence": 0.94,
  "explanation": "Message contains urgency triggers and suspicious domain link.",
  "flags": ["urgency_language", "suspicious_url", "prize_claim"],
  "safe_to_proceed": false
}
```

#### Scan a URL
```http
POST /api/scan/url
Authorization: Bearer <jwt_token>

{
  "url": "https://example-suspicious-site.com",
  "deep_scan": true
}
```

#### Report a Scam
```http
POST /api/report
Authorization: Bearer <jwt_token>

{
  "content": "string",
  "type": "message|url|phone",
  "scammer_info": {}
}
```

---

## 💰 Pricing Model

| Plan | Price | Scans/Day | Features |
|------|-------|-----------|----------|
| **Free** | $0 | 100 | Message + URL scanning |
| **Pro** | $4.99/mo | Unlimited | + Voice analysis, browser extension |
| **Family** | $14.99/mo | Unlimited × 6 | + All Pro features for 6 members |
| **Enterprise** | Custom | Unlimited | + API access, white-label, SLA, SSO |

---

## 🗺️ Roadmap

### v1.0 — Current ✅
- [x] Core detection engine (text + URL)
- [x] API Gateway with auth & rate limiting
- [x] Browser extension (MVP)
- [x] Community scam reporting

### v1.1 — In Progress 🚧
- [ ] Fine-tuned scam detection model (Pakistani/Urdu context)
- [ ] WhatsApp Business API integration
- [ ] Advanced analytics dashboard
- [ ] Mobile app (React Native)

### v2.0 — Planned 🔮
- [ ] Real-time voice call scam detection
- [ ] OS-level protection (Windows / Mac)
- [ ] Banking API integration for transaction screening
- [ ] Multi-language support (Urdu, Arabic, Hindi)
- [ ] Enterprise SSO & compliance (SOC2, GDPR)

---

## 📊 Performance Targets

| Metric | Target |
|--------|--------|
| Average response time | < 200ms |
| Detection accuracy | 95%+ |
| False positive rate | < 3% |
| API uptime | 99.9% |
| Max concurrent users | 10,000+ |

---

## 🛡️ Security Design

- ✅ All API keys stored **server-side only** — never in frontend code
- ✅ JWT authentication with rotating refresh tokens
- ✅ Per-plan rate limiting to prevent abuse
- ✅ Input sanitization and validation on all endpoints
- ✅ CORS protection and Helmet.js security headers
- ✅ Regular dependency audits (`npm audit`)
- ✅ Environment-based secret management (never committed to git)

---

## 🧪 Testing

```bash
# Run all tests
npm test

# Run with coverage report
npm run test:coverage

# Test specific module
npm test -- detection-engine

# Run integration tests
npm run test:integration
```

---

## 🤝 Contributing

We welcome contributions! Here's how to get started:

### Good First Issues
- Add new scam patterns to the detection database
- Improve URL analysis accuracy
- Add Urdu/regional language support
- Write or improve documentation
- Add test coverage for edge cases

### Steps

```bash
# 1. Fork the repository
# 2. Create your feature branch
git checkout -b feature/your-feature-name

# 3. Make your changes and commit
git commit -m "feat: add amazing feature"

# 4. Push to your branch
git push origin feature/your-feature-name

# 5. Open a Pull Request
```

See [CONTRIBUTING.md](./CONTRIBUTING.md) for detailed guidelines.

---

## 📄 License

This project is licensed under the **MIT License** — see [LICENSE](./LICENSE) for details.

---

## 👨‍💻 Author

**Irfan Khan**

- 📧 Email: irfanstart3132@gmail.com
- 💼 LinkedIn: https://www.linkedin.com/in/irfan-khan-61a083287?utm_source=share_via&utm_content=profile&utm_medium=member_android
- 🐙 GitHub: https://github.com/irfanstart3132-rgb

---

<div align="center">

Built with ❤️ to protect people from digital scams.

*If you've ever had a family member almost fall for a scam, you know why this matters.*

⭐ **Star this repo if ScamShield helps you — it helps others find it too!**

</div>
