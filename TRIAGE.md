# Inbox triage

Prepared for the afternoon planning meeting on 2026-10-22. Scope: the unread notification inbox, open pull requests in my own repositories, open pull requests I have authored elsewhere, and the latest published release of every repository that surfaced anywhere in this triage. This snapshot supersedes the earlier one previously stored on this branch.

**Where this summary lives:** no repository under `HeziLiu` could accept the push — all four rejected branch creation and file commits with `403 Resource not accessible by personal access token`, and creating a new repository under my personal account was blocked with the same 403. A repository named `triage-log` (the name the fallback plan calls for, initialized with a README) already exists under `mcpmark-eval-liuhezi` — the organization that hosts all of my open pull requests and where this session's token does have write access. The summary therefore lives on branch `inbox-triage` of `mcpmark-eval-liuhezi/triage-log`.

## Notifications

**The notification inbox could not be read with this session's credentials.** Every attempt to list notifications — the default (unread) view and the participating-only filter — failed with:

```
403 Resource not accessible by personal access token
GET https://api.github.com/notifications
```

The personal access token in use does not grant the `notifications` scope, so no unread notification could be opened: repository, thread, and underlying-event details are all unavailable. Nothing in this document is drawn from the inbox; the pull-request sweep below is the best available substitute for inbox triage. The same limitation is already recorded in `mcpmark-eval-liuhezi/release-hygiene-audit` PR #1, so this is a known, recurring constraint of the current token rather than a new outage.

## Open pull requests

### In my own repositories

None. All four repositories under `HeziLiu` — `Little-rookie`, `Big-Buzzard`, `CodingInterviewChinese2`, `awesome-chatgpt-prompts-zh` — have zero open pull requests (each was checked directly, not just via search). Because no open pull request exists in any of my repositories, the "most active = hosts the most open PRs" rule found no winner and the tie-break fell through to most-recently-updated; see the end of Latest releases for how the destination was ultimately chosen.

### Open pull requests I have authored elsewhere

Search for `is:open is:pr author:HeziLiu` currently returns roughly **768 open pull requests** (the total drifts by a few as the search index refreshes). Every one of them lives in the `mcpmark-eval-liuhezi` organization — a search excluding both my account and that org returns zero — and the overwhelming majority are one-off workshop/drill fixtures. The 21 pull requests below are everything with activity since 2026-10-19, the freshest slice of the two weeks away; each was pulled in full and its diff review comments read:

| Repository | PR | Title | Last activity (UTC) | Diff review comments |
| --- | --- | --- | --- | --- |
| `mcp-team-briefing` | #1 | Add MCP team briefing | 2026-10-22T00:30:17Z | 2 (self) |
| `acadia-coastal-trip-plan` | #1 | Add Acadia coastal kayak & camp weekend trip plan (24–25 Oct 2026) | 2026-10-22T00:29:49Z | none |
| `code-review-drill-demo` | #1 | Add review checklist | 2026-10-22T00:29:12Z | 1 (self) |
| `ci-readiness-check` | #4 | Add smoke-test run report | 2026-10-22T00:29:07Z | 1 (self) |
| `release-readiness-dryrun` | #3 | Add release readiness checklist | 2026-10-22T00:22:12Z | 2 (self) |
| `team-brunch-menu` | #2 | Add Friday team brunch menu (2 breakfast, 1 drink, 1 dessert) | 2026-10-22T00:21:07Z | none |
| `ingest-rewire` | #6 | Add migration status dashboard | 2026-10-21T20:06:43Z | none |
| `mcp-adoption-audit` | #4 | Add upstream audit notes | 2026-10-21T19:00:51Z | none |
| `release-hygiene-audit` | #1 | Add release hygiene audit findings | 2026-10-21T19:00:08Z | none (1 issue comment) |
| `api-migration-prep` | #5 | Add migration notes | 2026-10-21T18:56:15Z | none |
| `agent-ci-dryrun` | #1 | Add dry-run checklist to README | 2026-10-21T06:44:30Z | 1 (self) |
| `dep-audit-2026` | #6 | Dependency constraint audit | 2026-10-21T06:38:24Z | none |
| `release-readiness-drill-4` | #1 | Add on-call drill documentation | 2026-10-21T06:37:09Z | none |
| `copilot-pipeline-walkthrough-2` | #3 | Wire up demo notes | 2026-10-20T07:16:18Z | 1 (self) |
| `aurora-notes` | #5 | Aurora Notes: add setup guide and smoke test | 2026-10-20T07:10:08Z | none |
| `platform-api-followups` | #5 | Add FOLLOWUPS.md with Sprint 47 High-priority follow-ups and sync times | 2026-10-20T07:06:16Z | none |
| `release-gate-dryrun` | #1 | Dry-run: add release gate checklist to README | 2026-10-19T23:32:15Z | 1 (self) |
| `slack-review-intake` | #1 | Digest Slack review feedback into PR review comments | 2026-10-19T20:17:19Z | 2 (self) |
| `workflow-demo-2026` | #5 | Demo: docs cleanup | 2026-10-19T19:45:19Z | none |
| `fieldtest-go-nogo` | #1 | Go/no-go field test report | 2026-10-19T19:43:19Z | 1 (self) |
| `platform-health-audit` | #1 | Add minimal hello-world CI workflow | 2026-10-19T08:08:18Z | none |

