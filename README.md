# melogen skills — ai-powered music tools for claude code, copilot & more

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

ai agent skills for converting sheet music to MIDI, transcribing audio to MIDI, and analyzing music structure via the [melogen](https://melogenai.com) cli — the ai-powered music toolkit for serverless music intelligence.

compatible with claude code, github copilot, and other ai coding assistants. convert PDFs and images to MIDI with OMR, transcribe MP3/WAV audio to MIDI, analyze tonality, harmony, and form in 14 languages, and more.

## Installation

### Option 1: Install All Skills

```bash
npx @anthropic-ai/claude-code skills add melogenai/skills
```

### Option 2: Install Specific Skills

```bash
# Main CLI skill (sheet2midi + music2midi + analysis)
npx @anthropic-ai/claude-code skills add melogenai/skills@melogen
```

### Manual Installation

Copy to your skills directory:

```bash
# Claude Code
cp -r melogen ~/.claude/skills/

# GitHub Copilot
cp -r melogen ~/.copilot/skills/

# Project-level
cp -r melogen .claude/skills/
```

## Quick Start

```bash
# Install CLI
pip install melogenai

# Set API key
export MELOGEN_API_KEY=melo_xxx

# Convert sheet music (PDF/PNG/JPG) to MIDI
melogen sheet2midi https://example.com/score.pdf

# Transcribe audio (MP3/WAV/FLAC) to MIDI
melogen music2midi https://example.com/song.mp3

# Analyze music structure and harmony
melogen analysis --pdf https://example.com/score.pdf

# Verify API key
melogen auth verify
```

## Available Skills

| Skill | Description | Triggers |
|-------|-------------|----------|
| **[melogen](melogen/SKILL.md)** | Main CLI skill — sheet2midi, music2midi, analysis | melogen, sheet music, audio to midi, music analysis |

## Capabilities

| Category | Features |
|----------|----------|
| **Sheet Music → MIDI** | PDF, PNG, JPG input · MIDI + MusicXML output · multi-page PDFs · OMR (Optical Music Recognition) |
| **Audio → MIDI** | MP3, WAV, FLAC, OGG, M4A input · polyphonic transcription · stem separation · beat quantization |
| **Music Analysis** | Key signature, time signature, form, harmony · MusicXML, image, PDF input · streaming output · 14 languages |

## Supported Formats

| Input | Formats |
|-------|---------|
| **Sheet Music** | PDF, PNG, JPG/JPEG |
| **Audio** | MP3, WAV, FLAC, OGG, M4A |
| **Analysis** | MusicXML (.mxl), PNG/JPG images, PDF scores |

| Output | Formats |
|--------|---------|
| **MIDI** | Standard .mid files with note events, timing, and velocity |
| **MusicXML** | Full notation with notes, rests, dynamics, and layout |

## Documentation

- [FAQ](https://melogenai.com/zh/faq) — Frequently asked questions
- [Python SDK](https://github.com/melogenai/melogenai-python) — Programmatic access via Python
- [CLI Reference](melogen/references/cli-reference.md) — Full command reference

## Links

- **Website**: [melogenai.com](https://melogenai.com)
- **FAQ**: [melogenai.com/zh/faq](https://melogenai.com/zh/faq)
- **Python SDK**: [github.com/melogenai/melogenai-python](https://github.com/melogenai/melogenai-python)
- **CLI Install**: `pip install melogenai`
