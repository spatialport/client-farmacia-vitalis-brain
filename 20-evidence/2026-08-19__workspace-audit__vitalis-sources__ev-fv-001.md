---
id: ev-fv-001
client_id: farmacia-vitalis
record_type: evidence
service_path: company
status: proposed
owner: alex-bellesia
authority: alex-bellesia
ip_owner: client
access_scope: internal
sensitivity: confidential
source_ref: file://Documents/Claude/Projects/NXTO/projects/farmacia-vitalis/
schema_version: 1.1.0
created_at: 2026-08-19
updated_at: 2026-08-19
---
# Evidence — Workspace audit of Farmacia Vitalis sources (2026-08-19)

**Source:** NXTO project folder `Documents/Claude/Projects/NXTO/projects/farmacia-vitalis/` (full read of primary .md docs; brandbook skimmed for tokens; image folders, xlsx, docx not opened).
**Actors:** Spatial Port Inc. (Alex Bellesia, author of all docs) for client Farmacia Vitalis (Paride Zanetti).
**Redaction:** no secrets copied. `deploy-aws/site/config-social.js` contains a runtime API key — referenced as file-ref only; canonical secret location `aws-secretsmanager://spatial-port/prod/farmacia-vitalis/social-api-key`.

## Fatti chiave (from Alex, "inventario 2026-08-19" + docs)

- Client: **Paride Zanetti** (paride.z@live.com) — pharmacy in **Lumino (Ticino, Svizzera)**, in/next to **Centro Opti**; opening **September 2026** (exact day TBD). Founders: Biljana, Svetlana, Paride. Pharmacy WhatsApp number recorded in canon `people.md` (not repeated here).
- Live: client hub **https://farmaciavitalis.spatial-port.io** · public site **https://www.farmaciavitalis.ch** · link-in-bio bio.farmaciavitalis.ch.
- Infra: AWS account **786913936501**, region **eu-central-1** (hub bucket in us-west-1); DynamoDB **`vitalis-anteprima`** (landing leads) and **`vitalis-social`** (post validation); mail backend (API GW + Lambda + SES) and social backend (Lambda Function URL) deployed via scripts in the project folder.
- Legal context: **Switzerland — nLPD/Swiss FADP + LATer/OPuM**, not EU GDPR by default (GDPR applied prudentially for EU users in fase-3/04).

## Source inventory (one-liners)

### Contesto / brief
- `PROJECT_v2.md` — master project file: client, vision, team, 8 target segments, services, competitors, brand direction, Swiss advertising constraints, opening strategy, action items.
- `MASTER_PROMPT_FASE-2-3.md` — the orchestration prompt that produced fase 2+3; codifies non-negotiable rules (no contract economics in deliverables, Swiss ad law, IT/EN/SR, brand tokens §5, real dates).
- `ANALISI_COMPETITIVA.md` (24 Apr 2026, v2.0) — 8 competitors, service/digital matrices, positioning map, local SEO keywords, gap analysis, competitor visual identities, Sunday Natural benchmark.
- `prompt-link-in-bio.md` — brief for the link-in-bio page (style/quality reference for the landing).

