# Rachel Digital Human Production

Codex Skill for producing authorized digital-human talking-head videos with MiniMax overseas voice cloning and HeyGen Image-to-Video.

This skill turns a repeatable production workflow into a Codex-friendly playbook:

- Validate script, portrait, and voice-source assets before paid API calls.
- Use MiniMax for voice cloning and narration.
- Use HeyGen for image-driven digital-human video.
- Generate a 15-second preview before any full video.
- Wait for explicit user approval before full 1080p generation.
- Track `voice_id`, `asset_id`, `video_id`, job status, and outputs in `work/job-state.json`.
- Keep API keys, Authorization headers, signed URLs, private portraits, voice samples, and generated client videos out of the skill package.

## Install

Copy this folder into your Codex skills directory:

```bash
cp -R rachel-digital-human-production ~/.codex/skills/
```

Start a new Codex task, then invoke it explicitly:

```text
Use $rachel-digital-human-production to make a 15-second digital-human preview first.
```

## Expected Project Layout

```text
project/
├── inputs/
│   ├── portrait.jpg
│   ├── voice-source.mp3
│   └── script.md
├── work/
│   ├── voiceover-full.mp3
│   ├── preview-15s.mp3
│   └── job-state.json
└── outputs/
    ├── preview-15s.mp4
    └── final-1080p.mp4
```

## Environment Variables

The skill expects the user to provide their own accounts, billing, permissions, and API keys:

```bash
export MINIMAX_API_KEY="..."
export HEYGEN_API_KEY="..."
```

Do not commit `.env` files or real keys.

## Helper Scripts

Create a starter state file:

```bash
scripts/init_job_state.py --project demo --out work/job-state.json
```

Preflight common assets before API calls:

```bash
scripts/preflight_assets.py \
  --script inputs/script.md \
  --portrait inputs/portrait.jpg \
  --voice inputs/voice-source.mp3
```

## Safety

Use this only for authorized voice, portrait, script, and publishing workflows. Installing the skill does not grant access to MiniMax, HeyGen, OpenAI, paid credits, network access, legal clearance, or the author's files.

For public use, explicit invocation is required through `$rachel-digital-human-production` so paid production workflows do not trigger accidentally.

## License

MIT. See [LICENSE](./LICENSE).
