---
name: lyria-music
description: Generate a 30-second music clip from a text description or from an image's mood using Google Lyria 3. Trigger when user asks to create, generate, or compose music, songs, beats, or audio clips.
metadata:
  require-secret: true
  require-secret-description: Enter your Gemini API key. Get one at https://aistudio.google.com/apikey
  homepage: https://github.com/google-ai-edge/gallery/tree/main/skills/featured/lyria-music
---

# Lyria Music Generator

Generate 30-second high-fidelity music clips powered by Google Lyria 3.

## Examples

* "Create a cheerful acoustic folk song with guitar and harmonica"
* "Generate a dark ambient electronic track at 90 BPM"
* "Make a lo-fi hip hop beat, instrumental only"
* "Compose music that matches this image" (with an image)
* "Create a dreamy piano piece inspired by this sunset photo" (with image + text)

## Instructions

Call the `run_js` tool with the following exact parameters:
- data: A JSON string with the following field:
  - prompt: String. Required. A detailed music generation prompt.

**Constructing the prompt:**
Build the most detailed prompt you can from the user's request. Include any of these that fit:
- **Genre**: e.g., "lo-fi hip hop", "cinematic orchestral", "indie pop", "jazz fusion"
- **Instruments**: e.g., "acoustic guitar", "Fender Rhodes piano", "TR-808 drum machine"
- **Mood**: e.g., "nostalgic", "upbeat", "melancholic", "ethereal", "aggressive"
- **BPM / Tempo**: e.g., "120 BPM", "slow tempo around 70 BPM"
- **Key / Scale**: e.g., "in G major", "D minor"
- **Structure tags**: `[Verse]`, `[Chorus]`, `[Bridge]`, `[Intro]`, `[Outro]`
- **Timestamps**: e.g., `[0:00 - 0:10] Intro: soft piano`, `[0:10 - 0:25] Verse: add drums`
- For instrumental tracks, always include "Instrumental only, no vocals."
- For songs with lyrics, include the lyrics with section tags.

**Handling image inputs:**
When the user provides an image (with or without text), analyze its mood, colors, atmosphere, subject, and energy. Translate that analysis into a rich music prompt describing genre, instruments, tempo, and mood that capture the image's vibe.

DO NOT use any other tool. DO NOT call `run_intent`.

IMPORTANT: After the clip is generated, tell the user to tap the preview card to listen. If lyrics were returned in the tool result, share them with the user.
