---
name: behavioral-interview
profile: hybrid
status: stable
version: "1.0.0"
invocation: auto
host: any
---

# Goal
Prepare behavioral and structured interviews using STAR: build story bank, run mock Q&A, feedback rubric — for product, SOE 综测, general hire.

# Context
After job-prep-assistant routes behavioral prep. Triggers: "行为面试", "STAR", "国企结构化", "无领导小组".

# Constraints
- 精度：star-framework.md; stories must be author-real
- 伦理：no scripted lies; coach expression not fiction

# Inputs
## Required
- prep_task: string — role type or question focus

## Optional
- story_seeds: list — internships/projects author confirms real
- mock_count: number — default 5

# Outputs
**Profile:** hybrid

1. `job/behavioral-prep.md` — story bank STAR format
2. `job/mock-questions.md` — mock question list with hints
3. `job/mock-feedback.md` — after author answers

# Steps
1. READ refs/star-framework.md, routing-rules.md
2. ASK prep_task; ASK 2-3 real story_seeds from author
3. FOR each seed → EXPAND STAR; WRITE behavioral-prep.md
4. GENERATE mock-questions.md — role-specific (internet-product or state-owned-comprehensive)
5. RUN mock loop: ASK answer → SCORE per star-framework rubric → WRITE mock-feedback.md
6. IF author invents stories → refuse F4
7. UPDATE mock-questions-plan in session notes

# Decision
IF prep_task vague → infer from job/session.yaml target_job
IF SOE 综测 → add 价值观/职业规划/团队合作题
IF product PM → add 需求冲突、数据决策题

# Tools
- ask_user, file_read, file_write

# Failures
F1: no-stories | author gives nothing real | ask seeds
F2: vague-role | unknown interview type | clarify prep_task
F3: overfit-lies | polished fiction | refuse; return to facts
F4: fabrication-request | fake STAR events | refuse ethics
F5: therapy-scope | mental health crisis | limits; refer professional

# Deps
depends_on:
  - skill-core
  - job-prep-assistant
provides:
  - behavioral-interview-prep

# Version
version: "1.0.0"
status: stable
