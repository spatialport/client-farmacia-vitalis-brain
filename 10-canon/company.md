---
id: farmacia-canon-company
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
# Company

Purpose: Who the company is, legal/operating context, history, beliefs, mistakes, lessons and five-year ambition.

## Accepted knowledge

- **What:** Farmacia Vitalis is an independent pharmacy opening in **Lumino, Ticino, Switzerland** — Swiss law context, not EU (PROJECT_v2.md; inventario 2026-08-19). It combines classic pharmacy and natural medicine ("farmacia classica + naturale/omeopatia sotto lo stesso tetto") (PROJECT_v2.md).
- **Location:** inside/next to the **Centro Opti** complex, which also hosts THI LAND (indoor playground), THI Restaurant, a pediatric center (opening), a Denner supermarket and the post office; schools 20 m away, free parking, 2 min from the A2 exit (PROJECT_v2.md). Confirmed address: **Via Mesolcina 17, 6533 Lumino (TI)** — CAP 6533 recorded as "confirmed via e località, non il CAP: da verificare" (fase-3-landing-page/03-integrazioni-e-tracking.md). An earlier spec used working placeholder "Via Mesolcina 17, 6525 Lumino" (fase-3/01) — 6533 is the value used in the live docs.
- **Opening:** **September 2026** (exact day still a blocking placeholder `[DATA APERTURA — da confermare]` across all docs); pharmacy opens ahead of the collective Centro Opti inauguration planned for end of October 2026 (PROJECT_v2.md, fase-2/06).
- **Ownership:** three founders — **Biljana, Svetlana and Paride Zanetti**; Paride is the operational contact (fase-2/03, fase-2/10). Legal entity/ragione sociale and IDI/CHE number not yet provided (landing footer placeholder "Farmacia Vitalis SA `[ragione sociale da cliente]`") (fase-3/03).
- **Engagement:** managed by Spatial Port Inc. (Alex Bellesia); contract March 2026, discovery call 31 March 2026 (PROJECT_v2.md). Phases: 1 brand, 2 marketing plan, 3 landing page, 4 ADV launch, 5 social, 7a ongoing maintenance (PROJECT_v2.md §10).
- **Core belief / vision:** a proximity-and-trust pharmacy with a human, personalized approach, positioned against big chains; the claim that emerged from discovery: *«Ci prendiamo il tempo per te.»* (PROJECT_v2.md).
- **Staff at opening:** 4 people — 2 pharmacists + 2 pharmacy assistants; a naturopath gives free 10–15 min in-store consultations (PROJECT_v2.md).
- **Prior experience:** the founders ran a previous pharmacy where the "gira la ruota" opening mechanic was already tested successfully (PROJECT_v2.md §10, fase-2/06 §3.1).
- **Timeline reality check:** landing was planned live in May, went live July 2026; social was planned from June, started ~14 July 2026 with a 3-week catch-up plan (MASTER_PROMPT_FASE-2-3.md, fase-5/PIANO-CATCH-UP-LUGLIO-2026.md).
- **Digital estate:** client presentation hub https://farmaciavitalis.spatial-port.io (robots-blocked work area), public site https://www.farmaciavitalis.ch (landing), bio.farmaciavitalis.ch (link-in-bio); domain farmaciavitalis.ch registered, DNS on Infomaniak with only `www` (and `bio`) delegated to AWS Route53 (deploy-aws/README-DEPLOY.md, deploy-www/README-DEPLOY-WWW.md; inventario 2026-08-19).

## Open questions

- Exact legal form and registered name (SA? Sagl?) + IDI/CHE number — blocking for the site impressum (fase-3/03).
- Exact opening date in September 2026 — blocks countdown, event, PR (open in every doc as of July 2026).
- Surnames and professional roles of Biljana and Svetlana (pharmacists? assistants?) — and who "Valerija" is (a `team-valerija.webp` photo exists in deploy-www/site alongside Biljana and Svetlana, but no doc mentions her).
- Confirm CAP 6533 for Via Mesolcina 17 (client confirmed street/locality only).
