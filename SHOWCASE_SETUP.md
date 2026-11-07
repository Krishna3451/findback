# Fictional campus showcase setup

The showcase uses a separate state directory, `.findback/showcase/`, so it does not reset the earlier two-case implementation demo. The setup command is:

```sh
.venv/bin/python -m findback.showcase_setup --state-dir .findback/showcase --viewer-username krishna
```

Run this only for the explicitly fictional local showcase. It provisions resources and sends one pinned notice describing the scripted cohort. It does not start a runtime, create a domain database, seed fixture inventory, register found objects, run models or progress a case. Repeating it reuses saved enrollment and updates that same notice.

The current community is [Campus • Lost & Found](http://localhost:57898/switch/channels/findback-campus-2f0ae85d). The same local team contains private channels named **Priya • FindBack**, **Alex • FindBack**, **Maya • FindBack**, **Leo • FindBack**, and **Library • Review Desk**. Channel names are presentation labels; immutable IDs remain the authority.

Browser links use `showcase.browser_origin`, derived from the public Mattermost `SiteURL` only when it names a loopback host on the same local port. Here that is `http://localhost:57898`. Backend API calls retain `mattermost_url=http://127.0.0.1:57898`. This keeps browser requests on the server's canonical origin without changing its Origin checks, CORS settings or server configuration. All six room links are ordinary HTTP links rather than desktop deep links.

## People and real agent identities

There are **12 distinct fictional Mattermost accounts**:

| Key | Display name | Showcase role |
| --- | --- | --- |
| priya | Priya Shah | Claimant C001, headphone case |
| alex | Alex Chen | Claimant C002, similar headphone case |
| maya | Maya Patel | Claimant C003, bottle |
| leo | Leo Martins | Claimant C004, book |
| mira | Mira Library Desk | Enrolled custodian |
| jordan | Jordan Ellis | Finder |
| elena | Elena Ruiz | Volunteer |
| omar | Omar Malik | Commuter |
| noah | Noah Brooks | Cyclist |
| aisha | Aisha Khan | Student |
| ava | Ava Wilson | Finder |
| sam | Sam Library Team | Library assistant |

A separate thirteenth account is the nonadmin **FindBack Demo Observer**. Each scripted person has its own actual Mattermost account/token, client UUID and Switch transport sender. A story runner controls these fictional accounts; this is not evidence of twelve real users participating.

Six actual Switch agent identities are provisioned: the deterministic service, Matcher and four case-specific Intakes. Each has a separate regular owner and scoped key. Agent messages must be posted through those identities by the application, not fabricated by a human account with an AI-like display name. The setup itself posts no agent replies and claims no model inference.

## Privacy and observer exception

Community is public inside the local Mattermost team and contains broad notices only. Each case and staff room remains a private Mattermost channel with private Switch read/write visibility. Each Intake belongs only to its case; Matcher belongs only to staff; the service belongs to all six rooms.

For this fictional demonstration, two observers have explicit channel membership in all six rooms:

- The dedicated nonadmin demo observer.
- The already signed-in local account `@krishna`, resolved through its exact Mattermost user ID after its username was observed in the UI.

Neither is enrolled as a claimant or custodian. Their viewing access is disclosed in the pinned notice and channel headers. Existing viewer roles, passwords, security settings and preferences are not changed. The new fictional observer alone receives a full-name display preference.

Normal claimant accounts remain isolated from other cases and staff. Do not describe a demo observer as having production-style private claimant isolation. Do not copy identifying marks, contents or staff comparisons into community messages.

## Runtime contract

The saved `config.json` retains standard `cases`, `staff_room`, `staff` and `agents` fields, extended to four cases. It also includes:

```text
showcase.community_room {id, channel_id, url, display_name}
showcase.browser_origin
showcase.people[key] {id, token, username, password, client_id, actor_id,
                     external_identity_id, display_name, role, case_id, fictional}
showcase.observer {private fictional account credentials and bindings}
showcase.viewer {username, id, actor_id, client_id, external_identity_id, purpose}
showcase.notice_post_id
showcase.background_items
```

These private files are mode `0600` inside a `0700` directory and ignored by Git. No administrative Core/DB credential is written to the runtime config. Community bindings include all twelve immutable human identities so the natural-language adapter can independently verify their actual posts.

Use the showcase-specific runtime/runner to configure all four case bindings without fixture inventory. **Do not call the base fixture-enrolling CLI against this showcase state.** Custodian inventory registration should be driven by actual staff messages. `background_items` are coarse story planning metadata, not registered inventory or proof that an item was received.

The setup installs explicit addressing allowlists for each claimant/Intake pair and staff/Matcher, plus a community service rule for the twelve simulated people. It does not grant either observer command authority. Core addressing denial still demotes a mention to ordinary chatter; deterministic actor/room authorization remains separate.

## Measured access

The nonsecret [showcase access artifact](evidence/showcase-access-checks.json) records **94 passed read-only checks**, including four-case agent/human isolation, service membership, community access for all twelve people, distinct immutable identity mappings and the separate nonadmin observer's viewing access. No WebSocket was opened or displaced by these checks. They do not establish a story run, model quality, actual users or physical recovery.

The standard checker can repeat the base four-case checks without progressing the showcase:

```sh
.venv/bin/python -m findback.verify_access --state-dir .findback/showcase --gateway-owners --output evidence/showcase-base-access-checks.json
```

The dedicated showcase setup does not erase the earlier app state or its evidence. Never publish the private showcase checkpoints, account credentials, raw local database or native Switch configuration.
