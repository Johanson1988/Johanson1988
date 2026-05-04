<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0d1117,50:161b22,100:1f6feb&height=200&section=header&text=Johann%20Moreno&fontSize=42&fontColor=f0f6fc&fontAlignY=35&desc=Frontend%20Engineer%20%C2%B7%20Building%20systems%20that%20ship&descSize=16&descColor=8b949e&descAlignY=55&animation=fadeIn" width="100%"/>

<div align="center">

```
Telegram message → AI agents discuss → repo created → deployed to K8s → app live
```

**I build frontends.** To ship more of them, I automated everything else.

</div>

---

### What I ship

I build user-facing applications — from productivity tools to games to data visualizations.  
Here's a sample of what's live:

<table>
<tr>
<td align="center" width="25%">

**🎯 Epic Planner**<br/>
<sub>Urban micro-planner for Barcelona. Pick a day, pick an area, get a legendary route with concerts, events & bars.</sub><br/>
<sub><code>React</code> <code>Maps API</code></sub><br/>
<a href="https://github.com/Johanson1988/epic-planner">repo</a> · <a href="https://github.com/Johanson1988/epic-planner-v2-react">v2</a>

</td>
<td align="center" width="25%">

**🤿 Dive Computer**<br/>
<sub>Nitrox calculator & dive computer niche app for scuba diving planning.</sub><br/>
<sub><code>TypeScript</code> <code>React</code></sub><br/>
<a href="https://github.com/Johanson1988/dive-computer-niche">repo</a>

</td>
<td align="center" width="25%">

**🧠 Mente Digital**<br/>
<sub>Custom Obsidian-like knowledge app with Telegram integration for capturing ideas on the go.</sub><br/>
<sub><code>TypeScript</code> <code>Telegram API</code></sub><br/>
<sub>private</sub>

</td>
<td align="center" width="25%">

**🃏 Envite Canario**<br/>
<sub>Online card game — the traditional Canarian "envite" with animations and multiplayer.</sub><br/>
<sub><code>TypeScript</code> <code>React</code></sub><br/>
<sub>private</sub>

</td>
</tr>
<tr>
<td align="center" width="25%">

**🏋️ Healthy Habits**<br/>
<sub>Micro-exercise routine app. Set reminders, track movement breaks throughout the day.</sub><br/>
<sub><code>TypeScript</code> <code>Remix</code></sub><br/>
<sub>private</sub>

</td>
<td align="center" width="25%">

**🛸 OVNI Tenerife**<br/>
<sub>UFO sightings map for Tenerife. Report and explore sightings on an interactive map.</sub><br/>
<sub><code>TypeScript</code> <code>Maps</code></sub><br/>
<sub>private</sub>

</td>
<td align="center" width="25%">

**🏠 Casas Canarias**<br/>
<sub>Showcase of traditional Canarian architecture with 3D models and historical data.</sub><br/>
<sub><code>TypeScript</code> <code>React</code></sub><br/>
<sub>private</sub>

</td>
<td align="center" width="25%">

**🍲 Recetas Mamá**<br/>
<sub>Family recipe manager — save, organize and share cooking links and notes.</sub><br/>
<sub><code>TypeScript</code> <code>React</code></sub><br/>
<sub>private</sub>

</td>
</tr>
</table>

<details>
<summary><b>+ more shipped apps</b></summary>
<br/>

| App | What it does |
|-----|-------------|
| **Silbo Training** | Learn and practice Silbo Gomero (whistled language of the Canary Islands) |
| **Mama Fit** | Exercise routines with tagging and tracking |
| **Gestión Tareas Hogar** | Household task management |
| **Inventario Comida** | Home food inventory tracker |
| **Inventario Ropa** | Wardrobe inventory manager |
| **Juego de las Sillas** | Musical chairs game for kids |
| **CD Tenerife Data** | Stats & historical data for Club Deportivo Tenerife |
| **Dalton Dive** | Nitrox/gas blending calculator for diving |
| **App de Bienestar** | Office wellness reminder — move, stretch, breathe |

</details>

<br/>

> **30+ TypeScript applications** shipped in the last year.  
> That output is not accidental — it's engineered.

---

### How I ship

I built an autonomous pipeline that takes an idea from a Telegram message to a running app in Kubernetes — no manual DevOps, no boilerplate, no context switching away from the frontend.

