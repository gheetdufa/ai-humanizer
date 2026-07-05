# Humanizer

A single-page tool that makes AI-written text read like a person wrote it. It runs
entirely in your browser and is hosted on GitHub Pages, so you can bookmark it and
use it anytime.

## Two modes

- **⚡ Quick clean (no key, offline).** Instantly strips the machine fingerprints that
  detectors and readers flag:
  - Removes hidden/watermark Unicode (zero-width spaces, narrow no-break spaces, BOMs,
    soft hyphens) that AI tools inject on copy.
  - Straightens curly quotes and converts em/en dashes to normal punctuation.
  - Swaps ~150 overused AI buzzwords and filler phrases (delve, leverage, utilize,
    "it's important to note", "in today's fast-paced world", …) for plain language.
  - Adds natural contractions.

- **✨ Humanize with AI (your own key).** Sends the text straight from your browser to
  Anthropic's Claude with a prompt built from real research on what makes text read as
  AI: it varies sentence rhythm (burstiness), breaks the "rule of three", drops hedges,
  and rewrites in a natural human voice while preserving your meaning and facts.

An **AI-style signals** panel scores the text 0–100 and lists the specific tells it finds,
so you can see what changed.

## Using AI mode

1. Get an Anthropic API key at
   [console.anthropic.com](https://console.anthropic.com/settings/keys).
2. Open the site, expand **API key & privacy**, paste the key, and click **Save key**.
3. Pick a model, strength, and tone, then click **Humanize with AI**.

Your key is stored only in your browser's `localStorage` and is sent directly to
Anthropic — it never passes through any third-party server. AI usage bills your own
Anthropic account.

## How it's built

One static `index.html` (no build step, no dependencies, no backend). The browser calls
the Anthropic Messages API directly using the
`anthropic-dangerous-direct-browser-access` header.
