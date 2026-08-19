---
id: farmacia-canon-operations
client_id: farmacia-vitalis
record_type: knowledge
service_path: company
status: proposed
owner: alex-bellesia
authority: alex-bellesia
ip_owner: client
access_scope: internal
sensitivity: confidential
source_ref: file://Documents/Claude/Projects/NXTO/projects/farmacia-vitalis/
schema_version: 1.1.0
created_at: 2026-08-11
updated_at: 2026-08-19
---
# Operations

Purpose: How the physical business actually works, including constraints, seasonality, locations and customer journey.

## Proposed knowledge (awaiting review by Alex)

### Physical operations
- Single location: Centro Opti, Via Mesolcina 17, 6533 Lumino (TI) (fase-3/03). Free abundant parking; illuminated pharmacy cross (electrical pre-wiring done by Daniele) (PROJECT_v2.md §6).
- Hours: reduced vs. Castione competitor — closed at midday, Saturday afternoon and Sunday; locker 24/7 + emergency vending machine cover off-hours (PROJECT_v2.md §5; exact hours not yet fixed — landing `HOURS` map pending).
- Customer journey touchpoints: counter, private consultation room (saletta), naturopath corner, locker (order in-store/WhatsApp/phone → code → pickup), vending machine outside, kids' corner, gluten-free shelf (PROJECT_v2.md, fase-2/04).
- Seasonality drives the year-1 calendar: Difese d'Autunno (Oct–Nov 2026, flu/immune season), Il Natale sotto casa (Dec 2026), Vitalis in Fiore (Mar–Apr 2027, Easter Sunday given as 28 March 2027 in fase-2/05), Pronti Estate Via (Jun–Jul 2027) + 1 themed day per month with a reusable event checklist ("no event ends without contacts collected and reviews asked") (fase-2/05).
- Review engine: QR card at every purchase, personal staff ask, follow-up email; reply to all reviews within 48h; **never incentivize reviews** (fase-2/06 §6.2).

### Swiss regulatory constraints on advertising (RECORD — applies to ALL output)
Context: Switzerland — **LATer (Legge sugli agenti terapeutici) + OPuM (ordinanza sulla pubblicità dei medicamenti)** and **nLPD** (Swiss FADP, in force 1.9.2023). Not Italian/EU GDPR by default; GDPR is applied only prudentially for EU users (fase-3/04 §1).
- ❌ **Never advertise prescription medicines** (name, price, photo, availability) — public advertising of prescription-only medicines is prohibited (fase-2/07 §6.1, PROJECT_v2 §9).
- ❌ **Never advertise medicines/homeopathic remedies reimbursed by the cassa malati** (health-insurance-covered products/services).
- ❌ No therapeutic claims or healing promises on any product ("cura", "guarisce", "previene la malattia X") — supplements only with permitted generic wording ("supporta").
- ❌ No promos/discounts incentivizing medicine consumption (even OTC, cautiously); wheel/voucher rules must print the exclusion of reimbursed products (fase-2/06 §3.1).
- ❌ Locker must never be framed as "prescription meds anytime without a pharmacist" — communicate the *pickup service* of already-validated orders (fase-2/07 §6.1).
- ❌ Ad platforms: no health-condition targeting, no personal-attribute copy ("Sei celiaco?" forbidden → "Alimenti senza glutine a Lumino" OK), no before/after imagery, no recognizable prescription products in photos (fase-2/07 §6.4).
- ✅ Allowed perimeter: dermocosmetics, naturopathy/phytotherapy as department/consultation, supplements, parapharmacy, gluten-free foods, kids' corner, and **the pharmacy's services** (consultations, measurements, compression stockings, locker, vending, WhatsApp channel, themed days, opening event) (fase-2/07 §6.2).
- ⚠ Claims pending written validation by the **health-law medic of the complex** before any publication: vaccination as a service, check-up billable to cassa malati, "verifica calze gratuita tramite cassa malati", WhatsApp prescription flow (privacy), wheel regulations, partner mechanics (THI LAND member benefit, newborn kits, school communications, pediatrician materials, influencer briefs, company-convention benefit structure) (fase-2/03 ⚠ list of 8, fase-2/07 §6.3).
- Community management: never diagnoses, dosages or therapeutic advice in public comments/DMs; prescription-medicine questions only redirected to private/in-person (fase-2/08 §5).

