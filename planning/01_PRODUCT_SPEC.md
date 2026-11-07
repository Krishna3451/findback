# FindBack — product specification

## Current brief — large university group

Updated November 7, 2026 from the user's clarification. This section supersedes the original small, text-first scope below. It specifies the next build; it does not claim those features are already implemented.

**Pitch:** Describe what you lost in the university group; FindBack finds relevant earlier reports, helps verify your claim privately, and brings the librarian a clear release decision.

The user imagines a large university group with **100+ found-item reports per day**, mixed with ordinary conversation. This is a design scenario, not measured usage. The student should not need to scroll through days of messages or guess the finder's wording. Finding an older report is the first visible benefit. Librarian-approved human return completes that benefit.

### Primary journey

1. People post found-item photos/descriptions and locations in the existing group. FindBack ingests older history and new messages, preserving their exact source links, authors, times and attachments. It extracts visible characteristics for search and preserves unknown or uncertain values.
2. A student writes naturally, "I lost a black headphone case near the engineering library yesterday. Has anyone found it?" The agent searches across earlier reports and returns a few plausible candidates with public photos, dates, places, reasons for relevance, and original-message links. A broad query may need clarification or yield no match.
3. The student replies to a candidate, "This looks like mine." The claim is bound to that report. An unclear "mine" reference gets a clarification. The service creates/reuses the authenticated claimant's private case; a four-person pre-enrolled script is insufficient as the final intake experience.
4. In private, the agent asks for distinguishing details without providing the answer. The librarian/finder independently records observations. Features visible in the public image help retrieval but cannot serve as secret verification evidence. Agents cannot infer unseen contents or invent confirming observations.
5. The librarian sees a concise comparison of the selected item, claimant evidence, agreements, contradictions, missing information and custody status. A found report is not confirmed library custody. If the finder still holds the object, the library must receive/register it before the librarian can approve release.
6. Only the enrolled librarian approves the exact reviewed claim/item revision. The existing service reserves once and sends collection details privately. Staff record human handover; the claimant confirms receipt. A minimal update appears in the original group thread.

### Demo requirements and acceptance

- Use an established, clearly fictional group history. Suggested corpus: 300+ distinct found-item reports across several simulated days, with photo-led and text-only reports and some normal conversation. Preserve actual chat creation times; any simulated report dates are disclosed fixture metadata. Seed history before the live presentation.
- Show one natural loss query, a short source-linked shortlist, one verification and librarian-approved return. Include a similar distractor and an unresolved claimant. Hundreds of messages streaming during the presentation would obscure the useful interaction.
- Retrieve a true match older than the latest 200 messages and a short-caption/photo-led report through actual image interpretation. Vary query wording and report order; discovery must not depend on hardcoded story IDs.
- Demonstrate candidate-bound "mine", ambiguous selection, no match, public/private separation, librarian-only release, one active reservation, and handover plus claimant receipt. Record actual corpus size, ranks and retrieval latency rather than claiming real-campus accuracy or throughput.
- Keep agents quiet on unrelated chatter. Public cards contain public source material only; other claimants' answers and staff-only observations never enter the group search index.

### Current scope

**Required:** crowded historical group, image/text ingestion, natural group loss reports, source-linked retrieval, context-bound selection, private verification, librarian approval, human handover/receipt, persistence and real Switch interaction.

**Optional:** voice, reminders, multilingual input, a dashboard, advanced vector infrastructure and additional chat platforms. Two AI roles are sufficient. Reuse the existing authorization and return machinery.

The detailed original scenario below remains useful for testing ambiguity and authorization. Its small inventory, manually precreated case rooms, and optional-photo decisions no longer define the product's primary experience.

## Original verification fixture

## Who it helps

A student or community member trying to recover a lost possession, and the person looking after found property. The first setting is a campus library. People already communicate through chat; FindBack helps them complete the return.

The product outcome is **an item returned to the right claimant with a reviewable record**. A suggested match or collection appointment is an intermediate result.

## Core scenario

