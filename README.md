<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Ayuk — GitHub Profile</title>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@300;400;600;700&family=Syne:wght@400;700;800&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --bg: #050a0f;
    --surface: #0d1117;
    --card: #111820;
    --border: #1e2d3d;
    --accent: #00d4ff;
    --accent2: #7c3aed;
    --accent3: #10b981;
    --text: #e2e8f0;
    --muted: #64748b;
  }

  body {
    background: var(--bg);
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    font-family: 'Syne', sans-serif;
    overflow: hidden;
  }

  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(0,212,255,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,212,255,0.03) 1px, transparent 1px);
    background-size: 40px 40px;
    animation: gridPulse 8s ease-in-out infinite;
  }

  @keyframes gridPulse {
    0%, 100% { opacity: 0.5; }
    50% { opacity: 1; }
  }

  .orb {
    position: fixed;
    border-radius: 50%;
    filter: blur(80px);
    animation: orbFloat 12s ease-in-out infinite;
    pointer-events: none;
  }
  .orb1 { width: 400px; height: 400px; background: rgba(0,212,255,0.06); top: -100px; left: -100px; }
  .orb2 { width: 300px; height: 300px; background: rgba(124,58,237,0.08); bottom: -80px; right: -80px; animation-delay: -6s; }

  @keyframes orbFloat {
    0%, 100% { transform: translate(0,0) scale(1); }
    50% { transform: translate(20px, 30px) scale(1.1); }
  }

  .card {
    position: relative;
    width: 520px;
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 20px;
    overflow: hidden;
    box-shadow: 0 0 0 1px rgba(0,212,255,0.05), 0 40px 80px rgba(0,0,0,0.6), inset 0 1px 0 rgba(255,255,255,0.05);
    animation: cardIn 0.8s cubic-bezier(0.16,1,0.3,1) forwards;
    opacity: 0;
    transform: translateY(30px);
  }

  @keyframes cardIn { to { opacity: 1; transform: translateY(0); } }

  .card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, transparent, var(--accent), var(--accent2), transparent);
    z-index: 10;
  }

  .banner {
    height: 120px;
    background: linear-gradient(135deg, #0a1628 0%, #0d1f3a 40%, #0a0f1a 100%);
    position: relative;
    overflow: hidden;
  }

  .banner-circuit {
    position: absolute;
    inset: 0;
    opacity: 0.4;
  }

  .banner-text {
    position: absolute;
    bottom: 16px;
    left: 160px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    color: var(--accent);
    letter-spacing: 2px;
    text-transform: uppercase;
    opacity: 0.7;
  }

  .banner::after {
    content: '';
    position: absolute;
    top: -100%;
    left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, transparent, rgba(0,212,255,0.4), transparent);
    animation: scan 4s linear infinite;
  }

  @keyframes scan { to { top: 200%; } }

  .avatar-wrap {
    position: absolute;
    top: 60px;
    left: 28px;
    z-index: 5;
  }

  .avatar-ring {
    width: 108px;
    height: 108px;
    border-radius: 50%;
    padding: 3px;
    background: linear-gradient(135deg, var(--accent), var(--accent2));
    box-shadow: 0 0 30px rgba(0,212,255,0.3), 0 0 60px rgba(124,58,237,0.2);
    animation: ringPulse 3s ease-in-out infinite;
  }

  @keyframes ringPulse {
    0%, 100% { box-shadow: 0 0 30px rgba(0,212,255,0.3), 0 0 60px rgba(124,58,237,0.2); }
    50% { box-shadow: 0 0 40px rgba(0,212,255,0.5), 0 0 80px rgba(124,58,237,0.35); }
  }

  .avatar-inner {
    width: 100%;
    height: 100%;
    border-radius: 50%;
    overflow: hidden;
    background: var(--card);
    border: 2px solid var(--bg);
  }

  .avatar-inner img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    object-position: top center;
    filter: brightness(1.05) contrast(1.05);
    transition: transform 0.4s ease;
  }

  .avatar-inner img:hover { transform: scale(1.05); }

  .status-dot {
    position: absolute;
    bottom: 6px; right: 6px;
    width: 18px; height: 18px;
    border-radius: 50%;
    background: var(--accent3);
    border: 3px solid var(--card);
    box-shadow: 0 0 10px rgba(16,185,129,0.6);
    animation: blink 2s ease-in-out infinite;
  }

  @keyframes blink {
    0%, 100% { opacity: 1; }
    50% { opacity: 0.5; }
  }

  .body {
    padding: 20px 28px 28px;
    margin-top: 52px;
  }

  .name { font-size: 26px; font-weight: 800; color: var(--text); letter-spacing: -0.5px; line-height: 1; }
  .handle { font-family: 'JetBrains Mono', monospace; font-size: 13px; color: var(--accent); margin-top: 3px; letter-spacing: 0.5px; }

  .title-tag {
    display: inline-flex; align-items: center; gap: 6px; margin-top: 10px;
    padding: 4px 12px;
    background: rgba(0,212,255,0.08); border: 1px solid rgba(0,212,255,0.2);
    border-radius: 100px;
    font-family: 'JetBrains Mono', monospace; font-size: 11px; color: var(--accent); letter-spacing: 1px;
  }
  .title-tag .dot { width: 6px; height: 6px; border-radius: 50%; background: var(--accent); }

  .bio { margin-top: 14px; font-size: 13.5px; color: var(--muted); line-height: 1.6; font-family: 'JetBrains Mono', monospace; font-weight: 300; }
  .bio span { color: var(--accent3); }
  .bio .hi { color: var(--text); font-weight: 600; }

  .divider { margin: 20px 0; height: 1px; background: linear-gradient(90deg, var(--border), transparent); }

  .section-label { font-family: 'JetBrains Mono', monospace; font-size: 10px; color: var(--muted); letter-spacing: 2px; text-transform: uppercase; margin-bottom: 10px; }

  .tags { display: flex; flex-wrap: wrap; gap: 6px; }

  .tag {
    padding: 4px 10px; border-radius: 6px;
    font-family: 'JetBrains Mono', monospace; font-size: 11px; font-weight: 600; letter-spacing: 0.5px;
    border: 1px solid; transition: transform 0.2s, box-shadow 0.2s; cursor: default;
  }
  .tag:hover { transform: translateY(-2px); box-shadow: 0 4px 12px rgba(0,0,0,0.3); }
  .tag.py { background: rgba(59,130,246,0.1); border-color: rgba(59,130,246,0.3); color: #60a5fa; }
  .tag.ai { background: rgba(124,58,237,0.1); border-color: rgba(124,58,237,0.3); color: #a78bfa; }
  .tag.js { background: rgba(234,179,8,0.1); border-color: rgba(234,179,8,0.3); color: #fbbf24; }
  .tag.iot { background: rgba(16,185,129,0.1); border-color: rgba(16,185,129,0.3); color: #34d399; }
  .tag.web { background: rgba(239,68,68,0.1); border-color: rgba(239,68,68,0.3); color: #f87171; }
  .tag.cy { background: rgba(0,212,255,0.1); border-color: rgba(0,212,255,0.3); color: var(--accent); }

  .stats { display: grid; grid-template-columns: repeat(3, 1fr); gap: 12px; margin-top: 20px; }
  .stat-box {
    background: rgba(255,255,255,0.02); border: 1px solid var(--border); border-radius: 10px;
    padding: 12px; text-align: center; transition: border-color 0.2s, background 0.2s;
  }
  .stat-box:hover { border-color: rgba(0,212,255,0.3); background: rgba(0,212,255,0.04); }
  .stat-num { font-size: 20px; font-weight: 800; color: var(--text); line-height: 1; }
  .stat-num span { font-size: 12px; color: var(--accent); }
  .stat-lbl { font-family: 'JetBrains Mono', monospace; font-size: 9px; color: var(--muted); letter-spacing: 1.5px; text-transform: uppercase; margin-top: 4px; }

  .footer { display: flex; justify-content: space-between; align-items: center; margin-top: 20px; padding-top: 16px; border-top: 1px solid var(--border); }
  .location { font-family: 'JetBrains Mono', monospace; font-size: 11px; color: var(--muted); display: flex; align-items: center; gap: 6px; }
  .nexustem-badge {
    display: inline-flex; align-items: center; gap: 6px; padding: 5px 12px;
    background: linear-gradient(135deg, rgba(124,58,237,0.15), rgba(0,212,255,0.1));
    border: 1px solid rgba(124,58,237,0.3); border-radius: 100px;
    font-size: 11px; font-weight: 700; color: #c4b5fd; letter-spacing: 0.5px;
  }

  .cursor { display: inline-block; width: 2px; height: 13px; background: var(--accent); margin-left: 2px; animation: cursorBlink 1s step-end infinite; vertical-align: middle; }
  @keyframes cursorBlink { 0%, 100% { opacity: 1; } 50% { opacity: 0; } }

  .corner { position: absolute; width: 20px; height: 20px; border-color: rgba(0,212,255,0.3); border-style: solid; }
  .corner-tl { top: 8px; left: 8px; border-width: 1px 0 0 1px; }
  .corner-tr { top: 8px; right: 8px; border-width: 1px 1px 0 0; }
  .corner-bl { bottom: 8px; left: 8px; border-width: 0 0 1px 1px; }
  .corner-br { bottom: 8px; right: 8px; border-width: 0 1px 1px 0; }
</style>
</head>
<body>
  <div class="orb orb1"></div>
  <div class="orb orb2"></div>

  <div class="card">
    <div class="corner corner-tl"></div>
    <div class="corner corner-tr"></div>
    <div class="corner corner-bl"></div>
    <div class="corner corner-br"></div>

    <div class="banner">
      <svg class="banner-circuit" viewBox="0 0 520 120" xmlns="http://www.w3.org/2000/svg">
        <g stroke="#00d4ff" stroke-width="0.5" fill="none" opacity="0.6">
          <polyline points="160,20 200,20 200,40 280,40"/>
          <polyline points="280,40 320,40 320,20 400,20"/>
          <circle cx="200" cy="20" r="3" fill="#00d4ff" opacity="0.5"/>
          <circle cx="320" cy="40" r="3" fill="#00d4ff" opacity="0.5"/>
          <polyline points="180,80 220,80 220,60 300,60 300,80 380,80"/>
          <circle cx="220" cy="80" r="2.5" fill="#7c3aed" opacity="0.6"/>
          <circle cx="300" cy="60" r="2.5" fill="#7c3aed" opacity="0.6"/>
          <polyline points="400,20 440,20 440,60 480,60"/>
          <polyline points="160,60 170,60 170,100"/>
          <rect x="175" y="88" width="10" height="14" stroke="#00d4ff" opacity="0.4"/>
          <rect x="250" y="10" width="14" height="10" stroke="#7c3aed" opacity="0.4"/>
          <circle cx="380" cy="80" r="4" fill="none" stroke="#10b981" opacity="0.5"/>
          <polyline points="380,76 380,20 430,20"/>
        </g>
        <g fill="#00d4ff" opacity="0.8"><circle cx="400" cy="20" r="3"/><circle cx="480" cy="60" r="3"/></g>
        <g fill="#10b981" opacity="0.8"><circle cx="380" cy="80" r="2"/></g>
      </svg>
      <div class="banner-text">// nexustem_initiative.ng</div>
    </div>

    <div class="avatar-wrap">
      <div class="avatar-ring">
        <div class="avatar-inner">
          <img src="data:image/jpeg;base64,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" alt="Ayuk" />
        </div>
      </div>
      <div class="status-dot"></div>
    </div>

    <div class="body">
      <div class="name">Ayuk</div>
      <div class="handle">@ayuk · NexuSTEM</div>

      <div><span class="title-tag"><span class="dot"></span>Software & AI Engineer</span></div>

      <p class="bio">
        <span class="hi">Building</span> the future of <span>STEM education</span> in Africa.<br>
        Python · FastAPI · LLMs · Robotics · EdTech<span class="cursor"></span>
      </p>

      <div class="divider"></div>

      <div class="section-label">// tech stack</div>
      <div class="tags">
        <span class="tag py">Python</span>
        <span class="tag ai">AI / LLMs</span>
        <span class="tag js">FastAPI</span>
        <span class="tag iot">Robotics</span>
        <span class="tag web">Docker</span>
        <span class="tag cy">Web3</span>
        <span class="tag ai">ML / Data</span>
        <span class="tag iot">Electronics</span>
      </div>

      <div class="stats">
        <div class="stat-box"><div class="stat-num">7<span>+</span></div><div class="stat-lbl">Team Size</div></div>
        <div class="stat-box"><div class="stat-num">∞</div><div class="stat-lbl">Students</div></div>
        <div class="stat-box"><div class="stat-num">26<span>'</span></div><div class="stat-lbl">Launch</div></div>
      </div>

      <div class="footer">
        <div class="location">
          <svg width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" color="#10b981"><path d="M12 2C8.13 2 5 5.13 5 9c0 5.25 7 13 7 13s7-7.75 7-13c0-3.87-3.13-7-7-7z"/><circle cx="12" cy="9" r="2.5"/></svg>
          Abuja, Nigeria
        </div>
        <div class="nexustem-badge">⚡ NexuSTEM Initiative</div>
      </div>
    </div>
  </div>
</body>
</html>

<div align="center">

<!-- Animated Banner -->
<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0:00b4d8,100:0077b6&height=200&section=header&text=AYUK&fontSize=80&fontColor=ffffff&animation=fadeIn&fontAlignY=38&desc=Full-Stack%20AI%20Engineer%20%7C%20STEM%20Innovator%20%7C%20Builder&descAlignY=60&descAlign=50" />

<!-- Typing Animation -->
<img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&weight=600&size=28&duration=3000&pause=1000&color=00B4D8&center=true&vCenter=true&width=700&lines=🚀+Building+AI-Powered+Products;🤖+Full-Stack+Engineer+%7C+Python+%2B+React;🌍+Founder+of+NexuSTEM+Initiative;💡+Shipping+Real+Solutions+with+AI;⚡+Code.+Build.+Impact." alt="Typing SVG" />

<br/>

<!-- Profile Views + Followers -->
![Profile Views](https://komarev.com/ghpvc/?username=IFVERSE&color=00b4d8&style=for-the-badge&label=PROFILE+VIEWS)
![GitHub followers](https://img.shields.io/github/followers/IFVERSE?style=for-the-badge&color=00b4d8&labelColor=0d1117)

</div>

---

<img align="right" width="380" src="https://media.giphy.com/media/qgQUggAC3Pfv687qPC/giphy.gif" alt="coding gif"/>

## 👨🏾‍💻 Who Am I?

```python
class Ayuk:
    name       = "Ayuk"
    location   = "Abuja, Nigeria 🇳🇬"
    role       = "Full-Stack AI Engineer"
    mission    = "Build AI tools that solve real problems"

    tech = {
        "backend"  : ["Python", "FastAPI", "Flask"],
        "frontend" : ["React", "Vite", "TailwindCSS"],
        "AI/ML"    : ["Groq", "LLaMA", "LLM APIs"],
        "database" : ["SQLite", "PostgreSQL"],
        "tools"    : ["Docker", "Git", "GitHub"]
    }

    currently_building = [
        "🔍 AI Log Analyzer",
        "🏫 NexuSTEM Initiative",
        "🤖 AI Automation Tools"
    ]

    fun_fact = "I turned 3 days into a full AI product 🚀"
```

<br clear="right"/>

---

## 🧠 About Me

<table>
<tr>
<td>

🔭 **Building** AI-powered full-stack products with Python & React

🏫 **Founder** of [NexuSTEM Initiative](https://github.com/IFVERSE) — bringing hands-on STEM education (Coding, Robotics, AI) to secondary school students in Nigeria

🤖 **Obsessed** with integrating LLMs into real, working software

⚡ **Philosophy:** Ship fast · Solve real problems · Use AI every day

🌍 **Goal:** Build products that impact lives across Africa and beyond

📫 **Contact:** nicholasayuk1@gmail.com

</td>
<td>


</td>
</tr>
</table>

---

## 🛠️ Tech Stack & Tools

<div align="center">

### 💻 Languages
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)

### ⚙️ Backend & AI
![FastAPI](https://img.shields.io/badge/FastAPI-005571?style=for-the-badge&logo=fastapi)
![Flask](https://img.shields.io/badge/Flask-000000?style=for-the-badge&logo=flask&logoColor=white)
![Groq](https://img.shields.io/badge/Groq_AI-FF6B35?style=for-the-badge&logo=artificial-intelligence&logoColor=white)
![LLaMA](https://img.shields.io/badge/LLaMA_3.3-0467DF?style=for-the-badge&logo=meta&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-07405E?style=for-the-badge&logo=sqlite&logoColor=white)

### 🎨 Frontend
![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=for-the-badge&logo=vite&logoColor=white)
![TailwindCSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)

### 🔧 Tools & Platforms
![Git](https://img.shields.io/badge/GIT-E44C30?style=for-the-badge&logo=git&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2CA5E0?style=for-the-badge&logo=docker&logoColor=white)
![VS Code](https://img.shields.io/badge/VS_Code-0078D4?style=for-the-badge&logo=visual%20studio%20code&logoColor=white)
![Render](https://img.shields.io/badge/Render-46E3B7?style=for-the-badge&logo=render&logoColor=white)
![Vercel](https://img.shields.io/badge/Vercel-000000?style=for-the-badge&logo=vercel&logoColor=white)

</div>

---

## 🔥 Featured Projects

<div align="center">

<a href="https://github.com/IFVERSE/ai-log-analyzer">
  <img src="https://github-readme-stats.vercel.app/api/pin/?username=IFVERSE&repo=ai-log-analyzer&theme=tokyonight&hide_border=true&border_radius=15" />
</a>

</div>

<br/>

### 🔍 AI Log Analyzer

## 🎬 Watch the Demo

[![AI Log Analyzer Demo](https://img.youtube.com/vi/EHXsmp-HYQU/maxresdefault.jpg)](https://www.youtube.com/watch?v=EHXsmp-HYQU)

> 📺 Click the image above to watch the full demo on YouTube
> **The problem:** Developers waste hours reading long, confusing log files when software crashes.
> **The solution:** Upload any log file → AI reads it → Get root cause, errors, and fixes in 30 seconds.

| Feature | Description |
|---|---|
| 🤖 AI Analysis | Powered by Groq LLaMA 3.3 — fastest open-source AI |
| 🔴 Error Classification | Critical, Warning, Info — color coded |
| 🔍 Root Cause Detection | AI identifies the exact reason things broke |
| ✅ Fix Recommendations | Specific, actionable steps to resolve issues |
| 💬 Chat Interface | Ask follow-up questions about your logs |
| 📋 History | All past analyses saved and accessible |

**Stack:** `React` `FastAPI` `Groq AI` `LLaMA 3.3` `SQLite` `Tailwind CSS` `Python`

---

## 🏫 NexuSTEM Initiative

> **Bringing hands-on STEM education to the next generation in Nigeria**


---

## 📊 GitHub Stats

<div align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=IFVERSE&show_icons=true&theme=tokyonight&hide_border=true&border_radius=15&include_all_commits=true&count_private=true" width="49%" />
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=IFVERSE&layout=compact&theme=tokyonight&hide_border=true&border_radius=15" width="49%" />
</div>

<div align="center">
  <img src="https://github-readme-streak-stats.herokuapp.com/?user=IFVERSE&theme=tokyonight&hide_border=true&border_radius=15" width="70%" />
</div>

---

## 🏆 GitHub Trophies

<div align="center">
  <img src="https://github-profile-trophy.vercel.app/?username=IFVERSE&theme=tokyonight&no-frame=true&no-bg=true&margin-w=4&row=1" />
</div>

---

## 🌐 Connect With Me

<div align="center">

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/ayuk-nicholas)
[![Twitter](https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white)](https://x.com/africandevplug)
[![Gmail](https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:nicholasayuk1@gmail.com)
[![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/IFVERSE)

</div>

---

<div align="center">

<!-- Snake Animation -->
<img src="https://raw.githubusercontent.com/platane/snk/output/github-contribution-grid-snake-dark.svg" alt="Snake animation" />

<br/>

<!-- Footer Wave -->
<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0:0077b6,100:00b4d8&height=120&section=footer"/>

</div>
