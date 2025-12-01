
# 🚀 Claude Code + Gemini Full Setup Guide (Windows)

Ye guide aapko step-by-step Windows par **Claude-Code** aur **Google Gemini models** ko setup karne mein madad degi.  
Isme Node.js check karna, required tools install karna, config files banana, API key set karna aur daily workflow shamil hai.

---

## 🔥 Step 0 — Node.js Installation Check

Sabse pehle apne system mein Node.js install hai ya nahi, aur version 18 ya usse upar hai ya nahi, ye check karein:

PowerShell ya Command Prompt kholen aur ye command chalayein:

```bash
node --version

Agar version 18 ya usse zyada nahi dikh raha, to official website se latest version install kar lein:

👉 https://nodejs.org


---

🔥 Step 1 — Google API Key Le Kar Aana

Claude-Code mein Gemini model chalane ke liye Google API key chahiye hoti hai. Isko lene ke liye:

1. Browser mein jaake https://aistudio.google.com kholen


2. Wahan Get API Key ya Create API Key par click karein


3. Jo API Key mile, usko copy kar lein (ye kuch is tarah dikhega: AIzaSy...)




---

🔥 Step 2 — Required Tools Install Karna

Ab PowerShell ko Administrator mode mein open kar ke ye command chalayein:

npm install -g @anthropic-ai/claude-code @musistudio/claude-code-router

Ye dono tools global install ho jayenge jo Claude-Code aur Router ke liye zaruri hain.


---

🔥 Step 3 — Configuration Folders Banana

PowerShell normal mode mein ye commands chalayein taake config folders ban jayein:

mkdir $HOME\.claude-code-router
mkdir $HOME\.claude


---

🔥 Step 4 — Config File Banayein (config.json)

Windows mein cat << EOF command work nahi karta, is liye Notepad se config file banana hota hai.

PowerShell mein ye command chalayein:

notepad $HOME\.claude-code-router\config.json

Notepad khulega, usmein niche wala JSON bilkul waise hi paste karein:

{
  "LOG": true,
  "LOG_LEVEL": "info",
  "HOST": "127.0.0.1",
  "PORT": 3456,
  "API_TIMEOUT_MS": 600000,
  "Providers": [
    {
      "name": "gemini",
      "api_base_url": "https://generativelanguage.googleapis.com/v1beta/models/",
      "api_key": "$GOOGLE_API_KEY",
      "models": [
        "gemini-2.5-flash",
        "gemini-2.0-flash"
      ],
      "transformer": {
        "use": ["gemini"]
      }
    }
  ],
  "Router": {
    "default": "gemini,gemini-2.5-flash",
    "background": "gemini,gemini-2.5-flash",
    "think": "gemini,gemini-2.5-flash",
    "longContext": "gemini,gemini-2.5-flash",
    "longContextThreshold": 60000
  }
}

Phir file ko Save kar ke band kar dein.


---

🔥 Step 5 — Apni Google API Key Set Karein (Windows Environment Variable)

PowerShell ko Admin mode mein open karein aur ye command chalayein (apni key ke sath):

[System.Environment]::SetEnvironmentVariable('GOOGLE_API_KEY', 'YAHAN_APNI_API_KEY_DALEIN', 'User')

Misal ke taur par:

[System.Environment]::SetEnvironmentVariable('GOOGLE_API_KEY', 'AIzaSyXXXXX123456...', 'User')

⚠️ Important: PowerShell ko close kar dein aur naya PowerShell window kholen. Phir check karein ke key sahi set hui ya nahi:

echo $env:GOOGLE_API_KEY

Agar aapko apni key nazar aaye, to setup sahi hai.


---

🔥 Step 6 — Setup Verify Karein

Ab ye commands chalakar check kar lein:

claude --version
ccr version
echo $env:GOOGLE_API_KEY

Agar har command ka output mil jaye, to sab kuch theek se setup ho gaya hai.


---

🔥 Step 7 — Rozana Kaam Karne Ka Tareeqa (Daily Workflow)

Terminal 1:

Server start karne ke liye:

ccr start

Jab tak message na aaye:

✔ Service started successfully

Intezaar karein.

Terminal 2:

Apne project folder mein jaakar code ke sath interact karne ke liye:

cd your-project-folder
ccr code

Ya phir:

eval "$(ccr activate)"
claude


---

🔥 Step 8 — Verification Test

Terminal mein ye command chalayein:

ccr code

Phir type karein:

hi

Agar Claude se reply aa jaye, to mubarak ho! 🎉

Aapka Claude-Code + Gemini model Windows par successfully kaam kar raha hai! 🚀💯


---

Agar aapko koi masla aaye ya sawal ho, to issue raise karein ya discussion karein.

Happy Coding! 😊

---
