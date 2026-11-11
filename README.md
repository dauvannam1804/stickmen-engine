# Stickmen Engine

An automation engine that turns one text prompt into a finished ~60-second vertical short (1080×1920): 2D bean-man characters acting in 3D low-poly locations, with AI narration, word-synced captions, sound effects and music — rendered end-to-end with [Remotion](https://www.remotion.dev/).

## ⚠️ Source & Credits

**This code is not mine.** It is a working copy I saved to study and tinker with.

- Original video: [FREE AI Makes VIRAL Stickman Animations (No Claude Pro)](https://www.youtube.com/watch?v=0xKNsIK-HAU)
- Creator: [Bauka](https://www.youtube.com/@baukazhan-b1n) 🧑
- All credit for the engine's design and code belongs to the original creator. This repo is shared for educational purposes only — if you find it useful, please support the original video and channel.

Reference videos shown in the tutorial are **not** included here (copyright).

## What's inside

| Path | Purpose |
|---|---|
| `src/character/` | 2D bean-man characters drawn as SVG (poses, faces, headwear) |
| `src/location3d/`, `locations/` | 3D low-poly scenes defined as plain JSON (no code needed) |
| `src/scene/`, `src/fx/`, `src/captions/` | 2D scenes, props, effects, word-synced captions |
| `stories/*.json` | Story scripts: one shot per 1–3 s of narration |
| `scripts/make.ts` | One-command pipeline: story JSON → narrated, captioned MP4 |
| `scripts/tts.py` | Free AI narration via Microsoft Edge TTS (with per-word timestamps) |
| `scripts/gen_audio_assets.py` | Procedurally synthesizes all 54 SFX + 6 music tracks with numpy (royalty-free) |
| `.claude/skills/` | Skill docs that let an AI agent operate the engine end-to-end |

## Setup

```bash
npm install
pip install -r requirements.txt
npm run assets   # generate the sound library (one time, procedural)
```

## Make a video

```bash
npm run make -- stories/demo.json           # full render
npm run make -- stories/demo.json --preview # 50% resolution, fast check
npm run make -- stories/demo.json --stills  # one QA still per shot, no video
npm run make -- stories/demo.json --no-tts  # skip narration (offline timing)
npm run studio                              # open the Remotion studio
```

Output lands in `out/<story-slug>/<story-slug>.mp4`, loudness-normalized to −14 LUFS like YouTube Shorts.

## License / usage

Upstream project does not declare a license; this mirror inherits that. Personal and educational use only — ask the original creator before commercial use.
