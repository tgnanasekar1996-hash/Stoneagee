# THE FIRST FLAME

A 10-minute, 2D flat-cartoon Stone Age short. A cold village, a storm, a burning tree, a hungry wolf pack, and the night one curious hunter and his friends learn to make fire.

| | |
| --- | --- |
| Runtime | 10:00 (75 shots x 8 s) |
| Style | 2D flat cartoon, thick black outlines, flat colors, warm storybook palette. NOT realistic, NOT painterly, NOT 3D |
| Export | 1920x1080, 16:9, 24 fps (YouTube minimum 1280x720) |
| Cast | 7 adults: Karu, Bora, Tika, Elder Mappa, Elder Ammu, Ravi, Meera |
| Audio | Separate tracks: storyteller voice-over, music cues, sound effects |

## Repo layout

```
first-flame/
  README.md                 <- you are here (production bible)
  docs/character-bible.md   <- locked descriptions, faces, body language, expression library
  src/world.py              <- characters, expressions, environments, music cues (edit here)
  src/shots.py              <- all 75 shots (edit here)
  src/build.py              <- generates everything in output/
  output/script.md          <- full script: action, VO, music, SFX per shot
  output/prompts.md         <- 75 copy-paste video prompts (full character text in each)
  output/tracker.md         <- checklist for generation / VO / edit
  output/shots.json         <- same data for scripts and automation
```

Rebuild after any edit: `python src/build.py` (Python 3, no packages needed).

## Story in 15 chapters

| # | Chapter | Time | What happens |
| --- | --- | --- | --- |
| 1 | The Howl | 00:00 | Freezing night, wolves watch the village. Karu dreams of a better way |
| 2 | The Cold Morning | 00:40 | Dawn, Mappa's legend of a bright spirit, hunters set out |
| 3 | Into the Forest | 01:20 | Tracking a deer, Tika's sneeze ruins the hunt |
| 4 | Storm | 02:00 | Dark sky, rain, shelter, lightning strikes a tree |
| 5 | The Glow | 02:40 | The burning tree. Fear, wonder, the first warmth |
| 6 | Tika's Mistake | 03:20 | Tika's club catches fire; Karu learns fire eats and dies |
| 7 | Carrying the Flame | 04:00 | Karu carries a torch home; wind and rain put it out |
| 8 | News at Dusk | 04:40 | The village hears the story; Mappa knows the legend is true |
| 9 | First Tries | 05:20 | Failed attempts; Bora's axe makes a spark by accident |
| 10 | The Wolves | 06:00 | Wolves at the village; a spark scares them |
| 11 | The Long Night | 06:40 | Meera's tinder idea, Ammu's moss, dawn |
| 12 | Teamwork | 07:20 | Everyone gathers tinder; Bora's angle, Mappa's patience |
| 13 | The Spark | 08:00 | Ember, gentle breath, flame |
| 14 | Fire vs Fear | 08:40 | Wolves return and retreat from torchlight |
| 15 | The First Fire | 09:20 | Warmth, food, dance, fires in every cave, the stars |

## Visual rules (never break these)

1. **Characters:** paste the locked descriptions from `docs/character-bible.md` word for word. `build.py` does this automatically.
2. **Camera:** locked in every generated clip (no zoom, no pan), all characters fully in frame. Add the listed edit move later in your editor (see below).
3. **Faces:** every prompt names an expression from the library (fear, awe, relief...) with its face and body description, so reactions stay readable at 480p.
4. **Facing and positions:** every character has a stated screen position and who or what they face.
5. **Children:** none. All characters are adults (the video tool rejects scenes with children).
6. **Wolves:** friendly storybook style, never realistic or violent. They retreat from fire.

## Camera language

Generation is locked. In the editor add the move written in each shot of `script.md`:

| Edit move | How | Feeling |
| --- | --- | --- |
| Slow push-in | scale 100% to 108% over 8 s | focus, dread, wonder |
| Slow pull-back | scale 108% to 100% | reveal, release |
| Gentle pan right / left | shift crop 3-4% over 8 s | following walkers, discovery |
| Static | no move | comedy timing, big reactions |

Cut rhythm: 8-second shots. Comedy beats can be trimmed to 4-6 s. Hold the wide hero shots (shots 1, 5, 74, 75) the full 8 s.

## Music (compose or pick royalty-free tracks)

| Cue | Sound | Used for |
| --- | --- | --- |
| THEME | warm frame drum, bamboo flute, soft shakers | village life, walking |
| TENSION | low drone, slow heartbeat drum, bone clicks | cold, wolves, held breath |
| COMEDY | plucky pizzicato, bouncy hand drum, squeaky flute | Tika, trips, sneezes |
| WONDER | soft chimes, rising flute, airy oohs | the glow, sparks, discoveries |
| STORM | rolling timpani, string drone | the storm |
| URGENT | fast hand drums, driving flute | running, danger |
| HOPE | gentle flute over a warm drum pulse | decisions, teamwork |
| WATCH | sparse low flute, soft heartbeat | night, thinking |
| TRIUMPH | full tribal drums, chanting oohs, bright flute | the flame, victory |

Leitmotif idea: a 4-note rising flute phrase that first appears in shot 4 (Karu dreaming), returns half-finished in Chapter 5 and Chapter 9, and plays in full when the flame is born (shot 65).
Mix: VO at -12 dB, music at -22 dB under VO (-14 dB when no VO), SFX at -18 dB. Duck the music 6 dB under every VO line.

## Voice-over direction

- One narrator: warm, gravelly male storyteller, slow and kind, like an elder by a fire.
- About 700 words in total (about 5 minutes of speech), leaving the other 5 minutes for pictures, music and sound.
- Pace about 120 words per minute. Pause a full beat before the final line of each chapter.
- Characters make only non-verbal sounds (gasps, grunts, laughs, squeaks). No dialogue, no on-screen text except the title card at 00:32 and end card at 09:52.
- Free options: record your own voice, or use an AI narrator in your language; keep the same voice for all 75 shots.

## Workflow

1. Open `output/prompts.md`. Generate clip 01 first, three takes, pick the best. Save a clean frame where all seven are visible as your **reference image** for the later clips (if your tool supports image-to-video).
2. Generate clips in order. Tick `output/tracker.md` in GitHub as you go.
3. Import all clips into your editor (CapCut or DaVinci Resolve) in order, mute the generated audio, upscale to 1920x1080 if needed.
4. Record the VO lines from `script.md`. Lay music cues and SFX. Add the edit moves.
5. Add the title card over shot 5 and the end card over shot 75. Export 1080p.

If a clip drifts off-model, regenerate it. Do not edit the character text; instead strengthen the pose and expression words in that shot.

## Troubleshooting

| Problem | Fix |
| --- | --- |
| Characters look different between clips | use the reference image; keep character text identical |
| Faces look blank or sad | the prompt already names the expression; add "clearly animated face" |
| Characters leave the frame | keep the closing line; shorten the action |
| Tool rejects the prompt | no children, no violence; wolves must stay friendly cartoon style |
| Prompt too long for your tool | remove the environment sentence from that clip only |
