# AI Engineering Transition Plan

**Owner:** Graduate, CSE (Chandigarh University)
**Current stack:** PHP, Node.js, Next.js
**Target stack:** Python, FastAPI, Pydantic, Next.js (frontend retained)
**Target role:** AI Application Engineer
**Estimated duration:** 3 to 5 months

---

## 1. Objective

| # | Objective | Measure of done |
|---|-----------|-----------------|
| O1 | Build production-style Python services | FastAPI service with tests and Dockerfile |
| O2 | Integrate LLMs into applications | Streaming LLM endpoint consumed by Next.js |
| O3 | Produce structured, validated outputs | Pydantic-validated extraction endpoint |
| O4 | Measure AI quality systematically | Eval suite with results in README |
| O5 | Build retrieval-augmented systems | Document Q&A with citations and retrieval metrics |
| O6 | Operate AI systems in production | Caching, cost tracking, tracing, step-limited agent |

---

## 2. Baseline Assessment

### Strengths (transferable)

- [x] Python fundamentals
- [x] Machine learning and computer vision (college projects)
- [x] Model evaluation concepts (precision, recall, accuracy)
- [x] Web APIs and request lifecycles (PHP, Node.js)
- [x] Full-stack frontend (Next.js)

### Gaps (to close)

- [ ] FastAPI and async Python
- [ ] Pydantic schemas and validation
- [ ] LLM API integration (SDK, streaming, errors)
- [ ] Structured outputs and tool calling
- [ ] LLM-specific evaluation (rubrics, LLM-as-judge)
- [ ] Embeddings, vector search, pgvector
- [ ] RAG pipeline design
- [ ] Tracing and observability for LLM calls
- [ ] Agent loop design and safety limits
- [ ] Docker and deployment of Python services

---

## 3. Phased Path

### Phase 1: Bridge (Weeks 1 to 2)

**Goal:** Convert one existing ML project into a service.

| Task | Done |
|------|------|
| Select project (YOLO object detection or emotion detection) | [ ] |
| Set up project with `uv`, `pyproject.toml`, and folder structure | [ ] |
| Wrap model inference in a FastAPI endpoint | [ ] |
| Define request and response schemas with Pydantic | [ ] |
| Add tests with fixture inputs | [ ] |
| Write Dockerfile and run container locally | [ ] |
| Connect a Next.js page to the endpoint | [ ] |

**Exit criteria:** Service runs in Docker, returns validated JSON, and the frontend displays results.

### Phase 2: LLM Integration (Weeks 3 to 5)

**Goal:** Call an LLM from a Python service and stream output to the frontend.

| Task | Done |
|------|------|
| Make first API call with the Anthropic or OpenAI SDK | [ ] |
| Handle errors, timeouts, and retries | [ ] |
| Manage system prompts and multi-turn message history | [ ] |
| Stream responses through FastAPI (SSE or chunked) | [ ] |
| Consume the stream in Next.js | [ ] |
| Store API keys in environment variables, never in code | [ ] |

**Exit criteria:** Streaming chat endpoint works end to end from the Next.js frontend.

### Phase 3: Structured Outputs and Tool Calling (Weeks 6 to 7)

**Goal:** Get reliable, machine-readable outputs and connect the model to code.

| Task | Done |
|------|------|
| Define output schemas with Pydantic | [ ] |
| Validate model output and retry on malformed responses | [ ] |
| Define a tool (function) with clear name and parameters | [ ] |
| Execute tool in code and return results to the model | [ ] |
| Build an extraction endpoint for messy text input | [ ] |

**Exit criteria:** Extraction endpoint returns valid schema objects for at least 95% of test inputs.

### Phase 4: Evaluation (Weeks 8 to 9)

**Goal:** Measure quality so every change is verifiable.

| Task | Done |
|------|------|
| Build labeled dataset (start with 30 to 50 examples) | [ ] |
| Define metrics per task (exact match, F1, schema validity) | [ ] |
| Implement LLM-as-judge with a written rubric | [ ] |
| Compare prompt or model versions on the same dataset | [ ] |
| Add eval run to CI | [ ] |
| Publish results table in README | [ ] |

**Exit criteria:** One command runs the full eval and prints a score report.

### Phase 5: RAG with pgvector (Weeks 10 to 13)

**Goal:** Build document Q&A with citations.

| Task | Done |
|------|------|
| Ingest PDF, Markdown, and HTML documents | [ ] |
| Implement chunking with overlap | [ ] |
| Generate embeddings and store in pgvector | [ ] |
| Build top-k retrieval with metadata filtering | [ ] |
| Generate answers with cited sources | [ ] |
| Measure retrieval recall@k separately from answer quality | [ ] |
| Measure answer faithfulness with eval suite | [ ] |

