# MD 兼容视图 — `eval-tech-interview-lite.yaml`

> **权威源文件**：同目录 `eval-tech-interview-lite.yaml`（本文件由 `skill-core` 自动生成，请勿手改；改源文件后重新 `batch build` 或运行 compat 同步。）

| 项 | 值 |
|----|-----|
| 类型 | `yaml` |
| 路径 | `refs/eval-tech-interview-lite.yaml` |
| 用途 | Skill 编译测试断言（eval）；CI `batch build --test` 读取 YAML 源文件。 |

## 内容

```yaml
tests:
  - id: T1
    description: tech interview workflow
    assert:
      contains: ["tech-interview-guide", "java-backend", "mock-questions.md"]
      sections: ["Quick Start", "Workflow", "Failure Modes"]

  - id: T2
    description: topics
    assert:
      contains: ["Spring", "MySQL", "algorithm", "tech-prep.md"]

  - id: T3
    description: integrity
    assert:
      contains: ["OA cheat", "guaranteed pass", "refuse"]

  - id: T4
    description: deps
    assert:
      contains: ["job-prep-assistant", "prep_task"]
```
