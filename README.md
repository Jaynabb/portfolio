# Jamari "Jay" McNabb — AI Engineer & Builder

I design and ship production AI systems end to end — from company-wide automation operating systems to LLM-powered extraction pipelines, lead-scoring engines, and multi-tenant SaaS. I've built and shipped the products below to real paying businesses across the US and Latin America, working as the technical lead from architecture through production.

I work in the Claude / OpenAI / Gemini stack, ship continuously to production (Vercel, Firebase, Supabase), and care about the unglamorous parts — auth, billing, webhooks, RLS, and making AI output reliable enough to bet a business on.

📫 **jamarijmcnabb@gmail.com** · [GitHub @Jaynabb](https://github.com/Jaynabb)

> **About this repo:** The flagship products below are closed-source company assets that handle live customer data, so the source isn't public. This is a curated walkthrough of what I built, the problems they solve, and the architecture decisions behind them. Happy to do a live code walkthrough in an interview.

---

## 🧠 AIOS — an AI operating system that runs a company's stack
*Python · Claude-based agent & skill architecture · multi-source connector framework · live orchestration*

AIOS is an AI operations layer that sits on top of whatever tools a company already runs and makes them work as one system. It automates **any combination of a company's stack** — Slack, CRMs (GoHighLevel), databases (Firestore/Supabase), meeting transcripts, docs, spreadsheets — wires them together so they **talk to each other**, and gives an AI agent **shared context across all of them**. Then it acts: it **pulls live meeting transcriptions and turns them into decisions and action items**, **monitors Slack** for things that need attention, builds cross-source status boards, and automates recurring operational work. The idea is to hand a business an AI operator that already knows everything happening across its tools — and can take it from there.

**What I built:** the full system — a connector framework that normalizes any company's tools to a common interface, a context layer that gives agents shared memory across every source, and a skill library (meeting-transcript → decisions/actions, cross-source status boards, live monitoring, extraction-replay verification, CRM/snapshot ops). Architected on a **deterministic spine with AI judgment at the decision points** — deterministic where it must be reliable, AI where judgment actually adds value. Each deployment is provisioned per-company from their real stack rather than copy-pasted.

**Why it's interesting:** it's a serious attempt at the "AI that runs your operations" problem — not a chatbot, but a system that ingests everything a company does across every tool and acts on it.

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

## 🧭 KVM Sales Navigator — voice-enabled sales tool
*Vite · React · TypeScript · shadcn/ui · Supabase · ElevenLabs*

A focused sales-navigation tool with a lead dashboard, built on a Vite/React/shadcn front end with a Supabase backend and **ElevenLabs voice** integration. Demonstrates rapid, clean product development with a modern component system and edge-function backend.

---

## 🩺 ChiroScribe — local-first AI medical scribe for chiropractors
*Desktop app · Electron · React + TypeScript · Claude (Anthropic SDK) · better-sqlite3 · WebSocket audio*

A desktop AI notetaker that listens to a chiropractic visit and turns it into structured clinical notes, so the practitioner can focus on the patient instead of charting. Built as a desktop app on purpose: audio and patient data stay **local-first** (on-device SQLite), which is the right default for a healthcare workflow.

**What I built:** the entire Electron app — a WebSocket audio-capture pipeline in the main process, **Claude-backed note generation** (Anthropic SDK), a local `better-sqlite3` store for patients/visits/notes, Zod-validated IPC between the main and renderer processes, and a React UI.

**Why it's interesting:** turning live audio into reliable, structured medical notes — with a privacy-conscious, local-first architecture instead of shipping patient audio to the cloud.

---

## ⚖️ LegalFlow — legal client-intake command center
*Web app · React (Vite) · Express · built for a law firm (Richards Law)*

An intake "command center" built for a law firm to compress the path from prospective client to signed, onboarded client — capturing intake details and automating **retainer-agreement generation**. A React/Vite front end over an Express API, built rapid-fire as a hackathon project and demoed end to end.

**What I built:** the full app — the `IntakeCommandCenter` UI and the Express backend driving intake and document generation. ([code](https://github.com/Jaynabb/richards-law-intake))

**Why it's interesting:** shows I can take a real client's workflow from zero to a working, demoable product fast.

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
