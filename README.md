# 如何正确地和 AI 对话
# How to Talk to AI Effectively

> 一份关于如何向大语言模型（如 Claude、GPT 等）提问、让它给出真正有用回答的实用指南。
>
> A practical, no-nonsense guide to prompting large language models (Claude, GPT, etc.) so they actually give you useful answers.

---

## 为什么这很重要 / Why it matters

AI 不会读心。你给的输入质量，直接决定输出质量。同一个问题，问法不同，结果可能天差地别。学会怎么问，比换一个更强的模型更划算。

AI can't read your mind. The quality of your input directly determines the quality of its output. The same question, asked two different ways, can produce wildly different results. Learning *how to ask* pays off more than switching to a bigger model.

---

## 十条核心原则 / 10 Core Principles

### 1. 给足上下文 / Give enough context

把 AI 当成一个聪明、但对你的处境一无所知的新同事。它看不到你脑子里的背景。

Treat the AI like a smart new colleague who knows nothing about your situation. It cannot see what's in your head.

- ❌ “帮我改一下这段代码。” / "Fix this code for me."
- ✅ “这是一个 Python Flask 接口，高并发下会超时。代码如下 […]。帮我找出瓶颈并优化，保持接口签名不变。” / "This is a Python Flask endpoint that times out under load. Here's the code […]. Find the bottleneck and optimize it, keeping the signature unchanged."

### 2. 说清楚你到底要什么 / Be specific about what you want

模糊的请求得到模糊的回答。明确目标、范围、受众、长度。

Vague requests get vague answers. Pin down the goal, scope, audience, and length.

- ❌ “介绍一下机器学习。” / "Tell me about machine learning."
- ✅ “用 3 段话、面向完全没有技术背景的人，解释什么是机器学习，并配一个生活中的类比。” / "In 3 short paragraphs, for someone with zero technical background, explain machine learning with one everyday analogy."

### 3. 举例子（Few-shot）/ Show examples

给一两个“输入 → 期望输出”的例子，比任何描述都管用。

One or two "input → desired output" examples beat paragraphs of description.

> 把句子改写得更专业。例如：“这玩意儿坏了” → “该设备目前无法正常工作”。现在改写：[…]
>
> Rewrite sentences to sound more professional. e.g. "this thing is broken" → "the device is currently not functioning". Now rewrite: […]

### 4. 拆解复杂任务 / Break it down

别一次扔一个庞大任务。拆成步骤，或让 AI 先列计划、你确认后再执行。

Don't dump one giant task. Split it into steps, or have the AI propose a plan first and execute only after you approve.

> 先列出实现这个功能的步骤，等我确认后再开始写代码。
>
> First list the steps to build this feature; wait for my OK before writing any code.

### 5. 指定输出格式 / Specify the format

要表格就说表格，要 JSON 就说 JSON，要代码就说语言。

Want a table, JSON, or code? Say so explicitly.

> 用 Markdown 表格输出，列为：方案、优点、缺点、成本。
>
> Output as a Markdown table with columns: Option, Pros, Cons, Cost.

### 6. 设定角色与约束 / Set a role and constraints

角色让回答更聚焦；约束防止它跑偏。

A role focuses the answer; constraints keep it from wandering.

> 你是一位资深安全工程师，从攻击者视角审查这段代码。只用标准库，不要引入第三方依赖。
>
> You are a senior security engineer; review this code from an attacker's perspective. Use the standard library only — no third-party dependencies.

### 7. 让它先想再答 / Ask it to think first

对推理、数学、调试类问题，让它“一步步思考”再下结论，准确率明显更高。

For reasoning, math, and debugging, ask it to "think step by step" before concluding — accuracy goes up noticeably.

> 先分析所有可能的原因，再给出你认为最可能的那一个。
>
> Analyze all possible causes first, then give the single most likely one.

### 8. 迭代，而不是重开 / Iterate, don't restart

第一版不满意？别推倒重来，针对性地指出哪里不对。

Not happy with v1? Don't start over — point precisely at what's wrong.

> 很好，但第二点太笼统了，展开讲讲，并加一个具体例子。
>
> Good, but point 2 is too generic — expand it and add a concrete example.

### 9. 核实，别盲信 / Verify, don't trust blindly

AI 会自信地说错话（幻觉）。关键事实、数字、代码，自己验证，或让它给出依据。

AI can be confidently wrong (hallucination). Verify key facts, numbers, and code yourself — or make it cite sources.

> 这个 API 你确定存在吗？给出官方文档链接。
>
> Are you sure this API exists? Give me the official documentation link.

### 10. 给反馈 / Give feedback

告诉它什么有用、什么没用，它会在对话中调整。

Tell it what worked and what didn't; it adapts within the conversation.

> 以后回答都用中文，代码注释也用中文。
>
> From now on, answer in Chinese and write code comments in Chinese too.

---

## 常见误区 / Common Pitfalls

| 误区 / Pitfall | 怎么改 / Fix |
| --- | --- |
| 一句话问天问地，指望它猜中意图 / One vague line, expecting mind-reading | 给背景、目标、约束 / Give context, goal, constraints |
| 把第一个回答当最终答案 / Treating the first answer as final | 迭代追问 / Iterate |
| 不给上下文却怪它“不懂我” / Blaming it for context you never gave | 先把背景说清 / State the background first |
| 超长任务不拆解 / Dumping a huge task whole | 拆成步骤 / Break into steps |
| 盲信它的事实和代码 / Blindly trusting its facts & code | 自己核实 / Verify yourself |

---

## 万能模板 / A Universal Template

```
[角色 / Role]      你是一位 ___。 / You are a ___.
[背景 / Context]   我正在做 ___，目前情况是 ___。 / I'm working on ___; the situation is ___.
[任务 / Task]      请帮我 ___。 / Please help me ___.
[约束 / Limits]    要求：___（格式 / 长度 / 语气 / 限制）。 / Requirements: ___ (format / length / tone / limits).
[示例 / Example]   例如：___（可选）。 / For example: ___ (optional).
```

---

## 进阶技巧 / Advanced Tips

- **让它反过来问你** / Let it interview you：“动手前，先问我 3 个需要澄清的问题。” / "Before starting, ask me 3 clarifying questions."
- **让它自我检查** / Make it self-review：“写完后，从挑剔的审稿人视角找出 3 个潜在问题。” / "After finishing, find 3 weaknesses as a harsh reviewer would."
- **当陪练，而非答案机** / Use it as a sparring partner：“别直接给答案，引导我自己想出来。” / "Don't give the answer — guide me to it."
- **重要任务多生成几版再挑** / Generate several versions for important work：“给我 3 个不同风格的方案。” / "Give me 3 options in different styles."

---

## 一句话总结 / TL;DR

**把 AI 当成一个聪明、博学、但对你处境一无所知的合作者 —— 你说得越清楚，它帮得越好。**

**Treat AI as a smart, knowledgeable collaborator who knows nothing about your situation — the clearer you are, the better it helps.**

---

## 许可 / License

[MIT](LICENSE) · 欢迎自由使用、修改、分享。 / Free to use, modify, and share.
