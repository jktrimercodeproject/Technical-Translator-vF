# TechTranslator

Understand any technical infrastructure concept in 60 seconds — designed for non-technical investors.

**GitHub:** https://github.com/jktrimercodeproject/techtranslator

## Setup

### 1. Get a Groq API Key

1. Go to [https://console.groq.com](https://console.groq.com)
2. Sign in or create a free account
3. Navigate to **API Keys** and click **Create API Key**
4. Copy the key

### 2. Clone the Repo

```bash
git clone https://github.com/jktrimercodeproject/techtranslator.git
cd techtranslator
```

### 3. Configure the App

1. Copy `config.example.js` to `config.js`:
   ```bash
   cp config.example.js config.js
   ```
2. Open `config.js` in a text editor
3. Replace `YOUR_GROQ_API_KEY_HERE` with your actual API key:
   ```js
   const GROQ_API_KEY = "gsk_...your-key-here...";
   ```

> ⚠️ `config.js` is in `.gitignore` and will never be committed. Never share or commit your real API key.

### 4. Start the Local Server

**If you have Node.js:**
```bash
node -e "const h=require('http'),fs=require('fs'),path=require('path'),m={'html':'text/html','js':'application/javascript'};h.createServer((q,r)=>{let f=path.join(process.cwd(),q.url==='/'?'index.html':q.url);fs.readFile(f,(e,d)=>{if(e){r.writeHead(404);r.end();return;}r.writeHead(200,{'Content-Type':m[path.extname(f).slice(1)]||'text/plain'});r.end(d);});}).listen(8000,()=>console.log('http://localhost:8000'));"
```

**If you have Python:**
```bash
python3 -m http.server 8000
```

Then open your browser to: **http://localhost:8000**

### 5. Use the App

- Type any technical concept or company name into the search bar (e.g. "What does Snowflake do?")
- Press Enter or click the arrow button
- Results appear with a diagram, vendor landscape, investor framework, diligence questions, and more
- Click any example chip below the search bar to try a pre-set query
- Use the **↻ Regenerate** button to bypass cache and get a fresh response

## What It Produces

Each query returns a full analyst brief including:

- **Simple Explanation** — plain English, no buzzwords, concrete facts
- **ELI12** — real-world metaphor for the non-technical reader
- **How It Works** — internal mechanics diagram (not a generic flowchart)
- **Analogies** — two concrete comparisons
- **Enterprise Context** — who buys it, what budget it comes from, what it replaces
- **End Users** — specific job titles and daily workflows
- **Historical Context** — how the problem was solved before this existed
- **Vendor Landscape** — direct competitors with estimated TAM, revenue, and market share
- **Software Market Analogy** — structural comparison to a well-understood market with investor framework (stickiness, platform trajectory, margin profile, consolidation risk)
- **Diligence Questions** — 3-5 structurally-grounded questions with why-it-matters and red flags
- **Adjacent Categories** — upstream and downstream tools with leading vendors
- **Video Explainers** — YouTube search links for further learning

## File Structure

```
techtranslator/
├── index.html          ← Main app (all CSS and JS embedded, no build tools)
├── config.js           ← Your API key (gitignored — create from example)
├── config.example.js   ← Committed template showing the format
├── .gitignore          ← Excludes config.js
└── README.md           ← This file
```

## Troubleshooting

| Issue | Fix |
|-------|-----|
| "API key not configured" | Make sure `config.js` exists and contains your real Groq key |
| 401 / 403 error | Your API key is invalid or has been revoked — generate a new one |
| 429 error | You've hit the Groq rate limit — wait a moment and try again |
| Blank page | Open browser dev tools (F12) → Console tab for error details |
| JSON parse error | Click **↻ Regenerate** — occasionally the model response needs a retry |

## Notes

- Powered by Groq (`llama-3.3-70b-versatile`) — responses typically arrive in 3-6 seconds
- Responses are cached in `localStorage` by query (up to 50 entries, auto-evicts oldest)
- YouTube links open search results — videos are not embedded
- Runs entirely in the browser — no backend, no dependencies, no build step required
