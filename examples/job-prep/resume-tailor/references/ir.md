resume-tailor

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
Parse job description, map requirements to author real experience, produce tailored resume bullets and diff — no fabricated roles or dates.

## Context
After job-prep-assistant routes resume work. Triggers: "改简历", "对齐JD", "简历 bullet", "CV tailor".

## Constraints
- 精度：jd-parsing-guide.md; only verified author facts
- 伦理：劳动力市场信号理论 — honest signaling; no fake internship

---

# 2. Inputs（输入定义）

## Required Inputs
## Required
- prep_task: string — JD or target role
- resume_source: file or paste — current resume

## Optional
- output_lang, focus_sections

---

# 3. Outputs（输出定义）

**Profile:** hybrid

1. `job/jd-analysis.yaml`
2. `job/resume-tailored.md`
3. `job/resume-diff.md`
4. UPDATE job/application-checklist.md

---

# 5. Execution Plan（执行流程）

1. READ refs/jd-parsing-guide.md, resume-standards.md, routing-rules.md ethics
2. ASK prep_task; READ resume_source
3. PARSE JD → WRITE job/jd-analysis.yaml (must_have, keywords_for_resume)
4. MAP each JD requirement to real experience; FLAG gaps honestly
5. DRAFT resume-tailored.md bullets per resume-standards (verb + skill + result)
6. WRITE resume-diff.md — what changed and why
7. IF author asks to invent experience → refuse F4
8. SYNC application-checklist resume items checked

---

# 6. Decision Logic（决策系统）

```
IF JD missing → ASK paste or link summary
IF no matching experience → suggest honest gap narrative; no fabrication
IF inflated claims → tone down to verifiable facts
```

---

# 7. Tool / API Binding（工具绑定）

| Portable ID | Use | Constraints |
|-------------|-----|-------------|
| ask_user, | | |

---

# 10. Failure Modes（失败模式）

## F1: missing-jd
- Signal: no JD or role
- Recovery: ask prep_task
- Severity: block

## F2: missing-resume
- Signal: no source
- Recovery: ask paste
- Severity: block

## F3: gap-only
- Signal: no overlap
- Recovery: honest gap plan; no fake fill
- Severity: block

## F4: fabrication-request
- Signal: fake company or role
- Recovery: refuse ethics
- Severity: block

## F5: offer-guarantee
- Signal: user wants guaranteed hire
- Recovery: refuse
- Severity: block

---

# 12. Skill Graph Dependencies（依赖）

```yaml
depends_on:
  - skill-core
  - job-prep-assistant
provides:
  - resume-tailoring
```

---

# 13. Versioning（版本系统）

```yaml
version: "1.0.0"
status: stable
```
