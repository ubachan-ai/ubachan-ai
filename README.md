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
| **⚡ Workflow Automation** | n8n and Zapier pipelines that connect your tools and eliminate repetitive tasks |
| **🔗 CRM Integration** | Pipelines that keep deals moving without someone pushing them |
| **🌐 Web & SaaS Development** | Production-ready products built around automation from day one |
| **🗄️ Database & Backend** | Supabase architecture built for scale and real-time performance |

---

## Industries

⚖️ Law Firms &nbsp;·&nbsp; 🏠 Real Estate &nbsp;·&nbsp; 🏥 Clinics &nbsp;·&nbsp; 🛍️ E-commerce &nbsp;·&nbsp; 💼 Agencies &nbsp;·&nbsp; 🚀 SaaS

---

## Projects

### 1. AI Sales Agent — Omni-Channel Facebook Messenger Automation

An autonomous sales agent for Facebook Messenger that handles the full sales cycle — product questions via text, voice, or photo — through to inventory checking, fraud detection, and order placement. Transfers to a human agent when the situation needs it.

**Stack:** n8n · OpenAI · Google Gemini · Supabase · Pinecone · Postgres

```mermaid
flowchart TD
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
  style Tools fill:#2D3B45,color:#fff
```

**Key Features:**
- Gemini Vision identifies products from customer photos
- OpenAI Whisper transcribes and understands voice notes in real time
- Real-time inventory sync with Google Sheets — checks stock before confirming
- BD Courier API fraud scoring on COD orders before acceptance
- Pinecone vector DB for FAQ and policy retrieval
- Postgres memory keeps conversation context across sessions
- Supabase-triggered human handoff when complex support is needed

