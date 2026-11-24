# On The Spot Curtain Cleaning Specialists — Engineering Home

**Canonical production site:** <https://www.curtaincleaning.org> — live and healthy on Vercel as at 24 Nov 2026 (Lighthouse mobile 100/100/100/100, all 5 videos serving, zero errors).

> **DEPRECATED DOMAIN — DO NOT USE:** `curtainclean.co.za` is retired. It must never appear in code, DNS, links, social profiles, or copy. The only valid domains are `curtaincleaning.org` and `www.curtaincleaning.org` (apex enforces `301 → www`).

## What this repository is

The engineering home for executing **Build Spec v4.0** — the authoritative single source of truth for the On The Spot Curtain Cleaning Specialists platform:

- Mobile-first **Astro 5** static site (25 public routes, zero runtime JS by default)
- **Vercel** hosting with Cape Town-pinned serverless functions (`cpt1`)
- **Supabase** PostgreSQL/Auth/Storage in AWS Cape Town (`af-south-1`) with strict RLS
- Auth-gated **`/ops` operations dashboard** (lead inbox, field assessment pad, job board, renewal radar)
- **Resend** transactional email (lead alerts + client auto-replies)
- **Membrane** WhatsApp Business API automation (non-discount workflows)
- Consent-gated **GA4** (POPIA)

| Document | Purpose |
|---|---|
| [`docs/BUILD-SPEC-v4.0.md`](docs/BUILD-SPEC-v4.0.md) | Full specification (11 sections: architecture, NAP, design system, routes, data contracts, DB schema, ops dashboard, integrations, 10 tasks, A–Z assembly sequence, release gate) |
| [`docs/tasks/`](docs/tasks/) | 10 issue-ready task briefs — each has scope, acceptance criteria, dependencies, and current-state notes |
| Spec §10 (A–Z) | 26 ordered execution steps |
| Spec §11 | Environment variable matrix + mandatory Go/No-Go release gate |

## The 10 build tasks

| # | Task | Depends on | Brief |
|---|---|---|---|
| 1 | Cloud Foundation, Domain Governance & DNS Authentication | — | [`task-01`](docs/tasks/task-01-cloud-foundation.md) |
| 2 | Database Schema, Strict RLS & Private Storage | 1 | [`task-02`](docs/tasks/task-02-database-rls-storage.md) |
| 3 | Astro 5 Project Scaffolding & Edge Security | — (parallel with 1–2) | [`task-03`](docs/tasks/task-03-astro-scaffolding-security.md) |
| 4 | Atelier Design System & Mobile-First Chrome | 3 | [`task-04`](docs/tasks/task-04-design-system-chrome.md) |
| 5 | Typed Data Registries & Optimized Media Pipeline | 3 | [`task-05`](docs/tasks/task-05-data-registries-media.md) |
| 6 | 25 Pre-Rendered Public Routes & Dynamic SEO/JSON-LD | 4, 5 | [`task-06`](docs/tasks/task-06-public-routes-seo.md) |
| 7 | Lead Ingestion API & POPIA GA4 Gate | 2, 6 (+ Resend from 1) | [`task-07`](docs/tasks/task-07-lead-api-ga4.md) |
| 8 | Operations Dashboard Auth & Lead Inbox | 2, 3 | [`task-08`](docs/tasks/task-08-ops-auth-inbox.md) |
| 9 | Field Assessment Pad, Job Board & Renewal Radar | 8 | [`task-09`](docs/tasks/task-09-field-pad-jobs-renewals.md) |
| 10 | Security Firewall, Cross-Device QA, Cutover & Indexing | 1–9 | [`task-10`](docs/tasks/task-10-security-qa-cutover.md) |

## Non-negotiable rules (full text in the spec, Section 0)

1. Zero public pricing, discounts, or quote wizards — all CTAs route to `/contact`
2. Mobile-first at 360–430px, 100% content parity, 48px touch targets, fixed bottom thumb bar
3. South African co-location: Vercel `cpt1` + Supabase `af-south-1` (POPIA Section 72)
4. Zero runtime JS on public pages (static SSG; SSR only for `/api/*` and `/ops/*`)
5. Atelier Drapery Care palette only — no emojis, no square buttons, no competing warm hues
6. Exact taxonomy: 6 sectors + 7 services in an orphan-free 1 + 6 grid
7. Schema.org `DryCleaningOrLaundry`, `publicAccess: false`, no self-serving ratings, SAB disclaimer everywhere
8. RLS on every table — `anon` gets zero access

## Current status (24 Nov 2026)

