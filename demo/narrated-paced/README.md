# Narrated actual UI demo

[Play the narrated demo](findback-narrated-demo.mp4). English narration is an authorized ElevenLabs synthetic voice. The visuals are actual Mattermost browser screenshots of the scripted fictional campus demonstration, with real FindBack/Switch messages and AI calls. There are cuts, compressed waiting gaps and holds of selected actual screenshots; this is not continuous footage of every event. No UI or message content is generated for the video. The featured case ends at approved collection, before handover and receipt.

Duration: **169.995 seconds**. Each chapter follows its exact PCM narration duration, quantized to 24fps for video. Voice tempo factor: **0.75** (1 is unchanged; other values use pitch-preserving atempo). No extra interchapter silence. The original TTS files remain unchanged.

| Chapter | View | Audio start | Audio length | Final actual-frame hold |
|---|---|---:|---:|---:|
| 1 | Campus context: the public lost-and-found conversation | 0.000s | 14.053s | 3.500s |
| 2 | Found item: Ava reports the black headphone case | 14.053s | 17.049s | 4.375s |
| 3 | Alex replies directly to Ava’s found post; FindBack invites him privately | 31.102s | 20.691s | 8.417s |
| 4 | The public invitation leads into Alex’s private recovery chat | 51.793s | 18.443s | 3.500s |
| 5 | Alex privately supplies identifying details; his exact words are acknowledged | 70.236s | 31.241s | 16.333s |
| 6 | Mira reviews the actual AI comparison and approves Alex’s exact case | 101.476s | 26.112s | 2.958s |
| 7 | Alex receives the private reservation and complete collection instructions | 127.588s | 19.603s | 6.792s |
| 8 | The public claim, Mira’s actual approval, and Alex’s collection-ready ending | 147.191s | 22.804s | 4.625s |

`narrated-manifest.json` records source hashes, exact chapter durations and ffprobe checks. The separate native clips and silent 180-second scaffold remain in `../broll/`. `narration.wav` preserves the complete normalized voice track.

Visual cues use the original provider character alignment, scaled to each exact output audio duration and quantized to 24 fps. Original JPEGs are verified against the native capture hashes. These hard cuts reveal already-captured views; they do not depict live typing or imply that an event occurred at the narrated moment.

- Chapter 2: cut to the actual next chat view at **6.542s**, on “Alex spots”.
- Chapter 5: cut to the actual next chat view at **20.583s**, on “Alex describes”.
- Chapter 6: cut to the actual next chat view at **13.125s**, on “Mira checks”.
- Chapter 7: cut to the actual next chat view at **10.083s**, on “The collection instructions”.

Final QA: both complete MP4 files decoded without errors. The primary paced file is H.264/AAC, 650 × 770, 24 fps, mono 48 kHz audio, 169.994854 seconds. The natural cut is 127.600 seconds. Decoded before/after frames were visually checked at the identifying-answer, librarian-approval and pickup-instruction cues. Complete owner wording and actual authorization messages remain visible.
