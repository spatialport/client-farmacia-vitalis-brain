---
client_id: farmacia-vitalis
legal_name: "Farmacia Vitalis"
brain_spec_version: 1.1.0
authority: alex-bellesia
account_owner: alex-bellesia
active_service_paths: [branding, content, paid-media, landing-pages, software]
client_window_enabled: false
client_window_policy: accepted-client-scope-only
software_owner: spatial-port
deliverable_owner: client
source_file_owner: client
client_data_owner: client
videogo_enabled: false
drive_root_ref: gdrive://shared-drive-farmacia-vitalis-TBD
dashboard_client_ref: dashboard://farmacia-vitalis
credential_collection_ref: password-manager://spatial-port/farmacia-vitalis
machine_secret_prefix: aws-secretsmanager://spatial-port/prod/farmacia-vitalis/
retention_policy: contract-plus-legal-hold
created_at: 2026-08-11
updated_at: 2026-08-19
---
# Client Manifest

Complete every field. Unknown is allowed only as an explicit value such as `tbd`, never as a missing field.

## Change log — 2026-08-19 (workspace audit, ev-fv-001)

- `legal_name`: confirmed working name "Farmacia Vitalis". Exact legal form still tbd — the landing footer expects "Farmacia Vitalis SA `[ragione sociale da cliente]` · CHE-XXX" and the IDI/P.IVA has not been provided yet (fase-3-landing-page/03, 04).
- `active_service_paths`: set from the actual engagement evidenced in the NXTO project folder — **branding** (brandbook-v6, logo, print assets), **content** (fase-2 doc 08 + fase-5 social plan, 8 posts + 8 reels/month), **paid-media** (fase-2 doc 07 + fase-4 ADV kit, CHF 600/month ceiling), **landing-pages** (fase-3, live at www.farmaciavitalis.ch), **software** (Vitalis Mail backend, Vitalis Social backend, deploy scripts on AWS 786913936501 / eu-central-1). `crm` and `local-seo` exist as service-path folders but the work is currently embedded inside content/paid-media (Vitalis Mail, Google Business Profile) — not activated as standalone paths.
- `brain_spec_version`: 1.0.0 → 1.1.0.
- `updated_at`: 2026-08-11 → 2026-08-19.
- All other fields unchanged.
