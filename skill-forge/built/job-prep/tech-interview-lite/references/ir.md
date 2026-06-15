tech-interview-lite

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
Lite technical interview prep: JD-aligned fundamentals, algorithm drills, Java backend topics — mock-questions with guided review, not OA cheating.

## Context
After job-prep-assistant routes java-backend or tech roles. Triggers: "技术面试", "Java八股", "算法题", "后端面试".

## Constraints
- 精度：tech-interview-guide.md; level-appropriate depth
- 伦理：no OA cheating; no guarantee 原题命中

---

# 2. Inputs（输入定义）

## Required Inputs
## Required
- prep_task: string — stack and level

## Optional
- focus_topics: list — spring, mysql, redis, algorithm
- mock_count: number — default 8

---

# 3. Outputs（输出定义）

**Profile:** hybrid

1. `job/tech-prep.md` — topic outline + weak areas
2. `job/mock-questions.md` — categorized mock list
3. `job/mock-feedback.md` — review notes after practice

---

# 5. Execution Plan（执行流程）

1. READ refs/tech-interview-guide.md, jd-parsing-guide.md if JD available
2. ASK prep_task; READ job/jd-analysis.yaml if exists
3. BUILD tech-prep.md — must_have topics for java-backend level
4. GENERATE mock-questions.md — algorithm + CS basics + Java/Spring
5. RUN practice: author explains → feedback complexity and tradeoffs
6. WRITE mock-feedback.md; highlight gaps for study plan
7. IF user asks OA cheat → refuse F4

---

# 6. Decision Logic（决策系统）

```
IF intern/campus → trim system design; focus arrays trees basics
IF java-backend → emphasize Spring MySQL Redis concurrency
IF user only wants answers without understanding → coach mode; refuse dump
```

---

# 7. Tool / API Binding（工具绑定）

| Portable ID | Use | Constraints |
|-------------|-----|-------------|
| ask_user, | | |

---

# 10. Failure Modes（失败模式）

## F1: vague-stack
- Signal: no tech focus
- Recovery: ask prep_task
- Severity: block

## F2: oa-cheat
- Signal: complete online assessment fraud
- Recovery: refuse integrity
- Severity: block

## F3: over-scope
- Signal: expert SRE deep dive
- Recovery: narrow to lite guide
- Severity: block

## F4: fabrication-request
- Signal: fake project deep dive
- Recovery: refuse
- Severity: block

## F5: offer-guarantee
- Signal: guaranteed pass
- Recovery: refuse
- Severity: block

---

# 12. Skill Graph Dependencies（依赖）

```yaml
depends_on:
  - skill-core
  - job-prep-assistant
provides:
  - tech-interview-prep
```

---

# 13. Versioning（版本系统）

```yaml
version: "1.0.0"
status: stable
```
