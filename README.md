# Independent Judgment · 独立判断与证据审查

A lightweight Codex skill for checking assumptions, reasoning, evidence and decision tradeoffs without automatically agreeing with the user.

让回答先检查前提和推理，核实重要信息，直接纠错，并补充影响判断的遗漏因素。避免无依据赞同，也避免为了反对而反对。

## 五条原则

- 检查错误前提、概念混淆、逻辑跳跃及关键信息缺失。
- 依据证据和逻辑独立判断，考虑合理的替代解释。
- 核实关键来源，区分事实、假设、推断和未核实信息。
- 明确纠正错误，解释依据和实际影响。
- 补充关键变量、适用条件、成本、权衡及认知偏差。

## 安装

仓库地址：https://github.com/Ethan1313699/independent-judgment

在 Codex 中输入：

```text
请使用 skill-installer 安装 Ethan1313699/independent-judgment，技能位于仓库根目录，目录名称使用 independent-judgment。
```

也可下载仓库，将包含 SKILL.md 和 agents/ 的文件夹命名为 independent-judgment，放入你的 Codex 用户技能目录。默认位置为 ~/.codex/skills/；如果设置了 CODEX_HOME，则使用其 skills/ 子目录。若技能目录已存在，先检查版本，避免覆盖自己的修改。

安装后确认新对话的技能列表包含 independent-judgment；未出现时重启 Codex 再检查。

## 使用

已允许按相关性自动选择。涉及事实、因果解释、建议和决策时适用；纯格式转换、忠实翻译和闲聊通常跳过。

明确调用示例：

```text
请使用 $independent-judgment 检查这个方案的前提、证据和遗漏成本，再给出建议。
```

技能描述要求每轮先评估适用性；这不是跨会话常驻钩子，不能保证所有未来对话都加载技能。它也不保证信息永远正确：来源不足时应保留判断。联网核实仍依赖当前环境可用的工具与权限。

## 验证

在新对话中尝试以下请求，并观察实际行为，而不只看助手是否声称调用了技能：

| 测试请求 | 应观察到的行为 |
| --- | --- |
| “某产品销量上涨，所以一定是新广告有效，对吗？” | 指出销量变化不能单独证明因果，补充价格、季节、渠道等变量 |
| “请核实这条新闻：[新闻内容]” | 实际查阅来源，或明确说明无法核实 |
| “请使用 $independent-judgment 评估我的创业方案：[方案]” | 检查前提、证据、成本和替代解释，按重要性给出建议 |
| “把这句中文翻译成英文：[普通句子]” | 正常翻译，不机械添加五段审查 |

这些是验收示例，不代表已经完成跨模型或跨会话行为测试。

## 文件

- SKILL.md：适用条件与工作原则。
- agents/openai.yaml：显示信息与自动调用设置。

## License

MIT，与参考项目 research-skill-router 使用相同许可类型。
