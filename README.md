# Character Concept Generator
### by RLBdesigns.com — Free public tool
**GitHub:** github.com/amomsRLB/character-concept-generator

## File Structure
```
character-concept-generator/
├── index.html              ← the app
└── functions/
    └── api/
        └── generate.js     ← Cloudflare Pages Function (Groq proxy)
```

## Deployment Steps

### 1. GitHub
- Repo already set up at: `github.com/amomsRLB/character-concept-generator`
- Upload files maintaining exact folder structure above
- Push to `main` branch

### 2. Cloudflare Pages
- dash.cloudflare.com → Pages → Create a project
- Connect to Git → select `character-concept-generator`
- Settings:
  - Framework preset: **None**
  - Build command: *(leave blank)*
  - Build output directory: `/`
- Click **Save and Deploy**

### 3. Add Groq API Key
- In your Cloudflare Pages project → **Settings → Environment Variables**
- Click **Add variable**
  - Variable name: `GROQ_API_KEY`
  - Value: your Groq key from console.groq.com
- Set for both **Production** and **Preview**
- Click **Save** then **Redeploy**

### 4. Get your Groq API Key
- Go to console.groq.com
- Sign in → API Keys → Create API Key
- Copy the key and paste into Cloudflare environment variable above

### 5. Custom Subdomain
- In Cloudflare Pages project → **Custom domains** → Add domain
- Enter: `characters.rlbdesigns.com`
- In **Namecheap DNS** → Advanced DNS → Add new record:
  - Type: `CNAME`
  - Host: `characters`
  - Value: `your-project-name.pages.dev`
  - TTL: Automatic
- SSL certificate provisions automatically (5–10 min)

## Notes
- AI model: `llama-3.3-70b-versatile` (Groq) — fast, free tier generous
- Free tier: 14,400 requests/day on Groq, 100,000 requests/day on Cloudflare Pages Functions
- Your GROQ_API_KEY is never exposed to the browser — always server-side
- To update the app: edit index.html → push to GitHub → Cloudflare auto-deploys
