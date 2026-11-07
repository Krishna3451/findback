# Narrated actual UI demo

[Play the narrated demo](findback-narrated-demo.mp4). English narration is an authorized ElevenLabs synthetic voice. The visuals are actual Mattermost browser screenshots of the scripted fictional campus demonstration, with real FindBack/Switch messages and AI calls. There are cuts, compressed waiting gaps and holds of selected actual screenshots; this is not continuous footage of every event. No UI or message content is generated for the video. The featured case ends at approved collection, before handover and receipt.

Duration: **127.600 seconds**. Each chapter follows its exact PCM narration duration, quantized to 24fps for video. Voice tempo factor: **1.0** (1 is unchanged; other values use pitch-preserving atempo). No extra interchapter silence. The original TTS files remain unchanged.

| Chapter | View | Audio start | Audio length | Final actual-frame hold |
|---|---|---:|---:|---:|
| 1 | Campus context: the public lost-and-found conversation | 0.000s | 10.560s | 0.000s |
| 2 | Found item: Ava reports the black headphone case | 10.560s | 12.800s | 0.125s |
| 3 | Alex replies directly to Ava’s found post; FindBack invites him privately | 23.360s | 15.520s | 3.250s |
| 4 | The public invitation leads into Alex’s private recovery chat | 38.880s | 13.840s | 0.000s |
| 5 | Alex privately supplies identifying details; his exact words are acknowledged | 52.720s | 23.440s | 8.500s |
| 6 | Mira reviews the actual AI comparison and approves Alex’s exact case | 76.160s | 19.600s | 0.000s |
| 7 | Alex receives the private reservation and complete collection instructions | 95.760s | 14.720s | 1.917s |
| 8 | The public claim, Mira’s actual approval, and Alex’s collection-ready ending | 110.480s | 17.120s | 0.000s |

`narrated-manifest.json` records source hashes, exact chapter durations and ffprobe checks. The separate native clips and silent 180-second scaffold remain in `../broll/`. `narration.wav` preserves the complete normalized voice track.

Visual cues use the original provider character alignment, scaled to each exact output audio duration and quantized to 24 fps. Original JPEGs are verified against the native capture hashes. These hard cuts reveal already-captured views; they do not depict live typing or imply that an event occurred at the narrated moment.

- Chapter 2: cut to the actual next chat view at **4.917s**, on “Alex spots”.
- Chapter 5: cut to the actual next chat view at **15.458s**, on “Alex describes”.
- Chapter 6: cut to the actual next chat view at **9.833s**, on “Mira checks”.
- Chapter 7: cut to the actual next chat view at **7.583s**, on “The collection instructions”.

Final QA: both complete MP4 files decoded without errors. The primary paced file is H.264/AAC, 650 × 770, 24 fps, mono 48 kHz audio, 169.994854 seconds. The natural cut is 127.600 seconds. Decoded before/after frames were visually checked at the identifying-answer, librarian-approval and pickup-instruction cues. Complete owner wording and actual authorization messages remain visible.
