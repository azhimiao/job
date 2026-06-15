# 求职路由规则

读 `job-catalog.yaml`，打分 → **用户确认** → install → handoff。

## 匹配

- score = keyword_hits × 2 + major_match × 3
- min_score ≥ 2；tie ≤ 1 → ASK

## handoff

| skill | 首问 |
|-------|------|
| resume-tailor | 目标 JD 全文或链接 + 现有简历 |
| behavioral-interview | 岗位类型 + 最近 2 段可 STAR 的经历 |
| tech-interview-lite | 技术栈 + 目标级别（实习/校招/社招） |

## 伦理（劳动力市场信号理论语境）

- **信号**：简历与面试表现应真实反映能力（Spence signaling）
- 禁止：伪造学历/实习/项目、代写虚假经历
- 禁止：保证 offer、内推承诺
- 允许：结构化表达、STAR 演练、JD 对齐措辞（不夸大）
