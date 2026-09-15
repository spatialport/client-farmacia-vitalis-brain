---
id: farmacia-vitalis-ev-2026-09-08-email-system-audit
client_id: farmacia-vitalis
record_type: evidence
service_path: crm
status: proposed
owner: alex-bellesia
authority: alex-bellesia
ip_owner: client
access_scope: internal
sensitivity: internal
source_ref: https://app.clickup.com/t/869ez14m6
schema_version: 1.1.0
created_at: 2026-09-08
updated_at: 2026-09-08
---

# Audit sistema email e stato sito (8/9/2026)

## Source
Verifica in sessione Cowork (company-ops) su richiesta di Alex per la task ClickUp 869ez14m6: repo `farmacia-vitalis-workspace` (main + branch), API live `8nnw8bhsx2`, account Brevo "Farmacia Vitalis", sito live, evidence precedenti (2026-09-02 brevo-leads-dashboard, 2026-09-04 funnel-brevo).

## Actors
- Alex (decisione, deploy AWS), Jacopo (owner task 869ez14m6, campagne Brevo), Riccardo — Spatial Port

## Redaction result
Nessuna credenziale (chiavi Brevo/AWS e ADMIN_TOKEN restano fuori da chat e repo). Nessun dato personale di lead. Single-tenant.

## Factual summary
- Sistema email NON attivo: Brevo 0 contatti reali e 0 invii; in produzione gira la Lambda v1 di agosto (DynamoDB + SES); il deploy con `BREVO_API_KEY` non e' mai stato lanciato (`GET /leads` e `/codice` rispondono 404; `admin-leads.html` live con endpoint `REPLACE-ME`). Numero di iscrizioni in DynamoDB non verificabile senza AWS.
- Bug repo: la PR #2 (codice sconto univoco + rotte `/codice` + attributi Brevo) era stata fusa nel branch `feat/brevo-leads-panel` 14 secondi dopo il merge di quel branch in `main` (PR #1): il funnel non e' mai arrivato su `main`.
- Corretto con PR #3 (https://github.com/spatialport/farmacia-vitalis-workspace/pull/3): porta il funnel su main; email 1 (codice) inviata dalla Lambda come transazionale Brevo con template #1 (`BREVO_WELCOME_TEMPLATE_ID`, default 1) invece dell'automazione da configurare in UI; attributo `OPT_IN` + lista opzionale `BREVO_OPTIN_LIST_ID`; `admin-leads.html` precompilato sull'API `8nnw8bhsx2`; README con go-live.
- Brevo pronto: lista VITALIS (id 3), attributi NOME/CODICE/SCADENZA/APERTURA/FONTE/OPT_IN, template #1/#2/#3, campagne #4 (pre-apertura) e #5 (post-apertura) create in bozza dai template (lista da selezionare al momento della programmazione: Brevo rifiuta destinatari su lista vuota). Mittente placeholder `alex@spatial-port.com` fino allo swap su `info@farmaciavitalis.ch`.
- Sito live allineato all'ultimo commit (deploy-www verde 8/9 14:45): hero "A settembre", countdown nascosto, JSON-LD senza validFrom, form + Google Calendar + WhatsApp attivi; Pixel/GTM/GA4 non installati, quindi nessun dato traffico.
- Nessun report performance per la farmacia: nessuna email raccolta da riportare (regola di Alex).

## Candidate tasks
- 869ez2afu (Alex, 9/9): merge PR #3, deploy `BREVO_API_KEY BREVO_LIST_ID=3 ADMIN_TOKEN DATA_APERTURA ./deploy-vitalis-mail.sh`, test dal form; swap mittente quando ci sono gli accessi alla casella.
- Jacopo: programmare campagne #4 (D-3) e #5 (D+5) sulla lista VITALIS quando la data e' confermata.
- Dopo il deploy: riallineare in Brevo eventuali lead gia' in DynamoDB e mandare loro il codice a posteriori.

## Candidate decisions
- Email 1 come transazionale Brevo dalla Lambda (non automazione): supera la decisione del 4/9 perche' l'automazione non era creabile dal connettore e bloccava il go-live.

## Candidate canon
- operations: pipeline lead = landing -> Lambda `vitalis-mail-intake` (API 8nnw8bhsx2) -> DynamoDB `vitalis-anteprima` + Brevo lista 3 -> email 1 transazionale template #1; campagne #4/#5 per pre/post apertura; pannello `admin-leads.html` con ADMIN_TOKEN.
