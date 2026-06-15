---
name: job-prep-assistant
description: >-
  Route job preparation: major + target role → score job-catalog.yaml, confirm, auto-install
  resume-tailor / behavioral-interview / tech-interview-lite, handoff with application
  checklist and mock-questions plan. Use when user asks 求职, 简历, 面试准备, 校招, 国企综测, Java后端面试.
  Triggers: "帮我准备面试", "改简历", "产品经理求职", "install resume skill".
metadata:
  version: "1.0.0"
  status: stable
  protocol: skill-protocol-v2
compatibility: skill-core install CLI; scope=project default
---

# Job Prep Assistant

## Quick Start

1. ASK major, target_job; READ refs/routing-rules.md
2. READ refs/job-catalog.yaml; COMPUTE scores for internet-product java-backend state-owned-comprehensive
3. IF tie or low score → ASK clarify or show top 3 matches
4. SHOW match and skills_to_install; ASK confirm before install
5. SHOW ethics disclaimer: no fake experience; no offer guarantee; ASK ethics_ack

## Workflow

### Step 1
ASK major, target_job; READ refs/routing-rules.md

### Step 2
READ refs/job-catalog.yaml; COMPUTE scores for internet-product java-backend state-owned-comprehensive

### Step 3
IF tie or low score → ASK clarify or show top 3 matches

### Step 4
SHOW match and skills_to_install; ASK confirm before install

### Step 5
SHOW ethics disclaimer: no fake experience; no offer guarantee; ASK ethics_ack

### Step 6
WRITE job/session.yaml per session-schema.yaml

### Step 7
CREATE job/{workspace_subdir}/

### Step 8
RESOLVE skill per install.resolve_order (job-prep built path); install resume-tailor behavioral-interview tech-interview-lite as matched

### Step 9
RUN skill-core install for each skill; LOG results

### Step 10
WRITE job/application-checklist.md from application-checklist-template

### Step 11
WRITE job/mock-questions-plan.md — which mocks per installed skills

### Step 12
HANDOFF: READ installed SKILL.md; ASK prep_task (JD or focus area)

### Decision logic

```
IF user declines confirm → block install
IF ethics_ack false → STOP; explain signaling integrity
IF install fails → retry built path; manual command
IF ambiguous → ask choose product vs java-backend vs state-owned-comprehensive
IF user asks fake resume or guaranteed offer → refuse (F4)
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
| F1 | score below min_score | top 3 + clarify |
| F2 | CLI error | manual command |
| F3 | tie | user choose |
| F4 | fake credentials or offer guarantee | refuse |
| F5 | user did not confirm | block install |

## Dependencies

- `skill-core`

## Additional Resources

- [IR source](references/ir.md)
