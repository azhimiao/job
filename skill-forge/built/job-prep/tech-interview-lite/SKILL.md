---
name: tech-interview-lite
description: >-
  Lite technical interview prep: JD-aligned fundamentals, algorithm drills, Java backend
  topics — mock-questions with guided review, not OA cheating. Use when after
  job-prep-assistant routes java-backend or tech roles. Triggers: "技术面试", "Java八股", "算法题",
  "后端面试".
metadata:
  version: "1.0.0"
  status: stable
  protocol: skill-protocol-v2
---

# Tech Interview Lite

## Quick Start

1. READ refs/tech-interview-guide.md, jd-parsing-guide.md if JD available
2. ASK prep_task; READ job/jd-analysis.yaml if exists
3. BUILD tech-prep.md — must_have topics for java-backend level
4. GENERATE mock-questions.md — algorithm + CS basics + Java/Spring
5. RUN practice: author explains → feedback complexity and tradeoffs

## Workflow

### Step 1
READ refs/tech-interview-guide.md, jd-parsing-guide.md if JD available

### Step 2
ASK prep_task; READ job/jd-analysis.yaml if exists

### Step 3
BUILD tech-prep.md — must_have topics for java-backend level

### Step 4
GENERATE mock-questions.md — algorithm + CS basics + Java/Spring

### Step 5
RUN practice: author explains → feedback complexity and tradeoffs

### Step 6
WRITE mock-feedback.md; highlight gaps for study plan

### Step 7
IF user asks OA cheat → refuse F4

### Decision logic

```
IF intern/campus → trim system design; focus arrays trees basics
IF java-backend → emphasize Spring MySQL Redis concurrency
IF user only wants answers without understanding → coach mode; refuse dump
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
| F1 | no tech focus | ask prep_task |
| F2 | complete online assessment fraud | refuse integrity |
| F3 | expert SRE deep dive | narrow to lite guide |
| F4 | fake project deep dive | refuse |
| F5 | guaranteed pass | refuse |

## Dependencies

- `skill-core`
- `job-prep-assistant`

## Additional Resources

- [IR source](references/ir.md)
