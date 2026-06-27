# New Laptop Setup — Master Prompt for Claude

Paste everything in the box below into Claude on the new laptop.

---

```
Hi Claude — I'm Faiz, a beginner Computer Science student setting up a brand-new
Windows laptop. Help me (1) install a full dev environment, (2) restore all my
projects, and (3) restore your memory of me. Run the commands yourself and explain
simply as you go. I'm on Windows — use winget to install things.

=== WHO I AM ===
- GitHub username: faizcodesgo
- I use a free Google account for Gemini API keys + Google Drive.
- Beginner — please run commands for me and keep it simple.

=== STEP 1: INSTALL MY DEV TOOLKIT (winget) ===
First check what's already installed, then install whatever is missing. If any winget
ID errors, run "winget search <name>" to find the right one.

CORE (must have):
- Git                 ->  winget install Git.Git
- VS Code             ->  winget install Microsoft.VisualStudioCode
- Python 3.12         ->  winget install Python.Python.3.12   (make sure it's on PATH)
- Node.js (LTS)       ->  winget install OpenJS.NodeJS.LTS
- Google Chrome       ->  winget install Google.Chrome
- Windows Terminal    ->  winget install Microsoft.WindowsTerminal
- 7-Zip               ->  winget install 7zip.7zip
- Google Drive        ->  winget install Google.GoogleDrive
- GitHub CLI          ->  winget install GitHub.cli

GOOD FOR A CS STUDENT (install these too):
- Java JDK 21         ->  winget install EclipseAdoptium.Temurin.21.JDK
- C/C++ (MinGW g++)   ->  winget install BrechtSanders.WinLibs.POSIX.UCRT.GCC   (find an alternative if this fails)
- PowerToys           ->  winget install Microsoft.PowerToys

After installing, verify: git --version, python --version, node --version, code --version.
Then in VS Code, install extensions: Python, Pylance, Prettier (and Live Server for web).

=== STEP 2: RESTORE MY PROJECTS (from GitHub) ===
Clone all 3 repos into my Desktop:
- ClarityVoice  (speech-improvement web app, single index.html + Colab voice notebooks)
    https://github.com/faizcodesgo/clarityvoice          -> Desktop\clarity-voice
- TriVi-attendance  (Node + Express + MongoDB, deployed on Render)
    https://github.com/faizcodesgo/trivi-attendance      -> Desktop\trivi-attendance
- AI-Assistant  (Python, Gemini "brain"; run start-brain.bat)
    https://github.com/faizcodesgo/-ai-assistant         -> Desktop\AI-Assistant
    (NOTE: the repo name has a LEADING DASH: -ai-assistant)

=== STEP 3: RESTORE PRIVATE FILES (not on GitHub) ===
I also have a backup file "FaizProjects-Backup.zip" (check Downloads and Desktop; ask me
if you can't find it). It holds files that are NOT on GitHub:
- a "claude-memory" folder (your memory of my projects)
- trivi-attendance .env  (MongoDB password + keys) — keep PRIVATE; put it in Desktop\trivi-attendance\.env
- gemini_key.txt  (optional; I can also just re-enter the key)
If the zip exists, extract it and restore these. If not, that's fine — I'll re-enter keys
and recreate .env from Render.

=== STEP 4: RESTORE YOUR MEMORY OF ME ===
Copy everything from the backup's "claude-memory" folder into your Claude memory directory
for this Desktop (create the folder if it doesn't exist). Then READ MEMORY.md so you know
all my projects, history, and plans.

=== STEP 5: REMEMBER MY LOTTERY PROJECT DECISION (save this as a memory) ===
Save a memory note titled "Lottery project decision":
"The original idea (users pay a small fee, one winner wins an asset by chance) is an
ILLEGAL private lottery in India (Lotteries Regulation Act 1998 + Public Gambling Act
1867). DO NOT build it as-is. The viable, legal, fundable version = a BRAND-SPONSORED,
SKILL-BASED 'win aspirational things' engagement platform: brands fund the prizes as
marketing (kills under-subscription risk), users enter free or via a small skill-
competition fee, with audited provably-fair draws + regulated escrow + KYC'd public
winners. Revenue = B2B (brands pay for engagement + first-party data) — legal, not
gambling. Model to study: BOTB (UK, listed). Best capital-light pivots: 1) group-buying,
2) skill competitions, 3) prize-linked savings, 4) fractional ownership. Non-negotiables
before any launch: written legal opinion (skill vs chance), regulated escrow, audited
fair draws, and a guaranteed-draw/refund rule if under-subscribed. Status: NOT started."

=== STEP 6: KEYS & LOGINS TO RESTORE ===
Remind me to:
- Get my free Gemini key at https://aistudio.google.com/apikey, then: paste it into
  ClarityVoice's in-app Settings, and let AI-Assistant prompt me for it on first run.
- Sign into Google Drive for Desktop (my voice recordings are in a Drive folder
  called "clarityvoice-voice").
- Log into Render (TriVi's live deploy + secrets) and GitHub.
I did NOT store keys in any repo on purpose — don't put keys into code.

=== STEP 7: VERIFY EACH PROJECT ===
- ClarityVoice: open index.html in Chrome and confirm it loads.
- AI-Assistant: install any Python packages it needs, run start-brain.bat (or
  python brain_assistant.py); it should ask me for my Gemini key.
- TriVi-attendance: run npm install; tell me how to start it locally; remind me it's
  already live on Render.

=== MY NEXT GOAL ===
After setup, I want to keep building AI-Assistant in layers (more actions -> memory ->
voice, eventually using my ClarityVoice voice clone). The roadmap is in my restored
memory — read it and help me continue.

Start by checking what's already installed.
```
