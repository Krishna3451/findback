# FindBack recorded playback

`evidence/findback-demo.mp4` is a narrated text playback of the captured full Switch/Mattermost run recorded on November 7, 2026 at 13:25 UTC. It is **not a screen recording, a live UI capture, or footage of a physical handover**.

Every scene carries this disclosure:

> RECORDED PLAYBACK of captured live Switch run — scripted fictional inputs
>
> No physical handover • Text reconstruction, not a screen recording

The original run used real local Switch/Mattermost transport and signed-in Codex inference. The claimant and custodian messages were scripted through authenticated fictional accounts. No claim is made that real people typed them independently, that real users validated the product, or that a real possession changed hands. The narration is offline macOS text-to-speech, not an original participant's voice.

## Evidence and what the film shows

The source generator reads `evidence/live-run.json` and a consistent, read-only SQLite backup of `.findback/findback.db`. It checks that the shown result codes match the recorded source-event IDs and that the final return receipt exists. Model summaries are taken from stored `model_proposals`; the identifying assertion, staff reason and denial messages come from captured input/domain records. Scene headings and explanatory labels organize those records; they are not invented participant quotes.

The story covers two similar fictional cases, a confirmed report and non-leading question, unresolved ambiguity, Alex remaining in NEEDS_INFO, Priya's recorded identifying assertion, a refreshed staff comparison, unauthorized and stale-review refusals, reservation, and staff handover followed by claimant receipt. The complete-run totals are taken from the original `live-run.json` snapshot. Later diagnostic events in the database are not folded into those totals.

`evidence/findback-demo-manifest.json` records the source capture time, exact scene text/source references, rendering backend, source hashes, video hash, audio type and verified video duration. It contains no transport tokens. The private database/configuration files remain outside the distributable artifact.

## Reproduce offline

Prerequisites already installed on the rendering machine: Python 3, ffmpeg and ffprobe. On macOS, the generator can use `say` for narration and the system Swift compiler/AppKit frameworks if ffmpeg lacks its optional drawtext filter. No Python image package, font download, network access or new model call is required. A restricted macOS environment can prevent the installed voice engine from producing samples; the generator then falls back to a silent film at the first scene, or you can select `--silent` explicitly.

From the application directory, with the captured private database available:

```sh
python3 scripts/make_demo_video.py
```

For a silent film with the same readable text:

```sh
python3 scripts/make_demo_video.py --silent
```

Optional arguments are `--db`, `--live-run`, `--output`, `--voice` and `--keep-work`. Intermediates are private and removed by default. `--keep-work` retains the consistent database copy and rendered slides for local review; do not publish that work directory.

The generator first uses SQLite's read-only backup API to include committed WAL contents consistently. If the local sandbox prevents WAL shared-memory access, it permits immutable reading only when no nonempty WAL exists; otherwise it refuses rather than silently using a stale snapshot. Run with the necessary local read access or stop/checkpoint the existing service through its normal operator workflow. The generator itself does not change runtime/domain state.

The local ffmpeg build used for this artifact lacks drawtext and libass. The source therefore renders text with macOS's built-in AppKit/Arial through an embedded Swift helper, then encodes it with ffmpeg. A machine with ffmpeg drawtext and an installed supported font can use the direct drawtext path instead. There are no downloaded visual assets.

Verify independently:

```sh
ffprobe -v error -show_entries format=duration:stream=codec_name,width,height,r_frame_rate -of json evidence/findback-demo.mp4
```

The delivered video is **152.021333 seconds (2 minutes 32 seconds), 1920×1080 at 24 fps, H.264 video with AAC narration**, verified with ffprobe. The text was visually checked in rendered slides and extracted encoded frames. It is conservatively under three minutes. This is a project target, **not a verified official video limit**. Review the current interactive submission form before any upload. This artifact does not register, upload, publish or submit the entry.
