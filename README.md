# Niagara AI Agent 🧠

 ![Niagara 4.14+](https://img.shields.io/badge/Niagara-4.14%2B-blue)](https://www.tridium.com)
!![License: Commercial](https://img.shields.io/badge/License-Commercial-orange)](LICENSE)
!![Contact](https://img.shields.io/badge/Contact-WhatsApp-brightgreen)](https://wa.me/8613801909968)
!![Vendor](https://img.shields.io/badge/Vendor-Shanghai%20Gline%20Net-lightgrey)](https://www.glineweb.com)

> **Bring AI into your Niagara Station — query, analyze, automate, and decide, in natural language.**

---

## What Is It?

The Niagara AI Agent is a native Niagara 4 module that connects your station to large language models via the OpenAI-compatible API format. Instead of writing BQL queries by hand or clicking through Workbench, you can **ask questions in plain English** and get structured results written directly into Niagara points and histories.

> ✅ **Tested with:** DeepSeek via OpenAI-compatible API  
> 🔧 **Compatible with:** Any LLM that supports the OpenAI API format (GPT-4o, local ollama, vLLM, LM Studio, etc.) — not individually tested but expected to work.

---

## Real-World Examples

| You Ask | The AI Agent Does |
|---------|-------------------|
| *"What's the current temperature on floor 3?"* | Runs a BQL query, returns the value to a Niagara point |
| *"Compare today's energy usage to last Tuesday"* | Pulls history data, runs the comparison, writes result |
| *"Alert me if any AHU supply temp exceeds 28°C"* | Sets up an alarm condition using natural language |
| *"Summarize yesterday's alarms in zone B1"* | Queries alarm console, formats a summary, stores it |
| *"Generate a daily energy report and email it"* | Aggregates metering data, composes report, triggers email |

---

## Quick Start

### Option A — Use our pre-signed JAR (gline.pem)

```bash
# 1. Install gline.pem certificate into your station trust store
#    (available in this repository under /certs/)

# 2. Deploy the module
#    Place AIbotAgent-rt.jar in your Niagara modules/ directory

# 3. Get a trial license
#    Send your Host ID → jason.zhang@gline-net.com
#    We'll reply with a temporary license within 24 hours

# 4. Configure your AI provider
#    Open the AI Agent service in Workbench:
#    - Set base URL: https://api.deepseek.com (or your LLM endpoint)
#    - Enter your API key (encrypted with included ApiKeyEncryption tool)
#    - Choose your model name

# 5. Start asking questions
#    Wire the AI Agent input/output to any Niagara ControlPoint
```

### Option B — Custom certificate signing

If your organization requires a certificate signed with your own key:

```bash
# 1. Provide us with your certificate file (.pem) and password
# 2. We recompile and re-sign the JAR with your certificate
# 3. Deploy the custom-signed JAR to your station
# 4. No external certificate installation needed
```

Contact us for custom signing requests.

---

## Features

### 🔌 AI Provider Support

| Provider | Status | Notes |
|----------|--------|-------|
| **DeepSeek** | ✅ Tested | Recommended for cost efficiency |
| **OpenAI (GPT-4o, etc.)** | 🔧 Expected to work | OpenAI-compatible format |
| **Local LLM (ollama, vLLM)** | 🔧 Expected to work | Set your local endpoint as base URL |
| **Any OpenAI-compatible API** | 🔧 Expected to work | Same format, not individually tested |

### 🔗 Native Niagara Integration

- Queries BQL / NEQL and returns structured results
- Writes outputs directly to ControlPoints, histories, and alarm summaries
- Works inside PX pages, Program objects, and Workbench
- Low-latency async design — won't block your station

### 🛠 Auxiliary Tools Included

| Tool | Purpose |
|------|---------|
| **TokenCalculator** | Estimate token usage before calling the API |
| **HeapMonitor** | Monitor JACE memory impact in real time |
| **ApiKeyEncryption** | Securely store provider API keys in station database |
h

### 🔐 Security

- API keys encrypted at rest in station database
- No external outbound calls except to the configured LLM endpoint
- Optional on-premise / air-gapped LLM support for sensitive sites
- JAR can be re-signed with your own certificate on request

---

## Pricing

| Tier | License | Price | Best For |
|:-----:|---------|:-----:|----------|
| 🆓 | **Trial** | **Free** | Evaluation, testing, proof-of-concept |
| 🥇 | **Single Station** | **$299** | One JACE / Supervisor |
| 🏢 | **Site Pack (5 stations)** | **$999** | Multi-controller projects |
| 🌐 | **Enterprise** | **Contact us** | Large deployments, OEM, white-label |

> Trial license is valid for 30 days. No credit card required.
> All commercial licenses include 12 months of updates and email support.

---

## Requirements

| Component | Requirement |
|-----------|-------------|
| **Niagara Version** | 4.14 or later (JACE, Edge, Supervisor, Windows) |
| **JAR Signing** | Pre-signed with gline.pem, or custom-signed with your certificate on request |
| **Network** | Outbound HTTPS to your LLM provider |
| **JACE Memory** | 512 MB+ heap recommended (tested on JACE-8000) |

---

## FAQ

**Q: Do I need an internet connection?**  
A: Yes, to reach the LLM API. For air-gapped deployments, we support on-premise local LLMs via custom endpoint configuration.

**Q: Which LLMs have you tested?**  
A: We have tested DeepSeek (via OpenAI-compatible API). Any LLM that supports the OpenAI API format should work, but has not been individually tested.

**Q: Does the AI module impact JACE performance?**  
A: Each inference call is asynchronous and lightweight (non-blocking). Use the included HeapMonitor to verify on your hardware.

**Q: Can I use my own API key?**  
A: Yes. Configure any OpenAI-compatible endpoint with your own key. All keys are encrypted at rest.

**Q: How long does a query take?**  
A: Typically 1–5 seconds depending on LLM provider and query complexity.

**Q: Is the trial fully functional?**  
A: Yes — full features, no limitations. Only the license duration (30 days) is restricted.

**Q: Can I use my own certificate instead of gline.pem?**  
A: Yes. Provide us with your certificate and password. We will recompile and re-sign the JAR with your certificate at no additional charge.

---

## Repository Contents

```
├── AIbotAgent-rt.jar       ← Pre-signed module (gline.pem)
├── certs/
│   └── gline.pem           ← Default certificate
├── LICENSE
├── README.md
└── src/                    ← Source code (available on request)
```

---

## Support & Contact

- **Email**: [jason.zhang@gline-net.com](mailto:jason.zhang@gline-net.com)
- **WhatsApp**: [+86 138 0199 0968](https://wa.me/8613801909968)
- **Web**: [www.glineweb.com](https://www.glineweb.com)

**Shanghai Gline Net Co., Ltd.** — Your Partner in Smarter Automation

---

## License

This module is provided under a **proprietary commercial license**.

- **Free Trial**: 30-day evaluation, fully functional
- **Commercial**: Paid license required for production use

See [LICENSE](./LICENSE) for full terms.

© 2026 Shanghai Gline Net Co., Ltd. All rights reserved.
