# Literature Citation Audit Skill v7.3

[English](#english) | [中文](#中文)

## English

A citation-audit workflow for checking whether academic sources genuinely support the claims assigned to them.

Version 7 was rebuilt after testing exposed several failure modes in general chat and agent environments.

### What v7 changes

- A submitted paragraph automatically triggers a full audit.
- Complete bibliography entries are optional.
- The AI must identify references from in-text citations.
- At least a minimum web search is required for every source.
- A failed publisher page does not count as unavailable full text.
- Support judgments and percentage scores require verifiable full-text quotations.
- Sources without full text are marked unscored.
- Process narration, repeated confirmations, and unrequested rewriting are prohibited.
- Only actual citation and metadata problems are reported.

### Files

| File | Purpose |
|---|---|
| `SKILL.md` | English core skill |
| `SKILL.zh-CN.md` | Chinese core skill |
| `INPUT_TEMPLATE.md` | English user input form |
| `INPUT_TEMPLATE.zh-CN.md` | Chinese user input form |
| `TEST_PROMPT.md` | English compliance test |
| `TEST_PROMPT.zh-CN.md` | Chinese compliance test |
| `CHANGELOG.md` | Version history |

### Quick start

1. Install one skill file in the AI instruction environment.
2. Complete the matching input template.
3. Submit the paragraph with in-text citations.
4. Do not provide PDFs initially.
5. Upload a PDF only when the AI has exhausted reasonable retrieval routes and cannot verify the full text.

## 中文

用于核查学术引用是否真实存在，以及文献原文能否支持当前引文位置承担的具体命题。

v7 根据实际测试中暴露的问题重新设计。

### v7 的主要变化

- 用户提交段落后自动执行完整核查。
- 完整参考文献条目改为可选信息。
- AI 必须根据文内作者年份引用自行识别文献。
- 每篇文献至少完成最低网页检索。
- 出版社页面打不开不能直接判定全文不可获得。
- 支持性判断和百分比评分必须对应全文原句。
- 没有全文时标记暂不评分。
- 禁止过程播报、重复确认和未经要求的改写。
- 表格之后只报告真实问题。

### 快速开始

1. 在 AI 指令环境中安装一种语言的 Skill 文件。
2. 填写对应输入模板。
3. 提交带有文内引用的段落。
4. 首次不提供 PDF。
5. AI 完成合理检索后仍无法核验全文时，再补充 PDF。


## v7.1 evidence handling

- The first table column reconstructs complete bibliographic information and includes a DOI or official link when the user supplies only in-text citations.
- The evidence column supports verbatim evidence, full-text synthesis, and a direct unsuitable-source finding after full-text review.
- Grouped citations are evaluated across the citation group.
- Obvious source-text errors may be flagged without inferring intent or proposing corrections.

## v7.1 证据处理

- 用户只提供文内引用时，表格第一列补充完整书目信息和 DOI 或正式链接。
- 文献证据列支持原句证据、全文综合证据和全文核查后的不适合判断。
- 多篇文献共同引用时，按照整个引用组分配证据责任。
- 可以标记原文中直接可见的明显问题，但不能推测原意或提供修改方案。


## v7.2 source classification and link hygiene

- Review-section summaries are treated as secondary evidence, and original sources are prioritized for central claims.
- The source-evidence column is separated from analytical judgments.
- DOI values use canonical clickable URLs.
- Tracking parameters are removed from formal links.
- Results do not contain self-referential statements about the Skill or prompt.

## v7.2 来源分类与链接规范

- 文献综述中的既有研究概括归为二手证据，核心命题优先追溯原始来源。
- 文献证据列与适配性分析严格分开。
- DOI 使用可点击的标准 URL。
- 正式链接删除追踪参数。
- 结果中不再出现关于 Skill 或提示词的执行声明。


## v7.3 traced original sources

- Original sources traced from review or background sections are shown as separate rows immediately after the currently cited source.
- Review evidence and original-source evidence remain separate.
- Each source receives its own alignment score.
- Original-source supplementation or replacement is raised only for central theories, key mechanisms, concept definitions, or priority claims.

## v7.3 原始来源追溯

- 从综述或背景部分追溯到的原始来源，在同一核查表中另起一行，并紧接当前引用文献。
- 综述证据和原始来源证据严格分开。
- 两类文献分别评分。
- 只有核心理论、关键机制、概念定义或首创性主张，才在核查问题中说明原始来源是否应补充或替代当前引用。
