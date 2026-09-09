---
id: farmacia-vitalis-ev-2026-09-09-hero-headline
client_id: farmacia-vitalis
record_type: evidence
service_path: landing-pages
status: proposed
owner: alex-bellesia
authority: alex-bellesia
ip_owner: client
access_scope: internal
sensitivity: internal
source_ref: https://github.com/spatialport/farmacia-vitalis-workspace/commit/b2a3a13615bd026a8695f31541cf0ebef898bfcc
schema_version: 1.1.0
created_at: 2026-09-09
updated_at: 2026-09-09
---

# www.farmaciavitalis.ch — nuovo headline hero (2026-09-09)

## Cosa è cambiato

Su richiesta di Alex, l'headline della hero della landing www.farmaciavitalis.ch è passato da
"A settembre, a Lumino apre una farmacia che ti conosce per nome." a
"Lo sapevi che… Sta per aprire una farmacia unica a Lumino?" (enfasi su *unica*).

Aggiornati nello stesso commit anche i corrispondenti EN ("Did you know… A one-of-a-kind pharmacy is about to open in Lumino?") e SR ("Jesi li znao… Uskoro se u Luminu otvara jedinstvena apoteka?") nel dizionario I18N, così le tre lingue restano coerenti.

Non toccati: meta description / og:description (restano sul claim "ti conosce per nome"), badge, sottotitolo, tagline.

## Dove

- Repo: spatialport/farmacia-vitalis-workspace, file deploy-www/site/index.html (h1 #heroH1 + chiavi I18N hero.headline it/en/sr)
- Commit: b2a3a13 (via workflow ops-replace) — deploy-www run #12 verde, live verificato (last-modified 2026-09-09 20:42 UTC)

## Nota operativa

Aggiunto al workspace repo il workflow `.github/workflows/ops-replace.yml` (workflow_dispatch: path + replacements JSON + message → commit su main + lancio deploy). Serve a fare modifiche testuali chirurgiche da Cowork su file troppo grandi da rispedire interi tramite connettore (index.html ~300 KB). Candidato a diventare standard nel workspace-template.