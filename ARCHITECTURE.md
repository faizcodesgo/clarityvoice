# ADR-001: Architecture for ClarityVoice (Real-Time Speech Improvement Web App)

**Status:** Accepted
**Date:** 2026-06-25
**Deciders:** Faiz (solo developer)
**Project:** College / placement project

---

## Context

ClarityVoice takes a user's spoken or typed English, improves the grammar and
professionalism while preserving their intent, optionally translates it, and
speaks the result aloud. Constraints that shape every decision below:

- **Solo beginner developer** — must be simple to build and maintain.
- **Near-zero budget** — free tiers only; one optional ~$5/mo service (voice cloning).
- **Must demo well** — for placements, a clean live demo matters more than scale.
- **No real users / no scale requirement yet** — correctness and clarity over throughput.

### Non-functional requirements

| Requirement | Target |
|-------------|--------|
| Cost | ₹0 for core; ~$5/mo only if voice cloning is added |
| Setup for a new machine | Open one file in Chrome — no install |
| Latency (turn-based) | A few seconds is acceptable (NOT live-during-call) |
| Privacy | No backend storing user speech; keys live in the user's browser |
| Maintenance | One developer, occasional changes |

---

## Decision

Build ClarityVoice as a **single-page, front-end-only web app** (one `index.html`)
that calls third-party APIs directly from the browser. The user supplies their own
Google Gemini API key, stored in `localStorage`. No custom backend server for v1.

### Pipeline

```
                ┌─────────────┐
  🎤 Voice ───► │  Web Speech  │ ──► text
                │  (browser)   │
  ⌨️ Text  ────────────────────────► text
                                       │
                                       ▼
                          ┌────────────────────────┐
                          │  Gemini API (LLM)      │
                          │  • fix grammar         │
                          │  • set tone/professional│
                          │  • translate (optional) │
                          └────────────────────────┘
                                       │
                          improved text │ + translation
                                       ▼
                          ┌────────────────────────┐
                          │  Text-to-Speech         │
                          │  • Browser voices (free)│
                          │  • ElevenLabs (optional,│
                          │    cloned voice, paid)  │
                          └────────────────────────┘
                                       │
                                       ▼
                                  🔊 Audio out
```

### Components & chosen technology

| Layer | Choice | Why |
|-------|--------|-----|
| Speech-to-text | Browser Web Speech API (`webkitSpeechRecognition`) | Free, built in, zero setup |
| Improve / tone / translate | Google Gemini (`gemini-2.0-flash`) | Strong free tier, one API for all three |
| Grammar fallback (no key) | LanguageTool free API | App still works without a key |
| Text-to-speech | Browser `SpeechSynthesis` | Free, natural voices available |
| Voice cloning (optional, later) | ElevenLabs (~$5/mo) | Best instant cloning; voice ID cached in `localStorage` |
| Key/voice persistence | Browser `localStorage` | Simplest "remember me" with no database |

---

## Options Considered

### Option A: Front-end only, user-supplied key (CHOSEN)
| Dimension | Assessment |
|-----------|------------|
| Complexity | Low |
| Cost | ₹0 |
| Scalability | Low (fine — not needed yet) |
| Team familiarity | High (just HTML/JS) |

**Pros:** No server to run or pay for; instant to demo; nothing to deploy beyond a static file; each user brings their own free key so quota is never the developer's problem.
**Cons:** API key lives in the browser (acceptable since it is the *user's own* key, not a shared secret); no central storage of history; not how a real commercial product would handle secrets.

### Option B: Front-end + small backend (Node/Express or Python Flask)
| Dimension | Assessment |
|-----------|------------|
| Complexity | Medium |
| Cost | ₹0 on free hosting (Render/Vercel), but more moving parts |
| Scalability | Medium |
| Team familiarity | Lower (new concept for a beginner) |

**Pros:** Hides a shared API key safely; enables saved history, accounts, analytics; closer to a real product; stronger talking point in interviews.
**Cons:** More to build, deploy, and debug; the developer's own key absorbs all usage cost; overkill for a v1 demo.

### Option C: Use a single all-in-one realtime API (e.g. OpenAI/Gemini Live speech-to-speech)
| Dimension | Assessment |
|-----------|------------|
| Complexity | Medium-High |
| Cost | Higher; thinner free tiers |
| Scalability | High |
| Team familiarity | Low |

**Pros:** Lowest latency, true real-time, fewer moving parts in theory.
**Cons:** Costs add up fast; less control over the "improve grammar / set tone" step; harder for a beginner; not needed for turn-based use.

---

## Trade-off Analysis

The core tension is **simplicity/cost (Option A) vs. realism/defensibility (Option B)**.
For a v1 placement demo, shipping something that *works today with zero cost* beats a
more "correct" architecture that takes weeks longer. Option A wins now. Option B is the
natural **v2 upgrade** once the demo is solid — and "I started front-end-only, then added
a Node backend to secure the key and store history" is itself a strong interview narrative.

Option C is rejected: cost and complexity are not justified while the product is turn-based.

---

## Consequences

**Easier:**
- Anyone can run it by opening one file — perfect for live demos.
- No hosting bill, no server uptime to babysit.
- The whole data flow fits on one screen — easy to explain in an interview.

**Harder / deferred:**
- No saved conversation history (would need Option B).
- Real cloned-voice output requires the paid ElevenLabs step.
- Putting it on the public web means each visitor needs their own key (or migrate to Option B).

**To revisit later:**
- Move to a backend (Option B) before any public, multi-user launch.
- Add proper consent/disclosure if it is ever used on live calls (legal requirement in many regions).

---

## Action Items

1. [x] Front-end app with Speak + Type input
2. [x] Gemini integration for improve + tone + translation (with LanguageTool fallback)
3. [x] Browser voice selection (fix robotic default)
4. [ ] Get Gemini API key and test smart features end-to-end
5. [ ] (Optional) Add ElevenLabs voice cloning, cache voice ID in `localStorage`
6. [ ] Deploy static file to the public web (Netlify / GitHub Pages / Vercel)
7. [ ] (v2) Add a small backend to secure a shared key and store history
