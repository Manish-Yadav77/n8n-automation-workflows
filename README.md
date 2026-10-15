# n8n AI Automation Workflows

A collection of production-ready n8n workflows for automated ATS resume tailoring, PDF generation, email classification, and real-time WhatsApp alerts. Built to handle complex prompt engineering, LLM microservices, and external webhook triggers.

## Developer

- **Name**: Manish Kumar Yadav
- **Role**: Full Stack Developer
- **Portfolio**: [manishportfolio7.netlify.app](https://manishportfolio7.netlify.app)
- **GitHub**: [github.com/Manish-Yadav77](https://github.com/Manish-Yadav77)
- **LinkedIn**: [linkedin.com/in/manish-yadav-fullstack-mern](https://www.linkedin.com/in/manish-yadav-fullstack-mern/)

---

## Included Workflows

### 1. WhatsApp ATS CV Generator (`whatsapp-ats-cv-generator.json`)

An automated pipeline that receives raw job descriptions over WhatsApp, rewrites resume content to match applicant tracking systems (ATS), compiles a clean HTML template, converts it into a PDF via a custom microservice, and sends the finished document back over WhatsApp.

#### Technical Architecture
- **Trigger**: `WhatsApp Trigger` (Webhook endpoint)
- **AI Model**: `OpenAI / Moonshot AI` (Kimi-k3 via LangChain Agent)
- **State Management**: `Memory Buffer Window` (LangChain)
- **Logic Engine**: Custom `JavaScript` node for dynamic HTML rendering
- **PDF Microservice**: `HTTP Request` node POSTing to Render backend
- **Output**: `WhatsApp Node` sending document attachment back to user

#### Core Capabilities
- Extracts ATS keywords from incoming job posts in real time.
- Rewrites summary, technical skills, and project experience without making up false experience.
- Structures raw JSON into a clean HTML resume format.
- Generates downloadable PDFs on Render and delivers them back through WhatsApp instantly.

---

### 2. Gmail AI Email Classifier (`gmail-ai-email-classifier.json`)

An automated inbox monitoring system that polls Gmail every minute, passes incoming emails to NVIDIA NIM fast LLMs, creates custom Gmail labels, drafts candidate replies, and sends instant WhatsApp alerts for urgent recruiter messages.

#### Technical Architecture
- **Trigger**: `Gmail Trigger` (Polls every 60 seconds)
- **AI Engine**: `NVIDIA NIM Microservice` (`z-ai/glm-5.3-flash` via LangChain)
- **Router**: `Switch Node` routing across 5 distinct categories
- **Email Engine**: `Gmail Node` for dynamic label creation, label assignment, and draft creation
- **Alert System**: `WhatsApp Business Cloud API` for high-priority recruiter notifications

#### Core Capabilities
- Classifies messages into 5 categories: `URGENT_INTERVIEW`, `RELEVANT_JOB_MATCH`, `APPLICATION_STATUS`, `OUTSKILL_EMAIL`, and `IRRELEVANT_PROMO`.
- Automatically creates missing Gmail labels and tags incoming emails.
- Drafts customized recruiter replies signed by Manish Kumar Yadav highlighting relevant project details.
- Sends structured WhatsApp alerts for immediate recruiter inquiries so you don't miss opportunities.

---

## Setup and Installation

1. **Importing into n8n**:
   - Open your n8n canvas dashboard.
   - Click **Workflows** > **Import from File**.
   - Select either `whatsapp-ats-cv-generator.json` or `gmail-ai-email-classifier.json`.

2. **Required Credentials**:
   - **WhatsApp Cloud API**: Phone number ID and OAuth token.
   - **OpenAI / NVIDIA NIM API**: API keys for LangChain LLM nodes.
   - **Gmail OAuth2**: Authorized Google account for reading, labeling, and drafting emails.
   - **Render Microservice Endpoint**: Node.js HTML to PDF server URL for CV printing.

3. **Activation**:
   - Toggle the workflow status from **Inactive** to **Active** at the top right of the n8n editor canvas.

---

## Tech Stack & Integrations

- **Automation Engine**: n8n (Self-Hosted / Cloud)
- **AI & LLM Services**: LangChain Agent, OpenAI API, NVIDIA NIM Microservices
- **APIs & Webhooks**: WhatsApp Business Cloud API, Gmail API, Custom REST endpoints
- **Core Languages**: JavaScript (ES6+), HTML5, CSS3, JSON
