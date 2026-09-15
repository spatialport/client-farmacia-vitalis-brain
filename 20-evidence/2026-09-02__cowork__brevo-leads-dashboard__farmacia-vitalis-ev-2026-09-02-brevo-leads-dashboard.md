---
id: farmacia-vitalis-ev-2026-09-02-brevo-leads-dashboard
client_id: farmacia-vitalis
record_type: evidence
service_path: landing-pages
status: proposed
owner: alex-bellesia
authority: alex-bellesia
ip_owner: client
access_scope: internal
sensitivity: internal
source_ref: https://github.com/spatialport/farmacia-vitalis-workspace/pull/1
schema_version: 1.1.0
created_at: 2026-09-02
updated_at: 2026-09-02
---

# Attivazione Brevo e pannello lead admin-leads.html (mail backend) — codice pronto in PR, deploy AWS in sospeso

## Contesto

Richiesta di Alex: "mettere a posto tutto il flusso [lead] incluso Brevo", con attivazione della risposta
automatica via Brevo e un pannello di controllo stile cruscotto su tutti i nuovi lead, con funzionalità
a discrezione dell'esecutore. Ricerca preliminare sul canon (`channels.md`, `operations.md`) ha confermato
che Brevo era stato pianificato ma poi superato dal sistema custom "Vitalis Mail" (AWS Lambda + DynamoDB +
SES) — tuttavia il codice Lambda conteneva già l'integrazione Brevo completa, mai attivata perché le
variabili d'ambiente `BREVO_API_KEY`/`BREVO_LIST_ID` non erano mai state impostate. Confermato con Alex di
lasciare generico il campo "interesse" già rimosso dal form (non reintrodotto).

## Cosa è stato fatto (nel PR, non ancora in produzione)

PR aperta: https://github.com/spatialport/farmacia-vitalis-workspace/pull/1 (branch
`feat/brevo-leads-panel` → `main`, 5 file, 6 commit).

**1. Attivazione Brevo**: nessun nuovo codice necessario (già presente in `handler.py`); basta impostare
`BREVO_API_KEY`/`BREVO_LIST_ID` al deploy.

**2. Pannello lead** (`admin-leads.html`, nuovo, mirrorato identico in `deploy-www/site/` e
`fase-3-landing-page/landing/`): dashboard statica sullo stesso dominio del sito
(`https://www.farmaciavitalis.ch/admin-leads.html`, non indicizzata, protetta da token). Statistiche
aggregate, grafico a barre iscrizioni ultimi 30 giorni, tabella lead con ricerca/filtro/ordinamento,
export CSV. Nuovo endpoint Lambda `GET /leads` protetto da header `X-Admin-Token` (confronto a tempo
costante contro `ADMIN_TOKEN`, mai esposto via CORS/origin come unica barriera).

**3. Script di deploy** (`deploy-vitalis-mail.sh`): reso idempotente su installazioni già esistenti —
prima un bug faceva sì che permessi IAM (`dynamodb:Scan`) e CORS aggiornati non venissero mai applicati
a un deploy già esistente; corretto spostando quelle chiamate fuori dal blocco "crea se non esiste".

Testato: `py_compile` su handler.py, `bash -n` su deploy script, smoke test Playwright del pannello
(gate view + vista app con 40 lead sintetici, desktop e mobile, nessun errore console).

## Cosa manca per andare live

Questa sessione Cowork non ha credenziali AWS (solo connettori GitHub e ClickUp attivi) e quindi non può
eseguire il deploy. Serve che Alex (o chi ha accesso AWS CLI) lanci, da `vitalis-mail-backend/`:

```
BREVO_API_KEY="xkeysib-..." BREVO_LIST_ID="<id lista>" ADMIN_TOKEN="$(openssl rand -hex 24)" ./deploy-vitalis-mail.sh
```

Dopo il deploy, l'endpoint `/leads` stampato va incollato in `ADMIN.LEADS_ENDPOINT` in entrambe le copie
di `admin-leads.html` (commit di follow-up). Solo a quel punto il pannello e Brevo saranno verificabili
live — questo record resta `proposed` fino ad allora.
