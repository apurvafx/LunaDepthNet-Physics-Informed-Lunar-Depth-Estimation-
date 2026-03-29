# Feasibility & Viability — Concierge x ET

---

## Feasibility — ET Integration Touchpoints

| Integration Point | Method | What It Does | Effort |
|---|---|---|---|
| ET Web Embed | iframe / Web Component | Floats as widget inside ET article pages — no frontend rebuild needed | Low |
| ET Login / SSO | OAuth 2.0 — ET One Account | No new signup; existing ET account saves the user's FIRE plan | Medium |
| ET Article Context | REST API hook on article metadata | SIP / MF article auto-pre-fills the wizard with relevant goal context | Medium |
| ET Markets Data Feed | ET Markets REST API | Live NAV and fund performance from ET's existing data layer | High |
| ET App Deep Link | React Native WebView + SSO token | "Plan My FIRE" CTA in ET Markets app opens Concierge with user authenticated | Medium |
| ET Prime Paywall | ET Prime subscription API | Free: 1-goal summary — ET Prime: full roadmap + PDF export | Low |
| ET Push Notifications | ET Firebase Cloud Messaging pipeline | SIP reminders and FIRE milestones via ET app's existing push stack | Low |

---

## Technical Feasibility

| Dimension | Verdict | Rationale |
|---|---|---|
| Backend (FastAPI) | Feasible | Production-grade REST endpoints already defined, tested, Pydantic v2 validated |
| AI Response Latency | Feasible | DeepSeek + FAISS RAG benchmarks < 3 sec per plan on standard GPU instance |
| ET Embed Compatibility | Feasible | Vanilla HTML/JS — drops into any ET page via a single script tag, zero framework conflict |
| Multilingual (Hindi / Hinglish) | Feasible | LangChain prompt templates with language flags implemented and tested |
| SEBI / DPDP Compliance | Conditional | Advisory-only, no transactions processed; disclaimer + user consent required |
| LLM Hallucination Risk | Mitigated | Deterministic Python engine computes all figures; LLM only narrates, never calculates |
| Offline Fallback | Partial | FIRE Calculator works client-side; AI Mentor requires connectivity |

---

## Viability

| Dimension | Data Point | Advantage | Risk |
|---|---|---|---|
| Market size | 300M+ salaried Indians | No AI-first personal finance competitor at ET's distribution scale | Low |
| Built-in distribution | 250M+ ET MAUs | Zero cold-start; users already inside ET when they encounter Concierge | Low |
| Monetization | ET Prime upsell + affiliate leads | Free tier drives ET Prime conversions; Rs. 500–2,000 per MF / insurance referral | Medium |
| Competitor gap | Groww / ET Money are execution-first | Concierge plans first, then routes to execution — fills an unoccupied layer | Low |
| Regulatory risk | SEBI RIA rules / DPDP Act | Framed as educational tool; mandatory disclaimer on every plan output | Medium |
| Retention risk | One-shot plan generation | AI Mentor chat + ET push notifications sustain engagement post-plan | Medium |
| Infrastructure cost | ~Rs. 11K–26K/mo at 10K users | Token-based LLM pricing scales with usage; no fixed GPU cost at MVP stage | Low |
