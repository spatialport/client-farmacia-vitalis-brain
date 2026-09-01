---
id: farmacia-vitalis-ev-2026-09-01-team-andrea
client_id: farmacia-vitalis
record_type: evidence
service_path: landing-pages
status: proposed
owner: alex-bellesia
authority: alex-bellesia
ip_owner: client
access_scope: internal
sensitivity: internal
source_ref: https://github.com/spatialport/farmacia-vitalis-workspace/commit/9fcff6c620a897373e0c4c3bda54650333ffcdd6
schema_version: 1.1.0
created_at: 2026-09-01
updated_at: 2026-09-01
---

# Team landing — aggiunto Andrea (Farmacista FPH)

## Source
Richiesta diretta di Alex via Cowork (sessione 2026-09-01): aggiungere la
foto di Andrea alla sezione team del sito e scrivere un copy omogeneo con
gli altri membri, a partire da una bozza in prima persona fornita dal
cliente ("Farmacista FPH / Professionalita', aggiornamento costante ed
empatia... / L'approccio personalizzato alla terapia e la vostra salute
sono sempre al primo posto.").

## Factual summary
- Aggiunto un quarto membro alla sezione team (prima 3: Valerija, Biljana,
  Svetlana) in `deploy-www/site/index.html` (sito live) e nella sorgente
  `fase-3-landing-page/landing/index.html`, mantenute storicamente allineate.
- Nome: Andrea. Ruolo: "Farmacista FPH" (chiave i18n dedicata `team.rA`,
  solo italiano — le altre lingue del sito, EN e SR, restano invariate e
  al momento fanno fallback sul testo italiano per questa nuova voce).
- Copy riscritto in terza persona per coerenza di stile con gli altri
  profili e allineato per lunghezza (~152 caratteri, contro una media di
  ~142 sulle 3 schede esistenti): "Professionalita', aggiornamento
  costante ed empatia per una consulenza mirata e una terapia sempre su
  misura, con la vostra salute sempre al primo posto." (chiave `team.sA`).
- Foto fornita dal cliente, ritagliata a formato quadrato (busto/volto
  centrato, stesso stile delle altre) e ottimizzata in webp
  (`team-andrea.webp`, ~12KB, coerente con le altre foto del team).
- Aggiornata la griglia desktop della sezione team da 3 a 4 colonne
  (`.team-grid` breakpoint 768px) per il nuovo totale di 4 membri.
- Commit `9fcff6c620a897373e0c4c3bda54650333ffcdd6` su `main` ha innescato
  il deploy automatico (`deploy-www`, run `33500147279`, esito `success`).
  Verificato live: sezione team e immagine rispondono correttamente su
  www.farmaciavitalis.ch.

## Direct implications
- Le versioni inglese e serba/croata della sezione team non hanno ancora
  una traduzione dedicata per Andrea: se richiesto, va aggiunta in un
  prossimo giro (chiavi `team.rA`/`team.sA` nei blocchi i18n `en` e `sr`).
