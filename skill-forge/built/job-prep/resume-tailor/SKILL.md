---
name: resume-tailor
description: >-
  Parse job description, map requirements to author real experience, produce tailored resume
  bullets and diff — no fabricated roles or dates. Use when after job-prep-assistant routes
  resume work. Triggers: "改简历", "对齐JD", "简历 bullet", "CV tailor".
metadata:
  version: "1.0.0"
  status: stable
  protocol: skill-protocol-v2
---

# Resume Tailor

## Quick Start

1. READ refs/jd-parsing-guide.md, resume-standards.md, routing-rules.md ethics
2. ASK prep_task; READ resume_source
3. PARSE JD → WRITE job/jd-analysis.yaml (must_have, keywords_for_resume)
4. MAP each JD requirement to real experience; FLAG gaps honestly
5. DRAFT resume-tailored.md bullets per resume-standards (verb + skill + result)

## Workflow

### Step 1
READ refs/jd-parsing-guide.md, resume-standards.md, routing-rules.md ethics

### Step 2
ASK prep_task; READ resume_source

### Step 3
PARSE JD → WRITE job/jd-analysis.yaml (must_have, keywords_for_resume)

### Step 4
MAP each JD requirement to real experience; FLAG gaps honestly

### Step 5
DRAFT resume-tailored.md bullets per resume-standards (verb + skill + result)

### Step 6
WRITE resume-diff.md — what changed and why

### Step 7
IF author asks to invent experience → refuse F4

### Step 8
SYNC application-checklist resume items checked

### Decision logic

```
IF JD missing → ASK paste or link summary
IF no matching experience → suggest honest gap narrative; no fabrication
IF inflated claims → tone down to verifiable facts
```

## Outputs

Profile: `hybrid`

Return artifacts plus a narrative summary.

## Tools

| ID | Use | Constraints |
|----|-----|-------------|
| ask_user, |  |  |

## Failure Modes

| ID | Signal | Recovery |
|----|--------|----------|
| F1 | no JD or role | ask prep_task |
| F2 | no source | ask paste |
| F3 | no overlap | honest gap plan; no fake fill |
| F4 | fake company or role | refuse ethics |
| F5 | user wants guaranteed hire | refuse |

## Dependencies

- `skill-core`
- `job-prep-assistant`

## Additional Resources

- [IR source](references/ir.md)
