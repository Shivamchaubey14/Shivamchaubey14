<!--
  ════════════════════════════════════════════════════════════════════
   Shivam Kumar Chaubey — GitHub Profile README
   Palette: deep navy #0D1320 · ice blue #7DD3FC · violet #A78BFA · slate #9FB0C7
   Decorative art lives in ./assets/svg  ·  project shots in ./assets/img
  ════════════════════════════════════════════════════════════════════
-->

<!-- ============================================================= -->
<!--  HERO                                                         -->
<!-- ============================================================= -->

<div align="center">

<img src="./assets/svg/hero.svg" alt="Shivam Kumar Chaubey — Designing intelligent software systems" width="100%" />

<br/><br/>

<a href="#-selected-work"><img src="https://img.shields.io/badge/Selected_Work-7DD3FC?style=for-the-badge&labelColor=0D1320&color=0D1320" alt="Selected Work"/></a>
&nbsp;
<a href="#-ai-as-an-engineering-discipline"><img src="https://img.shields.io/badge/AI_Systems-A78BFA?style=for-the-badge&labelColor=0D1320&color=0D1320" alt="AI Systems"/></a>
&nbsp;
<a href="#-lets-build-something-that-has-to-work"><img src="https://img.shields.io/badge/Connect-E6EDF6?style=for-the-badge&labelColor=0D1320&color=0D1320" alt="Connect"/></a>

<br/>

<sub>
<a href="#systems-before-syntax">Philosophy</a> &nbsp;·&nbsp;
<a href="#-what-i-build">Expertise</a> &nbsp;·&nbsp;
<a href="#-selected-work">Projects</a> &nbsp;·&nbsp;
<a href="#-ai-as-an-engineering-discipline">AI Systems</a> &nbsp;·&nbsp;
<a href="#-the-toolkit">Stack</a> &nbsp;·&nbsp;
<a href="#-where-my-attention-is-now">Focus</a> &nbsp;·&nbsp;
<a href="#-lets-build-something-that-has-to-work">Connect</a>
</sub>

</div>

<img src="./assets/svg/divider.svg" width="100%" alt="" />

<!-- ============================================================= -->
<!--  PHILOSOPHY                                                    -->
<!-- ============================================================= -->

<div align="center">

### Systems Before Syntax

</div>

> Software is not a stack of libraries — it is a set of decisions that have to keep working under pressure.
>
> I build backend systems that stay predictable as they grow, and I treat artificial intelligence as an engineering discipline: retrieval, evaluation, and reliability — not a magic box. I care about the parts of a system most people never see: the API contract that doesn't break, the queue that absorbs a spike, the agent loop that stays traceable back to its sources.
>
> I think like a chess player — plan the structure, control the center, and only then commit to the move.

<br/>

<img src="./assets/svg/divider.svg" width="100%" alt="" />

<!-- ============================================================= -->
<!--  EXPERTISE                                                     -->
<!-- ============================================================= -->

<div align="center">

### ⬡ What I Build

_Four domains, one mindset — design the system, then write the code._

</div>

<br/>

<table width="100%">
<tr>
<td width="50%" valign="top">

#### ⬡ &nbsp;Backend Systems

Reliable services that hold their shape under load — clean REST contracts, normalized data models, async messaging, and deployments that don't surprise you.

`Django` · `DRF` · `PostgreSQL` · `Kafka` · `Redis`

</td>
<td width="50%" valign="top">

#### ◇ &nbsp;Applied AI

LLM features built as real systems: retrieval-augmented generation, agentic tool-use loops, and evaluation — grounded in data and traceable to sources.

`Claude` · `LangGraph` · `RAG` · `Qdrant` · `ChromaDB`

</td>
</tr>
<tr>
<td width="50%" valign="top">

#### ❖ &nbsp;Distributed & Infra

The machinery that keeps services independent and scalable — containerized workers, task queues, event streams, and reproducible deploys.

`Docker` · `Kubernetes` · `Celery` · `GitHub Actions`

</td>
<td width="50%" valign="top">

#### △ &nbsp;Engineering Foundations

