---
id: farmacia-canon-icp
client_id: farmacia-vitalis
record_type: knowledge
service_path: company
status: accepted
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
# Icp

Purpose: Who the business serves, jobs, pains, buying context, objections, geography and evidence.

## Accepted knowledge

### Geography
- Primary catchment: **Lumino**; extended: Bellinzona (north), Arbedo-Castione, San Vittore and Roveredo (both in Grigioni but Italian-speaking, gravitating on the Bellinzonese) — local road patterns make them all pass by the shopping complex (PROJECT_v2.md §3, fase-2/07 §2.2). ADV bacino estimated ~50–60k people; Flight 0 works Lumino + ~5 km only (fase-4/KIT-ADV).
- Languages: Italian primary; English and **Serbian** additional (Orthodox community; landing is trilingual IT/EN/SR in Serbian latinica) (PROJECT_v2.md §3, fase-3/02).

### Segments (priority per PROJECT_v2.md §3; value propositions per fase-2/02 §3)
| Segment | Priority | Key need | Message / hook |
|---|---|---|---|
| Families with children | High | practicality, solved emergencies, trust | "La farmacia delle famiglie del Centro Opti" — kids' corner, vending machine, pediatric center, WhatsApp |
| Elderly locals | High | relationship, continuity, unhurried service | "Qui c'è sempre la stessa faccia che ti conosce" — saletta, measurements, compression stockings, legible logo |
| Women 30–60 (natural medicine) | High | integrated approach, credible natural alternatives | "Natura e scienza insieme" — free naturopath, phytotherapy, Vitalis preparations, dermocosmetics |
| A2 commuters | Medium | speed, out-of-hours access | "Ordina, passa, ritira. Anche alle 23." — locker 24/7, WhatsApp prescriptions, parking |
| Orthodox community | Medium | community trust, own language | relational message via the parish priest's WhatsApp channel + Serbian on landing/at the counter ("Govorimo srpski") |
| Local company workers (120+ companies) | Medium | organized convenience | "Vitalis Aziende" conventions, lunch-break WhatsApp prescriptions, locker after shift |
| Young 18–25 | Medium | wellness/supplements, social-native | "Integratori spiegati senza fuffa"; IG reels/stories only |
| Celiac / gluten-intolerant | Medium | product availability nearby | "Senza glutine a Lumino: finalmente vicino a casa" (only source in the area) |

### Buying context and traffic peaks
- Morning: commuters, school parents, elderly after doctor visits; after-school: mothers with kids; evenings/weekends: THI LAND + restaurant families — pharmacy closed Saturday afternoon and Sunday, so locker + vending machine cover those windows (PROJECT_v2.md §3).
- CRM segmentation mirrors the segments: form attribute `INTERESSE` = naturale / famiglie / servizi_sanitari / senza_glutine / generale (fase-2/09 §1.2). Compliance note: interest choice is a commercial preference, **never** to be treated or profiled as health data (fase-3/04 §1.3 — absolute ban on health profiling, in Vitalis Mail, in ad audiences and in prompts to Claude).
- ADV audiences never target health conditions (Meta policy + ethics): only lifestyle/commercial interests (fase-2/07 §2.4).

## Open questions

- No first-party evidence yet (pharmacy not open): all segment sizes/behaviour are hypotheses from discovery — validate with month-1 in-store observation and the T-5 WhatsApp poll ("Quale servizio aspettate di più?") (fase-2/06).
- Real weight of the Orthodox community and of the celiac niche in the catchment (no numbers anywhere).
- Whether German-speaking demand exists ("Apotheke Lumino" keyword is targeted but the landing has no DE version — fase-2/07 §3.3 flags this).
