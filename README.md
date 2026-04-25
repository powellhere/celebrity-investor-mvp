# Win95 Investor MVP

一个 Win95 风格的投资人批判分析器。

你可以上传或粘贴一段 business plan / pitch memo / project proposal，然后选择一位投资人视角。系统会根据不同投资人的判断偏好，输出项目的 feasibility score、red flags、MVP validation 建议和 due diligence questions。

这个项目不是 AI chatbot，也不会调用外部模型。它是一个轻量级 MVP：用前端界面收集文本，用 Node.js 后端根据关键词、文本长度和投资人权重做启发式分析。

## 它能做什么

- 上传或粘贴项目计划书文本
- 选择 9 种投资人风格：
  - Donald Trump：brand / leverage / media
  - Elon Musk：first principles / tech
  - Warren Buffett：moat / cash flow
  - Mark Cuban：sales / operations
  - Cathie Wood：disruptive innovation
  - Peter Thiel：monopoly / secret
  - Masayoshi Son：TAM / platform scale
  - Ray Dalio：risk / systems
  - Chamath Palihapitiya：narrative / growth
- 从 5 个维度给项目打分：
  - Market
  - Defensibility
  - Unit economics
  - Execution
  - MVP validation
- 生成：
  - Overall feasibility
  - Critical Analysis
  - Red Flags
  - Minimum MVP Logic
  - Investor Due Diligence Questions

## 项目结构

```text
.
├── server.js              # Node.js 后端和静态文件服务
├── package.json           # 启动脚本和 Node 版本要求
└── public/
    ├── index.html         # 页面结构
    ├── styles.css         # Win95 视觉风格
    └── app.js             # 前端交互和报告渲染
```

## 如何运行

需要 Node.js 18 或以上版本。

```bash
npm start
```

然后打开：

```text
http://localhost:4173
```

如果想换端口：

```bash
PORT=3000 npm start
```

## 如何使用

1. 打开网页。
2. 上传一个项目计划文件，或直接粘贴文本。
3. 选择一个投资人风格。
4. 点击 `Run Critical Analysis`。
5. 查看右侧生成的批判报告。

建议输入至少 120 个字符。文本太短时，系统无法判断 market、finance、execution 等关键信号。

## 分析逻辑

后端会扫描计划书里是否出现与 5 个维度相关的信号词，例如：

- Market：market、TAM、用户、客户、痛点、增长
- Defensibility：moat、IP、data、护城河、专利、网络效应
- Unit economics：revenue、gross margin、CAC、LTV、定价、现金流
- Execution：team、roadmap、sales、团队、渠道、里程碑
- MVP validation：MVP、prototype、pilot、实验、访谈、demo

每位投资人都有不同权重。比如 Buffett 更看重 defensibility 和 unit economics，Musk 更看重技术壁垒、执行速度和 MVP validation，Son 更看重 market size。

最终分数不是投资建议，而是帮助用户快速发现计划书里的薄弱环节。

## 当前限制

- 这是规则型 MVP，不是大语言模型。
- PDF / DOCX 文件目前只是按浏览器文本读取能力尝试解析，TXT / MD 效果最好。
- 系统不会判断事实真假，只判断文本中有没有出现相关商业证据。
- 分数只能作为 early-stage feedback，不能替代真实客户访谈、财务建模或 investor due diligence。

## 适合的使用场景

- 早期创业 idea 自查
- pitch deck 写作前的逻辑检查
- business plan 的风险梳理
- 快速生成 investor-style 追问

## License

Private MVP. Add a license before using it as an open-source project.
