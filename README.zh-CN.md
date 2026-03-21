# better-work-skill

### 面向编码代理的验证优先执行协议

**[🇺🇸 English](README.md)** | **🇨🇳 中文**

`better-work-skill` 是一个轻量的 coding agent 工作协议。它不提供新工具，也不提供新模型能力，而是优化 agent 使用现有工具的方式：

- 更少猜测
- 更少过早放弃
- 更少过早要求用户介入
- 更少“没验证就说完成”
- 更多主动排查
- 更多基于证据的收尾
- 更好的阻塞交接质量
- 更好的多步骤任务连续性

这个版本把三层能力合在一起：

- 用 `high-agency` 做行为内核
- 用 `better-work` 做产品外壳和命令面
- 用轻量版 GSD 思路做长任务骨架

## 现在它多了什么

除了原来的高执行标准之外，这个版本还新增了：

1. 轻量阶段流
2. `plan / execute` 两个模式
3. 面向长任务的最小状态文件

它的目标不是把简单任务变重，而是让中等复杂度任务更稳。

## 工作流模型

Better Work 现在采用四阶段模型：

1. `intake`：澄清目标、约束、成功标准
2. `plan`：拆成可验证的小步
3. `execute`：逐步推进并保留最新证据
4. `closeout`：以验证完成或结构化交接结束

对于小任务，直接执行，不强制写文件。

对于多步骤或跨会话任务，可以使用 `templates/` 里的四个模板：

- `TASK.md`
- `PLAN.md`
- `STATE.md`
- `HANDOFF.md`

这些文件都应该保持简短，只服务执行，不写成长文档。

## 什么时候该用状态文件

以下场景建议启用这些模板：

- 任务涉及多个文件或多个系统
- 任务大概率会跨会话继续
- 任务已经开始循环或丢上下文
- 任务很可能需要交接

如果任务足够小，能马上完成并验证，就不要强行写文件。

## 命令

- `/better-work`
- `/better-work verify`
- `/better-work unstick`
- `/better-work handoff`
- `/better-work review`
- `/better-work plan`
- `/better-work execute`

其中：

- `verify`：强化验证和收尾质量
- `unstick`：强化诊断、换路和排障恢复
- `handoff`：输出高信息量交接
- `review`：检查同类问题、边界和上下游影响
- `plan`：澄清任务并拆解步骤
- `execute`：从现有计划或状态继续推进

## 轻量模板

这些模板故意保持很短，方便真实使用：

- [TASK.md](templates/TASK.md)
- [PLAN.md](templates/PLAN.md)
- [STATE.md](templates/STATE.md)
- [HANDOFF.md](templates/HANDOFF.md)

## 快速开始

### Codex CLI

```bash
mkdir -p ~/.codex/skills/better-work
curl -o ~/.codex/skills/better-work/SKILL.md \
  https://raw.githubusercontent.com/d-wwei/better-work-skill/main/codex/better-work/SKILL.md

mkdir -p ~/.codex/prompts
curl -o ~/.codex/prompts/better-work.md \
  https://raw.githubusercontent.com/d-wwei/better-work-skill/main/commands/better-work.md
```

然后在对话里输入：

```text
$better-work
```

## 使用预期

启用后，agent 应该更倾向于：

- 先查证，再提问
- 先验证，再宣称完成
- 重复失败后主动换方向
- 长任务时只在必要时写轻量状态
- 真阻塞时给出有边界、有证据的交接

## 为什么这版更强

旧版 Better Work 强在执行纪律，但对长任务的上下文保持支持不够。

这版保留了原来的“高执行标准”，同时补上了：

- 轻量计划模式
- 连续执行模式
- 最小状态模板
- 小任务和长任务的分流策略

结果是：依然轻，但更不容易在真实工程任务里散架。

## 仓库补充说明

- `.gitignore` 已忽略 `.DS_Store` 这类本地噪音文件
- `evals/trigger-prompts/` 提供最小触发样例
- `evals/closeout-cases.md` 用来约束后续版本的收尾行为
