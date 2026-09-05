---
id: farmacia-vitalis-ev-2026-09-04-funnel-brevo-codice-apertura
client_id: farmacia-vitalis
record_type: evidence
service_path: crm
status: proposed
owner: alex-bellesia
authority: alex-bellesia
ip_owner: client
access_scope: internal
sensitivity: internal
source_ref: https://github.com/spatialport/farmacia-vitalis-workspace/pull/2
schema_version: 1.1.0
created_at: 2026-09-04
updated_at: 2026-09-04
---

# Funnel post-iscrizione: codice sconto univoco + sequenza di 3 email su Brevo

## Contesto

Dalla call del 02/09/2026: "dopo c'e' da fare la prima mail che ti arriva una volta che ti sei
iscritto" (Alex); Jacopo prende in carico il funnel. Modello di riferimento: la sequenza gia'
fatta su THI LAND con Brevo. Oggi la landing raccoglie nome/email (+ telefono e data di nascita
facoltativi) ma **chi si iscrive non riceve nulla**: i lead si perdono prima dell'apertura.

Decisioni di Alex in questa sessione: codice sconto **univoco per lead** (non un codice unico
condiviso); l'email la manda un'**automazione Brevo con trigger**, non la Lambda; mittente
`info@farmaciavitalis.ch`; data di apertura **7 ottobre come placeholder** finche' non e' confermata.

## Il flusso mappato

1. **Iscrizione** — landing `farmaciavitalis.ch` -> `POST /iscrizione` (API `8nnw8bhsx2`) -> Lambda
   `vitalis-mail-intake` -> lead in DynamoDB `vitalis-anteprima`.
2. **Generazione codice** — la Lambda genera `VIT-XXXX-XX` e lo riserva con put condizionale su
   `vitalis-codici` (PK = `codice`): unicita' garantita, verifica O(1). Un lead = un codice.
3. **Contatto in Brevo** — upsert in lista con gli attributi `NOME`, `CODICE`, `SCADENZA`,
   `APERTURA`, `FONTE`. L'attributo deve esistere PRIMA dell'ingresso in lista, perche' e'
   l'ingresso in lista a innescare l'automazione.
4. **Email 1 — benvenuto immediato** (template Brevo id 1): conferma il regalo di apertura, mostra
   il codice, cosa trovi in farmacia, indirizzo, WhatsApp. Trigger: contatto aggiunto alla lista.
5. **Email 2 — pre-apertura** (template id 2): data di apertura, ripete il codice, invita alla
   consulenza naturopatica gratuita, mappa. Tempificata prima dell'apertura.
6. **Email 3 — post-apertura** (template id 3): chiede feedback (risposta diretta all'email),
   ricorda che il codice e' ancora valido a chi non e' passato, riapre la consulenza.
7. **Riscatto al banco** — `verifica-codice.html` (non indicizzata, protetta da token) chiama
   `GET /codice?c=...` e `POST /codice/riscatta`: valido / gia' usato / scaduto / inesistente.
   Il riscatto e' un update condizionale, quindi due cassieri sullo stesso codice non lo bruciano
   due volte.

## Stato al 04/09/2026

**Fatto:**
- Backend completo in PR #2 del workspace (impilata su PR #1): generazione codice, attributi Brevo,
  rotte di verifica e riscatto, deploy script con tabella e permessi. Verificato con `py_compile`
  e `bash -n`.
- I tre template email creati in Brevo (id 1, 2, 3), copy IT, con `{{ contact.CODICE }}`,
  `{{ contact.SCADENZA }}`, `{{ contact.APERTURA }}` e link di disiscrizione.
- Pagina di verifica al banco pronta (`verifica-codice.html`).

**Bloccato, e da chi dipende:**
- **Deploy AWS** — la sessione Cowork non ha credenziali AWS (stesso muro di PR #1 e di
  `fix-turni.sh` su THI LAND). Serve `ADMIN_TOKEN=... BREVO_API_KEY=... BREVO_LIST_ID=...
  ./deploy-vitalis-mail.sh` da una macchina con AWS CLI.
- **Lista, attributi e automazione Brevo** — il connettore Brevo di Cowork espone creazione di
  template e campagne, ma NON creazione di liste, attributi o automazioni: vanno fatte dalla UI.
- **Mittente** — l'account Brevo di Vitalis e' nuovo (creato il 04/09), piano free 300 email/giorno,
  unico mittente `alex@spatial-port.com`. Va aggiunto e verificato `info@farmaciavitalis.ch` e
  autenticato il dominio (DKIM su Infomaniak), altrimenti le email finiscono nello spam.
- **Test end-to-end** ("mail 1 entro 1 minuto dall'iscrizione") — non eseguibile finche' la Lambda
  non e' deployata con la chiave Brevo: senza, nessun contatto entra in lista e l'automazione non
  parte.

## Conflitto da segnalare

La **data di apertura** ha ora tre valori in circolazione: il sito live mostra un countdown al
**25 settembre**, la call del 25/08 riportava **30 settembre**, e Alex ha indicato **7 ottobre**
come placeholder per il nuovo funnel. Il placeholder e' stato applicato solo al backend e alle
email; la landing live non e' stata toccata, perche' cambiarla significa riscrivere 16 occorrenze
di "settembre" (titolo e descrizione SEO compresi) attorno a una data non confermata. Da
riconciliare col cliente prima di stampati e prima di far partire la sequenza.

## Nota nLPD

Il codice arriva come conseguenza diretta di una richiesta esplicita (email transazionale), e questo
regge. Per gli invii marketing successivi alla sequenza di apertura va attivato il **double opt-in**:
il flusso attuale e' single opt-in, con il benvenuto che fa da conferma.

## Candidate tasks

- Deploy `vitalis-mail-backend` con Brevo e ADMIN_TOKEN (Alex, macchina con AWS CLI).
- Creare lista, attributi e automazione in Brevo e collegarli ai template 1-3 (Jacopo).
- Verificare `info@farmaciavitalis.ch` in Brevo e aggiungere DKIM su Infomaniak (Alex).
- Confermare col cliente la data di apertura definitiva e allineare landing, canon e stampati.
- Test end-to-end con iscrizione reale dopo il deploy, e ok di Alex.
