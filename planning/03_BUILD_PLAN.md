# FindBack — implementation plan

## Current priorities — university group discovery

The original core return workflow below has been implemented; consult `app/README.md` and evidence for verified behavior. The user's latest clarification makes historical photo/text discovery central. The old instruction to cut photos and public intake first no longer applies to this extension.

1. **Catalogue actual group reports.** Add paginated history ingestion and durable source/attachment records. Keep public found reports distinct from librarian-confirmed inventory. Done when older-than-200-post reports survive restart without duplicates and source revisions remain traceable.
2. **Implement visual interpretation and retrieval.** Extract visible observations from actual attachments; search from varied natural loss descriptions; return a few original-message-linked candidates. Done when a photo-led buried report is found among hundreds of reports without story-specific IDs, with a similar distractor and an honest no-match path.
3. **Connect group selection to private cases.** Resolve replies to candidates, clarify ambiguous "mine", and provision/reuse the authenticated claimant's private case. Done when a new demo claimant can reach verification without being one of the existing four cases and without exposing others' details.
4. **Reuse librarian review and return.** Show a concise comparison, confirm custody, authorize the exact claim/item, reserve once, record human handover and claimant receipt. Preserve existing authorization/revision tests.
5. **Stage and measure the crowded-group demo.** Preload a clearly fictional corpus, targeting 300+ distinct reports across simulated days; retain actual message creation times. Show one live loss query and one recovery rather than streaming the corpus during the presentation. Record actual corpus size, source-linked results, model behavior and retrieval latency.

Cut voice, reminders, dashboards and extra platforms before cutting history search, images, source links or the librarian's decision. These priorities define the current product. The completed original milestones remain below as implementation history.

## Original core milestones

Work in this order. Reduce optional scope before reducing the completeness of the return workflow.

## 1. Inspect and establish the environment

Inspect repository instructions, existing tooling, installed agents, Docker, and Switch. Choose the least disruptive integration. Record versions and actual startup steps. Keep account login or key entry interactive when necessary; never print tokens in logs.

**Done when:** one human message reaches a real model-backed agent through Switch and its reply appears in Mattermost. Capture the actual event shape and sender identity fields.

## 2. Prove the room and identity boundaries

Provision one staff room and two separate claimant rooms manually. Enroll the demo accounts and configure addressing. Test from the actual unrelated claimant/agent credentials, not just an administrator account.

Identify the trusted path for staff commands. If sender identity cannot be reliably established, use a directly authenticated staff interface for authoritative actions and document exactly how it relates to the Switch conversation. Do not silently pretend that a display name proves authorization.

**Done when:** each claimant sees their own case; unrelated actors cannot read the other case or staff-only facts; staff authorization is checked against stable authenticated identity.

## 3. Implement durable domain records

Implement SQLite records, revisions, state validation, atomic reservation, audit events, and source-event deduplication. Load the fictional items in file 04 through an explicit fixture command.

Keep a local offline fixture mode for development. Label its output as a fixture run. It must not claim to be authenticated Switch traffic.

**Done when:** the happy path, rejected claim, stale approval, double reservation, replay, and restart behaviors can be checked without model calls.

## 4. Add useful AI behavior

Configure Intake to clarify the report and collect distinguishing details without revealing the answers. Configure Matcher to compare evidence for staff and explain ambiguity. Wire only the operations each role needs.

First support plain text. A genuine model must perform at least the intake or comparison work in the live workflow; a fully scripted conversation is not the final AI demonstration.

**Done when:** a vague report produces a useful question; a detailed answer produces a comparison grounded in source messages; a contradiction remains visible rather than being rewritten away.

## 5. Complete the live return

Connect the service to real Switch events. Accept the enrolled staff decision for an exact claim/item revision, reserve once, post collection instructions privately, record handover, and wait for claimant receipt before closure.

Separate agent-created drafts from human-confirmed records. Retry failures without duplicating reservations, notifications, or returns.

**Done when:** the complete case runs in actual chat and persists correctly across a service restart.

## 6. Verify and package

Run the targeted domain checks and actual Switch access checks. Review every message destination and the demo evidence. Provide a concise application README, environment-variable example without secrets, fixture instructions, live setup, known limits, and a recording under the event's current video limit.

The submission form may require interactive checks not visible in static HTML. Verify its current requirements before recording. Leave enough time for a clear demo and README.

**Done when:** another builder can reproduce fixture behavior from a clean clone and follow explicit steps for the live setup. Any untested dependency is named.

## Scope cuts if time is short

Keep the two similar items, insufficient-evidence case, real staff decision, and confirmed return. Cut photos, voice, reminder scheduling, automated room provisioning, public lobby, dashboard, and cross-platform support first. One chat platform and one location are sufficient.

## Definition of done

- Real Switch carries the user request, agent work, staff review, and outcome.
- At least one real human and one model-backed agent participate; both configured AI roles should be demonstrated if claimed.
- Privacy and authorization claims have actual checks, with remaining limits disclosed.
- Two similar objects are not merged into one record.
- Approval is exact, durable, and invalidated by relevant changes.
- Physical completion is represented only by the demo participants' explicit confirmations.
- Domain rules pass meaningful tests; the live integration has a separate evidence record.
- The final README and demo distinguish fictional data, offline fixtures, and genuine live interaction.

## Builder progress notes

As implementation proceeds, record the chosen stack and versions, verified Switch operations, actual run commands, test outcomes, evidence links, and unresolved issues in the application repository. Do not mark the project complete based only on these planning files.
