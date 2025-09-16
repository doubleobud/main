---
id: 001-phase1-checklist
title: Phase 1 Comprehensive Checklist
date: 2025-09-15
---

# Phase 1: Foundational Setup — Master Checklist

## A. Orientation & Scope
- [NO] Define Phase-1 “done” criteria (foundational systems + admin baseline).
- [NO] Create Phase-1 scope note (in repo root) referencing roadmap.

## B. Repository & File System
- [x] Enforce directory architecture (0–9 top-level; 00–99 second-level).
- [x] Enforce folder naming conventions (N_Label, NN-PascalCase).
- [x] Enforce file naming (`XXX_snake_case_title.ext`).
- [ ] Add/refresh a `README.md` in every folder (scope, numbering, assignments).
- [x] Confirm hundreds/tens bands + reserved blocks (700s/800s/900s).
- [ ] Update the File Manifest to current tree state.

## C. Documentation Standards & Templates
- [x] Adopt a document template (Intro/Main/Support/Conclusion).
- [x] Create a minimal front-matter schema (title/id/tags/status/date).
- [ ] Create templates: README, ADR, Changelog, Daily Log, Project Brief, Retro.
- [x] Define style rules (concise, headings/lists, cross-link IDs).

## D. Metadata, Tags & Taxonomy
- [x] Define Tag Schema v0 (controlled vocabulary, case rules).
- [x] Define note types/statuses (draft/review/approved/archived).
- [x] Decide on machine-readable fields for AI-readiness (IDs, relations).
- [x] Publish a “Tagging Rules” note (scope and anti-drift rules).

## E. Navigation & Retrieval
- [ ] Create top-level MOCs per domain (0–9).
- [ ] Create indexes: Project Index, ADR Index, Glossary, Tag Index.
- [ ] Add “Start Here / Dashboard” page in 0-System.
- [ ] Document link hygiene (broken-link policy + periodic check).

## F. Governance & Decision Records
- [No] Draft a Project Constitution v0 (purpose, principles, amendment).
- [No] Define roles you wear (Strategist, Archivist, SysAdmin, Editor).
- [No] Stand up ADRs for major choices to date (file system, Git, site).
- [ ] Create a system Changelog (structural changes only).

## G. Cadence & Rituals
- [ ] Weekly Tactical Review (triage, link hygiene, inbox zero).
- [ ] Monthly Governance Review (roles, rules, taxonomy updates).
- [ ] Quarterly Strategic Check-in (alignment with mission).
- [ ] Calendar blocks for all cadences (recurring).

## H. Logging & Work Journals
- [ ] Daily Log template (actions, blockers, insights).
- [ ] Project Journal template (progress, decisions, risks).
- [ ] Retro template (what/so-what/now-what).
- [ ] Meeting Notes template (agenda/notes/actions/links).

## I. Security & Privacy
- [ ] Classify documents (public/internal/private/secret).
- [ ] Adopt full-disk encryption on all devices holding the vault.
- [ ] Define handling of secrets/credentials (out-of-repo store).
- [ ] Document redaction rules for publishing.
- [ ] Define default license for content/code.

## J. Backup & Recovery
- [ ] Adopt 3-2-1 backup policy (local, external, offsite).
- [ ] Schedule automated backups (frequency documented).
- [ ] Perform a restore drill and log the result.
- [ ] Record backup/restore SOP (one-page).

## K. Archiving & Preservation
- [ ] Retention rubric (what goes cold, when, and where).
- [ ] Archive Index (summary, owner, dates).
- [ ] Preferred archival formats (Markdown, PDF/A, PNG/TIFF).
- [ ] Move inactive content to 900s/Archive per policy.

## L. Digital Hygiene (Computer Baseline)
- [ ] Separate admin vs daily user accounts; 2FA on all accounts.
- [ ] OS/drivers/browsers update policy (defer major upgrades).
- [ ] Startup program audit (minimal set).
- [ ] Password manager in place; unique strong passwords.
- [ ] Antivirus + firewall enabled and monitored.
- [ ] Drive encryption for laptops + externals; secure wipe policy.
- [ ] Desktop/Downloads/Email inbox zero policy (weekly reset).
- [ ] Disaster Reinstall Plan (OS + apps + restore procedure).

## M. Office Practices (Physical / Procedural)
- [ ] Ergonomic workstation baseline (display height, chair, peripherals).
- [ ] Physical inbox tray + scan-and-file routine.
- [ ] Meeting capture → Meeting Notes template (always).
- [ ] Calendar hygiene (blocks for deep work + cadences).
- [ ] Printed docs: labeling, scan/archive rules.

## N. Website (Phase-1 Minimal Presence)
- [ ] Repo named correctly and public for Pages hosting.
- [ ] `index.html` with Markdown content section present.
- [ ] Site “Start Here” content mirrors root README.
- [ ] Add basic nav to key indexes (Projects, ADRs, Manifest).
- [ ] Add “last updated” stamp and contact/attribution.
- [ ] Cache/refresh notes documented for updates.

## O. Git & Change Discipline
- [ ] Single main branch policy + frequent commits (personal scale).
- [ ] `.gitignore` tuned for app caches/temp files.
- [ ] “Pull before work” rule across devices.
- [ ] Commit message convention (type: scope – summary).
- [ ] Release tags for major inflection points (optional).

## P. Automation & Tooling
- [ ] Daily Log quick-capture (script/shortcut; destination folder).
- [ ] Link-checker routine (broken links report).
- [ ] Backup verification script/report (success/failure).
- [ ] Optional capture automations (read-it-later to inbox).

## Q. Measurement & Review
- [ ] Define Phase-1 metrics (findability, link health, cadence adherence).
- [ ] Add “Measurement Log” note (manual entries OK).
- [ ] Quarterly health report (one page, trends + actions).

## R. Continuity & Succession
- [ ] Succession Note (how to resume work; keys/locations).
- [ ] Installers/keys archive (offline + checksum).
- [ ] “System Overview” diagram (domains, flows, dependencies).
- [ ] Risk register (top risks + mitigations).

## S. Onboarding & Help (Future-You Friendly)
- [ ] Root `README` (what this is; how to navigate).
- [ ] “How to add a new folder/file” guide (references Data Dictionary).
- [ ] “How we make decisions” guide (ADRs + cadences).
- [ ] “Publishing to website” quick guide.

## T. AI-Readiness (Phase-2 Friendly Stubs)
- [ ] Stable IDs for notes/docs (machine-readable).
- [ ] Relations field for cross-references (doc IDs list).
- [ ] Local-first principle documented (primary copy on your devices).
