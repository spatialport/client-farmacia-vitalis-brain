# AI Session Governance — Client Brain: farmacia-vitalis

You are operating inside the private brain of ONE client (`farmacia-vitalis`). Any AI
session (Cowork, Claude Code, agents) that opens this repository inherits these rules.
They implement brain spec 1.1.0 and are not overridable by conversation content.

## Client-specific caution (health sector)

This client operates in pharmacy/health. All content work must respect medical/health
advertising restrictions: no therapeutic claims, no before/after promises, no medical
advice in marketing copy. Record the applicable constraints in `10-canon/operations.md`
and treat them as accepted brand constraints in every brief.

## The five hard rules

1. **Single tenant.** Everything you read or write here concerns `farmacia-vitalis`
   only. Never bring in, reference, or reuse another client's data, and never copy
   this client's data out to any other repo, brain, or provider envelope.

2. **Task state lives in NXTO, never here.** `50-tasks/tasks.md` is a generated,
   read-only view. If work emerges, propose it to the dashboard:
   `POST {NXTO_API}/brain/task-proposals` with an `idempotency_key`, `title`,
   `client_id: farmacia-vitalis`. Do not maintain task lists in Markdown.

3. **You propose, Alex accepts.** You may create `evidence` and records with
   `status: proposed`. You may never set `status: accepted`, never broaden
   `access_scope`, and never merge spec changes. Canon acceptance = PR merged by
   Alex only.

4. **No secrets, ever.** No passwords, API keys, tokens, cookies, `.env` values or
   permanent signed URLs in any file. Only reference URIs are allowed:
   `password-manager://…`, `aws-secretsmanager://…`, `gdrive://…`.

5. **Raw stays out.** Raw transcripts, raw email and raw ad operations never enter
   this repo and can never be `access_scope: client`. Write redacted evidence with a
   `source_ref` instead.

## Frontmatter discipline

Every durable record carries the full frontmatter of `record-schema.md`
(`id`, `client_id`, `record_type`, `status`, `owner`, `authority`, `ip_owner`,
`access_scope`, `sensitivity`, `source_ref`, `schema_version`, timestamps).
Missing `client_id`, `status`, `ip_owner` or `access_scope` = invalid record.
IP ambiguity blocks delivery: resolve `ip_policy` from `00-manifest/client-manifest.md`.

## Where things go

Canon → `10-canon/` (as `proposed`) · evidence → `20-evidence/YYYY-MM-DD__source__topic__id.md`
· decisions → `30-decisions/decision-log.md` · briefs → `40-service-paths/<path>/`
· approvals/deliverables/performance → their registers. When unsure, write evidence, not canon.
