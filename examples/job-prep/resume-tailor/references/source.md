---
name: resume-tailor
profile: hybrid
status: stable
version: "1.0.0"
invocation: auto
host: any
---

# Goal
Parse job description, map requirements to author real experience, produce tailored resume bullets and diff — no fabricated roles or dates.

# Context
After job-prep-assistant routes resume work. Triggers: "改简历", "对齐JD", "简历 bullet", "CV tailor".

# Constraints
- 精度：jd-parsing-guide.md; only verified author facts
- 伦理：劳动力市场信号理论 — honest signaling; no fake internship

# Inputs
## Required
- prep_task: string — JD or target role
- resume_source: file or paste — current resume

## Optional
- output_lang, focus_sections

# Outputs
**Profile:** hybrid

1. `job/jd-analysis.yaml`
2. `job/resume-tailored.md`
3. `job/resume-diff.md`
4. UPDATE job/application-checklist.md

# Steps
1. READ refs/jd-parsing-guide.md, resume-standards.md, routing-rules.md ethics
2. ASK prep_task; READ resume_source
3. PARSE JD → WRITE job/jd-analysis.yaml (must_have, keywords_for_resume)
4. MAP each JD requirement to real experience; FLAG gaps honestly
5. DRAFT resume-tailored.md bullets per resume-standards (verb + skill + result)
6. WRITE resume-diff.md — what changed and why
7. IF author asks to invent experience → refuse F4
8. SYNC application-checklist resume items checked

# Decision
IF JD missing → ASK paste or link summary
IF no matching experience → suggest honest gap narrative; no fabrication
IF inflated claims → tone down to verifiable facts

# Tools
- ask_user, file_read, file_write, web_fetch

# Failures
F1: missing-jd | no JD or role | ask prep_task
F2: missing-resume | no source | ask paste
F3: gap-only | no overlap | honest gap plan; no fake fill
F4: fabrication-request | fake company or role | refuse ethics
F5: offer-guarantee | user wants guaranteed hire | refuse

# Deps
depends_on:
  - skill-core
  - job-prep-assistant
provides:
  - resume-tailoring

# Version
version: "1.0.0"
status: stable
