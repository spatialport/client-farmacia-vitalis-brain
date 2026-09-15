---
id: farmacia-vitalis-ev-2026-09-15-produzione-post
client_id: farmacia-vitalis
record_type: evidence
service_path: content
status: proposed
owner: alex-bellesia
authority: alex-bellesia
ip_owner: client
access_scope: internal
sensitivity: internal
source_ref: https://farmaciavitalis.spatial-port.io/social-media/calendario/index.html?m=2026-10
schema_version: 1.1.0
created_at: 2026-09-15
updated_at: 2026-09-15
---

# Produzione dei post di settembre-ottobre 2026 sul sistema «Vitalis editorial» (2026-09-15)

## Source

Sessione Cowork del 15/9/2026 su richiesta di Alex: produzione visiva di dieci contenuti (post e caroselli) con Higgsfield, a partire dal brandbook v6, da tredici reference di stile fornite da Alex e dalle foto dello shooting del 9/9 (cartella «Farmacia foto»). File consegnati in `~/Downloads/Vitalis - post ottobre 2026/` (Mac di Alex) e pubblicati sulla dashboard cliente come anteprima nei box del calendario (`deploy-aws/site/social-media/calendario/media/`, dati in `data/2026-09.json`, `2026-10.json`, `2026-11.json`; commit b1ed716 e 08c0009).

## Actors

- Alex (brief, reference, decisioni), Riccardo (esecuzione e programmazione), farmacia (approvazione di ogni post: Valerija, Andrea, Biljana, Svetlana) — Spatial Port / Farmacia Vitalis

## Redaction result

Nessun dato personale oltre ai nomi del team già in canon; nessuna credenziale. Le foto reali restano nella cartella del Mac e sulla dashboard, non nel brain.

## Factual summary

- **Quindici contenuti, 38 slide, 1080×1350**: Cinque farmaci che nascono dalle piante (carosello 7, ⑨) · Andrea e Svetlana (presentazioni ④ nello stile delle card di Valerija e Biljana già pubblicate) · Come si legge l'etichetta di un integratore (carosello 7, con etichetta d'esempio evidenziata riga per riga) · La data, sabato 31 ottobre (card, foto del team davanti al cartellone «Lo sapevi che…») · Il team al completo · −1 Domani, il tempo è tutto per voi (borsina verde) · Le prime domande (carosello 7 con sticker «Fai una domanda al banco») · Difese d'autunno: cosa ha senso davvero (carosello 6) · tre post prodotto Ahura (Olio corpo Dren, Siero viso Ege, Gocce vitaminiche) · Domani apre anche THI LAND · due extra dallo shooting (Iscriviti: un regalo ti aspetta all'apertura; Ci trovi qui: Centro Opti). Didascalie e note semaforo nel file `00-DIDASCALIE.md` consegnato con i post.
- **Sistema visivo «Vitalis editorial»** (estensione del brandbook v6, non una deroga): sfondi avorio/crema dominanti (regola 70/30), deep green solo come accento, charcoal per il testo, lime per etichette e CTA; Instrument Serif come parola-display e citazioni, Urbanist per corpo ed etichette; etichetta di categoria con puntino lime in alto, contatore slide, firma «Farmacia Vitalis · Lumino» in basso (il brandbook prescrive di non sovrapporre il logo ai post; le card di presentazione mantengono il logo piccolo per coerenza con quelle pubblicate); foto reali dello shooting + scene generate senza testo (macro di crema e olio, still-life botanici, packshot su travertino/lino/ceramica) con luce naturale, grading caldo e muted, grana leggera.
- **Higgsfield** (modello nano_banana_pro, 2 crediti/immagine, ~26 immagini, nessun acquisto di crediti necessario): packshot Ahura generati dalle foto del sito del produttore mantenendo etichetta e forma; ritratti di Andrea e Svetlana dalle foto reali con solo lo sfondo sostituito (scaffali in rovere, vasi ambrati); tutte le generazioni senza testo, con il testo applicato in post-produzione (HTML → PNG).
- **Calendario aggiornato**: settembre (piano v2 dal 16/9, con i cinque contenuti prodotti collocati il 17, 18, 19, 25 e 28/9), ottobre (media su «la data» e «−1»; cinque proposte di collocazione segnate come tali: prime domande 3/10, dove siamo 13/10, difese d'autunno 17/10, team al completo 27/10, THI LAND 29/10), novembre (i tre post Ahura come proposte 2, 9 e 16/11, in attesa del piano di novembre).
- Riccardo ha già prodotto un carosello Ahura «Detergente bifasico» nello stile pharmacy (provino del 15/9) che resta valido per l'uscita ⑪ del 26/10.

## Direct implications

- Ogni post richiede l'approvazione della farmacia; i punti Gialli da verificare sono segnati nelle note: slide sul tasso (oncologia come fatto storico), copy dei tre Ahura (claim del produttore riscritti in linguaggio cosmetico), «solo prodotti da banco» per il locker, le cinque domande de «Le prime domande» (nostre, da sostituire con quelle reali).
- La foto `team-andrea.webp` sulla landing www.farmaciavitalis.ch non ritrae Andrea (ritratto generico): va sostituita con la foto reale dello shooting.
- Quota prodotto della strategia (feed ≤5% promo, un contenuto prodotto al mese): i tre post Ahura non stanno in ottobre; proposti in novembre o in storie/newsletter.
- «Domani apre anche THI LAND» dice «domani»: il 30/10 è occupato dalla vigilia (max un contenuto al giorno) → il 29 con copy «dopodomani» o in storia; da concordare con Daniele (THI LAND).
- Serve il consenso di Andrea e Svetlana sulle foto ambientate; orario di apertura del sabato ancora assente dai copy (vigilia).

## Candidate tasks

- Inviare i post alla farmacia per approvazione a blocchi settimanali (Riccardo) e programmare in Meta Business Suite quelli approvati.
- Sostituire la foto di Andrea sulla landing con quella reale (Alex/Jacopo).
- Confermare con Daniele il post THI LAND e la data del 29 o 30/10.
- Decidere la collocazione delle cinque proposte di ottobre e dei tre Ahura di novembre (Alex).

## Candidate decisions

- Il sistema «Vitalis editorial» (serif display + foto reali + scene generate senza testo, firma testuale al posto del logo) è lo standard visivo dei post dal 15/9/2026.
- Le immagini generate si usano solo per scene senza persone o come ambientazione di foto reali con volto invariato; mai per rappresentare il locale prima che esista.

## Candidate canon

- `10-canon/brand.md` (o equivalente): registrare il sistema «Vitalis editorial» come applicazione social del brandbook v6 e la regola «logo mai sovrapposto ai post, firma testuale».
- `10-canon/channels.md`: il calendario ospita anche settembre (v2) e le proposte di novembre; i media dei post vivono in `social-media/calendario/media/`.
