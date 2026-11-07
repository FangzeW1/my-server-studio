# Lesson 01 specification

## STUDIO-001 · Launch a tested calculator on an existing server

**Status:** Deployment kept by learner; runtime verification and personal browser result recorded. Full PR CI passed; final linked revision and merge verification pending.
**Next step:** Verify full CI on the final linked revision, merge PR #2, and confirm main CI and issue closure.
**Instructor implementation:** [issue #9](https://github.com/kaw393939/373_hosting/issues/9).
Create your own issue from the [lesson template](.github/ISSUE_TEMPLATE/studio-calculator.md).

## Agreed result

Launch the supplied published calculator image through your existing Traefik
network and a nonconflicting HTTPS hostname. Preserve unrelated services and
host access. Do not add another proxy/updater or build a substitute image.
The [release selection](studio/calculator-release.json) supplies the expected
commit and multi-platform digest independently of the running website.
An explicitly agreed adoption of a matching existing deployment is recorded
as adoption, not a fresh launch. This bounded lesson does not certify the whole
server baseline or a vulnerability-free image.

- **Public hostname:** https://calc.fwang-is373.lol (DNS A record verified as the agreed server).
- **New launch or adopted deployment, and reason:** New launch approved; no matching DNS name or existing Traefik route was found during inspection.
- **Own issue / feature branch:** [Issue #1](https://github.com/fangzew1/my-server-studio/issues/1); branch `codex/studio-001`.
- **Agreed scope or actual access/configuration gap:** One pinned published calculator on existing Docker/Traefik network `is373-practical-test_default`; preserve production, QA and Traefik. Read-only doctor reports ready without sudo. Release identity and source/publication links: [release selection](studio/calculator-release.json).

### Launch and HTTPS correction

The approved launch created a new calculator container, then stopped because trusted HTTPS was not ready. No successful initial-launch report was produced. The existing Traefik resolver was named `letsencrypt`; the generated route omitted TLS/resolver selection. Only the calculator’s generated remote `compose.json` was amended with `traefik.http.routers.is373-studio-calculator.tls=true` and `traefik.http.routers.is373-studio-calculator.tls.certresolver=letsencrypt`, and only its container was recreated. The proxy and existing applications were unchanged. These runtime-only labels must be retained if regenerating this deployment; no CLI template change is included in this lesson.

Subsequent `verify` passed with provenance `already-managed` / `new_launch=false`. That describes verification of the newly created container and does not establish its original creation time. DNS initially failed through the learner’s router while authoritative/public DNS was correct; the learner reports success after changing Edge to Google DNS.

Private SSH targets and configuration stay in ignored local state. Share only
reviewed, selected evidence; never commit credentials or raw server output.

## Evidence to keep

| Evidence | Actual result / link |
|---|---|
| Prepared Black/Pylint/pytest and real-image browser checks | Local fast checks passed: Black, Pylint, 91 tests; 2 E2E deselected. Local Docker unavailable; [full PR CI passed](https://github.com/FangzeW1/my-server-studio/actions/runs/42328000591), including the Docker/Chromium E2E job. The final revision must also pass before merge. |
| Hosted image/commit, trusted HTTPS, valid and rejected API cases | Passed: [sanitized verification](studio/evidence.json). Multiply 6 × 7 → 42 (200); division by zero → 400; numeric string → 422. |
| Preservation of unrelated services | Verify found 3 unrelated containers unchanged in identity/state/published ports. Production and QA both returned trusted HTTPS 200 after the calculator-only TLS correction. |
| Own prediction, check interpretation, browser observation and keep/revise reason | [LEARNING.md](LEARNING.md): prediction, check interpretation, personal browser 42 result, and keep rationale recorded; assistance disclosed. |
| Accuracy review before publishing learner excerpts | Learner approved publication and supplied the final interpretation and keep rationale verbatim. |
| Actual PR, latest CI, merge and issue closure | [PR #2](https://github.com/FangzeW1/my-server-studio/pull/2), closing [issue #1](https://github.com/FangzeW1/my-server-studio/issues/1). [Actual full CI](https://github.com/FangzeW1/my-server-studio/actions/runs/42328000591) passed; final-revision CI and merge/closure will be verified on GitHub. |

Link the exported `studio/evidence.json`, actual CI and issue/PR when available.
CI does not deploy this server. A fixture, green check, timestamp, closed issue
or AI assertion alone does not establish the full result. `status` reports
recorded evidence and readiness for instructor review; it does not grade,
certify authorship or establish understanding.

## Optional instructor history

The records below are background, not steps to repeat. Their original anchors
remain here so earlier links continue to work.

## HOST-001 · Keep the Traefik dashboard private

[Historical requirement and evidence](book/changes/hosting-spec-history.md#host-001--keep-the-traefik-dashboard-private).

## HOST-002 · Controlled host maintenance

[Historical requirement and evidence](book/changes/hosting-spec-history.md#host-002--controlled-host-maintenance).

## HOST-003 · Companion image security maintenance

[Historical requirement and evidence](book/changes/hosting-spec-history.md#host-003--companion-image-security-maintenance).
