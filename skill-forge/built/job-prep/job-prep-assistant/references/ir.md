job-prep-assistant

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
Route job preparation: major + target role → score job-catalog.yaml, confirm, auto-install resume-tailor / behavioral-interview / tech-interview-lite, handoff with application checklist and mock-questions plan.

## Context
User asks 求职, 简历, 面试准备, 校招, 国企综测, Java后端面试. Triggers: "帮我准备面试", "改简历", "产品经理求职", "install resume skill".

## Constraints
- 时间：routing + install one session
- 精度：confirm before install; ethics — no fake credentials, no offer guarantee
- 工具限制：skill-core install CLI; scope=project default

---

# 2. Inputs（输入定义）

## Required Inputs
## Required
- major: string
- target_job: string — role or JD summary

## Optional
- project_dir, host, scope, jd_text

---

# 3. Outputs（输出定义）

**Profile:** hybrid

1. `job/session.yaml`
2. `job/application-checklist.md`
3. `job/mock-questions-plan.md`
4. Installed prep skill(s)
5. HANDOFF with prep_task prompt

---

# 5. Execution Plan（执行流程）

1. ASK major, target_job; READ refs/routing-rules.md
2. READ refs/job-catalog.yaml; COMPUTE scores for internet-product java-backend state-owned-comprehensive
3. IF tie or low score → ASK clarify or show top 3 matches
4. SHOW match and skills_to_install; ASK confirm before install
5. SHOW ethics disclaimer: no fake experience; no offer guarantee; ASK ethics_ack
6. WRITE job/session.yaml per session-schema.yaml
7. CREATE job/{workspace_subdir}/
8. RESOLVE skill per install.resolve_order (job-prep built path); install resume-tailor behavioral-interview tech-interview-lite as matched
9. RUN skill-core install for each skill; LOG results
10. WRITE job/application-checklist.md from application-checklist-template
11. WRITE job/mock-questions-plan.md — which mocks per installed skills
12. HANDOFF: READ installed SKILL.md; ASK prep_task (JD or focus area)

---

# 6. Decision Logic（决策系统）

```
IF user declines confirm → block install
IF ethics_ack false → STOP; explain signaling integrity
IF install fails → retry built path; manual command
IF ambiguous → ask choose product vs java-backend vs state-owned-comprehensive
IF user asks fake resume or guaranteed offer → refuse (F4)
```

---

# 7. Tool / API Binding（工具绑定）

| Portable ID | Use | Constraints |
|-------------|-----|-------------|
| ask_user, | | |

---

# 10. Failure Modes（失败模式）

## F1: no-match
- Signal: score below min_score
- Recovery: top 3 + clarify
- Severity: block

## F2: install-fail
- Signal: CLI error
- Recovery: manual command
- Severity: block

## F3: ambiguous-match
- Signal: tie
- Recovery: user choose
- Severity: block

## F4: ethics-violation
- Signal: fake credentials or offer guarantee
- Recovery: refuse
- Severity: block

## F5: unconfirmed-install
- Signal: user did not confirm
- Recovery: block install
- Severity: block

---

# 12. Skill Graph Dependencies（依赖）

```yaml
depends_on:
  - skill-core
provides:
  - job-prep-router
```

---

# 13. Versioning（版本系统）

```yaml
version: "1.0.0"
status: stable
```
