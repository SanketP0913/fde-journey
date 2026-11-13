# Forward Deployed AI/ML Engineer: 52-Week Plan

Goal: be interview-ready for FDE / Applied AI roles in 12 months.
Budget: about 15–20 hrs/week (see "Weekly template"). If you have fewer hours, stretch each phase, but do not skip evals, deployment or customer skills.

Legend: **Learn** = study, **Build** = ship something, **LC** = LeetCode.

---

## 0. Tooling: Git, Copilot, LeetCode

### Git / GitHub (use from Day 1)
- Create three repos:
  1. `fde-journey`: weekly learning log (one markdown file per week), notes, and this plan.
  2. `leetcode`: solutions organized by pattern (`/arrays`, `/trees`, ...), with a README table of problem, pattern, date and notes.
  3. One repo **per project** (`rag-eval`, `support-agent`, `flagship-...`).
- Workflow, even when working solo:
  - `main` is always working. Work on branches: `feat/chunking`, `fix/retry-logic`.
  - Open a **Pull Request** for every change, with a description. Merge only when CI is green.
  - Use Conventional Commits: `feat:`, `fix:`, `docs:`, `test:`, `chore:`.
  - Use GitHub Issues as your backlog, and a Projects board for your weekly plan.
  - Use GitHub Actions for lint (ruff), tests (pytest) and Docker build, on every PR.
  - Tag releases (`v0.1.0`) when a project reaches a milestone.
- Learn by week 4: rebase vs merge, `git stash`, `git bisect`, resolving conflicts, `git reflog`, and `.gitignore` / never committing secrets.
- A visible green contribution graph and clean PR history are part of your hiring signal.

### GitHub Copilot (use as a pair, not a crutch)
| Phase | How to use it |
|---|---|
| Weeks 1–12 (learning) | Copilot **Chat for explanations only**. Type the code yourself. Ask "why does this work?" and "what are the edge cases?" |
| Weeks 13+ (building) | Use autocomplete for boilerplate, tests, docstrings, Dockerfiles, CI YAML, and regex. Use Chat to review your diffs. Use the PR-summary feature on pull requests. |
| Always | Read every suggestion before accepting it. If you can't explain a line, don't commit it. Write the core logic (retrieval, evals, prompts) yourself. |
| LeetCode | **Turn Copilot off** (or disable inline suggestions) while solving. After solving, you can ask it to critique your solution and complexity. |

Good prompts: "Write pytest tests for this function, including edge cases." "Review this diff for bugs and security issues." "Explain this error and the root cause." "Suggest a simpler design."

### LeetCode (about 170 problems over the year)
- Follow the **NeetCode 150** order, by pattern.
- Cadence: 3–4 problems per week in the early phases, and 2–3 timed ones later.
- Method for each problem:
  1. Try for 20–25 minutes unaided.
  2. If stuck, read the hint or the solution, then close it and **re-implement from memory the next day**.
  3. Log pattern, complexity and the mistake you made in the `leetcode` repo.
- Every 4th week is review: redo 3 problems you struggled with.
- Pattern order: arrays/hashing → two pointers → stack → sliding window → binary search → linked list → trees → heap → backtracking → tries → graphs → 1D DP → intervals → greedy.
- Also practice 5–10 SQL problems (LeetCode SQL 50) in Phase 0.

---