Priya lost a black wireless-headphone case near the library. Staff hold two black cases. One has a green triangle sticker beneath its lid; the other has a red thread attached to its zipper. A broad description fits both.

FindBack collects Priya's report, acknowledges the ambiguity, and asks her privately to describe distinguishing marks or accessories. It does not reveal the staff's answers in the question. Priya remembers the green triangle and supplies an earlier fictional photo. A staff reviewer compares the evidence, approves the specific item, and arranges collection. Staff record the physical handover; Priya confirms receipt; the case closes.

An incorrect claimant who describes only "a black headphone case" receives a request for more evidence. The system does not accuse them of fraud or decide ownership automatically.

## Participants

| Participant | Responsibility |
| --- | --- |
| Claimant | Reports the loss, supplies their own identifying evidence, confirms receipt. |
| Custodian/staff member | Registers found items, checks evidence, approves or rejects release, records handover. |
| Intake AI | Helps the claimant describe the loss and answer non-leading follow-up questions. |
| Matcher AI | Helps staff compare reports and evidence, explains ambiguity and contradictions. |
| FindBack service | Stores records, validates actions, enforces state transitions, and posts receipts. |

Two people and two AI roles are enough for the demonstration. The service can appear as a deterministic Switch agent; it is not a third AI model.

## MVP workflow

1. Staff register found items in a restricted staff room. Keep distinguishing details out of public announcements.
2. A claimant reports their loss in their own case room. The intake agent turns the description into a structured draft and asks the claimant to confirm it.
3. The service supplies staff with candidate matches using non-secret characteristics such as category, color, place, and time. The Matcher explains plausible matches without claiming certainty.
4. Intake asks a broad question such as "What marks, contents, or accessories would help staff identify yours?" It must not ask "Does yours have a green triangle?"
5. Claimant evidence is recorded with its authenticated source message. The staff room receives a comparison showing agreements, contradictions, and missing information.
6. A configured staff reviewer approves a specific claim/item pair and exact evidence revision. The service reserves that item atomically.
7. Collection instructions are sent privately. An appointment does not close the case.
8. Staff record handover and the claimant confirms receipt. The service marks the item returned and posts a minimal receipt to the appropriate rooms.

## Required behavior

- Similar-looking items stay distinct. One broad report can produce several candidates.
- "Not enough information" is a legitimate outcome.
- Staff can reject a proposed match, request more evidence, cancel a reservation, or correct a record. Record the reason and invalidate outdated approvals.
- One item cannot be reserved for two active claims.
- A claimant, AI agent, quoted message, or renamed display name cannot authorize staff actions.
- Secret identifying facts never appear in another claimant's room or a public lobby.
- Every authoritative change records the real source, time, affected revision, and outcome.
- Messages say what actually happened: "reserved," "collection arranged," and "returned" have different meanings.

## Room structure

Use one restricted staff room and one restricted case room per claimant. Create them manually for the first demo. A public intake lobby is a later convenience.

Verify access from the accounts and agent credentials used in the demonstration. Do not assume that a room name or the word "private" in a prompt establishes isolation. If the installed version cannot provide the required access behavior, redesign the flow before placing private facts there.

## Scope decisions

**Must have:** text-first reports, a small inventory, candidate comparison, private follow-up, staff approval, reservation, handover and receipt, persistent records, and actual Switch interaction.

**Optional after completion:** photos, voice notes, multilingual intake, reminders, a read-only status board, template-based room creation.

**Outside the MVP:** a citywide marketplace, facial recognition, autonomous ownership adjudication, physical locks, payments, police integrations, identity-document collection, public exposure of item secrets, or a custom chat application.

## Product language

Use calm, plain wording. Say "possible match" and "staff review needed." Explain what evidence is missing. Do not advertise a percentage as a probability of ownership. A match explanation can list what agrees without inventing confidence.

## Questions to validate with users

Ask staff to walk through their last three returns: where items were logged, how owners were identified, what took time, and what they would refuse to automate. Ask a recent claimant what they remembered, which channel they used, and how they proved the item was theirs. Revise the product if the real burden differs from this assumed workflow.
