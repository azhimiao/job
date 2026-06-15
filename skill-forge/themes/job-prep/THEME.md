---
title: 求职准备
tags: [job-prep, resume, interview, STAR, router]
status: stable
version: "1.0"
---

# Theme: job-prep（路线图 #6）

专业 + 目标岗位 → 确认 → 安装 **resume-tailor / behavioral-interview / tech-interview-lite**。

## Skills

| 源文件 | 作用 |
|--------|------|
| `job-prep-assistant.skill.md` | 路由 + install |
| `resume-tailor.skill.md` | JD 解析 + 简历 tailoring |
| `behavioral-interview.skill.md` | STAR 行为面试模拟 |
| `tech-interview-lite.skill.md` | 技术/笔试 lite 准备 |

## Catalog 示例

- 互联网产品 → resume + behavioral
- Java 后端 → resume + tech-interview-lite
- 国企综测 → behavioral + resume

## 编译

```bash
python skill-core/skill.py batch build job-prep --test
python skill-core/skill.py install examples/job-prep-assistant --host cursor --scope global
```

## 伦理

不代写虚假信息、不伪造经历、**不保证 offer**。
