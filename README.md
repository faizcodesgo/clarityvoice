<h1 align="center">🎙️ ClarityVoice</h1>

<p align="center">
  <strong>Speak naturally. Sound professional.</strong><br>
  An AI communication aid that rewrites your speech or text in real time — fixing grammar,
  refining tone, and translating across languages, while keeping your meaning and intent intact.
</p>

<p align="center">
  <a href="https://faizcodesgo.github.io/clarityvoice/"><strong>🌐 Live Demo »</strong></a>
</p>

---

## ✨ What it does

You say or type something imperfect — ClarityVoice gives you back a clear, professional version, and can speak it out loud or translate it.

> **You:** "Hello sir I send report tomorrow."
> **ClarityVoice:** "Hello sir, I'll send the report tomorrow."

### Features
- 🎤 **Speak or type** — two input modes
- 🧠 **Smart rewriting** — fixes grammar and makes speech sound professional (powered by Google Gemini)
- 🎭 **Tone control** — Professional, Friendly, Concise, or Confident
- 🌍 **Translation** — Hindi, Spanish, French, German, Arabic, Japanese, Chinese
- 🔊 **Read aloud** — hears the improved version in a natural voice
- 🔒 **Private by design** — your API key stays in your browser, never in the code

---

## 🧠 How it works

```
🎤 Voice  ─┐
           ├─►  Speech-to-Text (browser)  ─►  Gemini AI  ─►  Improved text (+ translation)  ─►  Text-to-Speech  ─►  🔊
⌨️ Text  ─┘                                  (grammar, tone, translate)
```

It's a single-page app with **no backend** — it calls the AI directly from the browser, so it's free to host and instant to run.

---

## 🛠️ Tech stack

| Layer | Tech |
|-------|------|
| Speech-to-text | Web Speech API (browser) |
| AI rewriting / translation | Google Gemini (`gemini-2.0-flash`) |
| Grammar fallback (no key) | LanguageTool API |
| Text-to-speech | Web Speech Synthesis |
| UI | Vanilla HTML/CSS/JS · Space Grotesk + Inter |
| Hosting | GitHub Pages |

---

## 🚀 Run it yourself

1. Clone the repo and open `index.html` in **Google Chrome** (or Edge for the most natural voices).
2. Get a **free** Google Gemini API key at [aistudio.google.com/apikey](https://aistudio.google.com/apikey).
3. Click **Settings** in the app, paste the key, and **Save**. (It's stored only in your browser.)
4. Type or speak — and click **Improve**.

> Note: the microphone needs a real web address (`https://`), so use the [live site](https://faizcodesgo.github.io/clarityvoice/) for voice input.

---

## 🗺️ Roadmap

- [x] Smart AI rewriting + tone control
- [x] Live translation
- [x] Deployed live on the web
- [ ] **Voice cloning** — output in the user's own voice
- [ ] **AI assistant integration** — attend meetings, understand spoken commands, and reply in the user's voice with their personality

---

## 📚 Project docs

- [`ARCHITECTURE.md`](ARCHITECTURE.md) — design decisions & trade-offs (ADR)
- [`RESEARCH.md`](RESEARCH.md) — fact-checked research on the tech stack, latency, and privacy/legal
- [`voice-clone-chatterbox.ipynb`](voice-clone-chatterbox.ipynb) — **voice cloning with emotion + pacing** (Chatterbox, free Colab) ⭐ primary
- [`voice-clone-colab.ipynb`](voice-clone-colab.ipynb) — older voice-cloning notebook (XTTS-v2) — fallback for languages Chatterbox lacks

---

## 👤 Author

**Faiz Ahmed** · [github.com/faizcodesgo](https://github.com/faizcodesgo)

<sub>Built as a learning project exploring real-time AI communication.</sub>
