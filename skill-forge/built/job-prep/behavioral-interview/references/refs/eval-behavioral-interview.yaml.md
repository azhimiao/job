# MD 兼容视图 — `eval-behavioral-interview.yaml`

> **权威源文件**：同目录 `eval-behavioral-interview.yaml`（本文件由 `skill-core` 自动生成，请勿手改；改源文件后重新 `batch build` 或运行 compat 同步。）

| 项 | 值 |
|----|-----|
| 类型 | `yaml` |
| 路径 | `refs/eval-behavioral-interview.yaml` |
| 用途 | Skill 编译测试断言（eval）；CI `batch build --test` 读取 YAML 源文件。 |

## 内容

```yaml
tests:
  - id: T1
    description: behavioral workflow
    assert:
      contains: ["star-framework", "STAR", "behavioral-prep.md"]
      sections: ["Quick Start", "Workflow", "Failure Modes"]

  - id: T2
    description: mock outputs
    assert:
      contains: ["mock-questions.md", "mock-feedback.md", "state-owned-comprehensive"]

  - id: T3
    description: ethics
    assert:
      contains: ["fake STAR", "refuse ethics"]

  - id: T4
    description: deps
    assert:
      contains: ["job-prep-assistant", "prep_task"]
```
