# Humanizer

A single-page tool that makes AI-written text read like a person wrote it. It runs
entirely in your browser and is hosted on GitHub Pages, so you can bookmark it and
use it anytime.

## No key required

The AI rewrite is **free** — you don't need an API key.

- **⚡ Quick clean (offline).** Instantly strips the machine fingerprints that
  detectors and readers flag, with no network at all:
  - Removes hidden/watermark Unicode (zero-width spaces, narrow no-break spaces, BOMs,
    soft hyphens) that AI tools inject on copy.
  - Straightens curly quotes and converts em/en dashes to normal punctuation.
  - Swaps ~150 overused AI buzzwords and filler phrases (delve, leverage, utilize,
    "it's important to note", "in today's fast-paced world", …) for plain language.
  - Adds natural contractions.

- **✨ Humanize (free).** A real LLM rewrite guided by research on what makes text read
  as AI: it varies sentence rhythm (burstiness), breaks the "rule of three", drops hedges,
  and rewrites in a natural human voice while preserving your meaning and facts. Pick an
  engine:
  - **Free — best quality:** routes through [Puter](https://puter.com) to reach
    GPT-4o / Claude-class models (a free Puter sign-in may appear the first time), and
    automatically falls back to the no-login engine if Puter is unavailable.
  - **Free — no login:** routes through [Pollinations](https://pollinations.ai) with no
    account at all.
  - **Your own Claude key (optional):** the most consistent quality, billed to your own
    Anthropic account.

An **AI-style signals** panel scores the text 0–100 and lists the specific tells it finds,
so you can see what changed.

## Optional: use your own Claude key

For the most consistent quality you can plug in an Anthropic key:

1. Get a key at [console.anthropic.com](https://console.anthropic.com/settings/keys).
2. Open the site, set **Engine** to *Your own Claude key*, expand **API key & privacy**,
   paste the key, and click **Save key**.

Your key is stored only in your browser's `localStorage` and is sent directly to
Anthropic — it never passes through any server of mine.

## How it's built

One static `index.html` (no build step, no backend). The only dependency is the optional
Puter script loaded from a CDN. Free rewrites call Puter or the Pollinations HTTP API from
the browser (both send permissive CORS headers); the key path calls the Anthropic Messages
API directly using the `anthropic-dangerous-direct-browser-access` header.

## Trade-offs, honestly

Frontier-quality inference costs *someone* money, so "free" means routing through providers
that absorb that cost (Puter's free tier, Pollinations' open models). Those are third-party
services, so availability and exact quality depend on them. The **own-key** path is the way
to guarantee a specific model and consistent output.
