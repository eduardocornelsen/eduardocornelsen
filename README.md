<div align='center'>
  
<a href="https://eduardocornelsen.com/?utm_source=github&utm_medium=referral&utm_campaign=portfolio_cover">
  <img src="https://github.com/user-attachments/assets/6a51d162-a94f-4e56-a219-cefade860447" alt="Data Science Cover">
</a>

# Eduardo Cornelsen's Applied Data Portfolio

<a href="https://www.linkedin.com/in/eduardo-cornelsen/"><img src="https://img.shields.io/badge/linkedin-673086.svg?&style=for-the-badge&logo=linkedin&logoColor=white" height=30></a> 
&nbsp;
<a href="https://eduardocornelsen.com/?utm_source=github&utm_medium=referral&utm_campaign=portfolio_badge"><img src="https://img.shields.io/badge/Live_Portfolio-673086.svg?&style=for-the-badge&logo=google-chrome&logoColor=white" height=30></a>
&nbsp;
<a href="mailto:eduardo.cornelsen@gmail.com"><img src="https://img.shields.io/badge/gmail-673086.svg?&style=for-the-badge&logo=gmail&logoColor=white" height=30></a>

<a href="https://wakatime.com/@4eb9be1d-cffd-4db6-a3b4-a831bb910af1">
  <img src="https://wakatime.com/badge/user/4eb9be1d-cffd-4db6-a3b4-a831bb910af1.svg" alt="Total Time Coded" />
</a>

---

<a href="#en-version"><img src="https://img.shields.io/badge/🇺🇸_ENGLISH_VERSION-24292e?style=for-the-badge" height=30></a>
&nbsp;
<a href="#pt-version"><img src="https://img.shields.io/badge/🇧🇷_VERSÃO_EM_PORTUGUÊS-24292e?style=for-the-badge" height=30></a>

</div>


<a name="en-version"></a>

<details open>
<summary><h1>🇺🇸 English Version</h1></summary>


## 👋 About Me

> **Data Analyst & Analytics Engineer | SQL · Python · dbt · Semantic Layers · AI Analytics**

**Data Analyst & Analytics Engineer with 5 years in analytics — independent consulting for SMBs since 2021 — and 2 years of consultative B2B SaaS sales at Omie, Brazil's leading cloud ERP.** I build governed analytics layers (dbt models, tested metric definitions, semantic layers) and the dashboards and AI analysts that read from them.

Currently building the data platform for a live specialty-coffee e-commerce: contribution margin by channel, monthly P&L, cost accounting, and an AI analyst that answers questions over SQL without ever computing a number itself.

**Stack:** `SQL` `Python` `dbt` `Postgres` `DuckDB` `BigQuery` `Looker Studio` `Streamlit` `Claude/Gemini APIs` `MCP` `TypeScript/Next.js`

**Domain:** revenue & marketing analytics · e-commerce and SaaS unit economics (CAC, LTV, churn, ROAS, contribution margin) · financial reporting (P&L, cash flow, reconciliation)

🎓 BBA, Insper · TripleTen Data Science program (700h+) · Databricks Academy accreditations · Lean Six Sigma Green Belt

---

## 🚀 Featured Projects

