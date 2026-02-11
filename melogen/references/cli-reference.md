# Melogen CLI Reference

## Input Formats

### Sheet Music (`sheet2midi`)

| Format | Extensions | Notes |
|--------|-----------|-------|
| PDF | `.pdf` | Single or multi-page. Digital PDFs preferred; scanned PDFs work at 300+ DPI. Multi-page PDFs preferred over separate images. |
| PNG | `.png` | Sheet music images. Transparency supported. |
| JPG/JPEG | `.jpg`, `.jpeg` | Photographs or scans of sheet music. |

Best practices for sheet music input:
- Resolution: 300 DPI or higher
- Clean, high-contrast backgrounds
- Standard musical notation (non-standard symbols may not be recognized)
- Avoid skewed or rotated scans

### Audio (`music2midi`)

| Format | Extensions | Notes |
|--------|-----------|-------|
| MP3 | `.mp3` | Compressed audio. Acceptable quality but lossy. |
| WAV | `.wav` | Lossless. Best accuracy for transcription. |
| FLAC | `.flac` | Lossless compressed. Same accuracy as WAV. |
| OGG | `.ogg` | Compressed audio. |
| M4A | `.m4a` | AAC compressed audio. |

Best practices for audio input:
- Use WAV or FLAC for highest transcription accuracy
- Shorter files process faster (default polling timeout: 600s)
- Enable `--stems` for multi-instrument recordings
- Enable `--quantize` for rhythmically clean output

### Analysis (`analysis`)

| Input | Flag | Notes |
|-------|------|-------|
| MusicXML | `--mxl` | `.mxl` files. Most structured input for analysis. |
| Image | `--image` | PNG/JPG sheet music images. |
| PDF | `--pdf` | PDF scores. |

At least one input source is required. Multiple can be provided in the same call.

## Output Formats

| Format | Extension | Produced By | Description |
|--------|-----------|-------------|-------------|
| MIDI | `.mid` | `sheet2midi`, `music2midi` | Standard MIDI file with note events, timing, and velocity. |
| MusicXML | `.musicxml` | `sheet2midi` | Full musical notation including notes, rests, dynamics, and layout. |

## Supported Languages (Analysis)

| Code | Language |
|------|----------|
| `en` | English |
| `zh` | Chinese (Simplified) |
| `tw` | Chinese (Traditional) |
| `ja` | Japanese |
| `ko` | Korean |
| `de` | German |
| `fr` | French |
| `es` | Spanish |
| `pt` | Portuguese |
| `it` | Italian |
| `ru` | Russian |
| `pl` | Polish |
| `el` | Greek |
| `vi` | Vietnamese |

## Error Types

All CLI errors print to stderr and exit with code 1.

| Error Class | HTTP Status | Default Message | Common Cause |
|-------------|-------------|-----------------|--------------|
| `AuthenticationError` | 401 | Invalid or expired API key | Wrong key, expired key, or missing `MELOGEN_API_KEY` |
| `InsufficientCreditsError` | 402 | Insufficient credits | Account balance depleted |
| `ValidationError` | 422 | Validation error | Unsupported file format, invalid URL, or missing required parameter |
| `RateLimitError` | 429 | Rate limit exceeded | Too many concurrent requests |
| `TaskTimeoutError` | -- | Task {id} timed out after {timeout}s | Processing took longer than the polling timeout |
| `TaskFailedError` | -- | Task {id} failed: {error} | Server-side processing failure |

## API Key

- **Format**: `melo_xxx` (prefixed with `melo_`)
- **Set via**: `--api-key` flag or `MELOGEN_API_KEY` environment variable
- **Get a key**: Sign up at [melogenai.com](https://melogenai.com), then Settings > API Keys
- **Security**: Store in environment variables; do not commit to version control; rotate periodically