**Repo:** [AI-Sales-Agent-Omni-Channel-Automation](https://github.com/ubachan/AI-Sales-Agent-Omni-Channel-Automation.git)

---

### 2. From DM to Delivered — Zero Website Order Flow

A full order management system for businesses selling through Instagram or Facebook DMs. No Shopify. No website. Customers submit orders through a form, payment screenshots upload to Google Drive automatically, fraud detection runs, and the owner approves or rejects from Telegram in one tap.

**Results:** 40hrs/week → 2hrs &nbsp;·&nbsp; 12 fake orders/week → 0 &nbsp;·&nbsp; 25,430+ orders processed &nbsp;·&nbsp; 99.1% verification rate &nbsp;·&nbsp; <1.5s response time

**Stack:** n8n · Airtable · Google Drive · Google Sheets · Gmail · Telegram Bot

```mermaid
graph TD
  A[Customer Order Form] --> B[Validate & Normalize Order]
  B --> C[Payment Screenshot → Google Drive]
  C --> D[Attach Screenshot URL]
  D --> E[Duplicate Data Check]
  E --> F[Fraud Detection Logic]
  F --> G{Duplicate or Fraud?}

  G -->|True| H[Send Fraud Alert via Telegram]
  G -->|False| I[Log Order to Google Sheets]
  I --> J[Send Order Placed - Gmail + Telegram]

  K[Telegram Callback] --> L[Parse Callback Data]
  L --> M[Fetch Order from Sheet]
  M --> N[Merge Order Data]
  N --> O{Owner Decision}

  O -->|Approve| P[Status: Confirmed]
  O -->|Reject| Q[Status: Rejected]
  O -->|Fraud| R[Status: Fraud]

  P --> P1[Send Confirmation - Gmail + Telegram]
  Q --> Q1[Send Rejection - Gmail + Telegram]
  R --> R1[Send Fraud Message - Gmail + Telegram]

  style G fill:#f9a,stroke:#333
  style O fill:#f9a,stroke:#333
```

**Repo:** [From-DM-to-Delivered-Zero-Website-Order-Flow](https://github.com/ubachan/From-DM-to-Delivered-Zero-Website-Order-Flow)

---

### 3. Agentic RAG — Intelligent Knowledge Base

An AI agent that retrieves contextually relevant answers from a custom database using vector search. Built for businesses that need a chatbot trained on their own data — not generic internet knowledge.

**Stack:** n8n · Pinecone · Groq · MongoDB

```mermaid
graph TD
  User((User Query)) --> Hook[n8n Webhook]
  Hook --> Embed[Generate Embedding]
  Embed --> Search{Vector Search}
  Search -- Query --> PDB[(Pinecone / MongoDB)]
  PDB -- Retrieved Context --> AI[AI Language Model]
  AI --> Result[Synthesized Answer]
  Result --> Response[Return to User]

  style Search fill:#f9f,stroke:#333
  style PDB fill:#27272e,stroke:#fff,color:#fff
```

**Key Features:**
- Intent recognition before retrieval
- Dynamic context injection based on query similarity
- Low-latency responses via Groq inference
- Works with any structured or unstructured business data

**Use Case:** Custom AI chatbots for law firms, clinics, and agencies that need to answer questions from their own documents and policies.

---

### 4. Automated WooCommerce OTP Fraud Prevention

An OTP verification layer for WooCommerce that blocks fake orders before they reach fulfillment. Verifies customer phone numbers at checkout via automated SMS, adds a confirmation step that most fraud bots and fake buyers won't complete.

**Stack:** n8n · WooCommerce · SMS API · Google Sheets

```mermaid
graph LR
  A[Customer Places Order] --> B[n8n Webhook Triggered]
  B --> C[Generate OTP Code]
  C --> D[Send SMS to Customer Phone]
  D --> E{OTP Verified?}
  E -->|Yes| F[Order Confirmed in WooCommerce]
  E -->|No / Timeout| G[Order Cancelled + Alert]
  F --> H[Log to Google Sheets]

  style E fill:#f9a,stroke:#333
```

**Repo:** [Automated-WooCommerce-OTP-Fraud-Prevention-System](https://github.com/ubachan/Automated-WooCommerce-OTP-Fraud-Prevention-System)

---

### 5. AI Logistics Report — Documentation & Validation

An automated pipeline that processes logistics data, validates it against business rules, flags errors, and generates structured reports. Removes the manual spreadsheet work from operations and compliance teams.

**Stack:** n8n · Google Sheets · AI Model · PDF/Doc generation

```mermaid
graph LR
  A[Raw Logistics Data] --> B[n8n Trigger]
  B --> C[Data Validation Layer]
  C --> D{Passes Rules?}
  D -->|Yes| E[AI Report Generation]
  D -->|No| F[Flag Errors + Notify Team]
  E --> G[Export PDF / Doc]
  G --> H[Send to Stakeholders]

  style D fill:#f9a,stroke:#333
```

**Repo:** [AI-Logistics-Report-Documentation-Validation](https://github.com/ubachan/AI-Logistics-Report-Documentation-Validation)

---

### 6. NBGC — Photos to UGC Ads

An automation pipeline that takes raw product photos and turns them into UGC-style ad content using AI vision and copy generation. Built for marketing agencies producing high volumes of creative assets.

**Stack:** n8n · Google Gemini · Cloudflare

```mermaid
graph LR
  A[Raw Product Photo] --> B[Gemini Vision Analysis]
  B --> C[AI Ad Copy Generation]
  C --> D[Asset Design & Formatting]
  D --> E[UGC-Ready Ad Asset]

  style B fill:#8E75B2,color:#fff
```

**Live:** [nbgc.pages.dev](https://nbgc.pages.dev/)

---

### 7. UreatorFlow — AI Operating Studio for Solo Creators

An AI-powered studio that manages the full content workflow for solo creators — planning, scheduling, and distribution in one automated system.

**Stack:** n8n · Supabase · Lovable

```mermaid
graph LR
  A[Content Idea Input] --> B[AI Content Planner]
  B --> C[Schedule & Queue]
  C --> D[Auto Distribute]
  D --> E[Facebook]
  D --> F[Instagram]
  D --> G[Other Platforms]

  style B fill:#3ECF8E,color:#fff
```

**Live:** [ureatorflow.pages.dev](https://ureatorflow.pages.dev/)

---

### 8. AI Vibe — Client Intake Automation

A consultation form that sends personalized reply emails automatically. When a client submits their request, an AI Agent reads it, writes a tailored email based on their specific service interest, and Gmail delivers it within seconds. No manual follow-up needed.

**Stack:** n8n · Google Gemini · Google Sheets · Gmail · Structured Output Parser

```mermaid
graph LR
  A[Client Submits Form] --> B[Log to Google Sheets]
  B --> C[AI Agent Reads Request]
  C --> D[Structured Output Parser]
  D --> E[Subject + Body Extracted]
  E --> F[Gmail Sends Personalized Email]

  style C fill:#8E75B2,color:#fff
```

**Repo:** [AI-Vibe-Client-Intake-Automation](https://github.com/ubachan/AI-Vibe-Client-Intake-Automation)

---

## Currently

- 🔨 **Building:** [UreatorFlow](https://ureatorflow.pages.dev/) — AI operating studio for solo creators &nbsp;·&nbsp; [NBGC](https://nbgc.pages.dev/) — product photos to UGC ads
- 📚 **Learning:** Multi-Agent Orchestration and scaling SaaS with n8n + Supabase
- 🤝 **Open to:** Freelance projects and open-source automation collaboration
- 💬 **Ask me about:** n8n, AI Agents, Supabase, CRM integrations, Telegram bots

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