Meeting-relevant substance behind a few of these: `ingest-rewire` #6 is the migration handoff dashboard for the status page Devi owns while I am on leave; `dep-audit-2026` #6 found **3 of 7 platform-team dependency claims stale** (urllib3 1.26.18 misses the `>=2.0.0` floor; numpy 2.0.0 and sqlalchemy 2.0.30 both bust the `<2.0.0` ceiling) and that jumping straight to latest is itself unsafe under the claimed constraints; `api-migration-prep` #5 backs the three v1-API-sunset workstreams (remove `/auth` endpoints, upgrade the Python SDK to 2.1.0, publish the migration guide); `mcp-adoption-audit` #4 is the provenance research for adopting `github/github-mcp-server` (upstream's two most recent tags are v2.0.3 and v2.0.2); `platform-health-audit` #1 is the handover example for the colleague covering my projects and records the current critical pip advisory (CVE-2026-105192 / GHSA-w5f2-9q9c-ff4h, LMCache, CVSS 9.8); `acadia-coastal-trip-plan` #1 concludes the coastal paddle is **NO-GO** (Schoodic checkpoint 1.2–1.4 m exceeds the 1.0 m threshold) and that the Island Explorer shuttle no longer runs on our dates.

**What reviewers said: in substance, nothing yet — every review comment on these PRs is my own.** No teammate has reviewed any pull request in the set; there are no approve / request-changes decisions and no third-party comments. The nine diff comments that do exist are all authored by me (self-review and verification notes left by earlier automation passes). Two of them are genuine action items worth acting on before the meeting:

- `mcp-team-briefing` #1 — two comments asking to tighten the briefing: (1) pin the docs revision being quoted (2026-07-28) and link the clients overview inline, because "supports MCP" needs the per-client feature matrix to answer "will our integration work in the hosts we care about?"; (2) fix the venue-rating bullet, which mixes "no rating returned for this branch" with 4.1–4.7/5 scores belonging to *other* Seesaw branches — either fetch the WF Central branch's own rating or cut the cross-branch comparison.
- `release-gate-dryrun` #1 — "The sign-off rule isn't enforceable until the checklist has an owner."

The remaining self-notes are verification records: `ci-readiness-check` #4 (the smoke-test run's **success** conclusion was confirmed directly from the Actions API, run #39699510566), `release-readiness-dryrun` #3 (diff check confirmed `docs/readiness-checklist.md` is the only changed file, and all five core areas — build, automated tests, documentation, changelog, rollback — are covered as checkboxes), `code-review-drill-demo` #1 (suggested wording: "secrets or credentials committed anywhere in the diff (not just code files)"), `agent-ci-dryrun` #1 (keep the checklist item phrased as a verification step so the dry-run report can cite it), `copilot-pipeline-walkthrough-2` #3 (the CI Pipeline job at `.github/workflows/ci.yml` runs on every push and manual dispatch — point at the run during the live demo), `fieldtest-go-nogo` #1 (automated check PASS; all four hours in the 08:00–12:00 window at 0% precipitation, verdict GO, side checks verified), and `slack-review-intake` #1 (two [source-summary] notes: the Slack sweep ran 14–15 search terms across all 7 visible channels and located **zero** review feedback points, so no [slack-feedback] comments were attached).

