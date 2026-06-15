---
name: behavioral-interview
description: >-
  Prepare behavioral and structured interviews using STAR: build story bank, run mock Q&A,
  feedback rubric — for product, SOE 综测, general hire. Use when after job-prep-assistant
  routes behavioral prep. Triggers: "行为面试", "STAR", "国企结构化", "无领导小组".
metadata:
  version: "1.0.0"
  status: stable
  protocol: skill-protocol-v2
---

# Behavioral Interview

## Quick Start

1. READ refs/star-framework.md, routing-rules.md
2. ASK prep_task; ASK 2-3 real story_seeds from author
3. FOR each seed → EXPAND STAR; WRITE behavioral-prep.md
4. GENERATE mock-questions.md — role-specific (internet-product or state-owned-comprehensive)
5. RUN mock loop: ASK answer → SCORE per star-framework rubric → WRITE mock-feedback.md

## Workflow

### Step 1
READ refs/star-framework.md, routing-rules.md

### Step 2
ASK prep_task; ASK 2-3 real story_seeds from author

### Step 3
FOR each seed → EXPAND STAR; WRITE behavioral-prep.md

### Step 4
GENERATE mock-questions.md — role-specific (internet-product or state-owned-comprehensive)

### Step 5
RUN mock loop: ASK answer → SCORE per star-framework rubric → WRITE mock-feedback.md

### Step 6
IF author invents stories → refuse F4

### Step 7
UPDATE mock-questions-plan in session notes

### Decision logic

```
IF prep_task vague → infer from job/session.yaml target_job
IF SOE 综测 → add 价值观/职业规划/团队合作题
IF product PM → add 需求冲突、数据决策题
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
| F1 | author gives nothing real | ask seeds |
| F2 | unknown interview type | clarify prep_task |
| F3 | polished fiction | refuse; return to facts |
| F4 | fake STAR events | refuse ethics |
| F5 | mental health crisis | limits; refer professional |

## Dependencies

- `skill-core`
- `job-prep-assistant`

## Additional Resources

- [IR source](references/ir.md)
