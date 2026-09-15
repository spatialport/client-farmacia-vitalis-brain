---
id: farmacia-vitalis-ev-2026-09-15-bacheca-carosello-reel
client_id: farmacia-vitalis
record_type: evidence
service_path: content
status: proposed
owner: alex-bellesia
authority: alex-bellesia
ip_owner: client
access_scope: internal
sensitivity: internal
source_ref: https://farmaciavitalis.spatial-port.io/feed-social.html
schema_version: 1.1.0
created_at: 2026-09-15
updated_at: 2026-09-15
---

# Terzo post pubblicato (carosello detergente bifasico) e primo reel del team in bacheca (2026-09-15, sera)

## Source

Sessione Cowork del 15/9/2026 (sera) su richiesta di Alex: aggiungere alla bacheca della dashboard il carosello «Detergente bifasico all'avocado» come terzo post pubblicato e il «Reel 1 da pubblicare» del team; file in `~/Downloads` (cartella «Carosello mancante», `Reel 1da pubblicare.mp4`). Repo `spatialport/farmacia-vitalis-workspace`, commit 71e85ac (media), 49edf60 (dati calendario), c601727 (calendario), 50b753e (bacheca e pagine). Tabella `vitalis-social` ricaricata con il workflow `ops-social-seed` (run verde).

## Actors

- Alex (decisioni), Riccardo (autore del carosello e del reel), farmacia Vitalis (approvazione) — Spatial Port / Farmacia Vitalis

## Redaction result

Nessun dato personale oltre ai nomi del team già in canon; nessuna credenziale.

## Factual summary

- **Carosello «Detergente bifasico all'avocado»** (Laboratorio Ahura, 6 slide, template pharmacy di Riccardo): pubblicato il 15/9/2026, terzo post del profilo dopo Valerija (4/8) e Biljana (6/8). In bacheca come post 03 «approvato / Pubblicato.», nel calendario al 15/9 con stato «Pubblicato»; il provino previsto al 26/10 è stato tolto.
- **Reel 1 «Il team che ti conoscerà per nome»** (30 s, 576×1024, senza audio nel file): nella card 01/04 compare Paride, che nei materiali dal 13/9 è sostituito da Andrea. Decisione di Alex: caricarlo comunque in bacheca (post 04, stato «modifiche», nota di rimontaggio) e nel calendario al 16/9 con il nuovo stato «Da rifare»; la caption è già scritta con Andrea. Il post Iscriviti-regalo slitta dal 16 al 17/9.
- **Dashboard**: il calendario parte ora da agosto 2026 (le due card pubblicate) e conosce lo stato `da_rifare`; `feed-social.html` e `piano-social.html` usano il campo `poster` dei post video per copertina e player. Bacheca = 19 post (3 pubblicati, 1 reel da rifare, 15 da validare).

## Direct implications

- Il reel non va programmato finché non viene rimontato con Andrea; quando arriva la versione nuova si sostituisce `social-media/04-reel-team.mp4` e il poster, e si ricarica la tabella.
- Con il carosello bifasico già uscito, i tre post Ahura del 9, 12 e 14/10 superano di molto la quota prodotto della strategia v3: da confermare o diluire.

## Candidate tasks

- Rimontare il Reel 1 con Andrea al posto di Paride (Riccardo), poi approvazione della farmacia e pubblicazione il 16/9 o alla prima data utile.
- Confermare o diluire i tre post Ahura di ottobre (Alex).

## Candidate decisions

- I post pubblicati entrano nel calendario con stato «Pubblicato» e con i media in `social-media/`; un contenuto esistente ma da rifare entra con stato «Da rifare», non resta fuori.

## Candidate canon

- `10-canon/channels.md`: aggiornare l'elenco dei post pubblicati (Valerija 4/8, Biljana 6/8, Detergente bifasico 15/9) e registrare che Andrea sostituisce Paride in tutti i materiali social, reel compresi.