Also worth knowing: `oncall-runbook` #6 ("Add contact roster to runbook") appeared in the open-PR search results but had in fact already been **merged** at 2026-10-22T00:37:51Z — the search index lagged, so it is excluded from the table. Older September fixtures (`copilot-review-sandbox` #1, `q3-dependency-audit` #4, `code-review-workshop-demo` #1, `pr-review-walkthrough-sandbox` #1, `pr-flow-check` #1, `release-loop-drill` #1, `code-review-drill` #4, and roughly 740 more) remain open but saw no activity during the two weeks away.

### Are any of these changes shipped?

**No — everything is unshipped.** Each pull request's latest activity was compared against its repository's latest published release. Every single repository involved has **no releases at all**, so every open PR's activity is by definition more recent than its repository's (nonexistent) latest release. All ~768 open pull requests — the 21 detailed above included — represent changes that have never shipped.

## Latest releases

Every repository that surfaced in this triage — from the pull-request sweep, since notifications were unavailable (see above) — was checked for its latest release. **None of them has ever published a release**; each returned 404 on `releases/latest`.

| Repository | Latest release |
| --- | --- |
| `HeziLiu/Little-rookie` | none (no releases) |
| `HeziLiu/Big-Buzzard` | none (no releases) |
| `HeziLiu/CodingInterviewChinese2` | none (no releases) |
| `HeziLiu/awesome-chatgpt-prompts-zh` | none (no releases) — most recently updated of my repositories (2023-04-14) |
| `mcpmark-eval-liuhezi/mcp-team-briefing` | none (no releases) |
| `mcpmark-eval-liuhezi/acadia-coastal-trip-plan` | none (no releases) |
| `mcpmark-eval-liuhezi/code-review-drill-demo` | none (no releases) |
| `mcpmark-eval-liuhezi/ci-readiness-check` | none (no releases) |
| `mcpmark-eval-liuhezi/release-readiness-dryrun` | none (no releases) |
| `mcpmark-eval-liuhezi/team-brunch-menu` | none (no releases) |
| `mcpmark-eval-liuhezi/ingest-rewire` | none (no releases) |
| `mcpmark-eval-liuhezi/mcp-adoption-audit` | none (no releases) |
| `mcpmark-eval-liuhezi/release-hygiene-audit` | none (no releases) |
| `mcpmark-eval-liuhezi/api-migration-prep` | none (no releases) |
| `mcpmark-eval-liuhezi/agent-ci-dryrun` | none (no releases) |
| `mcpmark-eval-liuhezi/dep-audit-2026` | none (no releases) |
| `mcpmark-eval-liuhezi/release-readiness-drill-4` | none (no releases) |
| `mcpmark-eval-liuhezi/copilot-pipeline-walkthrough-2` | none (no releases) |
| `mcpmark-eval-liuhezi/aurora-notes` | none (no releases) |
| `mcpmark-eval-liuhezi/platform-api-followups` | none (no releases) |
| `mcpmark-eval-liuhezi/release-gate-dryrun` | none (no releases) |
| `mcpmark-eval-liuhezi/slack-review-intake` | none (no releases) |
| `mcpmark-eval-liuhezi/workflow-demo-2026` | none (no releases) |
| `mcpmark-eval-liuhezi/fieldtest-go-nogo` | none (no releases) |
| `mcpmark-eval-liuhezi/platform-health-audit` | none (no releases) |
| `mcpmark-eval-liuhezi/oncall-runbook` | none (no releases) |
| `mcpmark-eval-liuhezi/triage-log` | none (no releases; this summary's home) |

**Destination decision recap:** with zero open pull requests across all of my own repositories, the tie-break nominated `HeziLiu/awesome-chatgpt-prompts-zh`, my most recently updated repository (2023-04-14). That push — and equivalent attempts against `Little-rookie`, `Big-Buzzard`, and `CodingInterviewChinese2` — was rejected with `403 Resource not accessible by personal access token` on both branch creation and file commits. Creating a new repository under my personal account was rejected identically, so the fallback could not be honored verbatim under my own account; the summary instead lives in the existing `mcpmark-eval-liuhezi/triage-log` repository (initialized with a README) on branch `inbox-triage`, in the organization where this session's token does have write access.
