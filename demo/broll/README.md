# Actual Mattermost B-roll

These clips show the actual local Mattermost browser UI. The demonstration uses fictional people, objects and handovers; FindBack's messages, Switch transport, model calls and checks run through the app. The intended final state is approved collection, before handover or receipt.

The native clips encode timestamped browser screenshots at their captured cadence, with a final 0.7-second hold. They are not a continuous recording of every event. Timed clips compress gaps longer than two seconds to 0.7 seconds, hold the final actual frame when short, and cut the tail when long. No UI, chat, motion, narration, text overlay or graphics are generated. Source pixels are padded to even dimensions where necessary and are not rescaled or cropped.

The silent assembly is a timing scaffold for a future voice recording. Scene boundaries can be moved to match the actual narration; do not treat these fixed durations as measured speech timing.

| Scene | View | Assembly start | Target length | Native capture | After gap cuts | Extra final-frame hold |
|---|---|---:|---:|---:|---:|---:|
| [1](clips/scene-01.mp4) | Campus context: the public lost-and-found conversation | 0:00 | 18s | 10.583s | 10.583s | 7.417s |
| [2](clips/scene-02.mp4) | Found item: Ava reports the black headphone case | 0:18 | 20s | 12.667s | 12.667s | 7.333s |
| [3](clips/scene-03.mp4) | Alex replies directly to Ava’s found post; FindBack invites him privately | 0:38 | 22s | 12.292s | 12.292s | 9.708s |
| [4](clips/scene-04.mp4) | The public invitation leads into Alex’s private recovery chat | 1:00 | 17s | 50.500s | 14.917s | 2.083s |
| [5](clips/scene-05.mp4) | Alex privately supplies identifying details; his exact words are acknowledged | 1:17 | 28s | 83.167s | 14.917s | 13.083s |
| [6](clips/scene-06.mp4) | Mira reviews the actual AI comparison and approves Alex’s exact case | 1:45 | 30s | 122.417s | 23.167s | 6.833s |
| [7](clips/scene-07.mp4) | Alex receives the private reservation and complete collection instructions | 2:15 | 25s | 99.667s | 12.792s | 12.208s |
| [8](clips/scene-08.mp4) | The public claim, Mira’s actual approval, and Alex’s collection-ready ending | 2:40 | 20s | 31.625s | 18.167s | 1.833s |

Native captures and byte-for-byte final screenshots are in `native/scene-XX/`. Each native manifest records original JPEG hashes, timestamps, exact omissions and encoding details. `broll-manifest.json` records the timed clips, holds, cuts and hashes.

[Play the 180-second silent assembly](findback-silent-180s.mp4).