### Brand identity
- `brandbook-v6.html` — **the good/definitive version** (v4/v5 superseded, ignore): colors (Lime #ACC90F … Off-White #F8F6F1), Urbanist + Instrument Serif italic, 70/30 rule, DNA pattern, tagline. Single self-contained HTML, images inline.
- `logo-orizzontale-colore.png`, `presentazioni/assets/` (logo, logo-croce), `materiali-vitalis.xlsx` (physical materials list — not opened), `images/` (interior renders, print mockups, 10 IG social mockups — not opened).

### Fase 2 — Marketing plan (12 docs + overview, `fase-2-marketing-plan/`)
- `00-OVERVIEW-MARKETING-PLAN.md` — executive summary, integrated timeline Jun 2026–Aug 2027, 10 next steps, open client decisions.
- `01-strategia-digitale-12-mesi.md` — 3 phases (pre-apertura/lancio/crescita), channel architecture, KPI (300 list pre-open, 20 reviews m1, 800 contacts, 1'200 IG), critical dependencies.
- `02-posizionamento-differenziazione.md` — positioning statement, tagline, 4 pillars, per-segment value props, boilerplates, "noi/loro" matrix, tone do/don't, normative message limits.
- `03-piano-partnership-locali.md` — 13 partner playbooks (THI LAND 4 levers, parish, schools, pediatricians, nurses, midwives, Belotti, influencers, 120+ companies, Denner, Comune), contact templates, 15 placeholders, 8 health-law checkpoints.
- `04-pacchetti-servizi-consulenza.md` — 10 named service packages in 4 families; all tariffs `[TARIFFA — da cliente]`.
- `05-piano-eventi-stagionali.md` — 4 major seasonal events + monthly themed days + reusable event checklist.
- `06-campagna-apertura-lancio.md` — launch direction: 8-week countdown «Il tempo sta per cominciare», copy #1–#8, gira-la-ruota mechanics, WhatsApp community, opening-event run-of-show + roles, days 1–30, 20-materials checklist.
- `07-piano-adv-meta-google.md` — 3 ADV flights, geo/audience/creative, keyword groups, CHF 600 ceiling confirmed §4.2, naming convention, compliance section (LATer/OPuM + platform policies).
- `08-calendario-editoriale-social.md` (+ .xlsx, not opened) — 6 rubriche, 8 posts + 8 reels/month contract rhythm, 8 recurring reel formats, 6-month plan, approval workflow via founders' WhatsApp.
- `09-strategia-email-marketing.md` — Vitalis Mail architecture (single master list, attributes, segments), Welcome flow (3 complete emails), seasonal/retention/reorder flows, newsletter, double opt-in requirement, KPI.
- `10-pacchetto-pr-locale.md` — 2 ready press releases, prioritized Ticino media list, outreach templates, micro-influencer plan, PR timeline, media-kit checklist; press office = Alex Bellesia.
- `11-template-report-mensile.md` (+ `11-kpi-dashboard.html`) — monthly report with 37 defined KPIs and traffic-light thresholds.
- `12-budget-marketing-canali.md` (v2.0, supersedes 3-scenario v1.0; + .xlsx not opened) — ADV-only budget, CHF 600/month ceiling to Feb 2027, monthly plan Jul 2026–Aug 2027 totaling CHF 6'100.

### Fase 3 — Landing (`fase-3-landing-page/`)
- `01-spec-design-landing.md` — full section-by-section spec: mobile-first, trilingual IT/EN/SR, countdown, segmented lead form, consent-first cookie banner, AA accessibility, schema.org Pharmacy, CONFIG placeholder block.
- `02-copy-deck-IT-EN-SR.md` — final copy in 3 languages (SR latinica, mother-tongue review mandatory); 3 hero headline variants (A recommended).
- `03-integrazioni-e-tracking.md` — master placeholder table (confirmed: WhatsApp 078 251 01 04, Via Mesolcina 17 6533 Lumino, info@farmaciavitalis.ch), deploy guide, Vitalis Mail form wiring, UTM/GBP conventions.
- `04-gdpr-compliance.md` — nLPD-first (GDPR prudential) privacy+cookie policy drafts, trilingual banner texts, pre-live checklist (legal validation blocking), pharmacy-specific notes (WhatsApp prescriptions = health data; prescription-ad ban).
- `05-redesign-v2-piano.md` — landing v2 "luxury tech minimal, ma caldo": aurora gradient replaces DNA helix, hero split, team placeholders; third-party Rosucci hero photo is dev-only placeholder (license ⚠).
- `landing/index.html` — the production single-file landing.

### Fase 4 — ADV (`fase-4-adv/`)
- `KIT-ADV-LANCIO-LUG-AGO-2026.md` (10 Jul 2026) — field-ready Flight 0 kit: 2 Meta campaigns + Google Search Brand, Jul CHF 300 / Aug CHF 450, 5 Meta ads + 5 Google RSAs written, UTM scheme, launch checklists.

### Fase 5 — Social (`fase-5-social/`)
- `PIANO-CATCH-UP-LUGLIO-2026.md` (10 Jul 2026) — profiles ~4 weeks late; 3-post starter kit + 15 contents over 3 weeks (14 Jul–3 Aug) with ready captions; community-management rules.
- `Calendario-Editoriale-30gg.xlsx`, `Calendario-Editoriale-Multicanale-30gg.xlsx`, `social-showcase.html`, `mockup-feed-ig.html` — operational calendars/mockups (not opened).

### Infrastruttura / deploy
- `deploy-aws/README-DEPLOY.md` + `deploy.sh` + `site/` — client hub farmaciavitalis.spatial-port.io (S3 us-west-1 + OAC + CloudFront + ACM + Route53, robots disallow, idempotent script). `site/config-social.js` = generated runtime config with social API URL + key (**file-ref only, never copy**); `site/social-seed.json` seed data.
- `deploy-www/README-DEPLOY-WWW.md` + `deploy-www.sh` + `site/` — www.farmaciavitalis.ch landing deploy; only `www` delegated from Infomaniak to Route53; site assets include hero webp images, team photos (biljana, svetlana, **valerija**), sitemap, Google verification file `google3f9fba064d327aac.html`.
- `deploy-bio/` — bio.farmaciavitalis.ch link-in-bio (same pattern).
- `vitalis-mail-backend/README-VITALIS-MAIL.md` + `deploy-vitalis-mail.sh` + `lambda/handler.py` — leads backend: POST /iscrizione → Lambda → DynamoDB `vitalis-anteprima` + SES welcome (sender ciao@farmaciavitalis.ch); currently **single opt-in** (double opt-in = required evolution); honeypot anti-bot.
- `vitalis-social-backend/deploy-vitalis-social.sh` + `lambda/handler.py` — post-validation backend: DynamoDB `vitalis-social`, Lambda `vitalis-social-api` Function URL, CORS locked to hub, password (PBKDF2 hash) + HMAC token auth; script writes config-social.js. No README present.

### Asset stampa / presentazioni
- `presentazioni/*.html` — 15 interactive presentations of the fase-2/3 deliverables (mirrored in deploy-aws/site).
- `images/` print mockups: toteBags, labCoats, nameBadge, vehicleWrap, stickers, envelopes, plasticBags, totemEsterno (not opened).
- `dashboard-competitiva.html`, `Analisi_Competitiva_Farmacia_Vitalis.docx` (docx not opened; .md is canonical).

## Direct implications
- Canon files 10-canon/* populated from this audit (status proposed).
- Compliance items are the operational backbone: nothing ⚠ publishes before health-law validation; legal validation of privacy texts blocks the definitive live posture.

## Candidate tasks
- Chase blocking placeholders: opening date, ragione sociale/IDI, tariffs, team names/photos, legal validation, double opt-in upgrade, SES production access.

## Candidate decisions
- Confirm active_service_paths in manifest (done, proposed); decide whether crm/local-seo become standalone paths.

## Candidate canon
- All 10-canon files updated 2026-08-19 (company, people, offer, icp, positioning, channels, operations, brand).
