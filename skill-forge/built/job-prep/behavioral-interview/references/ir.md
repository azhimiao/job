behavioral-interview

---

# 0. Compilation Target

```yaml
host: any
invocation: auto
output_profile: hybrid
```

---

# 1. Intent（意图）

Theme: job-prep

## Goal
Prepare behavioral and structured interviews using STAR: build story bank, run mock Q&A, feedback rubric — for product, SOE 综测, general hire.

## Context
After job-prep-assistant routes behavioral prep. Triggers: "行为面试", "STAR", "国企结构化", "无领导小组".

## Constraints
- 精度：star-framework.md; stories must be author-real
- 伦理：no scripted lies; coach expression not fiction

---

# 2. Inputs（输入定义）

## Required Inputs
## Required
- prep_task: string — role type or question focus

## Optional
- story_seeds: list — internships/projects author confirms real
- mock_count: number — default 5

---

# 3. Outputs（输出定义）

**Profile:** hybrid

1. `job/behavioral-prep.md` — story bank STAR format
2. `job/mock-questions.md` — mock question list with hints
3. `job/mock-feedback.md` — after author answers

---

# 5. Execution Plan（执行流程）

1. READ refs/star-framework.md, routing-rules.md
2. ASK prep_task; ASK 2-3 real story_seeds from author
3. FOR each seed → EXPAND STAR; WRITE behavioral-prep.md
4. GENERATE mock-questions.md — role-specific (internet-product or state-owned-comprehensive)
5. RUN mock loop: ASK answer → SCORE per star-framework rubric → WRITE mock-feedback.md
6. IF author invents stories → refuse F4
7. UPDATE mock-questions-plan in session notes

---

# 6. Decision Logic（决策系统）

```
IF prep_task vague → infer from job/session.yaml target_job
IF SOE 综测 → add 价值观/职业规划/团队合作题
IF product PM → add 需求冲突、数据决策题
```

---

# 7. Tool / API Binding（工具绑定）

| Portable ID | Use | Constraints |
|-------------|-----|-------------|
| ask_user, | | |

---

# 10. Failure Modes（失败模式）

## F1: no-stories
- Signal: author gives nothing real
- Recovery: ask seeds
- Severity: block

## F2: vague-role
- Signal: unknown interview type
- Recovery: clarify prep_task
- Severity: block

## F3: overfit-lies
- Signal: polished fiction
- Recovery: refuse; return to facts
- Severity: block

## F4: fabrication-request
- Signal: fake STAR events
- Recovery: refuse ethics
- Severity: block

## F5: therapy-scope
- Signal: mental health crisis
- Recovery: limits; refer professional
- Severity: block

---

# 12. Skill Graph Dependencies（依赖）

```yaml
depends_on:
  - skill-core
  - job-prep-assistant
provides:
  - behavioral-interview-prep
```

---

# 13. Versioning（版本系统）

```yaml
version: "1.0.0"
status: stable
```
