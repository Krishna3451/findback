# FindBack campus showcase

This is an actual Mattermost conversation driven by authenticated accounts.
The twelve people are fictional, and their messages are scripted. Switch
transport, the Intake and Matcher model calls, staff authorization, and the
durable case transitions run live. No physical property changes hands.

## People and rooms

| Key | Person | Role in the story |
| --- | --- | --- |
| priya | Priya Shah | Worried headphone-case claimant, C001 |
| alex | Alex Chen | Second, less certain headphone-case claimant, C002 |
| mira | Mira | Authorized library custodian |
| jordan | Jordan Ellis | Finds the first black case at Desk A |
| ava | Ava Wilson | Finds another black case in Study Room 2 |
| elena | Elena Ruiz | Volunteer; directs people to the staffed desk |
| omar | Omar Malik | Finds a book |
| maya | Maya Patel | Bottle owner, C003; separate recovery |
| noah | Noah Brooks | Cyclist looking after the unattended desk queue |
| aisha | Aisha Khan | Reassures Priya and waits for the actual result |
| leo | Leo Martins | Book owner, C004; separate recovery |
| sam | Sam, Library Team | Library assistant; closes the community thread |

The community room is the public story. Each claimant's identifying details
and receipt stay in their own enrolled private room. Staff observations and
the model's comparison stay in the enrolled staff room. A staff approval is a
reply to the actual immutable review card, which identifies the review being
approved without making a person copy database IDs.

## Narrative beats

1. Sam labels the demonstration honestly. Jordan and Ava independently report
   two similar found cases, using only coarse descriptions. Mira asks them to
   bring the objects to the desk and records each actual staff inventory entry
   privately. Distinguishing facts never appear in the community conversation.
2. Priya is anxious about losing her case before a study session. Alex reports
   a similar loss. The concierge routes each enrolled claimant to their own
   private intake; the runner follows the real bot response and case state.
3. Each claimant confirms the Intake model's actual report draft. A real
   Matcher comparison leaves both broad black-case reports ambiguous. Alex
   cannot receive an item solely because the category and color fit.
4. Priya independently supplies the under-lid sticker and cable details in
   her private room, after a non-leading information request. The refreshed
   real Matcher review reaches staff. Mira examines its facts and approves
   the matching case by replying in that exact review thread.
5. Mira arranges private collection. A staff handover record precedes Priya's
   receipt. The runner waits for the database's actual RETURNED state and
   actual receipt, then Priya posts a safe community thank-you. Alex remains
   unresolved until they provide stronger evidence.
6. Small book/bottle/witness messages make the room feel occupied. They never
   supply the answer to Priya's identification challenge. Maya and Leo have
   their own enrolled private cases, independently described details, actual
   model comparisons, separate staff approvals, handovers, and receipts. Three
   completed recoveries coexist with Alex's unresolved claim.

## Playback constraints

- Posts use the speaker's own Mattermost token, with a real typing indicator
  immediately before each message. All twelve accounts speak.
- Replies use actual Mattermost root IDs. Staff decisions are anchored to the
  actual emitted review card; community replies remain in inspectable threads.
- The runner waits for durable inbox completion, real model output delivery,
  and domain state. A timeout is a failure, not permission to advance the plot.
- A per-run journal records actual post IDs and timings. Restart reconciliation
  must match the expected account and a stable post property before reusing a
  post. It never resets the database or edits past messages.
- Aim for approximately three minutes after model warm-up; allow up to five
  minutes if real inference is slower. Editing or compressing the eventual
  screen recording must preserve the disclosure and the actual sequence.
- Final viewing should open the community channel in Mattermost, with its
  claimant and staff room links available to the authorized observer. No
  reconstructed frontend or generated transcript is presented as the UI.

## Reproduce

The single command creates a fresh fictional campus, starts the actual agents,
runs the conversation, and leaves those agents listening until Ctrl+C:

```sh
.venv/bin/python -m findback.showcase --viewer-username krishna --pace 0.7
```

It prints the actual Mattermost room URL and uses a new
`.findback/campus-<unique-id>` directory by default. `--state-dir` explicitly
reuses an existing enrollment, and `--evidence-dir` selects where to save its
credential-free run record. It never clears an earlier case history. The
separate operator commands remain available: provision the fictional showcase,
start the real runtime, then run:

```sh
.venv/bin/python -m findback.showcase_story \
  --state-dir .findback/showcase --scripted-roleplay --pace 0.7 --max-seconds 600
```

The driver requires the four-case setup. It writes its private restart journal
to the showcase state directory and a credential-free record of actual posts,
displayed agent cards, timings, and receipt IDs to `evidence/showcase-run.json`.
Running it again reconciles already-posted messages; a completed run reuses its
captured record instead of posting again into the same cases. Open the printed
Mattermost URL to inspect the actual conversation.

Private report confirmations reply to the actual draft card. Staff actions
reply to the actual immutable comparison card. Claimant receipt confirmations
reply to the actual handover card for that exact reservation. Natural phrases
therefore retain their authorization and revision context.

Read-only access verification is reproducible without taking over any agent
connection or posting a message:

```sh
.venv/bin/python -m findback.verify_showcase_access \
  --state-dir .findback/live-campus \
  --output evidence/live-campus/access-checks.json
```

The four-case cohort has 94 checks covering scoped agents, ordinary claimants,
the twelve distinct fictional human accounts, and the disclosed nonadmin demo
observer.

## The captured live campus

The preserved `live-campus` conversation completed three returns with twelve
speakers and left Alex's claim open. It also exposed a real category mismatch:
the Intake model said “paperback” while inventory said “book.” Bounded category
aliases fixed candidate lookup. Mira then posted `Review Leo again.` through
her actual account, a fresh real Matcher call produced the comparison, and the
same conversation continued through Leo's evidence, approval, handover, and
thread-bound receipt. No case history was reset and no agent card was invented.

Its evidence distinguishes total elapsed time, which includes the debugging
pause, from the final resumed driver session. Actual Mattermost creation times
remain attached to every scripted human post. The separate
`evidence/live-campus/verification.json` records the outcome, public disclosure
check, and each receipt's exact handover-thread binding.
