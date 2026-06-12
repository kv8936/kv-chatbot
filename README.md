# SCARP Usability Evaluation Questionnaire
## Deployment & Usage Guide

### What's in this package
```
index.html        ← The complete questionnaire (single file, no dependencies)
README.md         ← This guide
netlify.toml      ← Netlify config (optional, for custom headers)
```

---

### Before you go live — 2 things to update in index.html

Open `index.html` in any text editor (VS Code, Notepad++, etc.) and find:

**1. Chatbot link** (line ~130)
```html
<a href="#" class="chatbot-link-box" id="chatbot-link"
```
Replace `href="#"` with your actual SCARP chatbot URL:
```html
<a href="https://your-scarp-chatbot-url.com" class="chatbot-link-box" id="chatbot-link"
```

**2. Formspree endpoint** (already set to yours — no change needed)
```
https://formspree.io/f/mykadnqz  ✓ already configured
```

---

### Deploy to Netlify (recommended — free, 60 seconds)

**Option A: Drag & Drop**
1. Go to https://app.netlify.com/drop
2. Drag the entire `scarp-survey-package` folder onto the page
3. Done — you get a live URL instantly

**Option B: Netlify CLI**
```bash
npm install -g netlify-cli
netlify deploy --dir=scarp-survey-package --prod
```

---

### Deploy to GitHub Pages (alternative)

1. Create a new GitHub repository
2. Upload `index.html` to the root
3. Go to Settings → Pages → Source: main branch / root
4. Your URL: `https://yourusername.github.io/repo-name`

---

### Formspree — viewing responses

1. Log in at https://formspree.io
2. Open your form "Usability Evaluation Questionnaire..."
3. Click **Submissions** tab
4. Export as CSV for analysis in Excel / Python / SPSS

**Fields you'll receive per submission:**
- `language` — English or German
- `timestamp` — ISO 8601 datetime
- `q1` — Background
- `q2` — H&S experience
- `q3` — Prior chatbot use
- Likert statements (each named by full statement text, values 1–5)
- `q13_most_useful` — Open text (required)
- `q14_unclear` — Open text (optional)
- `q15_missing_info` — Open text (optional)
- `q16_improvement` — Open text (optional)
- `q17_rating` — Star rating 1–5

---

### Sharing with participants

Send participants this message (adapt as needed):

> "Please follow this link to complete a short usability questionnaire for my MSc dissertation.
> It takes approximately 5–8 minutes. The form is available in English and German.
> [INSERT YOUR NETLIFY URL HERE]"

---

### Troubleshooting

| Problem | Fix |
|---|---|
| Formspree not receiving submissions | Check your Formspree dashboard — you may need to confirm your email first |
| Form shows 50 submission limit warning | Upgrade Formspree to Gold (£8/mo) or use a new free account |
| Chatbot link not working | Make sure you updated `href="#"` to your real URL |
| Language not switching | Ensure JavaScript is enabled in the browser |

---

### Technical notes for dissertation write-up

- **Stack:** Pure HTML5, CSS3, vanilla JavaScript — no frameworks or build tools
- **External dependency:** Google Fonts CDN only (Inter + DM Serif Display)
- **Form backend:** Formspree (GDPR-compliant, data stored in EU region on paid plans)
- **Accessibility:** ARIA roles, keyboard navigation, screen reader labels on all inputs
- **Responsive:** Mobile-first, tested down to 320px viewport width
- **Privacy:** No cookies set, no tracking, language preference stored in localStorage only
