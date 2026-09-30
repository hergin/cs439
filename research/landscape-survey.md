# CS 439 Agentic Software Engineering: Landscape Survey

Compiled 2026-09-25 for CS 439 Agentic Software Engineering, a new course in Spring 2027.

**Course context**
- Junior/senior undergraduate elective, about 30 students.
- Meets Tue/Thu 2:00–3:15 pm in RB130.
- Students mostly *use* coding agents rather than build them.
- Each student is required to buy the cheapest Claude Code or ChatGPT Codex subscription for 4–5 months.

**Verification legend:** unmarked items were opened and checked by the research agents. **(unverified)** means the item came only from secondary sources or search snippets. Prices, product names and URLs changed often in 2026, so **re-check everything in Dec 2026 and Jan 2027.**

---

## 0. Top takeaways

1. **Peer courses already exist and are a direct benchmark.**
   - Geng et al. (Aug 2026) analyzed 23 US upper-division AI-assisted SE syllabi: https://arxiv.org/abs/2608.05898
     - About half the grade is projects (median 50%); proctored exams are rare (3 of 23).
     - AI use was *required* in graded work.
     - Claude Code is the tool named most often (6 courses).
   - Their recommendation: add AI skills on top of SE fundamentals rather than teach the tool for its own sake.
2. **The closest models for this course:**
   - **CMU 17-316**, and its adaptation at **Memphis COMP 4991**, a regional school.
   - **NJIT CS 485**, designed for mixed SE backgrounds.
   - **Stanford CS146S**, public materials but assumes more background.
   - **Northeastern CS 7180**, master's level, with very detailed rubrics.
   - **MIT Missing Semester, "Agentic Coding" lecture** as a week-1 reading.
3. **The common course structure:**
   - One semester-long team project run as lifecycle sprints: requirements → spec → frontend → backend → test → deploy → demo. This also teaches SE basics to juniors who haven't taken SE.
   - Protected human-only work: reflections, peer reviews, quizzes.
   - Required AI-use logs.
   - The rule "Don't submit code you can't explain."
4. **The central teaching tension is productivity versus understanding.**
   - Agents make students faster but reduce comprehension and later ability to extend their own code (Balepur et al. 2026; Shen & Tamkin 2026).
   - Design response: "modify without the agent" checkpoints, grading the process (session transcripts), and explicit teaching of conceptual questioning.
5. **Verification is the core skill, and code review is the hardest one for students.** Make review, testing and security analysis graded deliverables.
6. **Equity: stronger paid models widen the gap between strong and weak students** (Kataoka et al., ICSE-SEET 2026). Required equivalent tools for everyone is defensible, but price parity between the two options matters (see §4).
7. **Portable assignments are feasible.**
   - Claude Code reads `AGENTS.md` when a repo has no `CLAUDE.md`.
   - Both tools use `SKILL.md`.
   - Ship only `AGENTS.md` in assignment repos.
8. **Curricula lag behind practice.** CS2023 and SWEBOK v4 do not cover coding agents, so the course must justify itself from the research literature (§2).

---

## 1. Peer university courses

### 1a. Undergraduate courses where students use coding agents (most relevant)