| Area | Status |
|---|---|
| Production site | Live, healthy, Lighthouse mobile all 100 — no action needed |
| Build Spec v4.0 | Committed to this repo (transcribed from the image-only `Neonplan.pdf`; see provenance note in the spec) |
| Supabase | Exists under `curtaincleaning359@gmail.com` — ownership confirmation pending (359 vs 369 discrepancy, see open items) |
| Resend | **Not yet registered.** Required by Task 1 and all lead email workflows. Register manually (suggested: info@curtaincleaning.org) |
| Meta Business verification | Result expected Thu 26 Nov 2026 — follow-up calendar event 09:00–10:00 SAST is in place |
| WhatsApp WABA | Display-name fix pending Meta verification ("Johanesburrg Curtain Cleaning" → "On The Spot Curtain Cleaning", WABA 1254025262537486) |

## Open items requiring owner confirmation (as at 24 Nov 2026)

1. **359 vs 369 Gmail.** Session records show `curtaincleaning359@gmail.com` hosting Supabase + GitHub + GitLab (verified), while the social-account inventory lists `curtaincleaning369@gmail.com` for the old WordPress-era Vercel/Supabase logins. Confirm which account owns the current Supabase project and Vercel team; store both sets of credentials in the Vault.
2. **Street address discrepancy.** The spec's canonical NAP says "Martha North Road, Randburg, Johannesburg, 2194", but CIPC records are reported to say "Martha Avenue". Resolve the exact legal street string before GBP / schema.org / footer alignment (affects Tasks 6 and 10, and the Thursday agenda).
3. **Vault gaps.** Google Business Profile (`ssd89660@gmail.com`) and TikTok (`@onthespotcurtaincleaning`) credentials + 2FA destination are not yet recorded.
4. **Resend registration** (manual — no automation available).
5. **WABA display name + personnel assignment** (after Meta verification passes).

## Repository layout

```
/
├── README.md                     <- you are here
├── .gitignore
└── docs/
    ├── BUILD-SPEC-v4.0.md        <- authoritative specification
    └── tasks/
        ├── task-01-cloud-foundation.md
        ├── task-02-database-rls-storage.md
        ├── task-03-astro-scaffolding-security.md
        ├── task-04-design-system-chrome.md
        ├── task-05-data-registries-media.md
        ├── task-06-public-routes-seo.md
        ├── task-07-lead-api-ga4.md
        ├── task-08-ops-auth-inbox.md
        ├── task-09-field-pad-jobs-renewals.md
        └── task-10-security-qa-cutover.md
```

(The Astro 5 application source — `src/`, `public/`, `supabase/` — is scaffolded per Task 3 / Assembly step E when development begins. This repository currently carries the specification and execution plan.)

## Canonical home & mirroring

The designated canonical engineering home is GitLab: **`on-the-spot-group/on-the-spot-project`** (<https://gitlab.com/on-the-spot-group/on-the-spot-project>).

This GitHub repository seeds the content because the automation used on 24 Nov 2026 had read-only GitLab access. To sync everything into the canonical home:

```bash
git clone https://github.com/curtaincleaning359-dotcom/glowing-adventure.git
cd glowing-adventure
git remote add gitlab https://gitlab.com/on-the-spot-group/on-the-spot-project.git
git push gitlab main
```

Suggested housekeeping: rename this GitHub repo to `on-the-spot-project` (Settings → General → rename) for symmetry, then paste the 10 task briefs from `docs/tasks/` as GitLab issues (labels: `build-spec-v4`, `task-01` … `task-10`).

## Environment variables

Never commit secrets. The complete Preview/Production matrix is Section 11 of the spec. Required variables: `PUBLIC_SUPABASE_URL`, `PUBLIC_SUPABASE_ANON_KEY`, `SUPABASE_SERVICE_ROLE_KEY` (never `PUBLIC_`-prefixed), `RESEND_API_KEY`, `FROM_EMAIL`, `TO_EMAIL`, `CARE_GUIDE_PDF_URL`, `PUBLIC_GA_ID` (production only, POPIA-gated), and optional `MEMBRANE_API_TOKEN` / `MEMBRANE_CONNECTION_ID`.

## Key contacts & accounts (no credentials in this repo)

- Managing Director: Kathy Dunlop — info@curtaincleaning.org · +27 75 011 9200 (WhatsApp) · Studio line +27 71 622 6723
- Engineering accounts: GitHub `curtaincleaning359-dotcom` · GitLab `on-the-spot-group` · Vercel + Supabase under `curtaincleaning359@gmail.com` (pending 359/369 confirmation)
- Registrar: GoDaddy (`curtaincleaning.org`)
