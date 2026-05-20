<p align="center">
<img width="4950" height="1238" alt="Uba Chan - AI Integrator & Automation Architect" src="https://github.com/user-attachments/assets/1454fa7e-f333-45fc-a6f5-3345c32f3ae4" />
</p>

# Hey, I'm Uba Chan 👋

**AI Integrator & Automation Architect**

I build systems that handle the work businesses are still doing by hand.

Law firms chasing client intake. E-commerce brands checking payments manually. Clinics booking appointments through phone calls. Real estate teams following up on leads one by one. The bottleneck is almost always the same — too much manual work, not enough automation.

---

## What I Build

| Area | What it means in practice |
| :--- | :--- |
| **🤖 Custom AI Agents & Chatbots** | Context-aware systems for lead gen, client support, and decision-making — running 24/7 |
| **⚡ Workflow Automation** | n8n and Zapier pipelines that connect your tools and kill repetitive tasks |
| **🔗 CRM Integration** | Pipelines that keep deals moving without someone pushing them |
| **🌐 Web & SaaS Development** | Production-ready products built around automation from day one |
| **🗄️ Database & Backend** | Supabase architecture built for scale and real-time performance |

---

## Industries

⚖️ Law Firms &nbsp;·&nbsp; 🏠 Real Estate &nbsp;·&nbsp; 🏥 Clinics &nbsp;·&nbsp; 🛍️ E-commerce &nbsp;·&nbsp; 💼 Agencies &nbsp;·&nbsp; 🚀 SaaS

---

## Currently