| Course | Instructor, term | Prereq / background | Structure and notable features | Grading | URL |
|---|---|---|---|---|---|
| **CMU 17-316/616: AI Tools for Software Development** | Begel & Henley, Fall 2025 | None official (Python) | 2-week cycle: pair programming, then **mob programming** (the class directs one AI tool), then a 500-word reflection, then presentations. Team "startup imitation" project, P1–P7: requirements, dev spec, frontend, backend, testing, deploy, demo. **User interviews are done without AI.** | In-class 46%, project 42%, essays 12%; no exams. Essays AI-free | https://ai-developer-tools.github.io |
| **Memphis COMP 4991** (adapts CMU 17-316) | Scott Fleming, Spring 2026 | CS3 (Intro to Software Design) | Same design as CMU. Each student leads one mob session. Figma AI for mockups. Readings include Anthropic Academy and Cursor Learn. | 46/42/12, no exams | https://www.memphis.edu/cs/courses/syllabi/4991.pdf |
| **NJIT CS 485/698: AI-Assisted SE** | Martin Kellogg, Spring 2026 | None; extra reading for students without SE | Build a competitor to a real product, milestones P0–P7. 7 reflection essays. **Students must submit logs of all LLM interactions.** At least one paid agentic tool required (Claude Code, Cursor or Codex). | Project 50%, reflections 18%, participation 32% | https://kelloggm.github.io/martinjkellogg.com/teaching/cs485-sp26/ |
| **Stanford CS146S: The Modern Software Developer** | Mihail Eric, Fall 2025 & 2026 | CS111/161 | Weekly topics: prompting, MCP, context engineering, Claude Code, security (Semgrep), AI code review, UI prototyping, ops. Heavy industry speakers. Fall 2026 adds skills, AGENTS.md, background agents, "software factory". | Final project 80% (2025, unverified). Open-source PRs 30% (2026, unverified) | https://themodernsoftware.dev ; assignments: https://github.com/mihail911/modern-software-dev-assignments |
| **Michigan EECS 498-016: Applied Agentic SE** | Marcus Darden, Fall 2026 | EECS 281 + 201 | Apply → Analyze → Create in one growing repo. Students use Aider, then build their own agent with evals and permissions. **Zero cost** (local Ollama models). In-person hackathons verify understanding. | Project phases 90%, no exams | https://eecs498-aase.github.io ; slides: https://github.com/eecs498-aase/materials |
| **UT Austin CS 378: Agentic SE** | Emmett Witchel, Fall 2026 | Systems (CS 439) | Systems judgment plus agent practice: sandboxing, prompt injection, subagents, cost. Uses Claude Code and Codex through **university accounts**. Includes a PR round reviewing a classmate's repo. | HW 58%, final 30%, AI-free quizzes 12% | https://www.cs.utexas.edu/~witchel/378AC/ |
| **UW CSE 490A2: AI-Assisted Software Development** | Michael Ernst, Autumn 2025 | CSE 331/333/340/341 | The programmer as team lead of agents. One SE task per week on a staff codebase, with multiple tools tried. 2 credits. | Not public | https://courses.cs.washington.edu/courses/cse490a2/25au/ |
| **UMD CMSC 398Z: Coding with AI** | Pugh & Willis, Fall 2025 | CMSC 330/320 | Seminar with in-class pair work. Progresses from Copilot to `llm` to Claude Code. Weekly mini-projects; CI; AI code review (CodeRabbit). | Learning log 40%, participation 40%, code 20% | https://www.cs.umd.edu/class/fall2025/cmsc398z/ |
| **CMU 15-113: Effective Coding with AI** | Mike Taylor, Spring & Fall 2026 | CS1 only | Portfolio, web app and capstone. The class builds a shared best-practices page. Document AI use in comments; you must be able to explain your code. | HW 20%, participation 20%, projects 40%, AI-free exams 20% | https://www.cs.cmu.edu/~mdtaylor/113/S26/ |
| **UVA CS 4501: SE and LLMs** | Sebastian Elbaum, Fall 2025 | SE recommended, not required | Follows the SE lifecycle with LLMs, with in-class experiments. | Attendance 20%, assignments 50%, project 30% | https://www.cs.virginia.edu/~se4ja/files/seLLMs.html |
| **UCSD CSE 190/291P: GenAI and Programming** | Politz & Polikarpova, Spring 2026 | Git, testing, CLI | 4 open-ended projects, each going demo → **peer review** → revision. AI banned for human-to-human writing. About $100/quarter in API costs. | Threshold grading | https://ucsd-cse-115-215.github.io/sp26/ |
| **Northwestern CS 397: Applied AI for Software Development** | Hamilton Murrah, Spring 2025 onward | Seniors (30 students) | Team full-stack app with design docs, stand-ups and interviews with practicing engineers. Fundamentals first. | Not public | [course page](https://www.mccormick.northwestern.edu/computer-science/academics/courses/descriptions/397-6.html) |
| **Harvard CS 1060: SE with GenAI** | Christopher Thorpe, 2025 onward | — | Full software lifecycle for a team SaaS product with CI/CD (details unverified). | — | [Crimson article](https://www.thecrimson.com/article/2025/1/31/compsci-1060-launch/) |
| **UMass Lowell COMP 4600: AI Agents with Claude Code** | Jie Wang, Fall 2026 | Computing I & II | Announcement only (unverified details). | — | [announcement](https://www.uml.edu/myuml/submissions/2026/2026-04-15-16-21-07-announcing-a-new-topics-course-ai.aspx) |
| **Columbia COMS W4995: Agentic Engineering** | Nick Gu, Fall 2026 | Senior/grad | In-class "studios". Per-student repo whose AGENTS.md is read by the students' agents. Free tiers only. | Unverified | https://github.com/NickGuAI/agentic-engineering-course |
| **Northeastern CS 7180: AI-Assisted SE** (MS level) | John Guerra, Spring 2026 | MS | 3 portfolio projects with **detailed rubrics**: coverage thresholds, CI, evals, and a final Claude Code project with CLAUDE.md, skills, hooks, MCP, subagents, deploy and monitoring. | Projects 50%, HW 25%, AI-free quizzes 10%, participation 15% | https://johnguerra.co/classes/aiCoding_spring_2026/ |

**Reusable single modules**
- **MIT Missing Semester 2026, Lecture 7: Agentic Coding.** Covers AGENTS.md, skills, subagents, MCP and worktrees, with exercises: https://missing.csail.mit.edu/2026/agentic-coding/
- **"Software Engineering at Scale"** capstone (CC-BY). Students inherit a large app and handle ambiguous change requests: https://github.com/software-engineering-at-scale/course

### 1b. Background each course assumes (relevant for juniors)

| Assumes | Courses |
|---|---|
| CS1/CS2 only | CMU 15-113, UMass Lowell 4600, NJIT 485, CMU 17-316 |
| Data structures or CS3; SE not required | Memphis 4991, UVA 4501, UMD 398Z, UCSD 190, Michigan 498 |
| SE, systems or senior standing | UW 490A2, Northwestern 397, UT 378, Stanford CS146S |

### 1c. Graduate research courses (for ideas only)
- UIUC CS 598LMZ (Lingming Zhang): https://github.com/lingming/software-agents
- CU Boulder CSCI 7000 (Danny Dig), GenAI-powered SE and Building AI Agents: https://danny.cs.colorado.edu/courses/csci7000-011_F25/
- Waterloo CS 846 (Mei Nagappan): classmates build **counterexamples where each other's guidelines fail**, and students build the same app in week 2 and week 13 to measure change: https://cs.uwaterloo.ca/~m2nagapp/courses/CS846/1261/
- Berkeley Agentic AI MOOC (Dawn Song): https://rdi.berkeley.edu/agentic-ai/f25

### 1d. Patterns across courses
1. One semester-long team project run as lifecycle sprints.
2. Protected human-only work: reflections, peer reviews, quizzes, in-person checkoffs.
3. Transparency: AI-use logs or documentation. "Can't explain it, can't submit it."
4. Verification assignments: security fixes, AI review compared with human review, classmate PR review, eval suites, coverage thresholds.
5. Typical grading: 40–50% project, 15–45% participation and in-class work, 10–25% reflections or quizzes, no traditional final exam.

---

## 2. Research and curricular guidance

### Most decision-relevant papers
| Item | Key finding | Why it matters here |
|---|---|---|
| Geng et al. 2026, syllabus analysis — https://arxiv.org/abs/2608.05898 | 23 syllabi. Common learning objectives: human–AI collaboration, building with AI, and evaluating AI output. | Benchmark for learning outcomes and grading weights |
| ACM Task Force on GenAI & Programming Assessment, final report (2026) — https://acm-education-genai-task-force.github.io/ACM_Taskforce_GenAI_Report_16Feb26.pdf | About 500 educators. 68% changed their assessment, toward projects plus oral or in-person checks. The top barrier is a lack of best-practice examples. | Assessment design, and your course could itself become an experience report |
| Bouvier et al., "The Rest of the Robots," ITiCSE-WGR 2025 — https://doi.org/10.1145/3760545.3783970 | First working-group report on GenAI in *post-intro* courses. | Your course is post-intro |
| Balepur et al. 2026, "(Im)Paired Programming" — https://arxiv.org/abs/2607.26375 | 54 students. Agents made them faster but reduced comprehension. Auto-accepting was the worst pattern, and students struggled to extend their code without the agent. | "Modify without the agent" checkpoints and process grading |
| Shen & Tamkin 2026 (Anthropic), "How AI Impacts Skill Formation" — https://arxiv.org/abs/2601.20245 | Randomized study: AI hurt learning of a new library, except for interaction patterns built on conceptual questions. | Teach *how* to use the agent while learning |
| Kataoka et al., ICSE-SEET 2026 — https://arxiv.org/abs/2511.23157 | Stronger paid models raised averages but widened the gap between strong and weak students. | Equal tool access and extra support for weaker students |
| Prather et al., ICER 2024, "The Widening Gap" — https://doi.org/10.1145/3632620.3671116 | GenAI speeds up students with good metacognition and hurts students who struggle. | Build in metacognitive support (planning, self-checking) |
| Fang et al. 2026, "AgentForge" — https://arxiv.org/abs/2608.04148 | Novices rotated through roles in an agent pipeline; the code-reviewer role was the hardest. | Lab idea, and a reason to emphasize review |
| Fowles et al. 2026, code-review interviews — https://arxiv.org/abs/2605.21374 | Weekly oral code reviews kept exam performance steady despite heavy AI use. | Scalable way to verify understanding |
| Mircea et al. 2026, capstone baseline — https://arxiv.org/abs/2604.24521 | 178 students on real client projects. Clients accept AI use but expect understanding and data protection. | Team AI-governance agreements |
| Wyrich et al., FSE 2026 Education — https://arxiv.org/abs/2604.01110 | Students designed their own empirical studies of AI assistants. | Mini-experiment assignment idea |
| Huang et al. 2025, "Professional Developers Don't Vibe, They Control" — https://arxiv.org/abs/2512.14012 | Experts keep control of design and quality and delegate selectively. | The practice model to teach |
| Lulla et al. 2026, AGENTS.md impact — https://arxiv.org/abs/2601.20404 | An AGENTS.md file was linked to about 29% lower agent runtime and about 17% fewer output tokens. | Evidence for teaching context engineering |

### Productivity and quality evidence (for an evidence-literacy week)
- **METR RCT (2025)**, https://arxiv.org/abs/2507.09089
  - Experienced open-source developers were **19% slower** with AI but *believed* they were 20% faster.
  - 2026 follow-up (weak evidence, possible speed-up): https://metr.org/blog/2026-02-24-uplift-update/
- **Cui et al., *Management Science* 2026**, https://doi.org/10.1287/mnsc.2025.00535
  - Field experiments at Microsoft, Accenture and a Fortune 100 firm: **+26%** completed tasks.
  - Juniors gained more.
- **Murphy-Hill et al. 2026**, https://arxiv.org/abs/2607.01418
  - Microsoft's Claude Code and Copilot CLI rollout: about 24% more merged PRs.
  - The authors caution that merged PRs are only a proxy for value.
- **DORA 2025**, https://dora.dev/dora-report-2025/
  - "AI is an amplifier."
  - Throughput goes up while delivery stability suffers.
  - Engineering safety nets matter.
- **Security of AI-written code:**
  - Pearce et al. S&P 2022: about 40% of Copilot outputs were vulnerable.
  - Perry et al. CCS 2023: AI users wrote less secure code *and felt more confident*.
  - Agentic security PRs are reviewed more heavily: https://arxiv.org/abs/2601.00477

### Curricular guidance
- **CS2023** (ACM/IEEE/AAAI) predates coding agents. Its GenAI curricular-practices article: https://csed.acm.org/wp-content/uploads/2023/12/Generative-AI-Nov-2023-Version.pdf
- **SWEBOK v4** (2024) has no GenAI content. Use it as the fixed backbone and map agentic practices onto it.
- **ACM ethics and societal impact framework (ESI-Framework)**, for the ethics module: https://arxiv.org/abs/2511.15768
- **Watch in early 2027:** the ITiCSE 2026 working-group reports on GenAI in capstones, agentic AI in computing education, and GenAI literacy. https://iticse.acm.org/2026/2026-working-group-proposals/

### Vision readings (optional, advanced)
- Hassan et al., "Agentic SE: Foundational Pillars and a Research Roadmap." Its "merge-readiness pack" can become an assignment deliverable. https://arxiv.org/abs/2509.06216
- Hassan et al., "Towards AI-Native SE (SE 3.0)": https://arxiv.org/abs/2410.06107
- Hoda 2026, "Agentic SE Beyond Code": https://arxiv.org/abs/2510.19692

---

## 3. Industry and online material

### Free courses usable as pre-work or labs
- **Anthropic Academy:** Claude Code 101 and Claude Code in Action (free, with certificates). https://anthropic.skilljar.com/
- **DeepLearning.AI short courses** (1–2.5 h each, free to audit):
  - Claude Code: https://www.deeplearning.ai/courses/claude-code-a-highly-agentic-coding-assistant
  - Spec-Driven Development with Coding Agents (tool-agnostic): https://www.deeplearning.ai/courses/spec-driven-development-with-coding-agents
  - Agent Skills: https://www.deeplearning.ai/courses/agent-skills-with-anthropic
  - Evaluating AI Agents: https://www.deeplearning.ai/courses/evaluating-ai-agents
- **Hugging Face MCP course:** https://huggingface.co/learn/mcp-course/unit0/introduction
- **GitHub Spec Kit:** a ready-made spec-driven development lab scaffold. https://github.com/github/spec-kit
- **Coursera, Vanderbilt "Claude Code: SE with GenAI Agents"** (Jules White). Its parallel worktrees and "Best of N" lessons work well as a lab. https://www.coursera.org/learn/claude-code

### Tool documentation to pair for a compare-and-contrast assignment
- Claude Code best practices: https://code.claude.com/docs/en/best-practices
- Codex best practices: https://learn.chatgpt.com/guides/best-practices
- AGENTS.md standard: https://agents.md/

### Candidate required readings (about 15)
1. Karpathy, "vibe coding" tweet (Feb 2025): https://x.com/karpathy/status/1886192184808149383
2. Karpathy, "Software Is Changing (Again)" (Software 3.0). Slides and transcript: https://www.latent.space/p/s3
3. Willison, "Not all AI-assisted programming is vibe coding": https://simonwillison.net/2025/Mar/19/vibe-coding/
4. Willison, "Vibe engineering": https://simonwillison.net/2025/Oct/7/vibe-engineering/
5. Anthropic, "Building effective agents": https://www.anthropic.com/engineering/building-effective-agents
6. Anthropic, "Effective context engineering for AI agents": https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents
7. Claude Code and Codex best-practices guides (above).
8. Willison, "Designing agentic loops": https://simonwillison.net/2025/Sep/30/designing-agentic-loops/
9. Böckeler, "Understanding Spec-Driven Development": https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html
10. Osmani, "How to write a good spec for AI agents": https://addyosmani.com/blog/good-spec/
11. Böckeler, "Harness engineering for coding agent users": https://martinfowler.com/articles/harness-engineering.html. OpenAI's companion essay (https://openai.com/index/harness-engineering/) was blocked when the research agent tried to open it, so check it yourself.
12. Anthropic, "Effective harnesses for long-running agents": https://www.anthropic.com/engineering/effective-harnesses-for-long-running-agents
13. Anthropic, "Demystifying evals for AI agents": https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents
14. Willison, "The lethal trifecta": https://simonwillison.net/2025/Jun/16/the-lethal-trifecta/
15. METR productivity study: https://metr.org/blog/2025-07-10-early-2025-ai-experienced-os-dev-study/

**Alternates**
- Osmani, "The 80% Problem": https://addyo.substack.com/p/the-80-problem-in-agentic-coding
- Kent Beck, "Augmented Coding: Beyond the Vibes": https://tidyfirst.substack.com/p/augmented-coding-beyond-the-vibes
- Hashimoto, "My AI Adoption Journey": https://mitchellh.com/writing/my-ai-adoption-journey
- Böckeler, "TDD inside the agent loop": https://martinfowler.com/articles/exploring-gen-ai/tdd-in-the-agent-loop.html

**Free "textbook" option:** Simon Willison, *Agentic Engineering Patterns*. https://simonwillison.net/guides/agentic-engineering-patterns/

---

## 4. Tools, costs and the subscription requirement (prices as of 2026-09-25)

| Option | Monthly | 4–5 months | Notes |
|---|---|---|---|
| Claude Pro (cheapest plan with Claude Code) | $20 ($17 billed annually) | $80–100 | No student discount; the Free plan excludes Claude Code. Usage is capped per 5-hour window and per week. |
| ChatGPT Go (Codex) | $8 | $32–40 | Limits not published |
| ChatGPT Free (Codex) | $0 | $0 | Limits not published. Some sources say local CLI/IDE only, with no cloud tasks or code review **(needs testing)**. |
| OpenAI student credit | — | $100 of Codex credit, one time | Verified US/Canadian students; lasts 12 months. https://developers.openai.com/community/students |

Pricing: https://claude.com/pricing · https://learn.chatgpt.com/docs/pricing

**Implications for the syllabus**
- **Price parity.** Codex students may pay $0–40 while Claude Code students pay about $80–100. Consider stating a cap, such as "Claude Pro, ChatGPT Go, or equivalent, up to $20 a month."
- **First check for campus licenses** (Claude for Education or ChatGPT Edu). They would replace student purchases, and their contracts prohibit training on student data. UT Austin's course does this.
- **Hardship fallback.**
  - Several free tiers ended in 2026: Gemini CLI's free tier (June), new Cursor student sign-ups, and Copilot Student, now about $2 a month of credits.
  - Realistic fallbacks: ChatGPT Free plus the $100 credit, or Claude Code or Codex running against open-weight models via Ollama (`ollama launch claude`). The open models are weaker on multi-file work.
- **Usage caps.** Heavy Claude Pro sessions reportedly hit the 5-hour cap. Teach context hygiene (`/clear`, smaller models) and keep an instructor fallback.
- **Portability.**
  - Ship **only `AGENTS.md`** in assignment repos. Claude Code reads it when there is no `CLAUDE.md`.
  - `SKILL.md` works in both tools.
  - Both tools support MCP and subagents. Don't make grading depend on hooks.
- **CI and autograding.** Use an instructor-held API key (`claude -p` or `codex exec`); subscriptions are not meant for CI use.
- **Data.**
  - Consumer tiers can train on sessions unless students opt out: Claude at https://claude.ai/settings/data-privacy-controls; ChatGPT under Data Controls, and Codex has a separate setting.
  - Require a Week 1 screenshot of the opt-out.
  - Ban FERPA-covered or partner-company code on consumer tiers.
- **Pitfall:** if `ANTHROPIC_API_KEY` is set in the environment, Claude Code bills the API instead of the subscription.

---

## 5. Books

| Title | Fit |
|---|---|
| **Addy Osmani, *Beyond Vibe Coding* (O'Reilly, 2025)** | Best primary text; accessible to juniors. Check library access through O'Reilly Learning. |
| Addy Osmani, *Agentic Engineering* (O'Reilly, 2026; release date unverified) | Follow-on on supervising agents and verification |
| Gene Kim & Steve Yegge, *Vibe Coding* (IT Revolution, 2025) | Motivational and opinionated; optional |
| Ken Kousen, *Claude Code: Up and Running* (O'Reilly, early release) | Hands-on, but tied to one tool |
| Lelek & Skowroński, *Vibe Engineering* (Manning, about Nov 2026) | Lifecycle, testing and guardrails; good SE complement |
| Chip Huyen, *AI Engineering* (O'Reilly, 2024) | Selected chapters for evals |
| Hur & Song, *Build an AI Agent (From Scratch)* (Manning, 2026) | For an optional build-a-toy-agent module, which could use mini-swe-agent: https://github.com/SWE-agent/mini-swe-agent |

---

## 6. Emerging topic arc (from all sources)

**Week 0–2 primer for juniors:** git, branches and PRs, unit testing, code review. Every source assumes students already know these.

1. Vibe coding versus agentic engineering; Software 3.0 framing.
2. How coding agents work: the agent loop, tools, context window.
3. Context engineering: AGENTS.md, compaction, research → plan → implement.
4. Spec-driven development: Spec Kit, EARS requirements, specs as the durable artifact.
5. Extending agents: MCP, skills, subagents, hooks.
6. Tests as guardrails; TDD with agents; CI integration.
7. Reviewing AI output: human review compared with AI review, merge-readiness evidence.
8. Security: prompt injection, the lethal trifecta, sandboxing and permissions, Semgrep.
9. Harness engineering and background or parallel agents (worktrees).
10. Evals and benchmarks, including the SWE-bench validity story: OpenAI dropped SWE-bench Verified and later found about 30% of SWE-bench Pro tasks broken (unverified).
11. Evidence literacy: METR against the field experiments; measuring your own productivity.
12. Ethics, governance, equity, data, labor.
13. Legacy and brownfield codebases; comprehension debt.

---

## 7. Open items to verify before the syllabus is final
- Exactly which Codex features ChatGPT Free and Go include; test with a real account.
- Whether the campus has Claude for Education or ChatGPT Edu licenses.
- Whether RB130 is a lab or a laptop classroom (Wi-Fi, power outlets).
- Unverified course details: Stanford grading, UW assignments, Harvard syllabus, Columbia grading.
- The ITiCSE 2026 working-group reports, likely out in early 2027.
- Re-check all prices, limits and URLs in Dec 2026 and Jan 2027.
