---
id: farmacia-vitalis-ev-2026-09-15-rimodulazione-calendario
client_id: farmacia-vitalis
record_type: evidence
service_path: content
status: proposed
owner: alex-bellesia
authority: alex-bellesia
ip_owner: client
access_scope: internal
sensitivity: internal
source_ref: https://farmaciavitalis.spatial-port.io/social-media/calendario/index.html?m=2026-09
schema_version: 1.1.0
created_at: 2026-09-15
updated_at: 2026-09-15
---

# Calendario rimodulato sui contenuti prodotti e reset della bacheca social (2026-09-15, sera)

## Source

Sessione Cowork del 15/9/2026 (sera) su richiesta di Alex, subito dopo la produzione dei quindici contenuti (evidence `farmacia-vitalis-ev-2026-09-15-produzione-post`). Repo `spatialport/farmacia-vitalis-workspace`: commit 7b4c5cc (dati calendario), 02aac1d (`deploy-aws/site/social-seed.json`), 3ff6ac7 (workflow `ops-social-seed`), 00e66b4 (script `vitalis-social-backend/reseed-vitalis-social.sh`). Dashboard cliente: calendario e file seed live (deploy `deploy-portale` verde).

## Actors

- Alex (decisioni), Riccardo (esecuzione), farmacia Vitalis (approvazione dei post) — Spatial Port / Farmacia Vitalis

## Redaction result

Nessun dato personale, nessuna credenziale: la password della bacheca non è stata toccata né richiesta; l'ARN del ruolo IAM e l'id dell'account AWS compaiono solo nei file del repo, non qui.

## Factual summary

- **Regola decisa da Alex**: dal 16/9 il calendario editoriale contiene solo i contenuti già prodotti, tre a settimana (lun/mer/ven), finché ce ne sono; i reel restano in pausa (tolti dal calendario, non dalla strategia); i contenuti-evento del lancio restano a data fissa. Pubblicati finora sui social: solo le presentazioni di Valerija e Biljana.
- **Sequenza live**: settembre 16 Iscriviti-regalo · 18 Cinque farmaci dalle piante · 21 Andrea · 23 Etichetta di un integratore · 25 Svetlana · 28 Le prime domande · 30 Ci trovi qui; ottobre 1 La data (bloccato fino alla conferma scritta) · 5 Difese d'autunno · 7 Team al completo · 9/12/14 i tre Ahura · 26 La scelta di Svetlana (provino di Riccardo) · 29 THI LAND · 30 −1 (bloccato) · 31 Siamo aperti (da produrre). Vuoti: 16–25 ottobre e novembre.
- **Tolti dal calendario v3 di ottobre**: reel ①②④⑥, serie ⑤ «Sta prendendo forma», giveaway ⑬, card ⑨/⑩ non prodotte. I file media conservano il prefisso della prima collocazione.
- **Bacheca social** (Anteprima feed + Validazione): il seed passa da 35 post dell'anteprima di agosto (tutti «da validare», nessuna nota della farmacia) a 17: Valerija e Biljana come «approvato / Pubblicato.» + i quindici nuovi «da validare». La tabella DynamoDB `vitalis-social` non è stata ricaricata dal cloud: il workflow `ops-social-seed` fallisce perché il ruolo OIDC `github-actions-deploy-sites` non ha permessi DynamoDB (AccessDenied su Scan). Ricaricamento affidato ad Alex con lo script `reseed-vitalis-social.sh` (AWS CLI, mode replace/upsert); la policy IAM da aggiungere al ruolo è documentata nello script.

## Direct implications

- Fino al ricaricamento della tabella la dashboard mostra ancora i 35 post vecchi nell'anteprima feed; il calendario è già aggiornato.
- I tre Ahura in fila (9, 12, 14/10) eccedono la quota prodotto della strategia v3 (≤1 contenuto prodotto al mese sul feed): da confermare o diluire quando arriverà altra produzione.
- Il vuoto 16–25/10 e novembre vanno riempiti con la prossima produzione (o con i reel, se si esce dalla pausa).
- Prossimo task dichiarato da Alex: inserire le modifiche per correggere eventuali errori nei post.

## Candidate tasks

- Ricaricare la tabella `vitalis-social` con lo script (Alex) e, una tantum, dare al ruolo `github-actions-deploy-sites` i permessi DynamoDB per rendere usabile il workflow dal cloud.
- Raccogliere le correzioni ai quindici post e riprodurre le slide interessate (Claude/Riccardo).
- Pianificare la produzione per il 16–25/10 e novembre; decidere se e quando riattivare i reel (Alex).

## Candidate decisions

- Il calendario ospita solo contenuti prodotti o a data fissa; le uscite non prodotte non restano come segnaposto.
- La bacheca della dashboard contiene solo i post pubblicati e quelli in validazione: i post di anteprima superati si tolgono.

## Candidate canon

- `10-canon/channels.md`: ritmo di pubblicazione temporaneo tre a settimana con i soli contenuti prodotti, reel in pausa dal 15/9/2026 fino a nuova decisione; strumenti operativi della bacheca (`reseed-vitalis-social.sh`, workflow `ops-social-seed`).
