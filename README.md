# Jamari "Jay" McNabb — AI Engineer & Builder

I design and ship production AI systems end to end — from LLM-powered extraction pipelines and lead-scoring engines to multi-agent operating systems. I'm the **CTO and sole technical lead of [Edge AI Growth LLC](https://github.com/edge-ai-growth)**, a productized AI agency + SaaS company, where I've built and shipped the products below to real paying customers across the US and Latin America.

I work in the Claude / OpenAI / Gemini stack, ship continuously to production (Vercel, Firebase, Supabase), and care about the unglamorous parts — auth, billing, webhooks, RLS, and making AI output reliable enough to bet a business on.

📫 **jamarijmcnabb@gmail.com** · [GitHub @Jaynabb](https://github.com/Jaynabb)

> **About this repo:** The flagship products below are closed-source company assets that handle live customer data, so the source isn't public. This is a curated walkthrough of what I built, the problems they solve, and the architecture decisions behind them. Happy to do a live code walkthrough in an interview.

---

## 🛰️ LeadScout — Get customers, talk to them, close them
*Multi-tenant SaaS · Next.js 14 (App Router, TypeScript) · Supabase · Stripe · Claude API · Meta Ads · GoHighLevel*

A B2B platform for SMB operators (LATAM + US, WhatsApp-native, Spanish-bilingual) that unifies three jobs that normally require juggling Meta Ads Manager, GoHighLevel, and spreadsheets:

- **Get Leads** — search local businesses (Google Places / SerpAPI) → enrich (Hunter/Apollo) → **score with Claude** → surface the best prospects → generate outreach.
- **Talk to Customers** — a chatbot builder that deploys to **WhatsApp via GHL Conversation AI**, with a live conversations + contacts mirror.
- **Run Ads** — launch Meta click-to-WhatsApp campaigns and attribute conversations and sales back to spend.

**What I built:** the entire application — 15+ dashboard surfaces and 20+ API routes (`/score`, `/enrich`, `/outreach`, `/webhooks`, `/billing`, `/analytics`, `/ghl`, `/meta`), Supabase Postgres schema with Row-Level Security for multi-tenancy, Supabase Auth, Stripe Checkout + webhook billing, Zod-validated inputs everywhere, and cron-driven background jobs. The AI layer uses the Claude API for lead scoring and email generation.

**Why it's interesting:** it's a thin, opinionated UI over messy third-party APIs (Meta + GHL) that hides the bloat and exposes only what an operator actually needs — and it has to stay correct across billing, attribution, and live customer conversations.

---

## 📦 ImportFlow — AI customs & package-import manager
*Web app · React · Firebase/Firestore · Google Gemini + Cloud Vision · Twilio*

A package-tracking and customs-management system built for import businesses in El Salvador. The headline feature is **AI document scanning**: point it at a shipping label or invoice and it extracts tracking numbers, contents, declared values, customer info, carrier, and origin — then automatically computes El Salvador customs duties (the $300 exemption threshold, 13% VAT, HS-code duty rates).

**What I built:** the full stack — Gemini + Cloud Vision extraction pipeline with OCR fallback (Tesseract), Firestore data model and CRUD with activity logs, automatic duty/VAT calculation engine, Twilio SMS notifications across the package lifecycle (received → in customs → ready → delivered), and CSV/Sheets export for CRM.

**Why it's interesting:** real money rides on the extraction being right. Getting structured, total-reconciled output out of photos of messy real-world receipts — and verifying a prompt change actually improves it *before* shipping — is the hard, valuable part.

---

## 🧠 AIOS — an AI operating system for a productized agency
*Python · Claude Code plugin/skill architecture · OpenAI · connector framework*

The internal system that lets Edge AI deliver "an AI operations layer" to customers as a product. AIOS provisions a custom **"AIOS Jr"** workspace per customer — context files, GTD scaffolding, connector wiring (Slack, Firestore/Supabase, GHL, Gemini transcripts), and a tailored skill set — built from a discovery call or website rather than copy-pasted.

**What I built:** the provisioning spine and the skill/plugin layer — deterministic provisioning steps with AI judgment at the decision points, a connector framework, and reusable skills (customer status boards, meeting-transcript → decisions/actions, extraction-replay verification, GHL snapshot ops). The design principle throughout: **deterministic where it must be reliable, AI where judgment adds value.**

**Why it's interesting:** it's a real attempt to make AI delivery *scale past founder-hours* — turning a custom consulting engagement into a repeatable, productized install.

---

## 🧭 KVM Sales Navigator — voice-enabled sales tool
*Vite · React · TypeScript · shadcn/ui · Supabase · ElevenLabs*

A focused sales-navigation tool with a lead dashboard, built on a Vite/React/shadcn front end with a Supabase backend and **ElevenLabs voice** integration. Demonstrates rapid, clean product development with a modern component system and edge-function backend.

---

## 🛠️ Other work
A range of smaller production and prototype projects on [my GitHub](https://github.com/Jaynabb?tab=repositories) — AI invoice-extraction agents, a windshield-damage analyzer, a receiving-verification system, legal-intake automation, and review-scraping tools — most built around the same theme: **putting an LLM somewhere a business actually needed a decision made.**

---

## Stack at a glance
**Languages:** TypeScript, JavaScript, Python
**AI/LLM:** Claude API (Anthropic SDK), OpenAI, Google Gemini + Cloud Vision, prompt engineering, structured extraction, LLM scoring
**Frontend:** Next.js (App Router), React, Vite, Tailwind, shadcn/ui
**Backend/Data:** Supabase (Postgres + RLS), Firebase/Firestore, Node, serverless/edge functions, Zod
**Infra/Integrations:** Vercel, Stripe, Twilio, Meta Ads, GoHighLevel, Resend, ElevenLabs

*Open to full-time AI engineering roles. Let's talk — jamarijmcnabb@gmail.com*
