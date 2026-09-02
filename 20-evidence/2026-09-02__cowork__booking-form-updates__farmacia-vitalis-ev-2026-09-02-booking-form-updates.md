---
id: farmacia-vitalis-ev-2026-09-02-booking-form-updates
client_id: farmacia-vitalis
record_type: evidence
service_path: landing-pages
status: proposed
owner: alex-bellesia
authority: alex-bellesia
ip_owner: client
access_scope: internal
sensitivity: internal
source_ref: https://github.com/spatialport/farmacia-vitalis-workspace/commit/0af0b0a38d29fa78c23cf29d6f239deb23dcf534
schema_version: 1.1.0
created_at: 2026-09-02
updated_at: 2026-09-02
---

# Prenotazioni e form iscrizione: calendario auto-caricato/ingrandito, rimosso campo interesse e messaggio errore privacy

## Contesto

Richiesta di tre modifiche indipendenti al sito live, tutte gia verificate su copia sandbox prima dello shipping:
velocizzare l'accesso al widget di prenotazione, ingrandire il riquadro prenotazioni, e semplificare il form di
iscrizione newsletter/lead rimuovendo un campo facoltativo e un messaggio di errore ridondante.

## Cosa e stato fatto

**1. Calendario di prenotazione auto-caricato**: rimosso il click aggiuntivo "Carica il calendario" richiesto
dopo il consenso cookie -- l'iframe Google Calendar ora si carica automaticamente non appena il consenso cookie
funzionale e dato, riducendo l'attrito prima della prenotazione.

**2. Riquadro di prenotazione ingrandito** per riempire meglio la sezione: max-width 780px -> 980px,
min-height 340px -> 640px, .has-cal min-height 580px -> 760px, altezza iframe 640px -> 760px.

**3. Form iscrizione - rimosso il campo "Cosa ti interessa di piu?"**: eliminato il menu a tendina facoltativo
insieme alla relativa i18n (lead.fInt, lead.opt0-lead.opt6), alla validazione JS (case "inInt") e al
campo payload INTERESSE inviato al backend.

**4. Form iscrizione - rimosso il messaggio di errore privacy**: eliminato il testo "Per iscriverti serve il
consenso al trattamento dei dati. E la legge, e ci teniamo anche noi." mostrato quando la checkbox privacy
obbligatoria viene lasciata deselezionata. La checkbox resta obbligatoria e la validazione JS blocca comunque
l'invio del form senza consenso -- e stato rimosso solo il messaggio di testo mostrato all'utente.

Commit su main: 0af0b0a38d29fa78c23cf29d6f239deb23dcf534, applicato identico a entrambe le copie del sito
(deploy-www/site/index.html e fase-3-landing-page/landing/index.html).

## Verifica live

Deploy GitHub Actions deploy-www completato con successo (run 33650059746, conclusion success,
head commit 0af0b0a3). Nota tecnica: il push del commit di contenuto e stato fatto da un workflow con il
token predefinito di GitHub Actions, che per design non genera automaticamente altri workflow run -- e stato
quindi necessario un workflow_dispatch manuale su deploy-www per pubblicare su S3/CloudFront.

Confermato via fetch diretto (cache-busted) su https://www.farmaciavitalis.ch:
- ETag della risposta (d89045ceb07dd7f978e1458bf6393efc) e content-length (300897) identici al contenuto
  atteso, x-cache: Miss from cloudfront dopo l'invalidazione.
- Nessun riferimento residuo a INTERESSE, inInt, lead.fInt, o al testo "Per iscriverti serve il
  consenso...".
- Presenti nel CSS i nuovi valori 980px (max-width booking box), 640px/760px (min-height booking box /
  .has-cal / iframe).

Nessun impatto sui servizi prenotabili ne sui vincoli normativi gia documentati in operations.md.
