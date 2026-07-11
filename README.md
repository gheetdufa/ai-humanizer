# Humanizer

A single-page tool that makes AI-written text read like a person wrote it. It runs
entirely in your browser and is hosted on GitHub Pages — no API keys, no Anthropic
credits, no backend.

**Use it here:** [https://gheetdufa.github.io/ai-humanizer/](https://gheetdufa.github.io/ai-humanizer/)

## Free by default

- **⚡ Quick clean (offline).** Instantly strips the machine fingerprints that
  detectors and readers flag, with no network at all:
  - Removes hidden/watermark Unicode (zero-width spaces, narrow no-break spaces, BOMs,
    soft hyphens) that AI tools inject on copy.
  - Straightens curly quotes and converts em/en dashes to normal punctuation.
  - Swaps ~150 overused AI buzzwords and filler phrases (delve, leverage, utilize,
    "it's important to note", "in today's fast-paced world", …) for plain language.
  - Adds natural contractions.

- **✨ Humanize (free, anti-detect).** A real LLM rewrite aimed at the signals ZeroGPT-style
  detectors score: low perplexity (predictable words) and low burstiness (even sentence
  length). Default settings run a heavy rewrite, a second anti-detect pass, and a local
  rhythm cleaner that strips leftover AI glue and forces short/long sentence contrast.
  - **Free — best quality:** [Puter](https://puter.com) first (Claude / GPT-class models;
    a free Puter sign-in may appear once; each account gets a free monthly allowance),
    then automatic fallback to LLM7 → Pollinations.
  - **Free — no login:** [LLM7](https://llm7.io) / [Pollinations](https://pollinations.ai)
    with no account at all.

An **AI-style signals** panel scores the text 0–100 and lists the specific tells it finds,
so you can see what changed.

## How it's built

One static `index.html` (no build step, no backend). Puter is loaded from a CDN; free
rewrites call Puter, LLM7, or Pollinations from the browser (all send permissive CORS
headers). Nothing is billed to Anthropic.

## Trade-offs, honestly

Frontier-quality inference costs *someone* money, so "free" means routing through providers
that absorb that cost (Puter's free monthly allowance, LLM7 turbo models, Pollinations'
anonymous tier). Availability and exact quality depend on those services. Quick clean
always works offline as a deterministic backup.
