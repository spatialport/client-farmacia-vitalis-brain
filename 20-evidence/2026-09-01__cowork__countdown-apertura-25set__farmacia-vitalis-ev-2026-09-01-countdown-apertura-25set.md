---
id: farmacia-vitalis-ev-2026-09-01-countdown-apertura-25set
client_id: farmacia-vitalis
record_type: evidence
service_path: landing-pages
status: proposed
owner: alex-bellesia
authority: alex-bellesia
ip_owner: client
access_scope: internal
sensitivity: internal
source_ref: https://github.com/spatialport/farmacia-vitalis-workspace/commit/9a284f207dd10e8d8553f925652e72a1e00c0e04
schema_version: 1.1.0
created_at: 2026-09-01
updated_at: 2026-09-01
---

# Countdown apertura landing — data aggiornata 12 -> 25 settembre 2026

## Source
Richiesta diretta di Alex via Cowork (sessione 2026-09-01): "dovremmo cambiare
il conto alla rovescia per la farmacia. L'apertura sara' il 25 settembre e
mancano quindi 24 giorni." Nessun transcript raw da redigere.

## Factual summary
- Il countdown live su www.farmaciavitalis.ch e' pilotato da una singola
  costante `CONFIG.DATA_APERTURA` in `deploy-www/site/index.html` (repo
  `farmacia-vitalis-workspace`); il JS (`tickCountdown`) calcola giorni/ore/min
  a runtime, nessun valore statico da aggiornare altrove sul countdown stesso.
- Valore precedente: `2026-09-12T08:00:00+02:00`. Nuovo valore:
  `2026-09-25T08:00:00+02:00` (invariato l'orario 08:00 Europe/Zurich).
- Aggiornato in coerenza anche `openingHoursSpecification.validFrom` nel
  JSON-LD della pagina, da `2026-09-12` a `2026-09-25`.
- Modifica applicata in un unico commit atomico su 3 copie del file nel repo
  (mantenute storicamente allineate): sorgente
  `fase-3-landing-page/landing/index.html`, bundle interno
  `deploy-aws/site/fase-3-landing-page/landing/index.html`, e sito live
  `deploy-www/site/index.html`.
- Commit `9a284f207dd10e8d8553f925652e72a1e00c0e04` su `main` ha innescato in
  automatico il workflow GitHub Actions `deploy-www` (run `33497603256`,
  esito `success`): sync S3 + invalidation CloudFront su `www.farmaciavitalis.ch`.
- Verificato live via fetch diretto di https://www.farmaciavitalis.ch/ dopo il
  deploy: countdown e JSON-LD mostrano correttamente `2026-09-25`.

## Direct implications
- Nessun'altra pagina o asset nel repo referenzia la data di apertura in modo
  statico (nessun altro hit per `09-12` fuori da questi due punti), quindi non
  risultano altri posti da correggere per questo cambio.

## Conflitto da segnalare
Il record evidence `20-evidence/2026-08-25__call__opening-comms-plan__farmacia-vitalis-ev-2026-08-25-opening-comms-call.md`
(call del 25/08/2026) riporta come data di apertura discussa il **30/09/2026**,
diversa sia dalla vecchia costante nel sito (12/09) sia dalla nuova (25/09).
Da verificare con il cliente quale sia la data ufficiale definitiva prima
della pubblicazione di materiali stampa (locandina, ecc.) che dipendono da
questa data.

## Candidate tasks
- Confermare con il cliente la data di apertura ufficiale definitiva (25/09
  vs 30/09 menzionato nella call del 25/08) e allineare canon + eventuali
  materiali stampa/locandina.
