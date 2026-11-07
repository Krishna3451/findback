# Local enrollment and measured boundaries

Verified on November 7, 2026 with Switch Console **0.40.1** and its native Switch Core **0.31.0**. These notes document the installed implementation and actual local requests. They do not establish production readiness, real user demand, or physical possession of an object.

## What bootstrap creates

`bootstrap_local(state_dir)` returns the runtime config and saves `config.json` with mode `0600` inside a `0700` state directory. It checkpoints successful provisioning in private `provisioning.json` so accounts and completed room creation are reused. The CLI separately loads the explicitly fictional inventory and binds domain actors to enrollment.

The existing local tenant and Mattermost collaboration are reused. This is a workspace of **three private rooms**, not a newly isolated Switch tenant:

| Room | Human member | Role agent | Gateway room owner |
| --- | --- | --- | --- |
| C001 / Priya | Priya | Priya Intake | Dedicated nonadmin Intake owner |
| C002 / Alex | Alex | Alex Intake | Different nonadmin Intake owner |
| Staff | Custodian | Matcher | Dedicated nonadmin Matcher owner |

A fourth nonadmin owner owns the deterministic service agent. That agent is explicitly a member of all three rooms. Matcher is absent from claimant rooms, and each Intake belongs only to its case. The bundled local operator/administrators remain trusted and can administer these rooms. The bridge also adds its configured default local operator account to newly created channels.

Every room uses **both** Mattermost `channel_private` and Switch `read_visibility=private`, `write_visibility=private`. Mattermost privacy alone does not set Gateway privacy. Separate role sessions alone would not enforce this membership separation.

The fixture people are local demo accounts. Priya's successful initial spike identity is reused when its private checkpoint exists. The setup does not register or submit a hackathon entry.

## Identity is captured once by setup

Gateway's agent detail omits its transport actor ID, and the event's `sender_kind` can be null for an ordinary human. Setup therefore performs read-only metadata joins against the local Core database:

- `agents.client_id → clients.id / matrix_user_id` obtains the exact agent transport actor, not a guessed `@name`.
- `external_users.client_id → clients.id / matrix_user_id` binds each exact Mattermost user ID to its client UUID and transport actor.
- `external_users.id` supplies the distinct identity ID expected by addressing allowlists.

The privileged native environment and bridge credentials are used only by operator setup. The running service config contains scoped agent keys and fictional human account tokens; it contains no Core admin password, database password or server encryption key. Model calls receive neither this config nor a Switch API client.

Runtime independently checks a human command against the real Mattermost post: immutable user ID, channel ID, literal body and deterministic Switch event ID. For an ordinary text event, Core 0.31 derives the ID as:

```text
source = bridge_id + "\x1f" + channel_id + "\x1f" + mattermost_post_id
event_id = "sw_" + sha256(client_uuid + "\x1f" + source + "\x1f0")[:32]
```

This supports the text-only commands implemented here. A display name, an LLM's claimed role, a self-claimed platform account, a quoted approval or a relayed platform message is insufficient. Very old posts outside the verification window fail closed.

## Actual credential checks

The nonsecret result artifact is [evidence/privacy-checks.json](evidence/privacy-checks.json).

The opt-in checker can repeat HTTP membership/credential checks while the main runtime is active:

```sh
.venv/bin/python -m findback.verify_access --state-dir .findback --gateway-owners --output evidence/access-checks.json
```

It opens no WebSocket, claims no existing connection, posts no messages, calls no model and makes no case changes. `--gateway-owners` additionally uses the nonadmin owner logins in the private provisioning checkpoint; it does not read native administrator credentials. Its [recorded run](evidence/access-checks.json) passed all 31 checks. The separate addressing check below is an earlier actual message exercise, not something this read-only checker repeats.

| Actual request | Observed result |
| --- | --- |
| Service WebSocket and `read_context` in all three member rooms | Succeeded |
| Each tested Intake/Matcher WebSocket and own-room history | Succeeded |
| Priya Intake key reads staff; Matcher key reads Priya | HTTP 403 |
| Alex MM token reads Priya; Priya MM token reads staff; staff MM token reads Priya | HTTP 403 |
| Intake Gateway owner reads staff; Matcher owner reads Priya; service owner reads Priya | HTTP 403 |
| Intake key uses Matcher URL path to read staff | HTTP 403 |
| Same key and Matcher URL path read its own Priya room | HTTP 200; dispatch still uses the authenticated Intake identity |
| Priya, Alex and custodian Mattermost accounts | All lack `system_admin` |

`GET /agents/{id}/ops` returns the same generic operation registry for a valid agent credential, even when the path's ID differs. Its HTTP 200 is not an impersonation proof: operation dispatch uses the authenticated key's agent ID. The installed registry exposed 57 operations. The application exposes no general Switch tool to the model.

## Actual addressing checks

Bootstrap installs explicit room-scoped allowlists. Each Intake accepts its own enrolled human plus the service agent; Matcher accepts the custodian plus the service. The service accepts the enrolled human only in that human's room. The allowlists do not rely on symbolic ownership or platform-account self-claims.

Two labeled non-command messages were sent through the actual bridge while the runtime captured original envelopes:

- Priya mentioning her Intake produced `addressed=true` for that Intake.
- Priya Intake mentioning the human-only Service produced `addressed=false` for Service.

**Core demotes a denied mention to ordinary room chatter.** A `filter=all` subscriber still sees that chatter. Addressing policies control attention; actual membership controls room access, and FindBack's separately verified actor and room enrollment control commands. Do not describe mention denial as hiding a message or preventing every application from reacting to it.

## Transport contract

The adapter requests the supported legacy protocol 8 ticket cursor, an explicit room list, and a generation-fenced connection UUID. The reader continues answering heartbeat pings independently of model calls. Runtime durably stores the original envelope before `ack(frame)` advances its saved cursor; later acknowledgments cannot skip an earlier uncaptured frame. A replay gap stops processing for reconciliation.

`read_context` actually returned `{threads, truncated, oldest_timestamp}`. Each thread contains a root and replies; entries include `id`, `kind`, `sender`, `sender_name`, `body`, epoch-millisecond `timestamp`, and `attachments`. Roots may be repeated across history windows. `before`/`since` operation arguments are ISO timestamps. Timestamp-boundary pagination must detect nonprogress rather than skip a full boundary millisecond.

Per-room session selectors bind `connect_to_room` and the following operation under one application lock while retaining the independent reader's other room claims. Unknown POST outcomes are never automatically retried by this transport. The runtime reconciles stable outgoing markers against the expected posting actor before retrying; absolute exactly-once chat delivery is not claimed.

Seven isolated fake HTTP/WebSocket tests cover durable cursor acknowledgment, heartbeat independence, generation/resume, serialized room binding, unknown mutation outcomes, safe errors and replay gaps. An additional enrollment regression test deliberately separates Mattermost, client and external-identity IDs and checks that no human or agent inherits another room's addressing authority. Live permission checks are separate evidence. The main project evidence records the completed live workflow: five actual Codex calls, one scripted fictional case returned and one still needing information. These access checks do not by themselves prove that outcome.

## Portability and remaining setup limits

This bootstrap currently targets the native macOS Switch Console installation and its bundled Python/Core packages. It does not install Switch, start Docker, support a remote deployment or create a second collaboration/tenant. A failed provisioning HTTP call may require operator inspection before repeating unknown room/agent creation; the bootstrap is not a distributed provisioning transaction. It never deletes or resets an existing case.

Keep `.findback/`, database files, native configuration and real claimant data out of Git. The committed evidence file contains statuses and field names only; private enrollment files are ignored.
