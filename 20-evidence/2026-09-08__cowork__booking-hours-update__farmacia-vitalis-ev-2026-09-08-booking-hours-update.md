---
id: farmacia-vitalis-ev-2026-09-08-booking-hours-update
client_id: farmacia-vitalis
record_type: evidence
service_path: landing-pages
status: proposed
owner: alex-bellesia
authority: alex-bellesia
ip_owner: client
access_scope: internal
sensitivity: internal
source_ref: https://calendar.google.com/calendar/appointments/schedules/AcZssZ2NXej_Z8IfWWm69QM2nHnyJ1VylfmmvcHMUWi1QgR1GFUaNXKnOJ8lSEzQTx52fHiO4k-NTd5d?gv=true
schema_version: 1.1.0
created_at: 2026-09-08
updated_at: 2026-09-08
---

# Orari di prenotazione aggiornati sulla pagina Google Calendar del sito

## Contesto

Il sito www.farmaciavitalis.ch incorpora la pagina di prenotazione Google Calendar
"Appuntamento in farmacia — Farmacia Vitalis" (account `info@farmaciavitalis.ch`,
vedi evidence `2026-09-01__cowork__google-calendar-booking`). Gli orari degli slot
vivono nella configurazione della pagina di prenotazione, non nel codice del sito:
nessuna modifica al repo `farmacia-vitalis-workspace` è stata necessaria.

## Cosa è stato cambiato (richiesta di Alex, 8/9/2026)

Configurazione precedente: slot da 20 minuti, Lun–Ven 9:00–12:00 e 14:00–18:00,
Sab 9:00–12:00, Dom chiuso.

Configurazione nuova (salvata e verificata live sulla pagina pubblica):

- Durata appuntamento: **30 minuti**, senza pause tra uno slot e l'altro
- Mattina: **8:30–12:00** → slot 8:30, 9:00, 9:30, 10:00, 10:30, 11:00, 11:30 (ultimo finisce alle 12:00)
- Pomeriggio: **13:30–18:00** → slot 13:30, 14:00, 14:30, 15:00, 15:30, 16:00, 16:30, 17:00, 17:30 (ultimo finisce alle 18:00)
- Giorni: **lunedì–venerdì**; **sabato e domenica senza appuntamenti** (Alex ha
  confermato che "tutti i giorni tranne il sabato" esclude anche la domenica)
- Invariati: finestra di prenotazione da lunedì 28/9/2026, fuso Europa/Zurigo,
  modulo, descrizione, luogo

## Verifica

Pagina pubblica ricaricata dopo il salvataggio: mostra "30 min appointments", per
Lun 28/9 – Ven 2/10 esattamente gli slot 08:30…11:30 e 13:30…17:30, Sab 3/10 e
Dom 4/10 senza disponibilità.

## Nota per il sito

Gli orari di apertura mostrati nel sito (JSON-LD `openingHoursSpecification`
08:00–18:30 Lun–Ven, `HOURS` del badge live e la riga "Orari di apertura: li
pubblicheremo qui a settembre") sono ancora placeholder e non sono stati toccati:
vanno aggiornati con gli orari definitivi della farmacia quando il cliente li conferma.
