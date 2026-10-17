# Know The World — published content

Everything the app fetches at runtime: the lesson JSON, the voiceover clips, and the manifest
that indexes them. **Generated** by `tools/publish.py` in the app repo — do not edit by hand.

## Layout

```
manifest.json      days[] with sha256 + bytes, languages, media pointer
days/*.json        lessons: scenes, drawings, narration, quiz, per-language i18n
media.json         every voiceover clip with its byte size and sha256
audio/**           voiceover, English (audio/<lesson>/…) and Hindi (audio/hi/<lesson>/…)
```

## Base URL

Raw: `https://raw.githubusercontent.com/vishnuancha/knowtheworld-content/main`

Every file is fetched by the app as bytes and verified against the sha256 in `manifest.json`
(days) or `media.json` (audio) before it is used. A mismatch is discarded.

This repo is public because the app has no credentials to authenticate with; a private repo's
raw URLs would require a token on the device. Content is public to users anyway.
