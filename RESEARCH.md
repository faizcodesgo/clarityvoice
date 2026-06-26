# ClarityVoice — Technology & Risk Research (2026)

> Method: multi-agent web research with adversarial fact-checking (claims confirmed only
> if they survived a 3-vote verification). Some search angles failed mid-run, so sections
> are marked **[Verified]** (survived fact-check with citations) or
> **[Unverified — author's knowledge]** (gap the research did not cover; confirm before relying on it).

---

## 1. Speech-to-Text (how the app hears you) — [Verified]

- **Browser Web Speech API is the right starting point for a beginner.** It handles mic
  capture, chunking and streaming for you — no API keys, no upload pipeline. *(confidence: medium, 2-1)*
- **But it is NOT on-device.** In Chrome it sends your audio to Google's servers to transcribe
  (an opt-in local mode exists since Chrome 139 but is off by default). So your voice *does*
  leave the device — relevant to the privacy section below. *(high, 3-0)*
- **Browser support is uneven:** full in Chrome/Edge/Opera; partial in Safari (macOS 14.1+,
  iOS 14.5+) via the `webkitSpeechRecognition` prefix; off-by-default in Firefox. *(high, 3-0)*
- **Accuracy is limited** vs paid services: struggles with noise, accents, and technical words;
  no custom vocabulary; no uptime guarantee. Fine for a prototype, weak for production. *(high, 3-0)*
- **Affordable cloud STT (if you outgrow the browser):** Google Cloud Speech-to-Text
  (60 free min/month, 125+ languages), Deepgram (free credits, no card), Rev AI (5 free hours).
  ⚠️ Every specific per-minute price and latency number found online was *refuted* — check the
  provider's live pricing page before trusting any figure. *(high, 3-0)*

**Takeaway for us:** our current choice (browser Web Speech API) matches the recommended beginner path. ✅

---

## 2. LLM for grammar / professionalism / translation — [Unverified — author's knowledge]

The research could not verify this section. Based on general knowledge:
- **Google Gemini (`gemini-2.0-flash` / `2.5-flash`)** — generous free tier, no card needed,
  one API does grammar + tone + translation. **This is what we're using.** ✅
- Alternatives: OpenAI (paid), Anthropic Claude (paid), Groq (fast, free tier), local models (heavy).
- For a student, Gemini's free tier is the most beginner-friendly choice.

---

## 3. Text-to-Speech & Voice Cloning — [Unverified — author's knowledge]

The research could not verify this section. Based on general knowledge:
- **Free:** Browser `SpeechSynthesis` (what we use now) — natural-ish preset voices, ₹0.
- **Cloned (your real voice):** ElevenLabs is the leading instant-cloning service (~$5/mo).
  Persist a cloned voice by storing its **voice ID** in the browser (`localStorage`) — the
  voice itself lives on the provider's servers; you only remember the ID.
- ⚠️ **Legal caveat:** persisting a cloned voice profile likely counts as **biometric data** —
  see section 5.

---

## 4. Latency & Mobile Limits — [Partly verified]

- Specific millisecond latency claims were all **refuted** — don't quote benchmark numbers.
- **iOS is the real limit:** Apple does not let web/3rd-party apps sit invisibly between you and
  the system phone app. A browser app works in-page, but cannot intercept live phone-call audio.
- **Practical design choice:** keep ClarityVoice **turn-based** (speak → improve → hear), not
  live-during-a-call. This sidesteps the hardest latency problems entirely.

---

## 5. Privacy & Legal — [Verified] ⚠️ Most important section

- **Recordings are personal data under GDPR.** You need a lawful basis; consent must be freely
  given, specific, informed, and unambiguous (pre-ticked boxes / silence don't count). *(high, 3-0)*
- **Fines reach €20M or 4% of global turnover.** *(high, 3-0)*
- **Using any cloud STT/TTS makes YOU the "data controller"** — legally responsible, and you're
  supposed to have a Data Processing Agreement (DPA) with the provider. *(high, 3-0)*
- **Voice cloning is the biggest legal trigger.** The moment you process voice to identify a
  person (voiceprints/embeddings), it becomes **special-category biometric data** (GDPR Art. 9;
  Illinois BIPA requires *written* consent + a published retention schedule). *(high, 3-0)*
- **US call recording:** federal ECPA is one-party-consent; some states (e.g. California CIPA)
  require *all-party* consent and violations can be a felony. *(high, 3-0)*

**Takeaway for us:** for a turn-based demo where *you* speak in *your own* voice, risk is low.
Risk rises sharply if you (a) deploy publicly, (b) record *other people* on live calls, or
(c) store cloned voices. **Action: add a short privacy note in the app** ("your audio is sent to
Google/Gemini for processing; nothing is stored by us") before any public launch. This is
educational info, not legal advice.

---

## 6. Honest gaps

The fact-checked research fully covered **speech-to-text** and **legal/privacy**. It did **not**
verify TTS/voice-cloning, LLM API choices, or concrete latency/pricing numbers — those came from
general knowledge and should be confirmed against live provider pages before you rely on them.

*Key cited sources: MDN Web Speech API docs, caniuse.com, Google Cloud STT pricing, GDPR text
(gdpr-info.eu Art. 4/9/28/83), Illinois BIPA (740 ILCS 14), California Penal Code §632.*