|          Category           | Project                                                                     | Stack                                              |
| :-------------------------: | :-------------------------------------------------------------------------- | :------------------------------------------------- |
| **🏆 Analytics Eng / AI**   | [**Governed AI Analyst for a Live E-commerce**](#p-analyst)                 | Postgres + RLS · dbt · TypeScript · Claude API     |
| **Analytics Eng / AI**      | [**Full-Funnel AI Analytics**](#p-fullfunnel)                               | dbt · DuckDB · MetricFlow · MCP · Python           |
| **Product Analytics / ML**  | [**Epic Games Store: Ecosystem Analysis**](#p0)                             | Python · scikit-learn · NLP · Streamlit            |
| **RevOps / AI**             | [**RevOps Lead Engine**](#prevops)                                          | Python · Streamlit · Plotly                        |
| **SQL / Edu**               | [**PunkSQL — Mobile SQL Learning Platform**](#p-punksql)                    | Next.js · SQLite/WASM · Vercel                     |
| **Infra / AI Chatbot**      | [**Portfolio Website + AI Chatbot**](#p-portfolio-infra)                    | React · Gemini · Cloud Run · LangFuse · Docker     |

---

<br>

<!-- PROJECT: GOVERNED AI ANALYST -->
<div align="center" id="p-analyst">
<img src="https://img.shields.io/badge/🏆%20IN%20PRODUCTION-Governed%20AI%20Analyst-673086?style=for-the-badge">

<h2 style="margin-top: 10px;">🏆 Governed AI Analyst for a Live E-commerce</h2>

<h3><i>The pipeline computes, the model only reads · Postgres + RLS · dbt marts · guardrailed SQL agent</i></h3>

</div>

**Context:**
A specialty-coffee brand sells through its own e-commerce, a subscription club and other channels. The owner's real question is not "how much did we sell?" but "how much did we *keep* — per channel, after cost of goods, freight, gateway fees, taxes and ads?" I built the data layer and an AI analyst on top of it. The code is in private repositories (it runs a real business); this section describes the architecture.

**Architecture:**
```
ERP API · e-commerce DB ──► ingestion (Python, idempotent landing, sync state)
                         ──► dbt on Postgres: staging → intermediate → marts
                               · explicit cross-source dedup with per-source priority
                               · integer cents until the mart, BRL only in the mart
                               · full calendar spine
                         ──► semantic schema (one source of truth, CI fails on drift)
                         ──► AI analyst: question → SQL → read-only result → answer
```

**What makes it trustworthy:**
- **The model never computes a number.** Every metric it cites is a column in a tested dbt mart; a checker verifies each number in the answer against the query results.
- **Defense in depth for SQL:** read-only database role, statement allowlist + denylist, forced `LIMIT`, query timeout, and row-level security with `FORCE` on every tenant table. The tenant id comes from the session, never from the model.
- **Golden-metric regression checks** catch silent changes in the marts.
- **Business metrics, not vanity metrics:** contribution margin by sales channel, monthly P&L, moving-average cost of goods, cash projection.

![Postgres](https://img.shields.io/badge/Postgres_+_RLS-24292e?style=for-the-badge&logo=postgresql&logoColor=white)
![dbt](https://img.shields.io/badge/dbt-24292e?style=for-the-badge&logo=dbt&logoColor=white)
![Python](https://img.shields.io/badge/Python-24292e?style=for-the-badge&logo=python&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-24292e?style=for-the-badge&logo=typescript&logoColor=white)
![Claude](https://img.shields.io/badge/Claude_API-673086?style=for-the-badge&logo=anthropic&logoColor=white)

***

<br>

<!-- PROJECT: FULL-FUNNEL AI ANALYTICS -->
<div align="center" id="p-fullfunnel">
<img src="https://img.shields.io/badge/⭐%20OPEN%20SOURCE-Full--Funnel%20AI%20Analytics-673086?style=for-the-badge">

<h2 style="margin-top: 10px;">Full-Funnel AI Marketing Analytics</h2>

<h3><i>Zero metric drift between dbt and every AI answer · dbt + MetricFlow · golden metrics layer · MCP</i></h3>

<a href="https://github.com/eduardocornelsen/full-funnel-ai-analytics">
  <img src="https://github.com/eduardocornelsen/full-funnel-ai-analytics/raw/main/demo/videos/open-query.gif" width="100%" alt="Full-Funnel AI Analytics — /marketing command demo">
</a>
<br><br>

</div>

**Problem:**
Ask an AI assistant for "blended ROAS last quarter" twice and you can get two different numbers. Marketing teams need one definition of each metric, reused by every dashboard and every AI answer.

**What I built:**
- **dbt project with 30 models** (staging → intermediate → marts) and MetricFlow semantic definitions — ROAS, session CVR, CAC are defined once in YAML.
- **Golden metrics layer:** marts are exported to a versioned JSON that dashboards and AI clients read verbatim; a validation script re-queries the warehouse and fails CI on drift or stale data.
- **4 rule-based attribution models** — first-touch, last-touch, linear, time-decay.
- **MCP servers** for Google Ads, Meta Ads, GA4, HubSpot and Salesforce (mock APIs) plus an analytics server over the golden layer, used from Claude Desktop and other AI clients.
- **Runs on DuckDB in CI** (dbt profiles for BigQuery and Snowflake), plus a 50-case benchmark of how accurately the AI reproduces the canonical numbers.
- **Lead-scoring pipeline demo:** XGBoost → MLflow → FastAPI `/score` → n8n routing. It shows the plumbing; the features are synthetic, so it makes no predictive claim.

**Data:** real Olist e-commerce orders (public Kaggle dataset) + synthetic ad, web-analytics and CRM data generated around them.

<div align='center'>

[![View Repo](https://img.shields.io/badge/View_Repo-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/eduardocornelsen/full-funnel-ai-analytics)
[![Architecture Demo](https://img.shields.io/badge/Architecture_Demo-673086?style=for-the-badge&logo=youtube&logoColor=white)](https://youtu.be/cAWI6h1_6L0)
[![Demo Video](https://img.shields.io/badge/Demo_/_marketing_command-673086?style=for-the-badge&logo=youtube&logoColor=white)](https://www.youtube.com/watch?v=d29Lf2hdUkw&list=PLhSiQdI2GrpaJ2QW9k4M3lW7sS1LYNmUw)

</div>

***

<br>

<!-- PROJECT 0: EPIC GAMES -->
<div align="center" id="p0">
<img src="https://img.shields.io/badge/⚡%20Product%20Strategy%20%26%20UXR-Epic%20Games%20Ecosystem-24292e?style=for-the-badge">
  
<h2 style="margin-top: 10px;">⚡ Epic Games Store Ecosystem Intelligence: Strategic Audit (2026)</h2>

<a href="https://github.com/eduardocornelsen/epic-store-analysis">
  <img src="https://raw.githubusercontent.com/eduardocornelsen/epic-store-analysis/main/images/cover/Cover-H-16-9-EpicGames-UXResearch-low.jpg" width="100%" alt="Epic Games Store Strategic Audit Cover" style="border-radius: 8px;">
</a>
<br><br>

![Python](https://img.shields.io/badge/Python-673086?style=for-the-badge&logo=python&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-24292e?style=for-the-badge&logo=streamlit&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/Scikit_Learn-24292e?style=for-the-badge&logo=scikitlearn&logoColor=white)

</div>

**Business Context:**
A strategic audit transitioning the Epic Games Store from a digital storefront to an "Ecosystem of Intelligence." **Random Forest Regression (R²=0.392)** and **K-Means Clustering** decode the "UX Alpha" — proving 60% of player satisfaction is driven by intangible factors beyond price and specs.

**Key Findings:**
- **The "Hardware Wall":** High system requirements correlate negatively (-0.133) with user ratings — a critical churn zone
- **Behavioral Segmentation:** 4 Product Personas mapping the "Premium Friction" risk in high-cost Indie titles
- **SHAP values** revealing that review velocity outweighs review volume in driving satisfaction scores
- Built as part of my application process; I reached the final round for Epic Games' Data Analyst role (2026)

<div align='center'>

[![View UXR Slides](https://img.shields.io/badge/View_UXR_Presentation-673086?style=for-the-badge&logo=googledrive&logoColor=white)](https://drive.google.com/file/d/1-bqd7O1e-ZP4aW_Bcv4mSAc0QmXR0cmB/view?usp=drive_link)
[![View Dashboard](https://img.shields.io/badge/View_Interactive_Dashboard-24292e?style=for-the-badge&logo=streamlit&logoColor=white)](https://epic-store-analysis.streamlit.app/)
[![View Repo](https://img.shields.io/badge/View_Repo-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/eduardocornelsen/epic-store-analysis)
[![View Notebook](https://img.shields.io/badge/View_Technical_Notebook-24292e?style=for-the-badge&logo=googlecolab&logoColor=white)](https://colab.research.google.com/github/eduardocornelsen/epic-store-analysis/blob/main/notebooks/epic_notebook.ipynb)

</div>


***

<br>

<!-- PROJECT REVOPS: B2B LEAD ENGINE -->
<div align="center" id="prevops">
<img src="https://img.shields.io/badge/🚀%20RevOps%20%26%20AI-B2B%20Command%20Center-673086?style=for-the-badge">
  
<h2 style="margin-top: 10px;">🚀 RevOps Lead Engine: AI-Powered B2B Command Center</h2>

<h3><i>Full-cycle autonomous lead generation · Predictive scenario modeling · Post-sales retention analytics</i></h3>

<a href="https://revops-lead-engine.streamlit.app/">
  <img src="https://raw.githubusercontent.com/eduardocornelsen/revops_lead_engine/main/docs/images/cover-small.jpg" width="100%" alt="RevOps Lead Engine Dashboard" style="border-radius: 8px;">
</a>
<br><br>

![Python](https://img.shields.io/badge/Python-673086?style=for-the-badge&logo=python&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-24292e?style=for-the-badge&logo=streamlit&logoColor=white)
![Plotly](https://img.shields.io/badge/Plotly-24292e?style=for-the-badge&logo=plotly&logoColor=white)
![Pydantic](https://img.shields.io/badge/Pydantic-24292e?style=for-the-badge&logo=pydantic&logoColor=white)

</div>

**Business Context:**
Most B2B sales teams burn 60–70% of SDR time on manual prospecting. This project builds a **fully autonomous RevOps platform** — from ICP-driven lead discovery to AI-powered scoring, predictive revenue modeling, and post-sales retention tracking.

**Key Features:**
- **AI RevOps Copilot:** Natural-language chat for pipeline risk analysis and quota pacing
- **Revenue Scenario Modeler:** 4 levers (Volume, Win Rate, ACV, Cycle Time) → 90-day S-curve revenue projections
- **Post-Sales NDR Module:** Net Dollar Retention, Account Health scoring, ARR Waterfall charts
- **Explainable AI (XAI):** Every lead score includes transparent reasoning — no black-box models
- **10 Integrated Modules:** Revenue Dashboard, Lead Intelligence, Sales Navigator, Pipeline Analytics, and more

<div align='center'>

[![Live Demo](https://img.shields.io/badge/🚀_LIVE_DEMO-673086?style=for-the-badge&logoColor=white)](https://revops-lead-engine.streamlit.app/)
[![View Repo](https://img.shields.io/badge/View_Repo-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/eduardocornelsen/revops_lead_engine)

</div>


***

<br>

<!-- PROJECT: PUNKSQL -->
<div align="center" id="p-punksql">
<img src="https://img.shields.io/badge/🎮%20SQL%20Learning-PunkSQL%20Platform-24292e?style=for-the-badge">
  
<h2 style="margin-top: 10px;">>_ PunkSQL — Mobile SQL Learning Platform</h2>

<h3><i>Duolingo meets LeetCode · 112 challenges · Real in-browser SQL execution · Cyberpunk CLI aesthetic</i></h3>

<a href="https://punksql.vercel.app">
  <img src="https://raw.githubusercontent.com/eduardocornelsen/cv-educornelsen/main/src/assets/projects/punksql/demo-iphone-converted.gif" width="100%" alt="PunkSQL — Mobile SQL Learning Platform Demo">
</a>
<br><br>

![Next.js](https://img.shields.io/badge/Next.js-24292e?style=for-the-badge&logo=next.js)
![SQLite](https://img.shields.io/badge/SQLite-24292e?style=for-the-badge&logo=sqlite)
![Supabase](https://img.shields.io/badge/Supabase-24292e?style=for-the-badge&logo=supabase&logoColor=white)
![Vercel](https://img.shields.io/badge/Vercel-24292e?style=for-the-badge&logo=vercel)

</div>

**What it is:**
A mobile-first SQL learning platform with a cyberpunk terminal aesthetic. Write real SQL queries that execute in your browser using SQLite compiled to WebAssembly. No backend, no signup required to play.

**Key Features:**
- **112 SQL challenges** across 10 modules — SELECT → CTEs and DDL/DML, sequential unlocking
- **Real SQLite execution** via WASM — queries validated against expected output
- **Gamified** — 20 levels, XP system, 10 achievements, sound effects
- **Google OAuth** — persistent progress across sessions
- **Bilingual** — full EN/PT-BR support
- **$0/month** infrastructure — fully client-side

<div align='center'>
  
[![Play Now](https://img.shields.io/badge/▶_Play_Now-673086?style=for-the-badge)](https://punksql.vercel.app)
[![View Repo](https://img.shields.io/badge/View_Repo-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/eduardocornelsen/punksql)

</div>


***

<br>

<!-- PROJECT: PORTFOLIO INFRASTRUCTURE & AI CHATBOT -->
<div align="center" id="p-portfolio-infra">
<img src="https://img.shields.io/badge/⚙️%20Infra%20%2F%20AI%20Chatbot-Portfolio%20System-673086?style=for-the-badge">
  
<h2 style="margin-top: 10px;">⚙️ Portfolio Website + AI Chatbot Infrastructure</h2>

<h3><i>Streaming AI chatbot · Google Cloud Run · GitHub Actions CI/CD · LangFuse LLMOps · 4-layer security · $0/month</i></h3>

<a href="https://eduardocornelsen.com/?utm_source=github&utm_medium=referral&utm_campaign=infra_project">
  <img src="https://raw.githubusercontent.com/eduardocornelsen/cv-educornelsen/main/src/assets/projects/portfolio-infra/lp.webp" width="100%" alt="Eduardo Cornelsen Portfolio — Live Site">
</a>
<br><br>

![React](https://img.shields.io/badge/React_19-24292e?style=for-the-badge&logo=react&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-24292e?style=for-the-badge&logo=typescript&logoColor=white)
![Gemini](https://img.shields.io/badge/Gemini-673086?style=for-the-badge&logo=googlegemini&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-24292e?style=for-the-badge&logo=docker&logoColor=white)
![Cloud Run](https://img.shields.io/badge/Google_Cloud_Run-24292e?style=for-the-badge&logo=googlecloud&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-24292e?style=for-the-badge&logo=githubactions&logoColor=white)
![LangFuse](https://img.shields.io/badge/LangFuse-24292e?style=for-the-badge&logoColor=white)

</div>

**What it is:**
The production infrastructure powering this portfolio — not a side project, but the live system you're looking at right now. Built to be a proof of work in itself: a streaming AI chatbot, containerized via multi-stage Docker, deployed on Google Cloud Run through a zero-touch GitHub Actions pipeline, with every conversation traced in LangFuse for cost, latency, and security analysis.

**Architecture:**
```
GitHub push → Actions: Docker build → Artifact Registry → Cloud Run deploy
Browser → React 19 + Vite (SSE streaming) → Express proxy → Gemini 2.5 Flash
                                                           → LangFuse (trace every token)
```

**Key Features:**
- **Streaming AI chatbot** — Server-Sent Events deliver token-by-token responses; no waiting for the full reply
- **4-layer security model** — client sanitization, IP rate-limiting, canary token injection, intent classification (jailbreak detection)
- **LLMOps with LangFuse** — every conversation traced with cost, latency, and safety flag
- **Zero-touch CI/CD** — push to `main`, site is live in ~3 minutes via OIDC-authenticated GitHub Actions
- **$0/month at rest** — Cloud Run scales to zero when idle

<div align='center'>

[![Live Site](https://img.shields.io/badge/Live_Site-eduardocornelsen.com-673086?style=for-the-badge&logo=google-chrome&logoColor=white)](https://eduardocornelsen.com/?utm_source=github&utm_medium=referral&utm_campaign=infra_badge)
[![View Repo](https://img.shields.io/badge/View_Repo-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/eduardocornelsen/cv-educornelsen)

</div>


***

<br>

### Also

- **[Unified AI Data Framework](https://github.com/eduardocornelsen/unified-ai-data-framework)** — playbooks and personas that structure how I run data projects with Claude Code. The skill library is adapted from Nimrod Fisher's [data-analytics-skills](https://github.com/nimrodfisher/data-analytics-skills).
- **[MusicInsights AI](https://github.com/eduardocornelsen/spotify-music-insights-ai)** — Streamlit dashboard with a LangChain "chat with data" agent over 160k+ Spotify tracks ([live app](https://spotify-music-insights-ai.streamlit.app/)).

</details>

---

<a name="pt-version"></a>

<details>
<summary><h1>🇧🇷 Versão em Português</h1></summary>

## 👋 Sobre Mim

> **Analista de Dados & Analytics Engineer | SQL · Python · dbt · Camadas Semânticas · Analytics com IA**

**Analista de Dados & Analytics Engineer com 5 anos em analytics — consultoria independente para PMEs desde 2021 — e 2 anos de vendas consultivas B2B SaaS na Omie, o maior ERP em nuvem do Brasil.** Construo camadas de analytics governadas (modelos dbt, definições de métricas testadas, camadas semânticas) e os dashboards e analistas de IA que leem delas.

Hoje construo a plataforma de dados de um e-commerce de cafés especiais em produção: margem de contribuição por canal, DRE mensal, custeio, e um analista de IA que responde perguntas via SQL sem nunca calcular um número por conta própria.

**Stack:** `SQL` `Python` `dbt` `Postgres` `DuckDB` `BigQuery` `Looker Studio` `Streamlit` `Claude/Gemini APIs` `MCP` `TypeScript/Next.js`

**Domínio:** analytics de receita e marketing · unit economics de e-commerce e SaaS (CAC, LTV, churn, ROAS, margem de contribuição) · relatórios financeiros (DRE, fluxo de caixa, conciliação)

🎓 Administração, Insper · Programa de Data Science TripleTen (700h+) · Acreditações Databricks Academy · Green Belt Lean Six Sigma

---

## 🚀 Projetos em Destaque

|           Categoria            | Projeto                                                                      | Stack                                              |
| :----------------------------: | :--------------------------------------------------------------------------- | :------------------------------------------------- |
| **🏆 Analytics Eng / IA**      | [**Analista de IA Governado para um E-commerce Real**](#p-analyst-pt)        | Postgres + RLS · dbt · TypeScript · Claude API     |
| **Analytics Eng / IA**         | [**Full-Funnel AI Analytics**](#p-fullfunnel-pt)                             | dbt · DuckDB · MetricFlow · MCP · Python           |
| **Product Analytics / ML**     | [**Epic Games Store: Análise de Ecossistema**](#p0-pt)                       | Python · scikit-learn · NLP · Streamlit            |
| **RevOps / IA**                | [**RevOps Lead Engine**](#prevops-pt)                                        | Python · Streamlit · Plotly                        |
| **SQL / Edu**                  | [**PunkSQL — Plataforma de Aprendizado de SQL**](#p-punksql-pt)              | Next.js · SQLite/WASM · Vercel                     |
| **Infra / AI Chatbot**         | [**Portfólio + AI Chatbot**](#p-portfolio-infra-pt)                          | React · Gemini · Cloud Run · LangFuse · Docker     |

---

<br>

<!-- PROJECT: GOVERNED AI ANALYST PT -->
<div align="center" id="p-analyst-pt">
<img src="https://img.shields.io/badge/🏆%20EM%20PRODUÇÃO-Analista%20de%20IA%20Governado-673086?style=for-the-badge">

<h2 style="margin-top: 10px;">🏆 Analista de IA Governado para um E-commerce Real</h2>

<h3><i>O pipeline calcula, o modelo só lê · Postgres + RLS · marts dbt · agente SQL com guardrails</i></h3>

</div>

**Contexto:**
Uma marca de cafés especiais vende pelo próprio e-commerce, por um clube de assinatura e por outros canais. A pergunta real de quem toca o negócio não é "quanto vendemos?", e sim "quanto *sobrou* — por canal, depois de custo da mercadoria, frete, taxas de gateway, impostos e anúncios?". Construí a camada de dados e um analista de IA em cima dela. O código está em repositórios privados (roda um negócio real); esta seção descreve a arquitetura.

**Arquitetura:**
```
API do ERP · banco do e-commerce ──► ingestão (Python, pouso idempotente, estado de sync)
                                 ──► dbt no Postgres: staging → intermediate → marts
                                       · dedup explícito entre fontes, com prioridade por fonte
                                       · centavos inteiros até o mart, reais só no mart
                                       · spine de calendário completo
                                 ──► esquema semântico (fonte única; o CI falha se divergir)
                                 ──► analista de IA: pergunta → SQL → resultado somente-leitura → resposta
```

**Por que dá para confiar:**
- **O modelo nunca calcula um número.** Toda métrica citada é coluna de um mart dbt testado; um conferidor verifica cada número da resposta contra o resultado da consulta.
- **Defesa em profundidade no SQL:** papel somente-leitura no banco, allowlist + denylist de comandos, `LIMIT` forçado, timeout de consulta e row-level security com `FORCE` em toda tabela com tenant. O tenant vem da sessão, nunca do modelo.
- **Regressão de golden metrics** pega mudanças silenciosas nos marts.
- **Métricas de negócio, não de vaidade:** margem de contribuição por canal, DRE mensal, custo médio móvel da mercadoria, projeção de caixa.

![Postgres](https://img.shields.io/badge/Postgres_+_RLS-24292e?style=for-the-badge&logo=postgresql&logoColor=white)
![dbt](https://img.shields.io/badge/dbt-24292e?style=for-the-badge&logo=dbt&logoColor=white)
![Python](https://img.shields.io/badge/Python-24292e?style=for-the-badge&logo=python&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-24292e?style=for-the-badge&logo=typescript&logoColor=white)
![Claude](https://img.shields.io/badge/Claude_API-673086?style=for-the-badge&logo=anthropic&logoColor=white)

***

<br>

<!-- PROJECT: FULL-FUNNEL PT -->
<div align="center" id="p-fullfunnel-pt">
<img src="https://img.shields.io/badge/⭐%20OPEN%20SOURCE-Full--Funnel%20AI%20Analytics-673086?style=for-the-badge">

<h2 style="margin-top: 10px;">Full-Funnel AI Marketing Analytics</h2>

<h3><i>Zero divergência de métricas entre o dbt e cada resposta da IA · dbt + MetricFlow · camada de golden metrics · MCP</i></h3>

</div>

<a href="https://github.com/eduardocornelsen/full-funnel-ai-analytics">
  <img src="https://github.com/eduardocornelsen/full-funnel-ai-analytics/raw/main/demo/videos/open-query.gif" width="100%" alt="Full-Funnel AI Analytics — demo de consulta em linguagem natural">
</a>
<br><br>

**Problema:**
Pergunte duas vezes a um assistente de IA o "ROAS blended do último trimestre" e você pode receber dois números diferentes. Times de marketing precisam de uma única definição para cada métrica, reutilizada por todo dashboard e toda resposta de IA.

**O que construí:**
- **Projeto dbt com 30 modelos** (staging → intermediate → marts) e definições semânticas no MetricFlow — ROAS, CVR por sessão e CAC definidos uma vez em YAML.
- **Camada de golden metrics:** os marts são exportados para um JSON versionado que dashboards e clientes de IA leem sem recalcular; um script de validação reconsulta o warehouse e falha o CI se houver divergência ou dado desatualizado.
- **4 modelos de atribuição baseados em regras** — first-touch, last-touch, linear, time-decay.
- **Servidores MCP** para Google Ads, Meta Ads, GA4, HubSpot e Salesforce (APIs simuladas) e um servidor de analytics sobre a camada golden, usados no Claude Desktop e em outros clientes de IA.
- **Roda em DuckDB no CI** (com perfis dbt para BigQuery e Snowflake), mais um benchmark de 50 casos sobre a precisão com que a IA reproduz os números canônicos.
- **Demo de pipeline de lead scoring:** XGBoost → MLflow → FastAPI `/score` → roteamento no n8n. Mostra o encanamento; as features são sintéticas, então não há alegação preditiva.

**Dados:** pedidos reais de e-commerce da Olist (dataset público do Kaggle) + dados sintéticos de anúncios, web analytics e CRM gerados em torno deles.

<div align='center'>

[![Ver Repo](https://img.shields.io/badge/Ver_Repo-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/eduardocornelsen/full-funnel-ai-analytics)
[![Demo Arquitetura](https://img.shields.io/badge/Demo_Arquitetura-673086?style=for-the-badge&logo=youtube&logoColor=white)](https://youtu.be/cAWI6h1_6L0)
[![Vídeo Demo](https://img.shields.io/badge/Vídeo_Demo-673086?style=for-the-badge&logo=youtube&logoColor=white)](https://www.youtube.com/watch?v=d29Lf2hdUkw&list=PLhSiQdI2GrpaJ2QW9k4M3lW7sS1LYNmUw)

</div>

***

<br>

<!-- PROJECT 0 PT -->
<div align="center" id="p0-pt">
<img src="https://img.shields.io/badge/⚡%20Estratégia%20de%20Produto%20%26%20UXR-Epic%20Games-24292e?style=for-the-badge">
  
<h2 style="margin-top: 10px;">⚡ Epic Games Store: Auditoria Estratégica de Ecossistema (2026)</h2>

<a href="https://github.com/eduardocornelsen/epic-store-analysis">
  <img src="https://raw.githubusercontent.com/eduardocornelsen/epic-store-analysis/main/images/cover/Cover-H-16-9-EpicGames-UXResearch-low.jpg" width="100%" style="border-radius: 8px;">
</a>
<br><br>

![Python](https://img.shields.io/badge/Python-673086?style=for-the-badge&logo=python&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-24292e?style=for-the-badge&logo=streamlit&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/Scikit_Learn-24292e?style=for-the-badge&logo=scikitlearn&logoColor=white)

</div>

**Descobertas principais:** Hardware Wall (-0.133 correlação com satisfação), 4 Personas de Produto, 60% da satisfação do jogador impulsionada por fatores intangíveis de UX. SHAP values revelando que velocidade de reviews supera volume na predição de satisfação.

Feito durante meu processo seletivo; cheguei à rodada final para a vaga de Data Analyst na Epic Games (2026).

<div align='center'>

[![Ver Apresentação](https://img.shields.io/badge/Ver_Apresentação_UXR-673086?style=for-the-badge&logo=googledrive&logoColor=white)](https://drive.google.com/file/d/1-bqd7O1e-ZP4aW_Bcv4mSAc0QmXR0cmB/view?usp=drive_link)
[![Acessar Dashboard](https://img.shields.io/badge/Acessar_Dashboard-24292e?style=for-the-badge&logo=streamlit&logoColor=white)](https://epic-store-analysis.streamlit.app/)
[![Ver Repo](https://img.shields.io/badge/Ver_Repo-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/eduardocornelsen/epic-store-analysis)
[![Ver Notebook](https://img.shields.io/badge/Ver_Notebook_Técnico-24292e?style=for-the-badge&logo=googlecolab&logoColor=white)](https://colab.research.google.com/github/eduardocornelsen/epic-store-analysis/blob/main/notebooks/epic_notebook.ipynb)

</div>


***

<br>

<!-- PROJECT REVOPS PT -->
<div align="center" id="prevops-pt">
<img src="https://img.shields.io/badge/🚀%20RevOps%20%26%20IA-Central%20de%20Comando%20B2B-673086?style=for-the-badge">
  
<h2 style="margin-top: 10px;">🚀 RevOps Lead Engine: Central de Comando B2B com IA</h2>

<h3><i>Geração autônoma de leads · Modelagem preditiva de receita · Analytics de retenção pós-venda</i></h3>

<a href="https://revops-lead-engine.streamlit.app/">
  <img src="https://raw.githubusercontent.com/eduardocornelsen/revops_lead_engine/main/docs/images/cover-small.jpg" width="100%" alt="RevOps Lead Engine Dashboard" style="border-radius: 8px;">
</a>
<br><br>

![Python](https://img.shields.io/badge/Python-673086?style=for-the-badge&logo=python&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-24292e?style=for-the-badge&logo=streamlit&logoColor=white)
![Plotly](https://img.shields.io/badge/Plotly-24292e?style=for-the-badge&logo=plotly&logoColor=white)
![Pydantic](https://img.shields.io/badge/Pydantic-24292e?style=for-the-badge&logo=pydantic&logoColor=white)

</div>

**Contexto:** Plataforma RevOps totalmente autônoma — da descoberta de leads por ICP ao scoring com IA, modelagem preditiva de receita e rastreamento de retenção pós-venda. IA Explicável (XAI) em cada score de lead.

**Destaques:**
- **AI RevOps Copilot:** Chat em linguagem natural para análise de risco de pipeline e ritmo de quota
- **Revenue Scenario Modeler:** 4 alavancas (Volume, Win Rate, ACV, Cycle Time) → projeções de receita em curva-S de 90 dias
- **Módulo NDR Pós-Venda:** Net Dollar Retention, Account Health scoring, ARR Waterfall charts
- **XAI:** Cada score de lead inclui raciocínio transparente — sem modelos black-box

<div align='center'>

[![Demo ao Vivo](https://img.shields.io/badge/🚀_DEMO_AO_VIVO-673086?style=for-the-badge&logoColor=white)](https://revops-lead-engine.streamlit.app/)
[![Ver Repo](https://img.shields.io/badge/Ver_Repo-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/eduardocornelsen/revops_lead_engine)

</div>


***

<br>

<!-- PUNKSQL PT -->
<div align="center" id="p-punksql-pt">
<img src="https://img.shields.io/badge/🎮%20Aprendizado%20SQL-PunkSQL%20Platform-24292e?style=for-the-badge">

<h2 style="margin-top: 10px;">>_ PunkSQL — Plataforma de Aprendizado de SQL</h2>

<h3><i>Duolingo meets LeetCode · 112 desafios · Execução real de SQL no browser · Estética cyberpunk</i></h3>

</div>

<a href="https://punksql.vercel.app">
  <img src="https://raw.githubusercontent.com/eduardocornelsen/cv-educornelsen/main/src/assets/projects/punksql/demo-iphone-converted.gif" width="100%" alt="PunkSQL — Demo Plataforma de Aprendizado de SQL">
</a>
<br><br>

![Next.js](https://img.shields.io/badge/Next.js-24292e?style=for-the-badge&logo=next.js)
![SQLite](https://img.shields.io/badge/SQLite-24292e?style=for-the-badge&logo=sqlite)
![Supabase](https://img.shields.io/badge/Supabase-24292e?style=for-the-badge&logo=supabase&logoColor=white)
![Vercel](https://img.shields.io/badge/Vercel-24292e?style=for-the-badge&logo=vercel)

**Plataforma mobile-first** para aprender SQL com estética cyberpunk. 112 desafios, 10 módulos (SELECT → CTEs e DDL/DML), execução real de SQL no browser via SQLite/WASM, gamificação completa (20 níveis, XP, conquistas), Google OAuth, bilíngue EN/PT-BR. $0/mês de infraestrutura.

<div align='center'>

[![Jogar Agora](https://img.shields.io/badge/▶_Jogar_Agora-673086?style=for-the-badge)](https://punksql.vercel.app)
[![Ver Repo](https://img.shields.io/badge/Ver_Repo-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/eduardocornelsen/punksql)

</div>


***

<br>

<!-- PROJECT: PORTFOLIO INFRA PT -->
<div align="center" id="p-portfolio-infra-pt">
<img src="https://img.shields.io/badge/⚙️%20Infra%20%2F%20AI%20Chatbot-Portfolio%20System-673086?style=for-the-badge">

<h2 style="margin-top: 10px;">⚙️ Infraestrutura Portfolio Website + AI Chatbot</h2>

<h3><i>AI chatbot com streaming · Google Cloud Run · CI/CD GitHub Actions · LLMOps com LangFuse · segurança 4 camadas · $0/mês</i></h3>

</div>

<a href="https://eduardocornelsen.com/?utm_source=github&utm_medium=referral&utm_campaign=infra_project_pt">
  <img src="https://raw.githubusercontent.com/eduardocornelsen/cv-educornelsen/main/src/assets/projects/portfolio-infra/lp.webp" width="100%" alt="Eduardo Cornelsen Portfolio — Site ao Vivo">
</a>
<br><br>

![React](https://img.shields.io/badge/React_19-24292e?style=for-the-badge&logo=react&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-24292e?style=for-the-badge&logo=typescript&logoColor=white)
![Gemini](https://img.shields.io/badge/Gemini-673086?style=for-the-badge&logo=googlegemini&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-24292e?style=for-the-badge&logo=docker&logoColor=white)
![Cloud Run](https://img.shields.io/badge/Google_Cloud_Run-24292e?style=for-the-badge&logo=googlecloud&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-24292e?style=for-the-badge&logo=githubactions&logoColor=white)
![LangFuse](https://img.shields.io/badge/LangFuse-24292e?style=for-the-badge&logoColor=white)

**O que é:**
A infraestrutura de produção que roda este portfólio. Chatbot de IA com streaming, containerizado via Docker multi-stage, implantado no Google Cloud Run via GitHub Actions zero-touch, com cada conversa rastreada no LangFuse para custo, latência e segurança.

**Arquitetura:**
```
GitHub push → Actions: Docker build → Artifact Registry → Cloud Run deploy
Browser → React 19 + Vite (SSE streaming) → Express proxy → Gemini 2.5 Flash
                                                           → LangFuse (trace every token)
```

**Destaques:**
- **Segurança em 4 camadas** — sanitização no cliente, rate-limit por IP, canary token, classificação de intenção (detecção de jailbreak)
- **LLMOps com LangFuse** — cada conversa rastreada com custo, latência e flag de segurança
- **CI/CD zero-touch** — push para `main`, site no ar em ~3 minutos via GitHub Actions com OIDC
- **$0/mês em repouso** — Cloud Run escala para zero quando ocioso

<div align='center'>
  
[![Site ao Vivo](https://img.shields.io/badge/Site_ao_Vivo-673086?style=for-the-badge&logo=google-chrome&logoColor=white)](https://eduardocornelsen.com/?utm_source=github&utm_medium=referral&utm_campaign=infra_badge_pt)
[![Ver Repo](https://img.shields.io/badge/Ver_Repo-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/eduardocornelsen/cv-educornelsen)

</div>


***

<br>

### Também

- **[Unified AI Data Framework](https://github.com/eduardocornelsen/unified-ai-data-framework)** — playbooks e personas que estruturam como conduzo projetos de dados com o Claude Code. A biblioteca de skills é adaptada do [data-analytics-skills](https://github.com/nimrodfisher/data-analytics-skills), de Nimrod Fisher.
- **[MusicInsights AI](https://github.com/eduardocornelsen/spotify-music-insights-ai)** — dashboard Streamlit com um agente LangChain de "chat com os dados" sobre 160k+ faixas do Spotify ([app ao vivo](https://spotify-music-insights-ai.streamlit.app/)).

</details>

---

<div align='center'>

## 🏆 Certifications & Education

[![Business Administration - Insper](https://img.shields.io/badge/BUSINESS%20ADMIN-INSPER-CC0000?style=for-the-badge&logo=googleforms&logoColor=white)](https://www.insper.edu.br/en/home)
[![Data Science - TripleTen](https://img.shields.io/badge/DATA%20SCIENCE-TRIPLETEN-0077B5?style=for-the-badge&logo=googleanalytics&logoColor=white)](https://tripleten.com)
[![Databricks Academy](https://img.shields.io/badge/ACCREDITATION-DATABRICKS%20ACADEMY-FF3621?style=for-the-badge&logo=databricks&logoColor=white)](https://www.databricks.com/learn/training)
[![Green Belt Falconi](https://img.shields.io/badge/GREEN%20BELT-FALCONI-7b7423?style=for-the-badge)](https://falconi.com)

<br>

---

## ⚡ Neural Link Activity

<!--START_SECTION:wakatime-->

```python
From: 24 October 2025 - To: 16 October 2026

Total Time: 577 hrs 44 mins

Python                     254 hrs 49 mins       █████████▓░░░░░░░░░░░░░░░   38.30 %
TypeScript                 136 hrs               █████░░░░░░░░░░░░░░░░░░░░   20.44 %
Markdown                   116 hrs 44 mins       ████▒░░░░░░░░░░░░░░░░░░░░   17.55 %
Other                      87 hrs 35 mins        ███▒░░░░░░░░░░░░░░░░░░░░░   13.16 %
HTML                       23 hrs 11 mins        █░░░░░░░░░░░░░░░░░░░░░░░░   03.49 %
```

<!--END_SECTION:wakatime-->

***

## 📊 GitHub Stats

<br>

<div align="center"> 
  <img height="180" src="https://github-readme-stats.vercel.app/api?username=eduardocornelsen&show_icons=true&hide_border=true&bg_color=031b1b&title_color=01ea94&text_color=1e8f92&icon_color=EFEFEF" /> 
  
  <img height="180" src="https://github-readme-streak-stats.herokuapp.com/?user=eduardocornelsen&theme=taiga&hide_border=true&ring=00EB93" /> 

  <img height="180" src="https://github-readme-stats.vercel.app/api/top-langs/?username=eduardocornelsen&layout=compact&hide=html,css&show_icons=true&hide_border=true&bg_color=031b1b&title_color=01ea94&text_color=1e8f92&icon_color=EFEFEF" /> 
</div>
<br>

---

*© 2026 Eduardo Cornelsen — Data Analyst & Analytics Engineer*

</div>
