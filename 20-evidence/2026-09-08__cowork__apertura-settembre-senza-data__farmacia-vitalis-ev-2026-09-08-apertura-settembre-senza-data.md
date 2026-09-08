---
id: farmacia-vitalis-ev-2026-09-08-apertura-settembre-senza-data
client_id: farmacia-vitalis
record_type: evidence
service_path: landing-pages
status: proposed
owner: alex-bellesia
authority: alex-bellesia
ip_owner: client
access_scope: internal
sensitivity: internal
source_ref: https://github.com/spatialport/farmacia-vitalis-workspace/commit/eabfeb9b2ce7a7b1c687e4a4890e04c84d2bf4a6
schema_version: 1.1.0
created_at: 2026-09-08
updated_at: 2026-09-08
---

# Landing: apertura comunicata come "settembre 2026", senza giorno preciso

## Contesto

Richiesta di Alex dell'8/9/2026: "Cambiare il giorno in settembre senza precisare
esattamente una data nello specifico, perché questo non lo sapremo, ma sarà
settembre. Se tutto va bene." La farmacia non ha ancora confermato la data
(task ClickUp 869eye1r8); il 25/9 messo live il 1/9 (evidence
`2026-09-01__cowork__countdown-apertura-25set`) non è più affidabile.

## Cosa è stato cambiato (commit eabfeb9, main, deploy-www run 34240374642 verde)

- `CONFIG.DATA_APERTURA` svuotata → il countdown a giorni/ore/minuti è nascosto
  (comportamento già previsto dal codice: data non valida = blocco nascosto).
- Headline IT: "Il 25 settembre, a Lumino apre…" → "A settembre, a Lumino apre…"
  (HTML + stringa i18n `hero.headline`). EN e SR dicevano già "This September" /
  "U septembru": invariate.
- JSON-LD `openingHoursSpecification`: rimosso `validFrom: 2026-09-25`.
- Badge hero "Apertura: settembre 2026", title e meta description erano già
  generici: invariati.
- Mirror `fase-3-landing-page/landing/index.html` aggiornato identico a
  `deploy-www/site/index.html`.

Verificato live su www.farmaciavitalis.ch: H1 "A settembre, a Lumino apre una
farmacia che ti conosce per nome", nessun "25 settembre", nessun `validFrom`.

## Quando il cliente conferma la data

Rimettere l'ISO in `CONFIG.DATA_APERTURA` (es. `2026-09-25T08:00:00+02:00`),
riportare il giorno nella headline IT se voluto, e reinserire `validFrom` nel
JSON-LD. Task ClickUp: 869eye1r8.
