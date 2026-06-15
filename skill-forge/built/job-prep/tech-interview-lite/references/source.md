---
name: tech-interview-lite
profile: hybrid
status: stable
version: "1.0.0"
invocation: auto
host: any
---

# Goal
Lite technical interview prep: JD-aligned fundamentals, algorithm drills, Java backend topics — mock-questions with guided review, not OA cheating.

# Context
After job-prep-assistant routes java-backend or tech roles. Triggers: "技术面试", "Java八股", "算法题", "后端面试".

# Constraints
- 精度：tech-interview-guide.md; level-appropriate depth
- 伦理：no OA cheating; no guarantee 原题命中

# Inputs
## Required
- prep_task: string — stack and level

## Optional
- focus_topics: list — spring, mysql, redis, algorithm
- mock_count: number — default 8

# Outputs
**Profile:** hybrid

1. `job/tech-prep.md` — topic outline + weak areas
2. `job/mock-questions.md` — categorized mock list
3. `job/mock-feedback.md` — review notes after practice

# Steps
1. READ refs/tech-interview-guide.md, jd-parsing-guide.md if JD available
2. ASK prep_task; READ job/jd-analysis.yaml if exists
3. BUILD tech-prep.md — must_have topics for java-backend level
4. GENERATE mock-questions.md — algorithm + CS basics + Java/Spring
5. RUN practice: author explains → feedback complexity and tradeoffs
6. WRITE mock-feedback.md; highlight gaps for study plan
7. IF user asks OA cheat → refuse F4

# Decision
IF intern/campus → trim system design; focus arrays trees basics
IF java-backend → emphasize Spring MySQL Redis concurrency
IF user only wants answers without understanding → coach mode; refuse dump

# Tools
- ask_user, file_read, file_write, shell

# Failures
F1: vague-stack | no tech focus | ask prep_task
F2: oa-cheat | complete online assessment fraud | refuse integrity
F3: over-scope | expert SRE deep dive | narrow to lite guide
F4: fabrication-request | fake project deep dive | refuse
F5: offer-guarantee | guaranteed pass | refuse

# Deps
depends_on:
  - skill-core
  - job-prep-assistant
provides:
  - tech-interview-prep

# Version
version: "1.0.0"
status: stable