- 🔨 **Building:** [UreatorFlow](https://ureatorflow.pages.dev/) — AI operating studio for solo creators. And [NBGC](https://nbgc.pages.dev/) — turns raw product photos into UGC ads.
- 📚 **Learning:** Multi-Agent Orchestration and scaling SaaS with n8n + Supabase
- 🤝 **Open to:** Freelance projects, open-source automation collaboration
- 💬 **Ask me about:** n8n, AI Agents, Supabase, CRM integrations, Telegram bots

---

## Projects

### 1. AI Vibe — Client Intake Automation
A consultation form that sends personalized emails automatically. When a client submits their request, an AI Agent reads it, writes a tailored reply based on their service interest, and Gmail delivers it within seconds.

**Stack:** n8n · Google Gemini · Google Sheets · Gmail · Structured Output Parser

**Repo:** [AI-Vibe-Client-Intake-Automation](https://github.com/ubachan/AI-Vibe-Client-Intake-Automation)

---

### 2. Zero Website Order Flow — DM to Delivered
A full order management system for businesses selling through Instagram DMs. No Shopify. No website. Customers submit orders through a form, payment screenshots upload to Google Drive, fraud detection runs automatically, and the owner approves or rejects from Telegram in one tap.

**Results:** 40hrs/week → 2hrs · 12 fake orders/week → 0 · 25,430+ orders processed · 99.1% verification rate

**Stack:** n8n · Airtable · Google Drive · Google Sheets · Gmail · Telegram Bot

```mermaid
graph LR
  A[Order Form] --> B[Validate & Normalize]
  B --> C[Payment Screenshot → Drive]
  C --> D[Duplicate Check]
  D --> E[Fraud Detection]
  E -->|Clean| F[Log to Sheets + Notify Customer]
  E -->|Flagged| G[Fraud Alert → Telegram]
  F --> H[Owner Approves via Telegram]
  H -->|Approve| I[Confirmation Email + Telegram]
  H -->|Reject| J[Rejection Email + Telegram]
```

---

### 3. AI Sales Agent — Omni-Channel Facebook Messenger
An autonomous sales agent for Facebook Messenger that handles the entire sales flow — product questions via text, voice, or photo — through to inventory checking, fraud detection, and order placement. Hands off to a human when things get complex.

**Stack:** n8n · OpenAI · Google Gemini · Supabase · Pinecone · Postgres

```mermaid
graph TD
  User((User Input)) --> Webhook[n8n Webhook]
  Webhook --> Router{Input Type?}

  Router -->|Image| Vision[Gemini Vision]
  Router -->|Voice| Audio[Whisper Transcribe]
  Router -->|Text| Token[Token Check]

  Vision --> Agent
  Audio --> Agent
  Token --> Agent

  Agent["🤖 AI Sales Agent (RAG)"]

  subgraph Tools [Agent Tools & Memory]
    direction TB
    Agent <--> GSheets[("Google Sheets: Stock/Orders")]
    Agent <--> Vector[Pinecone: FAQ/RAG]
    Agent <--> Fraud[BD Courier API: Fraud Check]
    Agent <--> Handover[Supabase: Human Handoff]
    Agent <--> Memory[Postgres Chat Memory]
  end

  Agent --> Messenger[FB Messenger Reply]

  style Agent fill:#FF6D5A,color:#fff,stroke:#fff
  style Tools fill:#2D3B45,color:#fff,stroke:#fff
```

**Repo:** [AI-Sales-Agent-Omni-Channel-Automation](https://github.com/ubachan/AI-Sales-Agent-Omni-Channel-Automation.git)

---

### 4. Agentic RAG — Intelligent Knowledge Base
An AI agent that retrieves contextually relevant answers from a custom database using vector search. Built for businesses that need a chatbot that talks to their own data, not generic internet knowledge.

**Stack:** n8n · Pinecone · Groq · MongoDB

```mermaid
graph TD
  User((User Query)) --> Hook[n8n Webhook]
  Hook --> Embed[Embedding]
  Embed --> Search{Vector Search}
  Search -- Query --> PDB[(Pinecone/MongoDB)]
  PDB -- Context --> AI[AI Model]
  AI --> Result[Synthesized Answer]
  Result --> Response[Response]

  style Search fill:#f9f,stroke:#333
  style PDB fill:#27272e,stroke:#fff,color:#fff
```

---

### 5. NBGC — Photos to UGC Ads
An automation pipeline that takes raw product photos and turns them into UGC-style ad content using AI. Built for marketing agencies that produce a high volume of assets.

**Stack:** n8n · Google Gemini · Cloudflare

```mermaid
graph LR
  A[Raw Photo] --> B[Gemini Vision AI]
  B --> C[Ad Copy & Design]
  C --> D[UGC Asset Ready]
  style B fill:#8E75B2,color:#fff
```

**Live:** [nbgc.pages.dev](https://nbgc.pages.dev/)

---

### 6. UreatorFlow — AI Operating Studio
An AI-powered studio for solo creators to manage their content workflow. Handles planning, scheduling, and distribution in one place.

**Stack:** n8n · Supabase · Lovable

**Live:** [ureatorflow.pages.dev](https://ureatorflow.pages.dev/)

---

### 7. Automated WooCommerce OTP Fraud Prevention
An OTP verification layer for WooCommerce that blocks fake orders before they hit fulfillment. Verifies customer phone numbers at checkout via automated SMS.

**Stack:** n8n · WooCommerce · SMS API

**Repo:** [Automated-WooCommerce-OTP-Fraud-Prevention-System](https://github.com/ubachan/Automated-WooCommerce-OTP-Fraud-Prevention-System)

---

### 8. AI Logistics Report Documentation & Validation
An automated pipeline that processes logistics data, validates it against business rules, and generates structured reports — without anyone touching a spreadsheet.

**Stack:** n8n · Google Sheets · AI Model · PDF/Doc generation

**Repo:** [AI-Logistics-Report-Documentation-Validation](https://github.com/ubachan/AI-Logistics-Report-Documentation-Validation)

---

## Tech Stack

| Category | Tools |
| :--- | :--- |
| **Automation** | ![n8n](https://img.shields.io/badge/n8n-FF6D5A?style=flat&logo=n8n&logoColor=white) ![Zapier](https://img.shields.io/badge/Zapier-FF4A00?style=flat&logo=zapier&logoColor=white) ![Make](https://img.shields.io/badge/Make-000000?style=flat&logo=make&logoColor=white) ![Airtable](https://img.shields.io/badge/Airtable-18BFFF?style=flat&logo=airtable&logoColor=white) |
| **AI & LLM** | ![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=flat&logo=openai&logoColor=white) ![Gemini](https://img.shields.io/badge/Google_Gemini-8E75B2?style=flat&logo=googlegemini&logoColor=white) ![Anthropic](https://img.shields.io/badge/Anthropic-D97757?style=flat&logo=anthropic&logoColor=white) ![Groq](https://img.shields.io/badge/Groq-F55036?style=flat) ![Llama](https://img.shields.io/badge/Llama-04ADFF?style=flat&logo=meta&logoColor=white) |
| **AI Frameworks** | ![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=flat) ![Langflow](https://img.shields.io/badge/Langflow-000000?style=flat) ![ElevenLabs](https://img.shields.io/badge/ElevenLabs-2D3B45?style=flat) |
| **CRM & Comms** | ![GoHighLevel](https://img.shields.io/badge/GoHighLevel-00BF63?style=flat) ![Telegram](https://img.shields.io/badge/Telegram-26A5E4?style=flat&logo=telegram&logoColor=white) ![Gmail](https://img.shields.io/badge/Gmail-EA4335?style=flat&logo=gmail&logoColor=white) |
| **Database** | ![Supabase](https://img.shields.io/badge/Supabase-3ECF8E?style=flat&logo=supabase&logoColor=white) ![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=flat&logo=mongodb&logoColor=white) ![Pinecone](https://img.shields.io/badge/Pinecone-27272E?style=flat) |
| **Web Dev** | ![Next.js](https://img.shields.io/badge/Next.js-000000?style=flat&logo=nextdotjs&logoColor=white) ![React](https://img.shields.io/badge/React-61DAFB?style=flat&logo=react&logoColor=black) ![Vercel](https://img.shields.io/badge/Vercel-000000?style=flat&logo=vercel&logoColor=white) ![Cloudflare](https://img.shields.io/badge/Cloudflare-F38020?style=flat&logo=cloudflare&logoColor=white) |
| **Dev Tools** | ![Cursor](https://img.shields.io/badge/Cursor-02BDD3?style=flat) ![VS Code](https://img.shields.io/badge/VS_Code-007ACC?style=flat&logo=visual-studio-code&logoColor=white) ![Lovable](https://img.shields.io/badge/Lovable-FF00FF?style=flat) |

---

## GitHub Stats

![Uba's GitHub Stats](https://github-readme-stats-eight-theta.vercel.app/api?username=ubachan&show_icons=true&theme=radical&hide_border=true)

---

## Connect

Solo engineer. Select projects. Deep work.

[<img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" />](https://www.linkedin.com/in/ubachan)
[<img src="https://img.shields.io/badge/Website-000000?style=for-the-badge&logo=safari&logoColor=white" />](https://ubachan.site)
[<img src="https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white" />](mailto:aivibe@ubachan.com)
[<img src="https://img.shields.io/badge/WhatsApp-25D366?style=for-the-badge&logo=whatsapp&logoColor=white" />](https://wa.me/8801847791609)