The fundamentals that make the rest hold up — data structures, algorithms, and system-design thinking practiced deliberately, every day.

`DSA` · `System Design` · `Git` · `Linux`

</td>
</tr>
</table>

<img src="./assets/svg/divider.svg" width="100%" alt="" />

<!-- ============================================================= -->
<!--  SELECTED WORK                                                 -->
<!-- ============================================================= -->

<div align="center">

### ◆ Selected Work

_A few systems I've designed and shipped._

</div>

<br/>

<!-- DeepResearch — backend/AI flagship, architecture-led -->
<div align="center">

#### DeepResearch — Agentic AI Research Assistant

</div>

> Ask a question → an autonomous agent **plans** sub-questions, **searches** the web and your documents, **verifies** claims against sources, and streams back a **cited research report** — live, step by step.

Built as production engineering, not an API call: a Django/DRF API dispatches jobs onto **Kafka**, Python agent-workers run the plan→search→verify→cite loop against **Claude** with **Qdrant** for RAG, and **Redis** fans progress events back to the UI over SSE. Every service is containerized and scales independently on **Kubernetes**.

```
React (Vite) ─HTTP/SSE─► Django + DRF ─produce─► Kafka ─consume─► Agent Worker(s)
     ▲                        │   ▲              topics              │
     └─ live progress ◄ Redis ◄┴──────── events ──────────── Claude · Web Search
                                                              Qdrant (RAG store)
```

