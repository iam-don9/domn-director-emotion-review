# domn-director-emotion-review

![domn-director-emotion-review 封面](assets/readme/hero.webp)

> 情绪戏真实感审核与改写。

## 是什么

情绪戏真实感审核与改写。本仓库是一个 Agent 技能（SKILL.md 为唯一权威定义），把上面的方法论沉淀为可被对话触发的可执行流程。

## 怎么做（工作流）

<p align="center">
  <img src="./assets/readme/workflow.svg" width="100%" alt="domn-director-emotion-review 工作流：定位来源 → 审微动作 → 理台词 → 查连续 → 出改写。先判来源形式，再回对应分支">
</p>

1. **定位来源**
2. **审微动作**
3. **理台词**
4. **查连续**
5. **出改写**

## 怎么用

将本仓库放入支持 `SKILL.md` 的 Agent 技能目录：

- **WorkBuddy**：`~/.workbuddy/skills/domn-director-emotion-review/`
- **Codex / 其他**：对应 skills 目录

然后在对话中触发，例如：

```
用 domn-director-emotion-review 帮我处理一段需求。
```

## 依赖

纯提示词方法论，无代码依赖；接受剧本 / 分镜 / 视频提示词文本.

## 仓库结构

```
domn-director-emotion-review/
├── SKILL.md                 # 技能定义（唯一权威）
├── references/              # 方法论弹药库
├── assets/                  # 模板 / 占位素材
└── assets/readme/           # 本 README 的视觉资产（hero.webp / workflow.svg）
```

## 许可

本仓库内容以 `SKILL.md` 为唯一权威定义。如附带 `LICENSE` 文件，以其为准。

---

*README 由 `beautify-github-readme` 生成 · 封面图来自作者作品集，强调色由封面图采样派生。*