```mermaid
graph LR
    A["📱 Telegram"] -->|natural language| B["🌬️ Alisios"]
    B -->|creates GitHub issue| C["🤖 ForgeBot"]
    C -->|orchestrates| D["🧠 Agent Civilization"]
    D -->|specs + code| E["⚙️ R2D2"]
    E -->|repo + Docker + manifests| F["☸️ ArgoCD"]
    F -->|GitOps sync| G["🚀 Live App"]
    
    style A fill:#0d1117,stroke:#1f6feb,color:#f0f6fc
    style B fill:#0d1117,stroke:#1f6feb,color:#f0f6fc
    style C fill:#0d1117,stroke:#1f6feb,color:#f0f6fc
    style D fill:#0d1117,stroke:#1f6feb,color:#f0f6fc
    style E fill:#0d1117,stroke:#1f6feb,color:#f0f6fc
    style F fill:#0d1117,stroke:#1f6feb,color:#f0f6fc
    style G fill:#0d1117,stroke:#1f6feb,color:#f0f6fc
```

<table>
<tr>
<td width="50%">

#### 🌬️ Alisios

Telegram bot that bridges ideas to GitHub. Send a message describing what you want, and it creates a structured GitHub issue ready for agents to pick up.

`alisios-bot`

</td>
<td width="50%">

#### 🤖 ForgeBot + Agent Civilization

Multi-agent orchestration system. Agents with different roles (Product Owner, UX Designer, Functional Analyst, Senior Dev) discuss, debate, and converge on solutions — with persistent memory.

`forge-bot` · `forge-agents` · `forge-comms` · `forge-memory`

</td>
</tr>
<tr>
<td width="50%">

#### ⚙️ R2D2

DevOps agent that automates the entire deployment lifecycle: creates the GitHub repo, generates Dockerfile, builds K8s manifests, and registers the app in ArgoCD for continuous delivery.

`devops-agent-r2d2` · `devops-agent` · `infra-live`

</td>
<td width="50%">

#### 🏗️ Tajao Platform

The foundation everything runs on. A design system, a production-ready Remix starter, backend templates, and a database agent — all standardized so every app ships with consistent quality.

`tajao-design-system` · `remix-pod-starter` · `open-claw-generator` · `bbdd-agent`

</td>
</tr>
</table>

---

### Stack

<div align="center">

![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=black)
![Remix](https://img.shields.io/badge/Remix-000000?style=for-the-badge&logo=remix&logoColor=white)
![GraphQL](https://img.shields.io/badge/GraphQL-E10098?style=for-the-badge&logo=graphql&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)
![Styled Components](https://img.shields.io/badge/Styled_Components-DB7093?style=for-the-badge&logo=styledcomponents&logoColor=white)

![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)
![ArgoCD](https://img.shields.io/badge/Argo_CD-EF7B4D?style=for-the-badge&logo=argo&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white)
![Telegram Bot](https://img.shields.io/badge/Telegram_Bot-26A5E4?style=for-the-badge&logo=telegram&logoColor=white)

</div>

---

### Numbers

<div align="center">

<img src="https://github-readme-stats.vercel.app/api?username=Johanson1988&show_icons=true&theme=github_dark&hide_border=true&bg_color=0d1117&title_color=1f6feb&icon_color=1f6feb&text_color=8b949e&ring_color=1f6feb" height="170"/>
&nbsp;&nbsp;
<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=Johanson1988&layout=compact&theme=github_dark&hide_border=true&bg_color=0d1117&title_color=1f6feb&text_color=8b949e&langs_count=6" height="170"/>

<br/><br/>

<img src="https://github-readme-streak-stats.herokuapp.com/?user=Johanson1988&theme=github-dark-blue&hide_border=true&background=0d1117&ring=1f6feb&fire=1f6feb&currStreakLabel=1f6feb&sideLabels=8b949e&dates=8b949e" height="170"/>

</div>

---

<div align="center">

**163 repos** · **30+ apps shipped** · **1 human in the loop**

<sub>Based in the Canary Islands 🇮🇨 · Open to opportunities in Barcelona & Madrid</sub>

<br/>

<a href="https://www.linkedin.com/in/johannmoreno"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white"/></a>

</div>

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0d1117,50:161b22,100:1f6feb&height=100&section=footer" width="100%"/>
