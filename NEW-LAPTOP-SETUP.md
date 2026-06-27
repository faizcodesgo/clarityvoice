# New Laptop Setup — Master Prompt for Claude

Paste everything in the box below into Claude on the new laptop.

---

```
Hi Claude — I'm Faiz, a beginner Computer Science student on a brand-new Windows laptop.
Help me (1) install a full dev environment, (2) restore all my projects + your memory,
and (3) understand what to do next on each project. Run the commands yourself, explain
simply, and use winget. I prefer you to do things for me.

=== WHO I AM ===
GitHub: faizcodesgo | Free Google account for Gemini keys + Drive | Beginner dev.

=== STEP 1: INSTALL MY DEV TOOLKIT (check what's installed first; if a winget ID errors, run "winget search <name>") ===
CORE:
  Git.Git | Microsoft.VisualStudioCode | Python.Python.3.12 (ensure Add-to-PATH) |
  OpenJS.NodeJS.LTS | Google.Chrome | Microsoft.WindowsTerminal | 7zip.7zip |
  Google.GoogleDrive | GitHub.cli
CS-STUDENT EXTRAS:
  EclipseAdoptium.Temurin.21.JDK (Java) | BrechtSanders.WinLibs.POSIX.UCRT.GCC (C/C++ g++) |
  Microsoft.PowerToys
Then verify: git --version, python --version, node --version, code --version.
In VS Code, install extensions: Python, Pylance, Prettier, Live Server.

=== STEP 2: CLONE MY PROJECTS (to Desktop) ===
- ClarityVoice:   https://github.com/faizcodesgo/clarityvoice      -> Desktop\clarity-voice
- TriVi:          https://github.com/faizcodesgo/trivi-attendance  -> Desktop\trivi-attendance
- AI-Assistant:   https://github.com/faizcodesgo/-ai-assistant     -> Desktop\AI-Assistant  (NOTE leading dash)

=== STEP 3: RESTORE PRIVATE FILES ===
I have "FaizProjects-Backup.zip" (check Downloads/Desktop; ask if not found). Extract and restore the
files NOT on GitHub: the "claude-memory" folder, the TriVi .env (-> Desktop\trivi-attendance\.env, keep
PRIVATE), and gemini_key.txt. If the zip is missing, I'll re-enter keys instead.

=== STEP 4: RESTORE YOUR MEMORY ===
Copy the "claude-memory" files into your Claude memory directory for this Desktop (create if missing),
then READ MEMORY.md so you know all my projects, history, and plans.

=== STEP 5: KEYS & LOGINS ===
Remind me to: get my free Gemini key (https://aistudio.google.com/apikey) and paste it into ClarityVoice
Settings + let AI-Assistant prompt me for it; sign into Google Drive (recordings in "clarityvoice-voice");
log into Render + GitHub. Never put keys in code.

=== PER-PROJECT GUIDE (current state, how to run, how to deploy, and WHAT'S NEXT) ===

1) CLARITYVOICE  (speech-improvement web app)
   - State: LIVE at https://faizcodesgo.github.io/clarityvoice  (single index.html, no backend).
   - Run locally: open index.html in Chrome -> open Settings -> paste my Gemini key.
   - Deploy/update: it's on GitHub Pages. To publish changes: git add/commit/push to main; site
     auto-updates in ~1 min. (No new folder needed.)
   - Voice cloning (separate, in Google Colab — free GPU): use voice-clone-chatterbox.ipynb in the repo.
   - WHAT'S NEXT: (a) finish a good voice clone in Colab from my recordings; (b) FINE-TUNE on ~15 min of
     my Indian-accent English to fix the American-accent drift; (c) LATER, put my cloned voice live in the
     app by adding a small backend (Chatterbox behind an API + tunnel) — a static page alone can't run the
     voice model.

2) AI-ASSISTANT  (Python assistant with a Gemini "brain")
   - State: Layer-1 brain built (brain_assistant.py); roadmap is in my memory.
   - Run: python brain_assistant.py  (or start-brain.bat). It asks for my Gemini key on first run.
   - Develop: it has "actions" the brain can call; add more actions in the Python file.
   - Deploy: runs locally for now (a CLI). No cloud deploy yet.
   - WHAT'S NEXT (build in LAYERS): (1) add more ACTIONS (open apps/files/web, etc.); (2) add persistent
     MEMORY so it remembers across runs; (3) add VOICE — speak replies using my ClarityVoice clone; long
     term it should attend meetings and reply in my voice/personality. Read the roadmap in memory and
     continue from where I left off.

3) TRIVI-ATTENDANCE  (Node + Express + MongoDB attendance app)
   - State: LIVE on Render.
   - Run locally: cd into the folder -> npm install -> create .env (MongoDB URI + any keys; it's in my
     backup zip) -> npm start (or whatever the start script is in package.json).
   - Deploy/update: push to GitHub main -> Render auto-deploys. Secrets live in the Render dashboard's
     Environment settings (NOT in the repo).
   - WHAT'S NEXT: continue feature work — ASK ME what's pending before changing anything.

4) LOTTERY  (NOT started — decision already made)
   - DO NOT build the original idea (users pay a fee, one winner wins an asset by chance) — that's an
     ILLEGAL private lottery in India (Lotteries Regulation Act 1998 + Public Gambling Act 1867).
   - Build instead: a BRAND-SPONSORED, SKILL-BASED "win aspirational things" platform — brands fund the
     prizes as marketing; users enter free or via a small skill-competition fee; audited provably-fair
     draws + regulated escrow + KYC'd public winners; revenue is B2B (brands pay for engagement + data).
     Legal, fundable, not gambling. Model to study: BOTB (UK). Capital-light pivots: group-buying, skill
     competitions, prize-linked savings, fractional ownership.
   - WHEN I START IT, the path is: (1) get a written legal opinion (skill vs chance); (2) make a new
     project folder; (3) stack = Next.js + Node/NestJS + PostgreSQL/Redis + Razorpay with ESCROW + KYC
     (Digio/Hyperverge); (4) build the hard 80% first = escrow + KYC + legal + provably-fair draws (NOT
     the UI); (5) deploy (Vercel for frontend + a host for the backend). Non-negotiables before launch:
     legal opinion, regulated escrow, audited fair draws, guaranteed-draw/refund if under-subscribed.
   - Also SAVE this whole lottery decision as a memory note.

=== STEP 6: VERIFY EACH PROJECT RUNS ===
- ClarityVoice: opens in Chrome.
- AI-Assistant: runs and asks for my Gemini key.
- TriVi: npm install works; tell me how to start locally (it's already live on Render).

=== MY IMMEDIATE NEXT GOAL ===
Keep building AI-Assistant in layers (actions -> memory -> voice via my ClarityVoice clone). The roadmap
is in my restored memory — read it and help me continue.

Start by checking what's already installed.
```
