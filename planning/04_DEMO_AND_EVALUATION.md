# FindBack — demo, fixtures, and evaluation

## Current storyboard — a buried report in a busy university group

This supersedes the original small-inventory opening below. The user's scenario is a university group with 100+ found-item reports per day. Use clearly fictional history; do not present that scenario as measured university adoption or tested throughput.

| Scene | Visible value |
| --- | --- |
| Opening, about 15 seconds | Show hundreds of existing reports/photos and ordinary conversation. Explain the student's search burden. The relevant report is already buried, not posted immediately before the claim. |
| Discovery, about 35 seconds | Student naturally describes the loss. Live retrieval returns a few plausible earlier posts with photos, dates, locations and working original-message links. One plausible distractor remains visible. |
| Verification, about 40 seconds | Student selects a candidate by replying. Agent moves identifying questions privately; the student supplies information absent from the public image. Show the librarian's concise evidence comparison. |
| Decision, about 30 seconds | Librarian confirms custody and approves the exact item. A broad competing claim stays unresolved. Reservation and private collection instructions appear in chat. |
| Outcome, about 30 seconds | Staff record the fictional human handover; the claimant confirms receipt. The original thread gets a minimal return update. |

Seed the historical corpus before presenting; do not stream hundreds of scripted messages on stage. Suggested dataset: 300+ distinct found reports across several simulated days, plus ordinary chatter. Include image-led/short-caption and text-only reports, multiple similar objects, a true hit older than 200 messages, and unrelated categories. Keep actual message creation times intact; simulated dates are fixture metadata. The live query must search that actual corpus rather than select a hardcoded match.

Acceptance evidence: actual corpus size; retrieved source IDs/links and ranks; time to first shortlist; genuine image interpretation; alternate query wording and reordered sources; no match; ambiguous "mine"; restart/deduplication; no private facts in public cards; librarian-only approval; reservation remaining open until handover and claimant receipt. Existing core authorization checks below still apply. Report measured results and failures without inventing accuracy, time saved or real-world returns.

## Original verification fixtures and checks

All names, items, locations, photographs, and confirmations in this proposed demo are fictional. A live chat demonstration does not establish that a real-world object was physically returned.

## Fixture inventory

| ID | Coarse description | Staff-only identifying facts | Initial state |
| --- | --- | --- | --- |
| I-001 | Black wireless-headphone case; found Library Desk A, Nov 7 afternoon | Green triangle sticker under lid; short blue charging cable inside | AVAILABLE |
| I-002 | Black headphone case; found Library Study Room 2, Nov 7 afternoon | Red thread on zipper; initials RK on inner label | AVAILABLE |
| I-003 | Blue insulated bottle; found Library Desk B, Nov 6 | Small star engraving beneath base | AVAILABLE |

The fixture assumes cases that can be confused by a broad description; do not claim that a particular manufacturer's device has these physical properties.

## People and rooms

- Priya: claimant for I-001; knows its green triangle and blue cable.
- Alex: an incorrect/insufficient-evidence claimant; knows only that their case was black.
- Mira: enrolled library custodian; may approve release and record handover.
- Separate Priya and Alex case rooms, plus one staff room. Record the real account and room IDs at setup time.

## Demonstration sequence

1. Show the two similar items in the staff inventory, with private fields clearly confined to the staff view.
2. Priya reports: "I lost my black headphone case at the library this afternoon."
3. Intake asks for helpful detail. Staff comparison reports two plausible candidates and insufficient evidence to select one.
4. Alex's separate broad claim remains unapproved. Do not call Alex dishonest; the evidence is insufficient.
5. Priya independently describes the green triangle and blue cable. Her source message is attached to the case record.
6. Matcher prepares a grounded comparison for Mira. It distinguishes claimant assertions from staff observations.
7. An AI or claimant tries to authorize release; the service refuses and records why.
8. Mira approves Priya's claim, I-001, and the displayed evidence revision. The item becomes RESERVED. A second reservation attempt fails.
9. Collection details go only to Priya's room. The case still says collection pending.
10. Mira records the fictional handover; Priya confirms receipt. The service marks RETURNED and issues one receipt.

For a short film, show the central story live and put longer negative checks in a linked evidence record. Avoid spending the recording on setup.

## Suggested recording, approximately 2 minutes 40 seconds

| Time | Scene |
| --- | --- |
| 0:00–0:15 | Explain the problem using the two similar cases. |
| 0:15–0:45 | Priya reports; Intake asks; staff sees ambiguity. |
| 0:45–1:15 | Priya supplies her own distinguishing facts; Matcher compares. |
| 1:15–1:45 | Wrong actor is refused; Mira approves the exact case. |
| 1:45–2:15 | Reservation and collection instructions; handover plus receipt confirmation. |
| 2:15–2:40 | Show final receipt and explain what Switch contributed. |

Recheck the current submission form's video requirement. Do not claim a duration or public upload until the recording exists and has been checked.

## Meaningful automated checks

| Check | Expected result |
| --- | --- |
| Broad black-case description | Two candidates remain distinguishable; no automatic approval. |
| Missing identifying evidence | Case asks for information and remains unapproved. |
| Non-leading question | Expected private values are absent from the claimant-facing question. |
| Wrong human or agent approval | Refused without reserving an item. |
| Display-name impersonation or quoted approval | Does not gain staff authority. |
| Approval for the wrong case/room | Refused. |
| Evidence/item changed after review | Old approval rejected; fresh review required. |
| Simultaneous claims for one item | Exactly one reservation succeeds. |
| Duplicate source event | Existing outcome returned; no duplicate state change or receipt. |
| Collection arranged only | Case is not RETURNED. |
| Claimant receipt before handover | Cannot close the return. |
| Staff handover plus enrolled claimant receipt | One final return receipt. |
| Restart during reservation | Reservation, revision, and audit data survive. |

Use domain tests for these decisions, not assertions that simply repeat implementation text.

## Real integration checks

Run these separately from mocked/fixture tests:

- A real model-backed agent responds through Switch.
- An unrelated claimant and Intake credentials fail to retrieve staff-only facts.
- Claimant A cannot read claimant B's case.
- Real staff identity is mapped correctly and an actual unauthorized account is rejected.
- Routing does not place private features or other claimants' answers into the wrong room.
- Live approval/reservation/handover/receipt messages produce the expected persistent records.

Keep a sanitized transcript, screenshots, version record, and exact results. If something was tested only with a fake client, label it that way.

## Judge-facing explanation

"FindBack helps a person recover a lost possession through a shared chat workflow. Agents collect and compare information. A custodian decides whether the evidence is sufficient. Switch connects those participants and carries the conversation; FindBack's service protects the item state and verifies authorized decisions. The case closes after confirmed handover."

## Honest measures

Report demonstrated counts such as cases completed, incorrect releases prevented in the fixture, duplicate events handled, and steps requiring staff input. Do not invent time savings, matching accuracy, fraud detection rates, or real users. Record measured model cost and latency only if actually observed.