### Privacy / data protection (nLPD-first)
- Reference framework: **nLPD primary; GDPR applied prudentially** (border area, trilingual page, plausible EU users; possible art. 27 EU-representative question flagged to legal) (fase-3/04 §1.1–1.2). Note: PROJECT_v2 §7 loosely said "GDPR/privacy compliance CH/EU" and the fase-3 file is named "04-gdpr-compliance.md", but its content is correctly nLPD-first.
- Form data are NOT health data; the `INTERESSE` field is a commercial preference; **absolute ban on health profiling** anywhere, including prompts to Claude (fase-3/04 §1.3).
- Consent-first tracking: GTM/Meta Pixel/Calendly load only after explicit opt-in; double separate consents on the form (privacy required + marketing optional, not pre-checked) (fase-3/01 §3.11, fase-3/04).
- Prescriptions via WhatsApp = health data (special category): separate legal/health-law validation required before activating the service (fase-3/04 §6.1).
- Privacy/cookie policies exist as **drafts pending legal validation — blocking for live**; drafted retention: non-client leads 24 months; marketing subscribers until revocation (fase-3/04 §2, §5).
- Known gap: the deployed mail backend is **single opt-in** (welcome acts as confirmation) while doc 09 and the GDPR checklist require **double opt-in** — flagged as recommended evolution before large sends (vitalis-mail-backend/README-VITALIS-MAIL.md).

### Digital infrastructure (Spatial Port-operated; inventario 2026-08-19)
- AWS account **786913936501**, primary region **eu-central-1** for backends. No secrets in the repo docs; machine secrets under `aws-secretsmanager://spatial-port/prod/farmacia-vitalis/` (e.g. social API key → `aws-secretsmanager://spatial-port/prod/farmacia-vitalis/social-api-key`; the generated `deploy-aws/site/config-social.js` contains the runtime key and must never be quoted/copied).
- **Client hub** https://farmaciavitalis.spatial-port.io — S3 (bucket in us-west-1) + OAC + CloudFront + ACM + Route53, robots.txt disallow-all; publishes presentations, brandbook-v6, KPI dashboard, landing preview; deployed via `deploy-aws/deploy.sh` (idempotent) (deploy-aws/README-DEPLOY.md).
- **Public site** https://www.farmaciavitalis.ch — landing single-file; only the `www` (and `bio`) subdomains are delegated from Infomaniak DNS to Route53; apex + mail stay on Infomaniak; deployed via `deploy-www/deploy-www.sh`; `deploy-bio/` serves bio.farmaciavitalis.ch link-in-bio (deploy-www/README-DEPLOY-WWW.md).
- **Vitalis Mail backend** (leads): landing form → POST /iscrizione (API Gateway HTTP API) → Lambda Python → **DynamoDB `vitalis-anteprima`** + SES welcome email (sender ciao@farmaciavitalis.ch, domain DKIM on Infomaniak DNS; SES production access needed to mail unverified addresses); honeypot anti-bot; welcome sent only if `MARKETING_OPTIN=true`; deploy via `vitalis-mail-backend/deploy-vitalis-mail.sh` (README-VITALIS-MAIL.md).
- **Vitalis Social backend** (post validation/preview): **DynamoDB `vitalis-social`** + Lambda `vitalis-social-api` with Function URL, CORS restricted to the hub origin; client access via password (PBKDF2 hash in Lambda env) + HMAC-signed tokens; deploy script auto-writes `deploy-aws/site/config-social.js` with URL + key (file-ref only — never copy contents) (vitalis-social-backend/deploy-vitalis-social.sh).
- Landing CONFIG placeholders still open at last doc state: `FORM_ENDPOINT` (from mail backend deploy), `DATA_APERTURA`, Pixel/GTM IDs, Calendly URL, ragione sociale/IDI in footer, OG image (fase-3/03 §1).

### Working cadence
- Weekly alignment call founders–Spatial Port during active phases; monthly marketing report by day 5 (template with 37 KPIs, doc 11); partnership status as fixed 5-min agenda item (PROJECT_v2 §13, fase-2/11-template, fase-2/03 §4).

## Open questions

- Definitive opening hours (needed for GBP, landing `HOURS`, schema.org).
- Legal validation status of privacy/cookie texts and of the ⚠ claim list — nothing in the workspace marks them approved.
- Upgrade path/date for double opt-in in the mail backend before large sends.
- SES production access (out of sandbox) — status unknown.
- Whether the hub's us-west-1 bucket region vs. eu-central-1 backends is intentional (hub carries no personal data, so likely fine — confirm policy).