**Exit criteria:** Q&A returns cited answers, with recall@k and faithfulness reported in README.

### Phase 6: Production Layer and Agents (Weeks 14 to 17)

**Goal:** Make the system operable and add one bounded agent.

| Task | Done |
|------|------|
| Add response caching and prompt caching | [ ] |
| Track token usage and cost per request | [ ] |
| Add tracing (Langfuse, LangSmith, or OpenTelemetry) | [ ] |
| Implement input validation and output checks | [ ] |
| Add fallback behavior for provider errors | [ ] |
| Build one agent with tool calls | [ ] |
| Set max steps, timeouts, and human approval for risky actions | [ ] |

**Exit criteria:** Traces are visible for each request, and the agent stops within its step limit.

---

## 4. Learning Resources

| # | Resource | Phase | Status | Notes |
|---|----------|-------|--------|-------|
| R1 | [Corey Schafer: FastAPI Full Course (iukOehU5aF4)](https://www.youtube.com/watch?v=iukOehU5aF4) | Phase 1, 3, 6 | [ ] Not started | 13+ hour course; study by chapter (see Section 4.1) |
| R2 | [Apna College: Python Full Course, Lesson 1 (t2_Q2BRzeEE)](https://www.youtube.com/watch?v=t2_Q2BRzeEE&list=PLGjplNEQ1it8-0CmoljS5yeV-GlKSUEt0) | Reference only | [ ] Not started | Python basics; you already know these, so skip unless you hit a gap |
| R3 | [NeetCode.io (DSA roadmap and problems)](https://neetcode.io) | DSA track (parallel) | [ ] Not started | Solve problems in roadmap order; 30 to 45 min daily |

**Coverage gap:** Neither resource covers LLMs, embeddings, RAG, or evaluation. Phases 2, 4, 5, and parts of 6 need separate LLM-focused resources, which should be added to this table once selected.

### 4.2 DSA Track (NeetCode.io)

DSA runs alongside the phases, not inside them. Interviews for AI application roles still include coding rounds, so keep this track going all the way through.

| Rule | Detail |
|------|--------|
| Daily target | 1 to 2 problems, 30 to 45 minutes |
| Order | Follow the NeetCode roadmap sequence, not random problems |
| Method | Attempt for 20 minutes before reading the solution |
| Review | Re-solve missed problems after 3 days |
| Log | Record problem name, pattern, and time taken in Section 4.2.1 |

**4.2.1 DSA Log**

| Date | Problem | Pattern | Solved independently (Y/N) | Time |
|------|---------|---------|----------------------------|------|
| | | | | |

### 4.3 Resources to Find

These are needed for the phases that R1 and R2 don't cover. Find one primary resource for each, then add it to the table in Section 4.

| # | Topic | Needed for | What to look for | Status |
|---|-------|------------|------------------|--------|
| F1 | LLM APIs: SDK, streaming, tool calling | Phase 2, 3 | Official Anthropic or OpenAI docs and quickstarts | [ ] To find |
| F2 | Structured outputs with Pydantic | Phase 3 | Guides on JSON schema output and validation | [ ] To find |
| F3 | Prompt engineering | Phase 2, 3 | Course or guide with few-shot and output-format examples | [ ] To find |
| F4 | LLM evaluation and LLM-as-judge | Phase 4 | Eval course with rubric design and metric examples | [ ] To find |
| F5 | Embeddings and vector search | Phase 5 | Material covering cosine similarity, HNSW, and pgvector | [ ] To find |
| F6 | RAG pipeline design | Phase 5 | Hands-on RAG build with chunking, reranking, and citations | [ ] To find |
| F7 | PostgreSQL with pgvector | Phase 5 | Setup and querying guide for pgvector | [ ] To find |
| F8 | LLM observability and tracing | Phase 6 | Langfuse, LangSmith, or OpenTelemetry tutorial | [ ] To find |
| F9 | AI agents and tool loops | Phase 6 | Agent course focused on safety, step limits, and evaluation | [ ] To find |
| F10 | Production LLM concerns (caching, cost, fallbacks) | Phase 6 | Guide or talk on cost control and reliability | [ ] To find |

**Selection criteria:** Prefer official documentation and recent material (2025 or later), code you can run, and sources that include evaluation. Skip sources that only show demos without error handling.

**Study rules**

- One video per session, followed by one build task
- Write a short summary of each video in your own words
- Apply every concept in code within 48 hours of learning it

### 4.1 R1 Chapter Map (Corey Schafer, FastAPI)

**Study now (Phase 1):**

| Timestamp | Chapter | Why it matters |
|-----------|---------|----------------|
| 00:00:00 | Getting Started: Web App and REST API | Core FastAPI setup and first routes |
| 00:59:53 | Path Parameters: Validation and Errors | Input validation for the vision service |
| 01:36:09 | Pydantic Schemas | Request and response models (P1, P3) |
| 03:37:35 | Sync vs Async | Needed for non-blocking LLM and model calls (Phase 2) |
| 04:08:58 | Routers | Project structure for a real service |
| 06:30:32 | File Uploads | Image upload for YOLO inference |
| 10:11:44 | Testing with Pytest | Tests for the Phase 1 deliverable |
| 13:04:21 | Deploy with Docker | Dockerfile for the Phase 1 exit criteria |

**Study later (Phase 5 and 6):**

| Timestamp | Chapter | Phase |
|-----------|---------|-------|
| 01:59:51 | SQLAlchemy Models and Relationships | 5 (document metadata) |
| 08:38:03 | PostgreSQL and Alembic | 5 (pgvector setup) |
| 04:56:21 | Authentication with JWT | 6 (production) |
| 05:52:58 | Authorization | 6 (production) |
| 07:40:06 | Background Tasks | 6 (async jobs) |
| 09:25:04 | AWS S3 and Boto3 | 5 or 6 (document storage) |
| 11:33:16 | Deploy to a VPS | 6 (optional) |

**Skip (Next.js replaces these):**

- 00:23:04 HTML Frontend with Jinja2 Templates
- 04:28:18 Frontend Forms with JavaScript
- 03:01:54 Completing CRUD (skim only; not needed for AI services)
- 07:04:13 Pagination (revisit in Phase 5 if your document list needs it)

**R2 note:** Lesson 1 of the Apna College course covers installation, variables, data types, operators, type conversion, and input. Treat it as a reference. Watch only the sections on type conversion and inputs if you want a quick refresher.

---

## 5. Weekly Operating Rhythm

| Day | Activity | Duration |
|-----|----------|----------|
| Mon | Watch and take notes | 1 hr |
| Tue | Build from the lesson | 1.5 hr |
| Wed | Build from the lesson | 1.5 hr |
| Thu | Fix and test | 1 hr |
| Fri | Review, commit, update tracker | 45 min |
| Sat | Project work | 2 hr |
| Sun | Rest or light reading | Optional |

---

## 6. Progress Tracker

| Week | Phase | Planned output | Actual output | Status |
|------|-------|----------------|---------------|--------|
| 1 | 1 | Project setup and first endpoint | | |
| 2 | 1 | Dockerized service and Next.js page | | |
| 3 | 2 | First LLM call and error handling | | |
| 4 | 2 | Streaming endpoint | | |
| 5 | 2 | Streaming consumed in Next.js | | |
| 6 | 3 | Pydantic extraction schema | | |
| 7 | 3 | Tool calling implemented | | |
| 8 | 4 | Labeled dataset and metrics | | |
| 9 | 4 | Eval report in README | | |
| 10 | 5 | Ingestion and chunking | | |
| 11 | 5 | pgvector retrieval | | |
| 12 | 5 | Cited answers | | |
| 13 | 5 | Retrieval and faithfulness metrics | | |
| 14 | 6 | Caching and cost tracking | | |
| 15 | 6 | Tracing enabled | | |
| 16 | 6 | Agent with step limits | | |
| 17 | 6 | Final README, demo, and deployment | | |

---

## 7. Portfolio Deliverables

| # | Project | Phase | Repository contents |
|---|---------|-------|---------------------|
| P1 | Vision inference service (YOLO or emotion) | 1 | FastAPI, Pydantic, tests, Dockerfile, Next.js UI |
| P2 | Streaming LLM assistant | 2 | Streaming endpoint, error handling, Next.js client |
| P3 | Structured extraction API | 3 | Pydantic schemas, validation, retry logic |
| P4 | Eval suite | 4 | Dataset, metrics, judge rubric, CI job, results table |
| P5 | Document Q&A with citations | 5 | Ingestion, pgvector, retrieval metrics, eval results |
| P6 | Bounded agent with tracing | 6 | Tool definitions, step limits, trace screenshots |

---

## 8. Milestone Checks

- [ ] Week 2: P1 running in Docker
- [ ] Week 5: P2 streaming to Next.js
- [ ] Week 9: P3 and P4 complete with published metrics
- [ ] Week 13: P5 complete with retrieval and faithfulness scores
- [ ] Week 17: P6 complete, all projects documented, portfolio reviewed

---

## 9. Review Questions (answer at each phase end)

1. What does this component do, and what are its inputs and outputs?
2. How do I know it works? Which metric or test shows it?
3. What fails in production, and how does the code handle it?
4. What would I change if cost or latency doubled?

---

## 10. Revision Log

| Date | Change | Reason |
|------|--------|--------|
| | Initial plan created | Transition start |