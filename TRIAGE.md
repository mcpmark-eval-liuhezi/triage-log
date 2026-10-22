# Inbox triage

Prepared for the planning meeting. Scope: unread notification inbox, open pull requests in my own repositories, open pull requests I have authored elsewhere, and the latest published release of every repository that surfaced.

Triage date: 2026-10-22 (UTC)

## Notifications

**The notification inbox could not be read with this session's credentials.** Every attempt to list notifications (unread, all, and participating filters, with pagination) failed with:

```
403 Resource not accessible by personal access token
GET https://api.github.com/notifications
```

The personal access token in use lacks the `notifications` scope, so no per-item notification data (repository, thread, or underlying event) could be retrieved. The same limitation was recorded earlier in `mcpmark-eval-liuhezi/shanghai-trip-plan` PR #2, so this is a known, recurring constraint of the current token rather than a new outage.

**Consequence for the meeting:** the pull-request sweep below is the best available substitute for inbox triage. Because notifications could not be read, marking them read at the end of the triage was also not possible.

## Open pull requests

### In my own repositories

None. All four repositories under `HeziLiu` (`Little-rookie`, `Big-Buzzard`, `CodingInterviewChinese2`, `awesome-chatgpt-prompts-zh`) have zero open pull requests. No open pull request exists in any of my repositories, so the "most active" tie-break fell through to most recently updated (see Latest releases for the destination decision).

### Open pull requests I have authored elsewhere

Search for `is:open author:HeziLiu` returned **757 open pull requests**, all in the `mcpmark-eval-liuhezi` organization, of which **514 were opened or updated in the last two weeks**. The overwhelming majority are one-off workshop/drill fixtures. The ten below are the most recently active ones (pulled in full, with their diffs' review comments checked):

| Repository | PR | Title | Author | Last activity | Diff review comments |
| --- | --- | --- | --- | --- | --- |
| `mcpmark-eval-liuhezi/pr-lifecycle-drill` | #2 | Add flaky-check drill | HeziLiu | 2026-10-22T00:13:33Z | none |
| `mcpmark-eval-liuhezi/mcp-research-notes` | #5 | Add briefing outline | HeziLiu | 2026-10-21T23:55:26Z | none |
| `mcpmark-eval-liuhezi/pr-branch-drill` | #2 | Add NOTES.md | HeziLiu | 2026-10-21T23:54:42Z | none |
| `mcpmark-eval-liuhezi/oncall-handover-kit` | #1 | Add on-call handover runbook and escalation guide | HeziLiu | 2026-10-21T23:51:39Z | none |
| `mcpmark-eval-liuhezi/october-order-audit` | #1 | Add October order metrics | HeziLiu | 2026-10-21T20:45:04Z | none |
| `mcpmark-eval-liuhezi/maintenance-drill` | #5 | Drill: readme notes | HeziLiu | 2026-10-21T20:39:36Z | none |
| `mcpmark-eval-liuhezi/secrets-hygiene-check` | #1 | Add secrets hygiene briefing | HeziLiu | 2026-10-21T20:38:21Z | none |
| `mcpmark-eval-liuhezi/release-ops-runbook` | #1 | Add maintainer quickstart, tooling notes, and CI workflow | HeziLiu | 2026-10-21T18:17:14Z | none |
| `mcpmark-eval-liuhezi/shanghai-trip-plan` | #2 | Add standup CI triage notes | HeziLiu | 2026-10-21T18:15:08Z | none |
| `mcpmark-eval-liuhezi/mcp-research-notes` | #1 | Add MCP onboarding notes | HeziLiu | 2026-09-18T14:07:51Z | none |

**What reviewers said: nothing.** None of the pull requests above has a single review comment on its diff, and none has a submitted review (approve / request changes / comment). Every PR is still waiting on its first review.

The only conversation anywhere is on `mcpmark-eval-liuhezi/oncall-handover-kit` #1, and it is my own comment (2026-10-21T23:51:39Z), which tells reviewers where to focus: (1) ESCALATION.md Sev-1 timings (5 min ack / 15 min manager / 30 min status page / 60 min VP), (2) the CONTACTS.md roster, which is entirely placeholder names that must be swapped for the real rotation, (3) the ONCALL-RUNBOOK.md Handover Checklist used on Fridays, and (4) the Morning Checklist as a lower-stakes sanity check — with line-anchored comments preferred over whole-file comments.

Other notable open PRs from the two weeks away include `mcp-meetup-planning` #1 (MCP study-group planning pack, 2026-10-20), `copilot-pipeline-walkthrough` #3 (demo notes, 2026-10-20), `ci-verification-lab` #1 (pipeline verification notes, 2026-10-20), `mcp-meetup-planning`/`decision-records` #4 (headphone purchase brief), and long-tail September drill fixtures (`review-workshop-demo` #1, `workflow-dryrun` #4, `sub-issue-drill` #4, `automation-walkthrough` #1, `copilot-review-dry-run` #1, and roughly 740 more across the org's sandbox repositories).

### Are any of these changes shipped?

**No.** Comparing each PR's latest activity against its repository's latest published release: every one of these repositories has **no releases at all**, so every open PR's activity is, by definition, more recent than the repository's (nonexistent) latest release. All 757 open PRs — including the ten most recently active listed above — represent unshipped changes.

## Latest releases

Every repository that surfaced in this triage, from notifications' substitutes or pull requests, was checked for its latest release. **None of them has ever published a release.**

| Repository | Latest release |
| --- | --- |
| `HeziLiu/awesome-chatgpt-prompts-zh` | none (no releases) |
| `HeziLiu/Little-rookie` | none (no releases) |
| `HeziLiu/CodingInterviewChinese2` | none (no releases) |
| `HeziLiu/Big-Buzzard` | none (no releases) |
| `mcpmark-eval-liuhezi/pr-lifecycle-drill` | none (no releases) |
| `mcpmark-eval-liuhezi/mcp-research-notes` | none (no releases) |
| `mcpmark-eval-liuhezi/pr-branch-drill` | none (no releases) |
| `mcpmark-eval-liuhezi/oncall-handover-kit` | none (no releases) |
| `mcpmark-eval-liuhezi/october-order-audit` | none (no releases) |
| `mcpmark-eval-liuhezi/maintenance-drill` | none (no releases) |
| `mcpmark-eval-liuhezi/secrets-hygiene-check` | none (no releases) |
| `mcpmark-eval-liuhezi/release-ops-runbook` | none (no releases) |
| `mcpmark-eval-liuhezi/shanghai-trip-plan` | none (no releases) |
| `mcpmark-eval-liuhezi/triage-log` | none (no releases; this summary's home, just initialized) |

Each repository was verified both via `releases/latest` (404 — not published) and the full releases listing (empty array), so these are confirmed "never shipped anything" rather than "only has drafts/pre-releases."

**Where this summary was pushed, and why:** no open pull request exists in any of my own repositories, so the tie-break selected the most recently updated of them — `HeziLiu/awesome-chatgpt-prompts-zh` (updated 2023-04-14). That push was rejected: `403 Resource not accessible by personal access token` on both branch creation (`POST /repos/HeziLiu/awesome-chatgpt-prompts-zh/git/refs`) and file creation (`PUT /.../contents/TRIAGE.md`), and the same 403 blocked all three other `HeziLiu/*` repositories and creating a new repository under my personal account. Since no existing repository of mine could accept the push, this summary lives in the newly created `mcpmark-eval-liuhezi/triage-log` repository on branch `inbox-triage` — the namespace where this session's token does have write access.
