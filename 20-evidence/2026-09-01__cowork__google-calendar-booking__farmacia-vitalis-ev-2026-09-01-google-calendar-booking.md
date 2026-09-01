---
id: farmacia-vitalis-ev-2026-09-01-google-calendar-booking
client_id: farmacia-vitalis
record_type: evidence
service_path: landing-pages
status: proposed
owner: alex-bellesia
authority: alex-bellesia
ip_owner: client
access_scope: internal
sensitivity: internal
source_ref: https://github.com/spatialport/farmacia-vitalis-workspace/commit/e0edb69217e11460c33ee1ad38c3aca957954fe4
schema_version: 1.1.0
created_at: 2026-09-01
updated_at: 2026-09-01
---

# Sistema di prenotazione: implementato Google Calendar (supera raccomandazione Calendly)

## Contesto

Nella evidence precedente (`2026-09-01__cowork__banner-wa-booking`, PR #4) era stato raccomandato Calendly Free
come strumento di prenotazione, per zero modifiche di codice necessarie sullo scaffold già presente nel sito.

Il cliente ha valutato l'alternativa e ha scelto esplicitamente **Google Calendar** (funzione "Pagine di
prenotazione", gratuita con account Google personale/business, nessun upgrade a Workspace richiesto) al posto di
Calendly. Questa evidence documenta l'implementazione finale, che sostituisce la raccomandazione precedente.

## Cosa è stato fatto

**1. Pagina di prenotazione Google Calendar** creata sull'account Google dedicato alla farmacia
(`info@farmaciavitalis.ch`, non l'account personale dell'agenzia):

- Titolo: "Appuntamento in farmacia — Farmacia Vitalis"
- Durata appuntamento: 20 minuti
- Disponibilità: Lun-Ven 9:00-12:00 e 14:00-18:00, Sab 9:00-12:00, Dom chiuso
- Finestra di prenotazione: da lunedì 28 settembre 2026 (prima settimana lavorativa dopo l'apertura del
  25/09/2026), nessuna data di fine
- Luogo: "Riunione di persona" — Farmacia Vitalis, Via Mesolcina 17, 6533 Lumino, Svizzera
- Descrizione: testo su consulenza naturopata (gratuita), misurazioni, controllo calze a compressione —
  **deliberatamente esclusi vaccinazioni e check-up farmacista fatturabili a cassa malati**, per il blocco
  normativo LATer/OPuM identificato in `operations.md` (in attesa di validazione legale sanitaria)
- Domanda personalizzata obbligatoria nel form: "Di cosa hai bisogno? (es. consulenza naturopata, misurazione
  pressione, controllo calze a compressione)", oltre ai campi predefiniti Nome/Cognome/Email

Link pubblico pagina di prenotazione: `https://calendar.app.google/bSbwuf4DYFv5HWNq9`

**2. Sostituito lo scaffold Calendly-specifico nel sito** con l'embed Google Calendar (commit
`e0edb69217e11460c33ee1ad38c3aca957954fe4` su `main`, applicato a entrambi `deploy-www/site/index.html` e
`fase-3-landing-page/landing/index.html`, mantenuti identici):

- `CONFIG.CALENDLY_URL` → `CONFIG.BOOKING_URL`, valorizzato con l'URL iframe Google Calendar:
  `https://calendar.google.com/calendar/appointments/schedules/AcZssZ2NXej_Z8IfWWm69QM2nHnyJ1VylfmmvcHMUWi1QgR1GFUaNXKnOJ8lSEzQTx52fHiO4k-NTd5d?gv=true`
- Funzione JS `loadCalendly()` → `loadBooking()`; variabili `calendlyLoaded`/`calendlyUserRequested` →
  `bookingLoaded`/`bookingUserRequested`
- Rimosso il parametro query Calendly-specifico `hide_gdpr_banner=1` (non applicabile a Google Calendar)
- Copy i18n (`book.ready`, IT/EN/SR) aggiornato per non nominare più uno strumento specifico, evitando
  accoppiamento futuro tra copy e vendor
- **Preservato il pattern di consenso cookie esistente**: l'iframe viene creato via JS solo dopo consenso
  cookie funzionale + click esplicito dell'utente su "Carica il calendario" (requisito nLPD)

**3. Verifica live**: deploy GitHub Actions `deploy-www` completato con successo (run `33524701350`,
conclusion `success`). Confermato via curl su `www.farmaciavitalis.ch`: nessun riferimento residuo a "Calendly",
`BOOKING_URL` valorizzato correttamente, banner "in costruzione" rimosso, pulsante WhatsApp flottante presente.

## Limite noto — lingua del widget di prenotazione

Test diretto sull'URL pubblico della pagina di prenotazione (browser senza sessione Google specifica) mostra che
i controlli dell'interfaccia di Google Calendar (es. "Select an appointment time", nomi giorni, pulsanti) si
adattano alla lingua del browser/account Google del **visitatore**, non a quella dell'organizzatore — quindi non
sono bloccati sull'italiano. Il titolo e la descrizione dell'appuntamento, invece, restano sempre nel testo
inserito dall'organizzatore (italiano), per tutti i visitatori, in tutte le lingue del sito (IT/EN/SR): Google
Calendar Free permette una sola pagina di prenotazione, quindi non è possibile avere versioni localizzate
separate per lingua senza upgrade o strumento alternativo. Impatto: visitatori EN/SR vedranno il riquadro di
prenotazione con testo descrittivo in italiano. Non bloccante per il lancio; da rivalutare se serve piena
localizzazione.

## Servizi prenotabili (invariato rispetto alla ricerca precedente)

Confermato conforme a `operations.md`: consulenza naturopata (gratuita), misurazioni, controllo calze a
compressione, giornate a tema. Vaccinazioni e check-up farmacista fatturabili a cassa malati restano esclusi
dalla comunicazione pubblica fino a validazione legale sanitaria (blocco LATer/OPuM).
