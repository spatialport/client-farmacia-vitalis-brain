---
id: farmacia-vitalis-ev-2026-09-01-banner-wa-booking
client_id: farmacia-vitalis
record_type: evidence
service_path: landing-pages
status: proposed
owner: alex-bellesia
authority: alex-bellesia
ip_owner: client
access_scope: internal
sensitivity: internal
source_ref: https://github.com/spatialport/farmacia-vitalis-workspace/commit/370b9d8b3975aea39a3948a43d2e9e935af0b0ce
schema_version: 1.1.0
created_at: 2026-09-01
updated_at: 2026-09-01
---

# Landing — rimossa barra "in costruzione", aggiunto pulsante WhatsApp, ricerca per sistema di prenotazione

## Source
Richiesta diretta di Alex via Cowork (sessione 2026-09-01), tre punti in un
solo messaggio: (1) rimuovere il testo "Sito in fase di costruzione · lo
stiamo preparando con cura"; (2) aggiungere un pulsante WhatsApp fisso in
basso a destra e poi un sistema di prenotazione gratuito ("cosa usiamo?
deve essere gratuito"); (3) prima di scegliere il sistema di prenotazione,
consultare brand book e documenti di discovery per capire quali servizi
della farmacia sono davvero prenotabili.

## Factual summary — implementato e live

- Rimossa interamente la "BARRA IN FASE DI COSTRUZIONE" (HTML, CSS e le 3
  chiavi i18n `constr.text` IT/EN/SR) da `deploy-www/site/index.html` e
  dalla sorgente `fase-3-landing-page/landing/index.html`, mantenute
  allineate come da prassi.
- Aggiunto un pulsante WhatsApp flottante fisso in basso a destra
  (`.wa-float`, id `waFloat`), stile verde WhatsApp per riconoscibilità
  immediata, posizionato per non sovrapporsi alla sticky-CTA mobile
  esistente e nascosto quando è aperto il banner cookie. Usa lo stesso
  numero già configurato (`CONFIG.WHATSAPP_NUMBER`) e lo stesso helper
  `waUrl()`/`refreshWaLinks()` già presenti nel codice (aggiornato per
  includere anche `waFloat`), quindi resta coerente con lingua e
  messaggio precompilato degli altri link WhatsApp del sito.
- Commit `370b9d8b3975aea39a3948a43d2e9e935af0b0ce` su `main` ha innescato
  il deploy automatico (`deploy-www`, run `33516631433`, esito `success`).
  Verificato live su www.farmaciavitalis.ch: banner assente, pulsante
  WhatsApp presente e funzionante.

## Ricerca per il sistema di prenotazione (non ancora implementato)

Letti `10-canon/offer.md`, `10-canon/operations.md`,
`05-onboarding/discovery-question-bank.md`, `10-canon/company.md`,
`10-canon/positioning.md` e il brand book (`deploy-aws/site/brandbook-v6.html`).

- Il sito ha già un'impalcatura di prenotazione pronta e pensata
  esplicitamente per **Calendly**: slot dedicato `CONFIG.CALENDLY_URL`,
  box `.booking-box`/`#bookingBox`, stati gestiti da `renderBookingState()`
  e `loadCalendly()` (iframe caricato solo dopo consenso cookie + click
  utente, coerente con nLPD). Con `CALENDLY_URL` vuoto il box mostra già
  oggi, correttamente, un messaggio "le prenotazioni arrivano presto" con
  invito a scriversi alla lista o su WhatsApp — quindi nessuna sezione
  rotta nel frattempo.
- **Raccomandazione: Calendly free** (1 solo tipo di evento gratuito per
  sempre, prenotazioni illimitate, domande personalizzate incluse) — non
  richiede alcuna modifica di codice, basta creare un account gratuito e
  incollare il link nello slot già pronto. Un solo tipo di evento generico
  ("Appuntamento in farmacia", con una domanda personalizzata tipo "di
  cosa hai bisogno?") copre i servizi oggi comunicabili pubblicamente
  (vedi vincolo sotto), senza bisogno del limite di più tipi di evento.
- **Vincolo legale da rispettare** (da `operations.md`, sezione vincoli
  pubblicitari svizzeri LATer/OPuM): vaccinazioni e check-up rimborsabile
  da cassa malati sono tra le claim **⚠ bloccate in attesa di validazione
  scritta del medico responsabile del complesso** — non vanno quindi
  offerte come prenotabili pubblicamente finché non arriva quel via
  libera. I servizi già nel perimetro consentito e prenotabili da subito:
  consulenza naturopata (gratuita, 10–15 min), misurazioni (es. pressione),
  controllo calze a compressione, giornate a tema ("Le Giornate Vitalis").
- **Blocco per procedere**: manca solo un account Calendly gratuito del
  cliente/agenzia con il link di prenotazione da incollare in
  `CONFIG.CALENDLY_URL` — non è qualcosa che posso creare per conto del
  cliente. Appena arriva il link, l'attivazione è immediata (nessuna
  modifica strutturale al sito).

## Direct implications
- Il testo attuale della sezione prenotazioni ("...la consulenza con la
  naturopata, i check-up e le misurazioni...") usa la parola "check-up" in
  modo generico: da rivedere con il cliente per assicurarsi che non venga
  letta come il check-up farmacista rimborsabile da cassa malati, ancora
  bloccato in attesa di validazione legale.
- Conferma già segnalata in evidence precedente
  (`2026-09-01__cowork__countdown-apertura-25set`): permane il conflitto
  sulla data di apertura definitiva (25/09 sul sito vs 30/09 in una
  chiamata precedente) — da chiudere con il cliente prima di stampare
  qualunque materiale con data fissa.