`Django` · `Kafka` · `Qdrant` · `Redis` · `Claude` · `Docker` · `Kubernetes`
&nbsp;&nbsp;[**Explore the repository →**](https://github.com/Shivamchaubey14/research-agent)

<br/>

<!-- PayZap — backend, architecture-led -->
<div align="center">

#### PayZap — Payment Gateway Backend

</div>

> A payments platform backed by the unglamorous pieces that actually matter: settlements, payouts, fraud checks, and webhooks that never drop a message.

A Django service split into focused domains — `payments`, `payouts`, `settlements`, `merchants`, `fraud`, and `webhooks` — with monitoring, load tests, and a production Docker Compose stack. The interesting work is correctness under failure: idempotent webhook delivery, settlement reconciliation, and fraud signals evaluated inline.

`Django` · `PostgreSQL` · `Redis` · `Docker` · `Fraud Detection` · `Webhooks`
&nbsp;&nbsp;[**Explore the repository →**](https://github.com/Shivamchaubey14/payzap)

<br/>

<!-- LexAI — has real screenshot -->
<table width="100%">
<tr>
<td width="48%" valign="middle">

#### LexAI — Legal Contract Intelligence

**Counsel-grade contract review in under 30 seconds.**

An autonomous agent that reads a contract end-to-end: it flags 12+ risky clause types, scores overall exposure, suggests redlines in a diff view, and answers questions with citations to the **exact clause and page**.

A **LangGraph** agent drives the loop — searching contract chunks and a legal-playbook knowledge base in **ChromaDB**, grounding every answer in real text. The full pipeline runs async on **Celery + Redis**.

`Django` · `LangGraph` · `ChromaDB` · `Claude Sonnet` · `Celery`

[**Explore the repository →**](https://github.com/Shivamchaubey14/legal-agent)

</td>
<td width="52%" valign="middle">
<a href="https://github.com/Shivamchaubey14/legal-agent">
<img src="./assets/img/lexai.png" width="100%" alt="LexAI — legal contract intelligence agent"/>
</a>
</td>
</tr>
</table>

<br/>

<!-- AlgoScope — has real screenshot -->
<table width="100%">
<tr>
<td width="52%" valign="middle">
<a href="https://github.com/Shivamchaubey14/leetcode_visualizer">
<img src="./assets/img/algoscope.png" width="100%" alt="AlgoScope — AI-powered algorithm visualizer"/>
</a>
</td>
<td width="48%" valign="middle">

#### AlgoScope — Algorithm Visualizer

**Understand algorithms by watching them run.**

Step through a LeetCode solution **line by line** — every variable mutation, array shift, and call-stack frame rendered in real time via a custom `sys.settrace()` execution engine, drawn as a color-coded SVG flow graph.

Each problem ships with an **AI-generated explanation** (English & Hindi) from LLaMA 3.1, cached permanently after first load — zero repeat API calls.

`Django` · `Python` · `sys.settrace` · `LLaMA 3.1` · `SVG`

[**Explore the repository →**](https://github.com/Shivamchaubey14/leetcode_visualizer)

</td>
</tr>
</table>

<br/>

<div align="center">
<details>
<summary><b>More from the workshop</b></summary>
<br/>

| Project                                                                                         | What it is                                                                                                  | Stack                                   |
| :---------------------------------------------------------------------------------------------- | :---------------------------------------------------------------------------------------------------------- | :-------------------------------------- |
| [**MilkKart**](https://github.com/Shivamchaubey14/milkkart-backend)                             | Dairy quick-commerce platform — async Django backend + React Native app, Blinkit-style hyper-local delivery | `Django` · `MySQL` · `Redis` · `Celery` |
| [**Video Renting Services**](https://github.com/Shivamchaubey14/Video-Renting-Backend-Services) | Backend services for a video-rental platform — catalog, rentals, billing                                    | `Django` · `DRF`                        |
| [**Issue Tracker**](https://github.com/Shivamchaubey14/issue-tracker)                           | Ticketing system to track and resolve common hostel issues                                                  | `Django`                                |
| [**Solutions**](https://github.com/Shivamchaubey14/Solutions)                                   | A growing library of LeetCode solutions & hints                                                             | `Python`                                |

</details>
</div>

<img src="./assets/svg/divider.svg" width="100%" alt="" />

<!-- ============================================================= -->
<!--  AI SYSTEMS                                                    -->
<!-- ============================================================= -->

<div align="center">

### ◇ AI as an Engineering Discipline

_Not a feature bolted on — a set of moving parts that have to be designed, measured, and trusted._

<br/>

<img src="./assets/svg/ai-ecosystem.svg" width="90%" alt="AI engineering ecosystem: LLMs, RAG pipelines, vector search, agents, embeddings, prompt design, tool use and evals connected around an inference core"/>

<br/><br/>

</div>

A useful AI feature is a pipeline, not a prompt. Retrieval decides what the model sees; prompt structure decides how it reasons; evaluation decides whether you can ship it. I build these pieces to fit together — grounding language models in real data, keeping outputs traceable to their sources, and treating _"is this actually correct?"_ as a first-class requirement rather than an afterthought.

<img src="./assets/svg/divider.svg" width="100%" alt="" />

<!-- ============================================================= -->
<!--  STACK                                                         -->
<!-- ============================================================= -->

<div align="center">

### ❖ The Toolkit

_Chosen for what they let me build — grouped by where they live in a system._

<br/>

**Languages & Core**

<img src="https://skillicons.dev/icons?i=python,js,ts,html,css&theme=dark" alt="Python, JavaScript, TypeScript, HTML, CSS"/>

**Backend & Data**

<img src="https://skillicons.dev/icons?i=django,fastapi,postgres,mysql,redis,sqlite,kafka&theme=dark" alt="Django, FastAPI, PostgreSQL, MySQL, Redis, SQLite, Kafka"/>

**AI & Frontend**

<img src="https://skillicons.dev/icons?i=pytorch,react,bootstrap,tailwind&theme=dark" alt="PyTorch, React, Bootstrap, Tailwind"/>

**Infrastructure & Tooling**

<img src="https://skillicons.dev/icons?i=docker,kubernetes,git,github,linux,vscode&theme=dark" alt="Docker, Kubernetes, Git, GitHub, Linux, VS Code"/>

</div>

<img src="./assets/svg/divider.svg" width="100%" alt="" />

<!-- ============================================================= -->
<!--  CURRENT FOCUS                                                 -->
<!-- ============================================================= -->

<div align="center">

### △ Where My Attention Is Now

</div>

<table width="100%">
<tr>
<td width="33%" align="center"><br/><b>Agentic AI</b><br/><sub>RAG, tool use,<br/>evaluation loops</sub><br/><br/></td>
<td width="33%" align="center"><br/><b>Distributed Backends</b><br/><sub>Kafka, queues,<br/>scale &amp; reliability</sub><br/><br/></td>
<td width="33%" align="center"><br/><b>Cloud &amp; Containers</b><br/><sub>Docker, Kubernetes,<br/>reproducible deploys</sub><br/><br/></td>
</tr>
</table>

<br/>

<div align="center">

[![Currently building](https://img.shields.io/badge/Currently_building-DeepResearch_·_PayZap-7DD3FC?style=flat-square&labelColor=0D1320)](https://github.com/Shivamchaubey14?tab=repositories)
&nbsp;
[![Daily DSA](https://img.shields.io/badge/Daily-DSA_practice-A78BFA?style=flat-square&labelColor=0D1320)](https://github.com/Shivamchaubey14/Solutions)

</div>

<img src="./assets/svg/divider.svg" width="100%" alt="" />

<!-- ============================================================= -->
<!--  STATS                                                         -->
<!-- ============================================================= -->

<div align="center">

### ▲ The Work, Measured

<br/>

<img src="https://github-readme-stats.vercel.app/api?username=Shivamchaubey14&show_icons=true&include_all_commits=true&count_private=true&hide_border=true&bg_color=0D1117&title_color=7DD3FC&icon_color=A78BFA&text_color=9FB0C7&cache_seconds=86400" height="165" alt="GitHub stats"/>
&nbsp;
<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=Shivamchaubey14&layout=compact&langs_count=8&hide_border=true&bg_color=0D1117&title_color=7DD3FC&text_color=9FB0C7&cache_seconds=86400" height="165" alt="Top languages"/>

<br/><br/>

<img src="https://streak-stats.demolab.com/?user=Shivamchaubey14&hide_border=true&background=0D1117&ring=7DD3FC&fire=A78BFA&currStreakNum=E6EDF6&currStreakLabel=7DD3FC&sideNums=E6EDF6&sideLabels=9FB0C7&dates=8A99AD&stroke=1F2A3A" height="165" alt="Contribution streak"/>

<br/><br/>

<img src="https://github-readme-activity-graph.vercel.app/graph?username=Shivamchaubey14&theme=react-dark&hide_border=true&area=true&bg_color=0D1117&color=7DD3FC&line=A78BFA&point=E6EDF6" width="92%" alt="Contribution activity graph"/>

</div>

<img src="./assets/svg/divider.svg" width="100%" alt="" />

<!-- ============================================================= -->
<!--  CONNECT                                                       -->
<!-- ============================================================= -->

<div align="center">

### ◈ Let's build something that has to work.

I'm most interested in conversations about backend architecture, applied AI, and the craft of making software that lasts. If you're working on something ambitious — or hiring for a team that is — I'd like to hear about it.

<br/>

[![GitHub](https://img.shields.io/badge/GitHub-Shivamchaubey14-E6EDF6?style=for-the-badge&logo=github&logoColor=white&labelColor=0D1320)](https://github.com/Shivamchaubey14)
&nbsp;
[![Email](https://img.shields.io/badge/Email-shivamc36@gmail.com-7DD3FC?style=for-the-badge&logo=gmail&logoColor=white&labelColor=0D1320)](mailto:shivamc36@gmail.com)
&nbsp;
[![Open to work](https://img.shields.io/badge/Open_to-Backend_·_AI_·_Full--Stack-A78BFA?style=for-the-badge&labelColor=0D1320)](mailto:shivamc36@gmail.com)

</div>

<!-- ============================================================= -->
<!--  FOOTER                                                        -->
<!-- ============================================================= -->

<img src="./assets/svg/footer-wave.svg" width="100%" alt="" />

<div align="center">

<sub><i>"First, solve the problem. Then, write the code."</i></sub>

<br/>

<sub>Designed &amp; built by Shivam Kumar Chaubey · Uttar Pradesh, India</sub>

</div>
