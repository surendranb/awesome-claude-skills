---
name: llm-readiness-audit
description: Measures a website's "AI Visibility" for agents like Claude and Gemini. It audits for LLM context curation (llms.txt), Agent Interactivity (WebMCP), and Semantic Clarity, providing marketers with an AI Visibility Score and actionable recommendations for their web teams.
category: Marketing
subcategory: SEO & Growth
tags: llms.txt, webmcp, ai-seo, visibility-score, marketing-audit, agent-ready
---

# LLM & Agent Readiness Audit

This skill performs a marketer-focused audit of a website to determine how well it is optimized for the emerging "Agentic Web" (as highlighted at Google I/O 2026). Traditional SEO optimizes for Google Search; this audit optimizes for AI agents (Claude, Gemini, ChatGPT).

## Goal
Measure the website's "AI Visibility Score" by checking for agent-specific standards and semantic clarity, providing diagnostic reasoning and actionable recommendations that marketers can pass to their engineering or CMS teams.

## Audit Workflow

### Step 1: Context Curation Check (`llms.txt`)
AI models use RAG (Retrieval-Augmented Generation) and web scraping to understand brands. An `llms.txt` file serves as a curated, high-fidelity index specifically designed for these models.
- **Action:** Attempt to fetch `/llms.txt` at the root of the provided URL.
- **Evaluation:** Does it exist? If so, is it formatted well?
- **Marketer Context:** If missing, LLMs have to guess what content is most important, which can lead to hallucinations about your brand's pricing, features, or messaging.

### Step 2: Agent Interactivity Check (WebMCP)
WebMCP is the new open standard that allows websites to expose interactive tools (like "search inventory" or "book a demo") natively to AI agents.
- **Action:** Attempt to fetch `/.well-known/mcp`.
- **Evaluation:** Does the endpoint exist and return a valid manifest?
- **Marketer Context:** Without this, AI agents cannot natively take actions on your site. Users engaging with AI will have to leave their workflow and navigate your site manually, adding friction to the conversion funnel.

### Step 3: Semantic Clarity Check
When agent-specific files are missing, AI relies entirely on crawling the HTML.
- **Action:** Analyze the homepage source for semantic HTML (e.g., `<article>`, `<nav>`, `<main>`) and Schema.org JSON-LD.
- **Evaluation:** Is the structure clean and easily parsable by an automated crawler? Does it avoid excessive client-side rendering blockages?
- **Marketer Context:** Clean semantics ensure that even basic AI scrapers accurately absorb the brand message.

## Scoring & Report Generation
Calculate the **AI Visibility Score (0-100)**:
- **llms.txt Present:** +40 pts
- **WebMCP Endpoint Present:** +30 pts
- **Strong Semantic HTML/JSON-LD:** +30 pts

Output the final report using the following markdown structure:

```markdown
# 🤖 LLM & Agent Readiness Audit for [URL]

**AI Visibility Score:** [Score]/100
*This score reflects how easily AI agents (like Claude and Gemini) can understand your brand and interact with your website.*

---

## 1. Context Curation (`llms.txt`)
- **Status:** [Found / Not Found]
- **Why it matters:** Without an `llms.txt` file, AI models scrape your site blindly. Providing this file guarantees they read your most critical messaging, pricing, and documentation without guessing.
- **Recommendation for your Web Team:** [Provide a simple recommendation, e.g., "Create a markdown file at `/llms.txt` containing a 2-paragraph summary of your value prop and links to your 3 most important pages."]

## 2. Agent Interactivity (WebMCP)
- **Status:** [Found / Not Found]
- **Why it matters:** WebMCP allows AI to natively perform actions on your site (like searching a catalog). If absent, you lose potential conversions from users who prefer AI-driven workflows.
- **Recommendation for your Web Team:** [Provide a basic suggestion on what tools they might expose, e.g., "Explore implementing a WebMCP endpoint at `/.well-known/mcp` to expose your product catalog directly to AI agents."]

## 3. Semantic Clarity
- **Status:** [Good / Needs Improvement]
- **Why it matters:** Clean code is the fallback for AI understanding. If your site relies heavily on complex JavaScript without semantic tags, AI scrapers will struggle to summarize your brand accurately.
- **Recommendation for your Web Team:** [Specific fix based on the audit, e.g., "Ensure core content is available in the initial HTML load, not just rendered client-side, and implement basic Schema.org JSON-LD."]

---
**Next Steps:** Hand these recommendations to your engineering or CMS team (Webflow, WordPress, etc.) to immediately boost your visibility in the Agentic Era.
```