## Weekly template (about 15–20 hrs)
| Slot | Time | What |
|---|---|---|
| Mon / Wed | 1.5 hrs each | Learn (course, docs, paper) |
| Tue / Thu | 1.5 hrs each | LeetCode (see the week's topic) |
| Fri | 1 hr | Git hygiene: PRs merged, issues updated, learning-log written |
| Sat | 4–5 hrs | Build (deep work block) |
| Sun | 3–4 hrs | Build, or review + plan the next week |

**Friday checklist:** all work is in a PR or merged. Learning log is written. LeetCode repo is updated. Next week's issues exist.

---

## Phase 0: Foundations (Weeks 1–4)

| Wk | Learn | Build | LC |
|---|---|---|---|
| 1 | Environment setup (Python 3.12, uv or venv, VS Code, Copilot, SSH keys). Git basics: init, commit, branch, PR. | Create `fde-journey` and `leetcode` repos. Write the Week 1 log. Practice branch → PR → merge. | Arrays/hashing: Two Sum, Contains Duplicate, Valid Anagram |
| 2 | Python depth: typing, dataclasses, generators, exceptions, context managers, `pytest` | CLI that fetches a public API and stores results in SQLite, with tests | Group Anagrams, Top K Frequent, Valid Palindrome, Two Sum II |
| 3 | SQL (joins, CTEs, window functions), Docker, docker-compose | Move the CLI's storage to Postgres in Docker. Write 5 analytical queries. | 3Sum, Container With Most Water, Valid Parentheses, Min Stack (+ 5 SQL problems) |
| 4 | REST/HTTP, FastAPI basics, GitHub Actions | Expose the data via FastAPI. Add CI (ruff + pytest + Docker build). Tag `v0.1.0`. | Best Time to Buy/Sell Stock, Longest Substring Without Repeating, Binary Search, Daily Temperatures. **Review:** redo 3 earlier problems. |

**Milestone M0:** a Dockerized FastAPI + Postgres app with CI and tests, plus about 15 LeetCode problems.

---

## Phase 1: ML fundamentals (Weeks 5–12)

| Wk | Learn | Build | LC |
|---|---|---|---|
| 5 | Linear algebra and calculus intuition (3Blue1Brown), NumPy | Implement linear regression with gradient descent in NumPy | Sliding window: Permutation in String, Min Window Substring |
| 6 | pandas, EDA, data cleaning, visualization | Pick the Project 1 dataset (churn/fraud/healthcare). Do EDA and a baseline. | Binary search: Search Rotated Array, Koko Eating Bananas |
| 7 | scikit-learn pipelines, train/test/CV, metrics (precision/recall/ROC/PR) | Baseline model with a proper pipeline and cross-validation | Linked list: Reverse List, Merge Two Lists, Cycle Detection |
| 8 | Trees, random forest, XGBoost, tuning, class imbalance, leakage | Improve the model and add error analysis | Linked list: Remove Nth Node, Reorder List, LRU Cache |
| 9 | Model interpretation (SHAP), calibration, fairness basics | **Project 1:** finish the model and write the report | Review week: redo 4 problems |
| 10 | Experiment tracking (MLflow or W&B), reproducibility | Package Project 1 as a FastAPI model service with Docker and CI. Release `v1.0.0`. | Trees: Invert Tree, Max Depth, Same Tree, Subtree |
| 11 | PyTorch: tensors, autograd, training loop (fast.ai or the PyTorch tutorials) | Train a small neural net (MNIST or tabular) | Trees: Level Order, Validate BST, Kth Smallest in BST |
| 12 | Karpathy "micrograd" / "makemore" | Re-implement micrograd. Write a blog draft: "What I learned building a NN from scratch". | Trees: LCA, Construct Tree, Max Path Sum |

**Milestone M1:** Project 1 shipped and documented, a blog draft, and about 40 LeetCode problems.

---

## Phase 2: LLM engineering (Weeks 13–26)

| Wk | Learn | Build | LC |
|---|---|---|---|
| 13 | Transformers, tokenization, attention. Karpathy "Let's build GPT" / "Tokenizer". | Notebook that visualizes tokenization and attention. Compare token counts and costs across models. | Heap: Kth Largest, Last Stone Weight, K Closest Points |
| 14 | LLM API basics: Claude and OpenAI SDKs, system prompts, temperature, structured output (JSON/schema), prompt design | CLI assistant with structured extraction (invoices or clinical notes into JSON) | Heap: Task Scheduler, Median from Data Stream |
| 15 | Tool/function calling, streaming, retries, rate limits, prompt caching, batching | Add tools and streaming to the assistant. Track token cost per request. | Backtracking: Subsets, Combination Sum, Permutations |
| 16 | Embeddings, similarity, vector search, pgvector | Semantic search over a document set with Postgres + pgvector | Backtracking: Subsets II, Word Search |
| 17 | RAG v1: parsing PDFs, chunking strategies, metadata | **Project 2 start:** ingest messy PDFs and build a naive RAG | Review week: redo 4 problems |
| 18 | Hybrid search (BM25 + vectors), reranking, query rewriting, citations | Improve retrieval and add citations | Tries: Implement Trie, Add/Search Words |
| 19 | **Evals:** golden datasets, retrieval metrics (recall@k, MRR), LLM-as-judge, regression tests | Build an eval harness. Measure naive vs improved RAG. | Tries: Word Search II. Graphs: Number of Islands |
| 20 | Tracing and observability (Langfuse or LangSmith) | **Project 2:** finish with a UI (Streamlit), eval report and demo video. Release `v1.0.0`. | Graphs: Clone Graph, Max Area of Island, Pacific Atlantic |
| 21 | Agents: tool loops, planning, memory, failure modes | **Project 3 start:** a tool-using agent (support triage, or a data analyst over SQL) | Graphs: Course Schedule, Rotting Oranges |
| 22 | MCP (Model Context Protocol): servers, clients, resources, tools | Build an MCP server for your own data source and connect it to an agent | Graphs: Connected Components, Graph Valid Tree |
| 23 | Guardrails: input validation, prompt injection, output checks, human-in-the-loop | Add guardrails and an approval step to the agent | Review week: redo 4 problems |
| 24 | Agent evals: task success, trajectories, cost and latency budgets | **Project 3:** finish with an eval suite and cost dashboard. Release `v1.0.0`. | 1D DP: Climbing Stairs, House Robber, Coin Change |
| 25 | Fine-tuning: LoRA/QLoRA with Hugging Face (`transformers`, `peft`, `trl`). When *not* to fine-tune. | Fine-tune a small model on a narrow task (Colab or a cloud GPU) | 1D DP: Longest Increasing Subsequence, Word Break |
| 26 | Compare prompting vs RAG vs fine-tuning on one task | **Project 4:** a comparison report with numbers (quality, cost, latency) | Review week |

**Milestone M2:** 3 LLM projects with evals and write-ups, one blog post published, and about 95 LeetCode problems.

---

## Phase 3: Production and deployment (Weeks 27–36)

| Wk | Learn | Build | LC |
|---|---|---|---|
| 27 | FastAPI production patterns: auth (JWT/OAuth), SQLAlchemy, migrations (Alembic), config and secrets | Harden the Project 2 or 3 API | 2D DP: Unique Paths, Longest Common Subsequence |
| 28 | Redis, caching, queues (Celery or SQS), background jobs, idempotency | Make ingestion asynchronous with a job queue | Intervals: Insert Interval, Merge Intervals |
| 29 | AWS core: IAM, S3, EC2/ECS, Lambda, VPC basics | Deploy the service to AWS (or GCP/Azure) manually | Intervals: Non-overlapping Intervals, Meeting Rooms II |
| 30 | Infrastructure as code (Terraform), CI/CD pipelines | Re-create the deployment with Terraform and GitHub Actions | Greedy: Maximum Subarray, Jump Game |
| 31 | Kubernetes fundamentals (pods, deployments, services, ingress, Helm) | Run the service on a local cluster (kind or minikube) | Greedy: Gas Station, Hand of Straights |
| 32 | Model serving: vLLM, quantization, batching, GPU cost tradeoffs | Serve an open-source model with vLLM and benchmark it against an API | Review week |
| 33 | Observability: structured logs, metrics, alerts, drift detection | Add dashboards (Grafana or CloudWatch) and alerts | Math/Bit: Reverse Bits, Number of 1 Bits, Missing Number |
| 34 | Security and compliance: PII redaction, secrets, SOC2/HIPAA awareness, VPC/on-prem deployment patterns | Add PII redaction and audit logging | Mixed mediums, 3 timed |
| 35 | Data pipelines: dbt, Airflow or Dagster, Snowflake/Databricks basics | Build a small ELT pipeline that feeds your RAG system | Mixed mediums, 3 timed |
| 36 | Review and integration | **Project 5:** full production deployment, with CI/CD, monitoring, a cost report, and a README written *for a customer* | Review week |

**Milestone M3:** a deployed, monitored AI service with infrastructure as code, and about 130 LeetCode problems.

---

## Phase 4: Forward-deployed skills (Weeks 37–44)

| Wk | Learn | Build / practice | LC |
|---|---|---|---|
| 37 | Customer discovery: how to ask questions, scope, and find the real problem. Choose your domain (healthcare, finance, logistics, etc.). | Write a one-page "customer profile" for your chosen domain. Run 2 mock discovery calls with a friend. | 2 timed mediums |
| 38 | Proposals, success metrics, and ROI. Writing status updates and handling objections. | Write a proposal for the flagship project: problem, success metrics, risks, timeline | 2 timed mediums |
| 39 | Integrations: OAuth, webhooks, Slack/Jira/Salesforce/SharePoint APIs, legacy database access | Build two integrations as MCP tools or API connectors | 2 timed mediums |
| 40 | Rapid prototyping: Streamlit and Next.js UIs, demoing under uncertainty | Build a working demo in 2 days as a drill | 2 timed mediums |
| 41 | **Flagship build, part 1:** data ingestion and core pipeline | Flagship project: core functionality | 2 timed mediums |
| 42 | Flagship, part 2: evals and guardrails | Flagship: evaluation suite, error analysis | 2 timed mediums |
| 43 | Flagship, part 3: deployment and handoff docs | Flagship: deploy, runbook, training doc for end users | 2 timed mediums |
| 44 | Storytelling: case studies, demo videos | Write the flagship case study (problem → approach → impact in numbers) and record a 3-minute demo | Review week |

**Milestone M4:** a flagship project with a real impact story, a case study, a demo video, and about 150 LeetCode problems.

---

## Phase 5: Job hunt (Weeks 45–52)

| Wk | Focus | Output |
|---|---|---|
| 45 | Portfolio polish: pin your best 4 repos, fix READMEs, add architecture diagrams. Update resume and LinkedIn. | Final resume (1 page), portfolio site or GitHub profile README |
| 46 | Write 1–2 blog posts. Make a small open-source contribution (docs fix, bug fix, or MCP server). | Published posts, 1 merged OSS PR |
| 47 | ML and LLM system design: RAG at scale, eval pipelines, cost control, multi-tenant deployments | 3 written design answers |
| 48 | Coding mock interviews (timed, with a friend or a platform like Pramp or interviewing.io) | 4 mock sessions, with notes |
| 49 | Case-study / scoping interviews: "a customer wants X, what do you do?" Behavioral stories (STAR). | 6 prepared stories, 3 mock case studies |
| 50 | **Application wave 1:** 15–20 targeted applications plus referrals and cold outreach to FDEs | Tracker spreadsheet |
| 51 | Application wave 2 and live interviews. Debrief every interview. | Updated tracker and notes |
| 52 | Retrospective. Iterate on weak spots. Negotiate offers or plan the next sprint. | Year-in-review post |

Target companies: Palantir, OpenAI, Anthropic, Cohere, Scale AI, Databricks, Glean, Sierra, Harvey, and AI-native startups. Stepping stone titles: solutions engineer, applied AI engineer, AI engineer.

---

## Progress scoreboard (update monthly)
| Month | Weeks | Projects done | LC solved (target) | Blog posts |
|---|---|---|---|---|
| 1 | 1–4 | M0 app | 15 | 0 |
| 3 | 9–12 | Project 1 | 40 | 1 draft |
| 6 | 22–26 | Projects 2–4 | 95 | 1 |
| 9 | 33–36 | Project 5 | 130 | 1 |
| 11 | 41–44 | Flagship | 150 | 2 |
| 12 | 45–52 | Interviews | 170 | 2 |

## Rules
1. If you fall behind, drop LeetCode volume before dropping builds, but never drop to zero.
2. Every project ends with numbers (accuracy, latency, cost, hours saved).
3. Build in public: commit daily, post weekly.
4. Review this plan on the first Sunday of each month and adjust.
