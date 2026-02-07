# AI (LLMs and Agents) Applied to the Software Development Life Cycle
## Comprehensive Research Report -- Academic Papers, Industry Surveys, and Quantitative Data (2023--2026)

---

## TABLE OF CONTENTS

1. [Overall Landscape and Industry Surveys](#1-overall-landscape-and-industry-surveys)
2. [Stage 1: Feasibility Study and Estimation](#2-stage-1-feasibility-study-and-estimation)
3. [Stage 2: Requirements Elicitation and Analysis](#3-stage-2-requirements-elicitation-and-analysis)
4. [Stage 3: Software Design and Architecture](#4-stage-3-software-design-and-architecture)
5. [Stage 4: Implementation / Coding](#5-stage-4-implementation--coding)
6. [Stage 5: Testing](#6-stage-5-testing)
7. [Stage 6: Deployment and DevOps](#7-stage-6-deployment-and-devops)
8. [Stage 7: Evolution and Maintenance](#8-stage-7-evolution-and-maintenance)
9. [Stage 8: Project Management](#9-stage-8-project-management)
10. [AI Agent Capabilities and Benchmarks](#10-ai-agent-capabilities-and-benchmarks)
11. [Code Quality When Using AI](#11-code-quality-when-using-ai)
12. [The Changing Role of the Software Engineer](#12-the-changing-role-of-the-software-engineer)

---

## 1. OVERALL LANDSCAPE AND INDUSTRY SURVEYS

### 1.1 Major Industry Surveys

**Stack Overflow Developer Survey 2024**
- 76% of developers are using or plan to use AI tools (up from 70% in 2023).
- 62% currently use AI tools (up from 44% in 2023).
- 82% of those using AI tools use them to write code; 46% of non-users are most curious about AI for testing.
- Favorability dropped from 77% (2023) to 72% (2024); decline attributed to disappointing results with complex tasks.
- 45% of developers believe AI tools are bad or very bad at handling complex tasks.
- 79% cite misinformation/disinformation in AI output as a top ethical concern.
- 70% of professionals do not feel AI is a threat to their job.
- Source: Stack Overflow, "2024 Developer Survey -- AI Section," 2024. https://survey.stackoverflow.co/2024/ai

**JetBrains State of Developer Ecosystem 2024**
- Nearly 80% of companies allow third-party AI tools or have no formal restrictions.
- 77% of developers reported using AI assistants during development.
- ChatGPT used by 82% of AI-using developers; GitHub Copilot by 68%.
- Source: JetBrains, "The State of Developer Ecosystem 2024," December 2024. https://blog.jetbrains.com/team/2024/12/11/the-state-of-developer-ecosystem-2024-unveiling-current-developer-trends-the-unstoppable-rise-of-ai-adoption-leading-languages-and-impact-on-developer-experience/

**JetBrains State of Developer Ecosystem 2025**
- 85% of developers regularly use AI tools for coding and development.
- 62% rely on at least one AI coding assistant, agent, or code editor.
- 41% of all code written in 2025 was AI-generated.
- 68% of developers anticipate AI proficiency will become a job requirement.
- Survey included 24,534 developers (April--June 2025).
- Source: JetBrains, "The State of Developer Ecosystem 2025," October 2025. https://blog.jetbrains.com/research/2025/10/state-of-developer-ecosystem-2025/

**GitHub Octoverse 2024**
- 59% surge in contributions to generative AI projects on GitHub.
- 98% increase in AI-related projects overall.
- Python overtook JavaScript as the most popular language on GitHub.
- 1.4 million new developers joined open source globally.
- Source: GitHub, "Octoverse 2024: AI leads Python to top language," October 2024. https://github.blog/news-insights/octoverse/octoverse-2024/

**GitHub Octoverse 2025**
- 1.1M+ public repositories import an LLM SDK (+178% YoY).
- 50% of open source projects have at least one maintainer using GitHub Copilot.
- 43.2 million pull requests merged monthly on average (+23% YoY).
- Nearly 1 billion commits pushed in 2025 (+25.1% YoY).
- Source: GitHub, "Octoverse 2025: The state of open source," 2025. https://octoverse.github.com/

**Microsoft New Future of Work Report 2025**
- GenAI investment reached $33.9 billion in private funding in 2024 (18.7% increase from 2023).
- AI-generated "workslop" (content with errors) affects nearly 40% of employees monthly.
- AI's productivity impact follows a J-curve: short-term disruption, long-term gains.
- Software engineers who used AI received lower competency ratings on identical work.
- Source: Microsoft Research, "New Future of Work Report 2025," December 2025. https://www.microsoft.com/en-us/research/publication/new-future-of-work-report-2025/

**Gartner Predictions (2024--2025)**
- By 2028, 90% of enterprise software engineers will use AI code assistants (up from <14% in early 2024).
- By 2027, GenAI will require 80% of the engineering workforce to upskill.
- By 2026, 40% of enterprise apps will feature task-specific AI agents (up from <5% in 2025).
- By 2028, 33% of enterprise software will incorporate agentic AI; agentic AI will make 15% of day-to-day work decisions autonomously.
- Source: Gartner, "Top Predictions for IT Organizations 2025 and Beyond," October 2024. https://www.gartner.com/en/newsroom/press-releases/2024-10-22-gartner-unveils-top-predictions-for-it-organizations-and-users-in-2025-and-beyond

### 1.2 Comprehensive SDLC Surveys

**Fan, C. (Hymel). "The AI-Native Software Development Lifecycle: A Theoretical and Practical New Methodology." arXiv:2408.03416, August 2024.**
- Proposes the V-Bounce model, an adaptation of the traditional V-model with AI integrated end-to-end.
- AI dramatically reduces time in implementation phases, shifting emphasis toward requirements gathering, architecture design, and continuous validation.
- Redefines human role from primary implementers to validators and verifiers; AI acts as implementation engine.
- https://arxiv.org/abs/2408.03416

**Liu, J., Wang, K., Chen, Y., Peng, X., Chen, Z., Zhang, L., & Lou, Y. "Large Language Model-Based Agents for Software Engineering: A Survey." ACM Transactions on Software Engineering and Methodology, 2024.**
- Collected 124 papers; categorized from SE and agent perspectives.
- LLM-based agents substantially extend versatility beyond standalone LLMs through external resource perception and tool use.
- Multi-agent synergy and human interaction hold promise for complex real-world SE problems.
- https://dl.acm.org/doi/10.1145/3712003

**Rasheed, Z. et al. "Software Development Life Cycle Perspective: A Survey of Benchmarks for Code LLMs and Agents." arXiv:2505.05283, May 2025.**
- Systematic evaluation of benchmarks across all SDLC phases.
- Identifies that existing evaluation frameworks primarily focus on code generation, understanding, and repair without comprehensively covering all SDLC phases.
- DevBench (Li et al., 2024) is the only benchmark covering all phases across four programming languages.
- https://arxiv.org/html/2505.05283v2

**Nascimento, N. et al. "LLMs' Reshaping of People, Processes, Products, and Society in Software Development: A Comprehensive Exploration with Early Adopters." arXiv:2503.05012, March 2025.**
- LLMs are particularly effective for ideation, testing, and debugging tasks.
- Less useful for generating requirements or reviewing code, especially in collaborative environments.
- https://arxiv.org/html/2503.05012v1

### 1.3 AI Market Data

- AI code generation market valued at $4.91 billion in 2024; projected to hit $30.1 billion by 2032 (27.1% CAGR).
- 48% of organizations use two or more AI coding tools.
- 41.7% of organizations report top-down licensing of AI coding tools.
- 22.5% have published formal AI coding policies.
- GitHub Copilot: 15 million+ users globally; 1.3 million paid subscribers; 90% of Fortune 100 companies adopted it.

---

## 2. STAGE 1: FEASIBILITY STUDY AND ESTIMATION

### 2.1 Key Papers

**Lopez-Martin, C. et al. "Leveraging Large Language Models for Predicting Cost and Duration in Software Engineering Projects." arXiv:2409.09617, September 2024.**
- Uses the ISBSG dataset; fine-tunes GPT-3.5 for cost estimation.
- Innovative approach using LLMs to enhance accuracy and usability of project cost predictions.
- https://arxiv.org/html/2409.09617v1

**Hasnain, M. et al. "Effort and Size Estimation in Software Projects with Large Language Model-based Intelligent Interfaces." arXiv:2402.07158, February 2024.**
- Addresses estimation challenges when LLM-based AI agents are included in software design.
- Proposes enhanced specifications of natural language-based questions by accounting for data sources, interfaces, and algorithms.
- https://arxiv.org/abs/2402.07158

**Ali, A. et al. "Advancement of Artificial Intelligence in Cost Estimation for Project Management Success: A Systematic Review of ML, DL, Regression, and Hybrid Models." MDPI, April 2025.**
- Systematic review synthesizing 39 articles from 2016--2024.
- Artificial neural networks enhance predictive accuracy in complex project environments.
- https://www.mdpi.com/2673-3951/6/2/35

**Cabrera-Diego, L. A. et al. "Large Language Models for Early-Stage Software Project Estimation: A Systematic Mapping Study." Applied Sciences (MDPI), December 2025.**
- Examined 30 primary studies on LLM applications in early project estimation.
- Effort estimation studies span 2022--2025, peaking in 2024 (11 studies) and 2025 (5 studies).
- https://www.mdpi.com/2076-3417/15/24/13099

**Bui, T.-L. "An LLM-based multi-agent framework for agile effort estimation." arXiv:2509.14483, September 2025.**
- SEEAgent: multi-agent framework for agile effort estimation and sprint planning.
- Aims to provide accurate estimates while facilitating informational interactions with agile team members.
- https://www.arxiv.org/pdf/2509.14483

**Generative AI in Systems Engineering: A Framework for Risk Assessment of LLMs. arXiv:2602.04358, February 2026.**
- Introduces the LLM Risk Assessment Framework (LRF) classifying applications along autonomy and impact dimensions.
- ~50% of ChatGPT-generated outputs for risk analysis require expert correction.
- Documented systematic failures in risk estimation accuracy.
- https://arxiv.org/html/2602.04358

### 2.2 Tools in Production
- **Jira + Atlassian Intelligence**: AI-assisted project scoping and estimation.
- **Forecast PSA**: AI-native project/resource management with automated scoping and budgeting.
- **Azure DevOps + GitHub Copilot**: Integration for sprint estimation.
- **ChatGPT / Claude**: Used ad-hoc for project scoping and feasibility brainstorming.

### 2.3 Quantitative Data
- LLM-based effort estimation shows promising but inconsistent accuracy; best results come from fine-tuned models on domain-specific datasets (ISBSG).
- 50% of LLM outputs for risk assessment require expert correction.
- Hybrid models (LLM + traditional estimation methods) outperform either approach alone.

### 2.4 Challenges
- LLMs exhibit systematic failures in risk estimation accuracy.
- Hallucination risks in cost/effort predictions.
- Limited domain-specific training data for software estimation tasks.
- Difficulty comprehending complex project dependencies.

---

## 3. STAGE 2: REQUIREMENTS ELICITATION AND ANALYSIS

### 3.1 Key Papers

**Panigo, J. M., Diaz, F. J. et al. "Inteligencia Artificial en Ingenieria de Software." XXX Argentine Congress of Computer Sciences (CACIC), La Plata, Argentina, October 7--11, 2024.**
- Analyzed feasibility of using LLMs in software engineering processes.
- Applied various tools for generating interviews in the requirements elicitation stage and in the analysis/specification stage through user stories.
- http://sedici.unlp.edu.ar/handle/10915/178398

**Sami, M. A., Waseem, M., Zhang, Z., Rasheed, Z., Systa, K., & Abrahamsson, P. "Early Results of an AI Multiagent System for Requirements Elicitation and Analysis." In: Product-Focused Software Process Improvement (PROFES 2024), Tartu, Estonia, December 2024. Springer LNCS vol. 14483.**
- Multi-agent system deploying AI models to generate user stories from initial requirements, assess/improve quality, and prioritize them.
- Empirically investigates effectiveness of LLMs in automating requirements analysis tasks.
- https://dl.acm.org/doi/10.1007/978-3-031-78386-9_20

**Also published as preprint: arXiv:2409.00038, August 2024.** https://arxiv.org/abs/2409.00038

**Gaire, N. et al. "Advancing Requirements Engineering through Generative AI." 2024.**
- Focuses on leveraging LLMs for requirements engineering tasks.
- https://nzjohng.github.io/publications/papers/gaire2024.pdf

**Kim, J. et al. "Exploring the Use of LLMs for Requirements Specification in an IT Consulting Company." arXiv:2507.19113, July 2025.**
- Reports on using LLMs in IT consulting for automating requirements specification.
- Investigated GPT-3.5-turbo, GPT-4o, and Llama-3-70B for generating Epic FDS and user stories.
- https://arxiv.org/html/2507.19113v1

**Gonzalez, R. et al. "Can LLMs Generate User Stories and Assess Their Quality?" arXiv:2507.15157, July 2025.**
- 10 state-of-the-art LLMs evaluated for automated user story generation via customer interview emulation.
- LLMs can generate user stories similar to humans in coverage and stylistic quality but exhibit lower diversity and creativity.
- LLMs can reliably assess semantic quality with clear evaluation criteria.
- https://arxiv.org/abs/2507.15157

**Fakhoury, S. et al. "LLM-Based Agents for Automating the Enhancement of User Story Quality: An Early Report." Springer, 2024.**
- Examines LLMs for enhancing user story analysis in agile contexts.
- https://link.springer.com/chapter/10.1007/978-3-031-61154-4_8

**Zhao, W. et al. "Elicitron: An LLM Agent-Based Simulation Framework for Design Requirements Elicitation." arXiv:2404.16045, April 2024.**
- LLM-based agents represent simulated users who engage in product interactions.
- Provides insights into user needs by articulating actions, observations, and challenges.
- https://arxiv.org/abs/2404.16045

**Frontiers review: "Research directions for using LLM in software requirement engineering: a systematic review." Frontiers in Computer Science, 2025.**
- Prompt engineering strategies: Zero-shot (44%), Few-shot (29%) dominate.
- GPT-based models lead adoption (90%).
- https://www.frontiersin.org/journals/computer-science/articles/10.3389/fcomp.2025.1519437/full

### 3.2 Tools in Production
- **ChatGPT / GPT-4o**: Requirements brainstorming, user story generation.
- **Claude**: Requirements specification, interview simulation.
- **Llama 3**: Open-source alternative for requirements analysis.
- **MARE framework**: Multi-phase RE framework (elicitation, modeling, verification, specification).
- **Elicitron**: Simulated-user framework for design requirements.

### 3.3 Quantitative Data
- GPT-based models account for 90% of RE research usage.
- LLMs match human coverage and stylistic quality for user stories but show lower diversity and creativity.
- Zero-shot prompting used in 44% of RE studies; Few-shot in 29%.

### 3.4 Challenges
- Difficulty with domain-specific language subtleties.
- Hallucination in requirements generation.
- Inability to comprehend complex dependencies across requirements.
- Lower diversity and creativity than human analysts.
- Elicitation and validation remain the most active but challenging focus areas.

---

## 4. STAGE 3: SOFTWARE DESIGN AND ARCHITECTURE

### 4.1 Key Papers

**Galster, M. et al. "Artificial Intelligence for Software Architecture: Literature Review and the Road Ahead." arXiv:2504.04334, April 2025.**
- Systematic literature review analyzing 18 research articles.
- Despite widespread AI impact on SE, explicit application to software architecture remains relatively under-explored.
- 2024 shows steep increase (10 articles); 5 articles in early 2025.
- 73% of models used are decoder-only (GPT, Llama, DeepSeek); 21% encoder-only (BERT); 7% encoder-decoder.
- https://arxiv.org/html/2504.04334v1

**Gopalakrishnan, R. et al. "Software Architecture Meets LLMs: A Systematic Mapping Study." arXiv:2505.16697, May 2025.**
- Comprehensive mapping of how LLMs are being applied to software architecture tasks.
- https://arxiv.org/pdf/2505.16697

**Garcia, A. et al. "Generative AI for Software Architecture. Applications, Challenges, and Future Directions." arXiv:2503.13310, March 2025.**
- Reviews generative AI applications across software architecture tasks.
- https://arxiv.org/html/2503.13310v2

**Dhar, S. et al. "DRAFT-ing Architectural Design Decisions using LLMs." 2025.**
- Novel approach combining RAG and fine-tuning for generating Architectural Design Decisions (ADDs).
- Two-phase approach: offline fine-tuning + online generation.
- https://arxiv.org/pdf/2506.22688

**Helmi, A. "ARLO: A Tailorable Approach for Transforming Natural Language Software Requirements into Architecture using LLMs." 2025.**
- Automated transformation of NL requirements into architectural designs.

**De Luca, V. et al. "LLM-Based Explainability at Design Time: Detecting Elasticity Antipatterns in Software Architectures." Springer, 2025.**
- Uses LLMs to detect antipatterns in software architectures at design time.
- https://link.springer.com/chapter/10.1007/978-3-032-04403-7_14

**Perez, M. et al. "LLM-Based Quality Assessment of Software Architecture Diagrams: A Preliminary Study with Four Open-Source Projects." Springer, 2025.**
- Evaluates LLMs for assessing quality of architecture diagrams.
- https://link.springer.com/chapter/10.1007/978-3-032-02138-0_8

**Taibi, D. et al. "Exploring Architectural Smells Detection Through LLMs." Springer, 2025.**
- LLMs applied to detect architectural smells in software systems.
- https://link.springer.com/chapter/10.1007/978-3-032-02138-0_6

### 4.2 Tools in Production
- **ChatGPT / Claude**: Architecture brainstorming, design pattern recommendations, diagram generation.
- **GitHub Copilot**: In-IDE architecture suggestions, API design.
- **Cursor / Claude Code**: Full-project architectural analysis and refactoring.
- **Eraser.io**: AI-generated architecture diagrams.
- **Various DB design tools**: LLM-assisted schema generation (natural language to SQL DDL).

### 4.3 Quantitative Data
- Research output surging: 10 articles in 2024, 5 already in early 2025 (vs. minimal before 2023).
- DeepSeek and Qwen gained traction in 2024--2025, signaling shift toward emerging alternatives.
- GPT-based models dominate (73% decoder-only).

### 4.4 Challenges
- Software architecture remains relatively under-explored compared to coding tasks.
- LLMs struggle with system-level architectural reasoning across large codebases.
- Validation of architectural decisions generated by AI is difficult.
- Limited benchmarks for architecture-specific tasks.

---

## 5. STAGE 4: IMPLEMENTATION / CODING

### 5.1 Key Papers

**Peng, S., Kalliamvakou, E., Cihon, P., & Demirer, M. "The Impact of AI on Developer Productivity: Evidence from GitHub Copilot." arXiv:2302.06590, February 2023. Published in Communications of the ACM, March 2024.**
- Controlled experiment with N=95 freelance programmers implementing an HTTP server in JavaScript.
- Treatment group completed task 55.8% faster.
- Heterogeneous effects suggest AI pair programmers can help transition into software careers.
- https://arxiv.org/abs/2302.06590

**METR. "Measuring the Impact of Early-2025 AI on Experienced Open-Source Developer Productivity." arXiv:2507.09089, July 2025.**
- Randomized controlled trial: 16 experienced developers, 246 tasks on their own mature projects.
- AI tools (Cursor Pro + Claude 3.5/3.7 Sonnet) increased completion time by 19%.
- Developers predicted AI would reduce time by 24%; actual result was +19% (43-point perception gap).
- AI least effective when developers had deep prior expertise and did not need documentation.
- https://arxiv.org/abs/2507.09089

**Jaspan, C. et al. (Google). "Developer Productivity With and Without GitHub Copilot: A Longitudinal Study." arXiv:2509.20353, September 2025.**
- Longitudinal study examining sustained productivity impacts.
- https://arxiv.org/pdf/2509.20353

**Singla, A. et al. "Experience with GitHub Copilot for Developer Productivity at Zoominfo." arXiv:2501.13282, January 2025.**
- Industry case study documenting real-world enterprise deployment.
- https://arxiv.org/html/2501.13282v1

**Wang, Y. et al. "LLMs: A game-changer for software engineers?" ScienceDirect (Journal of Computer Languages), 2025.**
- Comprehensive analysis of LLM impact on software engineering practice.
- https://www.sciencedirect.com/science/article/pii/S2772485925000171

### 5.2 Tools in Production

| Tool | Type | Key Feature |
|------|------|-------------|
| **GitHub Copilot** | IDE plugin | 15M+ users, autocomplete + chat, 90% Fortune 100 adoption |
| **Cursor** | AI-native IDE | Fast autocomplete, integrated chat, agent mode for medium-scope tasks |
| **Claude Code** | Terminal-native agent | 200K token context, large codebase refactoring, deep architectural understanding |
| **Windsurf (Cognition)** | AI IDE | First IDE with integrated agent mode, $15/month, now owned by Cognition/Devin team |
| **Devin (Cognition)** | Autonomous agent | Fully autonomous SE agent; 13.86% on original SWE-bench (first baseline) |
| **Amazon Q Developer** | IDE plugin + chat | Evolved from CodeWhisperer; integrated with AWS ecosystem |
| **Google Gemini Code Assist** | IDE plugin + chat | Part of Google Cloud ecosystem; Gemini 2.5 Pro-powered |
| **Tabnine** | IDE plugin | Focus on privacy/security; on-premise deployment option |
| **Augment Code** | Agent | Record-breaking SWE-bench score combining Claude Sonnet + O1 |
| **Codex (OpenAI)** | Cloud agent | Asynchronous task execution in sandboxed environments |

### 5.3 Quantitative Data

**GitHub Copilot Metrics:**
- 55% faster task completion (controlled experiment, Peng et al.).
- Code suggestion acceptance rate: 21.2%--23.5%.
- Code quality improvements: readability +3.62%, reliability +2.94%, maintainability +2.47%, conciseness +4.16% (all statistically significant).
- 73% of developers say it helps them "stay in the flow."
- 87% say it preserves mental effort during repetitive tasks.

**METR Study (Contrasting):**
- Experienced developers: 19% slower with AI tools (vs. 24% faster predicted).
- Finding specific to expert developers working on their own mature codebases.

**Market Adoption:**
- 85% of developers regularly use AI tools (JetBrains 2025).
- 41% of all code written in 2025 was AI-generated (JetBrains 2025).
- 97% of developers have tried AI tools (GitHub 2024).

### 5.4 Challenges
- Perception vs. reality gap: developers overestimate AI productivity gains.
- AI may slow down experts on familiar codebases while helping novices.
- Context window limitations for large-scale projects.
- Higher code churn (code rewritten within 2 weeks).
- Sustainability of pricing models (Cursor unlimited usage becoming unsustainable).

---

## 6. STAGE 5: TESTING

### 6.1 Key Papers

**Wang, J. et al. "Software Testing with Large Language Models: Survey, Landscape, and Vision." IEEE Transactions on Software Engineering, 2024.**
- Comprehensive review of 102 studies on LLMs for testing.
- LLMs successfully applied for unit test generation, test oracle generation, and system test input generation.
- https://dl.acm.org/doi/10.1109/TSE.2024.3368208

**Dakhel, A. M. et al. "Effective Test Generation Using Pre-trained Large Language Models and Mutation Testing." Information and Software Technology, 2024.**
- MuTAP: augments prompts with surviving mutants to improve test effectiveness.
- Detects up to 28% more faulty human-written code snippets than baseline.
- 17% of bugs remain undetected by both automated tools (Pynguin) and LLMs.
- https://www.sciencedirect.com/science/article/abs/pii/S0950584924000739

**Tufano, R. et al. "On the Use of Large Language Models in Mutation Testing." arXiv:2406.09843, June 2024.**
- Large-scale evaluation: 6 LLMs, 851 real-world bugs across two Java benchmarks (Defects4J 2.0, ConDefects).
- GPT-4o: 93.4% fault detection rate vs. LEAM 71.7%, PIT 51.3%, Major 74.4%.
- LLMs generate more diverse mutations behaviorally closer to real bugs.
- https://arxiv.org/html/2406.09843v2

**Macklon, K. et al. "LLMorpheus: Mutation Testing Using Large Language Models." IEEE TSE, 2025.**
- Mutation testing tool for JavaScript using LLMs to suggest mutants via placeholders.
- Evaluated on 13 subject packages.
- https://ieeexplore.ieee.org/iel8/32/11048386/10977824.pdf

**Meta Engineering. "Mutation-Guided LLM-based Test Generation at Meta." FSE 2025 (Industry Papers).**
- Automated Compliance Hardening (ACH) tool deployed across Facebook, Instagram, WhatsApp, Meta wearables.
- Privacy engineers accepted 73% of generated tests; 36% judged privacy-relevant.
- Trial: October--December 2024.
- https://conf.researchr.org/details/fse-2025/fse-2025-industry-papers/16/Mutation-Guided-LLM-based-Test-Generation-at-Meta

**Systematic Review on LLM-Based Unit Testing (2025).**
- Analyzed 105 papers (up to March 2025).
- Test generation dominates: ~60% of total research volume.
- Explosive growth: 1 paper in 2021, 2 in 2022, 14 in 2023, 73 in 2024, 15 by March 2025.

**Barr, E. et al. "Large Language Models for Software Testing: A Research Roadmap." arXiv:2509.25043, September 2025.**
- Semi-systematic review identifying knowledge gaps in LLM-based testing.
- https://arxiv.org/html/2509.25043v1

### 6.2 Tools in Production
- **Meta ACH**: Production mutation-guided test generation across Meta platforms.
- **Copilot for Tests**: Generates unit tests inside VS Code.
- **Codium AI (Qodo)**: AI-powered test generation and review.
- **Diffblue Cover**: AI-powered Java unit test generation (enterprise).
- **Pynguin**: Automated Python test generation (baseline tool).
- **EvoSuite**: Search-based Java test generation (traditional baseline).

### 6.3 Quantitative Data
- GPT-4o achieves 93.4% fault detection rate (vs. 51--74% for traditional tools).
- LLM mutation-based testing detects 28% more bugs than baseline.
- Meta: 73% acceptance rate for AI-generated compliance tests.
- Research volume: 73 papers published in 2024 alone on LLM-based testing.
- Test generation accounts for ~60% of all LLM testing research.

### 6.4 Challenges
- Generating meaningful test oracles remains difficult.
- Flaky test generation with LLMs.
- Limited ability to test non-functional requirements (performance, security).
- LLMs may generate tests that "game" coverage metrics without meaningful assertions.
- Integration testing and system-level testing remain largely manual.

---

## 7. STAGE 6: DEPLOYMENT AND DEVOPS

### 7.1 Key Papers and Reports

**Joshi, S. "A Review of Generative AI and DevOps Pipelines: CI/CD, Agentic Automation, MLOps Integration, and Large Language Models." SSRN, 2025.**
- Reviews 50 key research works (2023--2025).
- Analysis of AI-driven solutions across SDLC including infrastructure management and CI/CD.
- https://papers.ssrn.com/sol3/Delivery.cfm/5290005.pdf?abstractid=5290005

**Pereira, M. et al. "Comparative Analysis of AI-Driven Security Approaches in DevSecOps: Challenges, Solutions, and Future Directions." arXiv:2504.19154, April 2025.**
- Academic research spanning 2015--2024, mostly published from 2022 onwards.
- https://arxiv.org/html/2504.19154v1

**Goncalves, R. et al. "AI Techniques in the Microservices Life-Cycle: A Systematic Mapping Study." Computing (Springer), 2025.**
- Maps AI technologies used in microservices including deployment, monitoring, and scaling.
- https://link.springer.com/article/10.1007/s00607-025-01432-z

### 7.2 Tools in Production
- **Netflix**: ML-enabled chaos engineering for system reliability during deployments.
- **Google**: AI-optimized Kubernetes-based CI/CD pipelines for resource efficiency.
- **Harness**: AI-powered continuous delivery platform with automated rollbacks.
- **Datadog AI**: AI-driven monitoring, anomaly detection, root cause analysis.
- **PagerDuty AIOps**: Intelligent incident management and alerting.
- **Spacelift**: AI-enhanced Infrastructure as Code management.
- **Kubecost + AI**: AI-optimized Kubernetes resource allocation.

### 7.3 Quantitative Data
- DevOps for LLM accelerates CI/CD, boosting release speed by 35% (2025 data).
- LLMs help predict failures and generate scripts, cutting deployment time by 40% (2025 CNCF survey).
- 67% of DevOps teams increased investment in AI for DevOps in 2024--2025.
- However, 73% of respondents have yet to adopt AI in CI/CD workflows (JetBrains 2025).
- Significant gap between AI DevOps potential and actual implementation.

### 7.4 Challenges
- Low actual adoption despite high investment intent (73% not yet using AI in CI/CD).
- Security concerns with AI-generated infrastructure configurations.
- Reliability and trust issues for production deployments.
- Difficulty integrating AI into existing CI/CD pipelines.
- Observability and explainability of AI-driven deployment decisions.

---

## 8. STAGE 7: EVOLUTION AND MAINTENANCE

### 8.1 Key Papers

**Nogueira, M. et al. "ACE: Automated Technical Debt Remediation with Validated Large Language Model Refactorings." arXiv:2507.03536, July 2025.**
- GPT-4 detects 86.7% of real-world refactoring opportunities across 20 Java projects.
- Generated functionally correct refactorings only 37% of the time.
- With validation: 98% of remaining refactorings improve code health while retaining original behavior.
- Precision elevated from 37% to 98% via validation pipeline.
- https://arxiv.org/html/2507.03536v1

**Alomar, E. et al. "LLM-Driven Code Refactoring: Opportunities and Limitations." Queen's University, 2025.**
- Systematic analysis of where LLMs succeed and fail in refactoring tasks.
- https://seal-queensu.github.io/publications/pdf/IDE-Jonathan-2025.pdf

**Paltenghi, M. et al. "AI-powered Code Review with LLMs: Early Results." arXiv:2404.18496, 2024.**
- Examines effectiveness of LLMs for automated code review.
- https://arxiv.org/html/2404.18496v2

**Santos, J. et al. "Investigating The Smells of LLM Generated Code." arXiv:2510.03029, October 2025.**
- Extended study on code smells in LLM-generated code.
- https://arxiv.org/html/2510.03029v1

**Kacimi, S. et al. "PromptDebt: A Comprehensive Study of Technical Debt Across LLM Projects." arXiv:2509.20497, September 2025.**
- Identifies "prompt smells" and "prompt requirement smells" as new forms of technical debt.
- Poor prompt engineering practices compromise model performance.
- https://arxiv.org/html/2509.20497v1

**Okesola, O. et al. "Automating documentation and legacy code modernization: Revitalizing legacy systems with AI." World Journal of Advanced Engineering Technology and Sciences, 2025.**
- Reviews AI approaches for legacy system documentation and modernization.
- https://journalwjaets.com/content/automating-documentation-and-legacy-code-modernization-revitalizing-legacy-systems-ai

**Using LLMs to Enhance Code Quality: A Systematic Literature Review. ScienceDirect, 2025.**
- Analyzed 49 studies on LLMs for refactoring, smell detection, and code improvement (up to September 2024).
- https://www.sciencedirect.com/science/article/abs/pii/S095058492500299X

### 8.2 Tools in Production
- **SonarQube + AI**: Traditional static analysis augmented with AI insights.
- **CodeRabbit**: AI-first PR reviewer; 2M+ repositories, 13M+ PRs reviewed.
- **Snyk + AI**: AI-enhanced security vulnerability detection.
- **Claude Code / Cursor**: Large-scale refactoring and legacy codebase understanding.
- **AWS Transformation tools**: COBOL-to-Java migration assistance.
- **ModLogix**: Legacy modernization platform leveraging generative AI.

### 8.3 Quantitative Data
- GPT-4 detects 86.7% of refactoring opportunities but generates correct refactorings only 37% of the time (98% with validation).
- GPT-4 code smell detection: precision 0.79, F1 0.54 (surpassing SonarQube), recall 0.41.
- Detailed prompts improve smell detection from 64% to 82%.
- 63% of businesses trialling generative AI for code maintenance tasks (2024).
- 40% of IT budgets dedicated to addressing technical debt from legacy systems by 2025 (Gartner).
- 62% of developers cite technical debt as top frustration (Stack Overflow 2024).
- GitClear: 8x increase in code blocks with 5+ duplicated lines during 2024.

### 8.4 Challenges
- LLM-generated refactorings are functionally correct only 37% of the time without validation.
- Validation/verification pipelines are essential but add complexity.
- Cross-language migration (COBOL to Java) still requires significant human oversight.
- AI may increase technical debt while trying to reduce it (paradox).
- New form of technical debt: "prompt debt" from poor prompt engineering.
- 60% report reduced effort for routine refactoring; but only 2.5/5 rating for major adjustments.

---

## 9. STAGE 8: PROJECT MANAGEMENT

### 9.1 Key Papers

**Garcia, J. et al. "AI-Driven Decision Support Systems in Agile Software Project Management: Enhancing Risk Mitigation and Resource Allocation." MDPI Systems, 2025.**
- Framework achieved 94% accuracy in risk identification.
- Enhanced workload management by 25%.
- 18% improvement in sprint completion rates.
- https://www.mdpi.com/2079-8954/13/3/208

**Bui, T.-L. "An LLM-based multi-agent framework for agile effort estimation." arXiv:2509.14483, September 2025.**
- SEEAgent for agile effort estimation and sprint planning.
- https://www.arxiv.org/pdf/2509.14483

**Psaltis, E. et al. "Cognitive Agents Powered by Large Language Models for Agile Software Project Management." MDPI Electronics, January 2025.**
- Cognitive agents for automated project management tasks.
- https://www.mdpi.com/2079-9292/14/1/87

**Santos, R. et al. "Integrating Generative AI for Advancing Agile Software Development and Mitigating Project Management Challenges." ResearchGate, 2024.**
- Examines GenAI integration in agile workflows.
- https://www.researchgate.net/publication/379523708_Integrating_Generative_AI_for_Advancing_Agile_Software_Development_and_Mitigating_Project_Management_Challenges

### 9.2 Tools in Production

| Tool | AI Features |
|------|------------|
| **Atlassian/Jira (AI)** | AI agents for project plans, trend identification, risk flagging. 2025 Gartner Magic Quadrant Leader. |
| **ClickUp Brain** | Custom AI agents, automated progress tracking, workflow triggers. |
| **Asana AI (Smart Assists)** | Instant summaries, risk highlighting, AI Studio for custom workflows. |
| **Linear** | AI-powered issue summarization, Triage Intelligence for auto-categorization/prioritization. |
| **Forecast PSA** | AI-native project/resource management, automated budgeting and capacity planning. |
| **Monday.com AI** | AI-powered workload balancing and timeline prediction. |

### 9.3 Quantitative Data
- 94% accuracy in AI-driven risk identification.
- 25% improvement in workload management.
- 18% improvement in sprint completion rates.
- AI-assisted planning reduces administrative overhead by automating task assignment and reporting.

### 9.4 Challenges
- AI recommendations need human validation for strategic decisions.
- Difficulty capturing implicit team dynamics and organizational context.
- Integration with existing PM workflows remains complex.
- Risk of over-reliance on AI predictions without understanding limitations.

---

## 10. AI AGENT CAPABILITIES AND BENCHMARKS

### 10.1 SWE-bench Scores (Evolution)

**SWE-bench Original (2024):**
- Devin: 13.86% (first agent to substantially exceed 1.96% baseline).
- Represented a major milestone in autonomous software engineering.

**SWE-bench Verified (Q4 2025):**
- Top AI agents: 50--65% resolution rate on real GitHub issues.
- Claude 3.7 Sonnet: 62.3%.
- Gemini 2.5 Pro: 63.8%.
- Claude Code: 72%+ (running fully locally).
- Augment Code: Highest recorded score (combining Claude Sonnet 3.7 + O1).
- Source: https://www.swebench.com/ and https://epoch.ai/benchmarks/swe-bench-verified

**HumanEval (Code Generation):**
- 63 models evaluated; top models exceed 90% Pass@1.
- 164 programming problems assessing language comprehension, algorithms, and mathematics.
- Source: https://llm-stats.com/benchmarks/humaneval

**AutoCodeBench (2025):**
- 3,920 problems across multiple languages.
- Claude Opus 4 consistently ranks first in both reasoning and non-reasoning modes.
- Source: https://arxiv.org/html/2508.09101v1

### 10.2 Key Benchmark Papers

**Jimenez, C. E. et al. "SWE-bench: Can Language Models Resolve Real-World GitHub Issues?" ICLR 2024.**
- The foundational benchmark for evaluating AI agents on real-world software engineering tasks.

**Rasheed, Z. et al. "Software Development Life Cycle Perspective: A Survey of Benchmarks for Code LLMs and Agents." arXiv:2505.05283, May 2025.**
- Comprehensive survey of benchmarks across all SDLC phases.
- https://arxiv.org/html/2505.05283v2

### 10.3 Tool Comparison Summary (Late 2025 / Early 2026)

| Agent | Strengths | Limitations |
|-------|-----------|-------------|
| **Claude Code** | 200K context, deep architectural understanding, terminal-native, best for large refactors | CLI-only interface |
| **Cursor** | Fast autocomplete, smooth flow, good for small-medium tasks | Struggles with long-running refactors, looping behavior |
| **Windsurf** | Affordable ($15/mo), first IDE with agent mode, smooth UX | Divided opinions on keeping pace with competitors |
| **Devin** | Full autonomy, end-to-end task handling | Expensive, slower, limited success rate on complex tasks |
| **GitHub Copilot** | Massive user base, deep IDE integration, enterprise trust | More autocomplete than agent; less capable on autonomous tasks |
| **Augment Code** | Record SWE-bench scores, multi-model approach | Newer, less mature ecosystem |

---

## 11. CODE QUALITY WHEN USING AI

### 11.1 Key Studies

**GitClear. "AI Copilot Code Quality: 2025 Data Suggests 4x Growth in Code Clones." February 2025.**
- Database of 211 million lines of structured code change data (2020--2024).
- Code associated with refactoring sank from 25% (2021) to <10% (2024).
- "Copy/pasted" (cloned) lines rose from 8.3% to 12.3%.
- 8x increase in code blocks with 5+ duplicated lines during 2024.
- New code revised within 2 weeks: 3.1% (2020) to 5.7% (2024) -- rising to 7.9% of all newly added code.
- https://www.gitclear.com/ai_assistant_code_quality_2025_research

**CodeRabbit. "State of AI vs Human Code Generation Report." December 2025.**
- Analyzed 470 open-source GitHub PRs.
- AI-generated PRs: 10.83 issues each vs. human-generated: 6.45 issues (1.7x more).
- AI code 1.88x more likely to introduce improper password handling.
- AI code 1.91x more likely for insecure object references.
- AI code 2.74x more likely for XSS vulnerabilities.
- AI code 1.82x more likely for insecure deserialization.
- XSS: AI fails to generate secure code 86% of the time.
- Log injection: insecure code generated 88% of the time.
- https://www.coderabbit.ai/blog/state-of-ai-vs-human-code-generation-report

**Apiiro Research. "4x Velocity, 10x Vulnerabilities: AI Coding Assistants Are Shipping More Risks." 2025.**
- Security vulnerabilities rise 1.5--2x in AI-written code.
- Code readability problems increase 3x+.
- AI-assisted developers exposed Azure credentials nearly twice as often.
- https://apiiro.com/blog/4x-velocity-10x-vulnerabilities-ai-coding-assistants-are-shipping-more-risks/

**"Assessing the Quality and Security of AI-Generated Code: A Quantitative Analysis." arXiv:2508.14727, 2025.**
- Quantitative analysis of security and quality in AI-generated code.
- https://arxiv.org/abs/2508.14727

**Frontiers in Big Data. "A systematic literature review on the impact of AI models on the security of code generation." 2024.**
- Comprehensive review of security implications.
- https://www.frontiersin.org/journals/big-data/articles/10.3389/fdata.2024.1386720/full

### 11.2 Positive Quality Indicators (GitHub Research)
- Readability improved by 3.62%.
- Reliability improved by 2.94%.
- Maintainability improved by 2.47%.
- Conciseness improved by 4.16%.
- All improvements were statistically significant.
- (Note: These are GitHub's own studies on Copilot, which may have methodological biases.)

### 11.3 Summary of Quality Concerns
| Metric | Finding |
|--------|---------|
| Issue density | AI PRs have 1.7x more issues than human PRs |
| Security vulnerabilities | 1.5--2x higher in AI code |
| Code duplication | 8x increase in cloned blocks (2024) |
| Code churn | Revision within 2 weeks rose from 3.1% to 7.9% |
| XSS vulnerability rate | AI fails 86% of the time |
| Credential exposure | Nearly 2x more frequent with AI assistance |
| Refactoring activity | Dropped from 25% to <10% of changes |

---

## 12. THE CHANGING ROLE OF THE SOFTWARE ENGINEER

### 12.1 Key Studies and Reports

**Gartner, Q4 2024 Survey of 400 SE Leaders (US/UK).**
- Up to half of software development teams employ GenAI tools.
- AI acts as force multiplier rather than replacement.
- New roles emerging: prompt engineers, AI integration specialists.
- 80% of engineering workforce will need to upskill by 2027.
- https://www.gartner.com/en/newsroom/press-releases/2024-10-03-gartner-says-generative-ai-will-require-80-percent-of-engineering-workforce-to-upskill-through-2027

**Modestino, A. et al. "The Impact of Generative AI on Job Opportunities for Junior Software Engineers." Northeastern University, 2025.**
- After ChatGPT release, postings requiring 0--3 years of experience declined sharply.
- Contraction in junior-level opportunities rather than increase in senior-level demand.
- https://aliciasassermodestino.com/wp-content/uploads/2025/06/Impact_of_GenAI_on_SWEs_061625.pdf

**Russo, D. "From Today's Code to Tomorrow's Symphony: The AI Transformation of Developer's Routine by 2030." arXiv:2405.12731, May 2024.**
- Envisions developer transformation from manual coders to AI orchestrators.
- https://arxiv.org/html/2405.12731v1

**Wu, Y. et al. "How AI Agents Are Transforming Software Engineering." IEEE Computer, 2025.**
- Engineers evolve to define strategic vision, set guardrails, and ensure AI alignment with business objectives.
- https://www.computer.org/csdl/magazine/co/2025/05/10970187/260SnIeoUUM

**Guerrero, A. et al. "Software engineering education in the era of conversational AI: current trends and future directions." Frontiers in Artificial Intelligence, 2024.**
- Examines how SE education must adapt to the AI era.
- https://www.frontiersin.org/journals/artificial-intelligence/articles/10.3389/frai.2024.1436350/full

**Pullflow. "State of AI Code Review 2025."**
- 1 in 7 PRs now involve AI agents (14.3%).
- https://pullflow.com/state-of-ai-code-review-2025

### 12.2 Key Trends
1. **From coder to orchestrator**: Engineers increasingly define requirements, validate outputs, and steer AI agents.
2. **AI-first mindset**: Natural-language prompt engineering and RAG skills becoming essential.
3. **Junior-level disruption**: Sharp decline in entry-level job postings post-ChatGPT.
4. **Upskilling imperative**: 80% of workforce needs upskilling by 2027 (Gartner).
5. **New metrics**: Industry shifting from lines-of-code to outcome-based productivity measures.
6. **Human-in-the-loop**: Up to 80% of programming jobs will remain human-centric despite automation.
7. **Competency perception bias**: Engineers using AI receive lower competency ratings for identical work (Microsoft 2025); effect doubled for women.

---

## APPENDIX: CITATION INDEX BY STAGE

### Feasibility & Estimation (6 sources)
1. Lopez-Martin et al. (2024) -- LLMs for cost/duration prediction
2. Hasnain et al. (2024) -- Effort estimation with LLM interfaces
3. Ali et al. (2025) -- AI cost estimation systematic review
4. Cabrera-Diego et al. (2025) -- LLMs for early-stage estimation mapping study
5. Bui (2025) -- SEEAgent multi-agent effort estimation
6. LLM Risk Assessment Framework (2026)

### Requirements (8 sources)
1. Panigo & Diaz et al. (CACIC 2024) -- AI in SE requirements
2. Sami et al. (PROFES 2024) -- Multi-agent RE system
3. Gaire et al. (2024) -- Advancing RE through GenAI
4. Kim et al. (2025) -- LLMs for requirements specification in consulting
5. Gonzalez et al. (2025) -- LLMs for user story generation/quality
6. Fakhoury et al. (2024) -- LLM agents for user story quality
7. Zhao et al. (2024) -- Elicitron simulation framework
8. Frontiers systematic review (2025) -- LLM in RE

### Design & Architecture (8 sources)
1. Galster et al. (2025) -- AI for software architecture literature review
2. Gopalakrishnan et al. (2025) -- Software architecture meets LLMs mapping study
3. Garcia et al. (2025) -- Generative AI for software architecture
4. Dhar et al. (2025) -- DRAFT-ing ADDs using LLMs
5. Helmi (2025) -- ARLO NL-to-architecture
6. De Luca et al. (2025) -- Elasticity antipatterns detection
7. Perez et al. (2025) -- Quality assessment of architecture diagrams
8. Taibi et al. (2025) -- Architectural smells detection

### Implementation/Coding (5 key papers + 10 tools)
1. Peng et al. (2023/2024) -- GitHub Copilot controlled experiment
2. METR (2025) -- 19% slower for experienced developers
3. Jaspan et al. (2025) -- Longitudinal study at Google
4. Singla et al. (2025) -- Copilot at Zoominfo
5. Wang et al. (2025) -- LLMs as game-changer for SE

### Testing (7 sources)
1. Wang et al. (2024) -- Software testing with LLMs survey (102 studies)
2. Dakhel et al. (2024) -- MuTAP mutation-guided testing
3. Tufano et al. (2024) -- LLMs in mutation testing (GPT-4o: 93.4%)
4. Macklon et al. (2025) -- LLMorpheus for JavaScript
5. Meta Engineering (FSE 2025) -- Mutation-guided testing at Meta
6. LLM-Based Unit Testing Systematic Review (2025) -- 105 papers
7. Barr et al. (2025) -- LLM testing research roadmap

### Deployment & DevOps (3 papers + 7 tools)
1. Joshi (2025) -- GenAI and DevOps pipelines review (50 works)
2. Pereira et al. (2025) -- AI-driven DevSecOps
3. Goncalves et al. (2025) -- AI in microservices lifecycle

### Evolution & Maintenance (7 sources)
1. Nogueira et al. (2025) -- ACE technical debt remediation
2. Alomar et al. (2025) -- LLM-driven refactoring
3. Paltenghi et al. (2024) -- AI-powered code review
4. Santos et al. (2025) -- Code smells in LLM code
5. Kacimi et al. (2025) -- PromptDebt
6. Okesola et al. (2025) -- Legacy modernization
7. ScienceDirect systematic review (2025) -- LLMs for code quality

### Project Management (4 sources + 6 tools)
1. Garcia et al. (2025) -- AI decision support in agile PM
2. Bui (2025) -- SEEAgent for agile estimation
3. Psaltis et al. (2025) -- Cognitive agents for agile PM
4. Santos et al. (2024) -- GenAI in agile development

### Overall/Cross-Cutting (12+ sources)
1. Stack Overflow Developer Survey 2024
2. JetBrains Developer Ecosystem 2024 & 2025
3. GitHub Octoverse 2024 & 2025
4. Microsoft New Future of Work Report 2025
5. Gartner Predictions 2024--2025
6. Hymel (2024) -- AI-Native SDLC
7. Liu et al. (2024) -- LLM-Based Agents for SE survey
8. Rasheed et al. (2025) -- SDLC benchmark survey
9. Nascimento et al. (2025) -- LLMs reshaping SE
10. GitClear Code Quality Report 2025
11. CodeRabbit AI vs Human Code Report 2025
12. METR Study (2025)

---

**Total unique sources identified: 75+**
**Date range: 2023--2026**
**Primary focus: 2024--2025**

---

*Report compiled: February 2026*
