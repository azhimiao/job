# MD 兼容视图 — `eval-job-prep-assistant.yaml`

> **权威源文件**：同目录 `eval-job-prep-assistant.yaml`（本文件由 `skill-core` 自动生成，请勿手改；改源文件后重新 `batch build` 或运行 compat 同步。）

| 项 | 值 |
|----|-----|
| 类型 | `yaml` |
| 路径 | `refs/eval-job-prep-assistant.yaml` |
| 用途 | Skill 编译测试断言（eval）；CI `batch build --test` 读取 YAML 源文件。 |

## 内容

```yaml
tests:
  - id: T1
    description: job prep router
    assert:
      contains: ["job-catalog.yaml", "resume-tailor", "session.yaml"]
      sections: ["Quick Start", "Workflow", "Failure Modes"]

  - id: T2
    description: confirm install
    assert:
      contains: ["confirm", "install", "resolve_order", "job-prep"]

  - id: T3
    description: prep skills list
    assert:
      contains: ["behavioral-interview", "tech-interview-lite", "no offer guarantee", "internet-product"]

  - id: T4
    description: handoff checklist
    assert:
      contains: ["HANDOFF", "application-checklist.md", "block install"]
```
