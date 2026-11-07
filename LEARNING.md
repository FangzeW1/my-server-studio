# Lesson 01 · Conversation evidence

AI-drafted task summary, not a transcript or grade. It may be public. Use actual
short quotes or labeled paraphrases, name any help supplied, and link actual
work. Leave missing contributions Pending. A learner can review, correct or
remove excerpts before publication; accuracy approval is not proof of learning.
Label role-play honestly rather than treating it as an actual learner response.

**Lesson:** STUDIO-001. **Available conversation context:** This STUDIO-001 chat.

## Prediction

Learner quote: “I predict that DNS will direct the request to my server's IP address, where Traefik will recognize the hostname and route the request to the calculator's Docker container. Traefik will also handle HTTPS.”

Help: AI requested the prediction before explaining the deployment plan.

## Check interpretation

Learner explanation: “The API test confirmed that 6 × 7 returned 42 over HTTPS, demonstrating that this specific calculation and request path work. My personal browser test confirmed the calculator interface also produced 42. However, these tests alone do not prove every possible calculation or invalid input is handled correctly.”

Help: AI supplied the actual API input, expected result and observed result, then asked what the check establishes and leaves untested.

## Browser observation

Learner quote: “The calculator now loads successfully in my browser after switching Edge to Google DNS. I personally tested 6 × 7 and observed the correct result of 42.”

Help: AI compared laptop/router DNS with public and authoritative DNS. The learner changed Edge DNS and personally retried the browser.

## Keep decision

Learner quote: “I approve keeping this deployment.”

Learner rationale: “I chose to keep the deployment because the calculator works correctly over HTTPS, and my existing production and QA services remain operational.”

## Review

The learner approved the proposed record for publication, then supplied the check interpretation and keep rationale above verbatim and authorized committing, PR creation and merging after all required checks pass. Accuracy approval records consent and record accuracy, not a grade or proof of understanding.

## AI work and next step

AI completed setup, read-only inspection, DNS checks and the approved pinned-image launch. Initial launch started the container but failed trusted HTTPS; AI added TLS and the existing letsencrypt resolver to the calculator route only. Subsequent verify passed release/API/HTTPS and preservation checks. Fast checks passed (91 tests); full E2E awaits PR CI because local Docker is unavailable. The learner created [issue #1](https://github.com/fangzew1/my-server-studio/issues/1). Browser automation failed to start. See [SPEC](SPEC.md) and [sanitized verification](studio/evidence.json). No successful initial-launch report exists; the later already-managed report is repeat verification, not evidence of launch time.
