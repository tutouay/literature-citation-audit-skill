# Literature Citation Audit Skill v7.3

[English](#english-version) | [中文](#chinese-version)

<a name="english-version"></a>
## English

A citation-audit workflow for checking whether academic sources genuinely support the claims assigned to them.

Version 7 was rebuilt after testing exposed several failure modes in general chat and agent environments.

### Quick start

1. Paste the Skill file into the AI chat box. ChatGPT Thinking mode is recommended.
2. Enter the following instruction in the chat box:
```text
Process the following text using this Skill file:
```
3. Paste the sentence or paragraph you want to audit. The text should contain at least one in-text citation.
Example:
```text
I love learning very much, and it brings me joy (XXX, 2026).
```
4. Send the message and wait for the audit result.
   
> ‼️ To improve processing speed, you may also provide the corresponding reference entries, with or without links.
Example:
```text
XXX. (2026). Good good study, day day up. https://doi.org/12.345.com
```
> ‼️ You do not need to provide PDF files at the beginning. If the AI still cannot verify the full text after completing its search, you may upload the relevant PDF later.

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

## v7.1 evidence handling

- The first table column reconstructs complete bibliographic information and includes a DOI or official link when the user supplies only in-text citations.
- The evidence column supports verbatim evidence, full-text synthesis, and a direct unsuitable-source finding after full-text review.
- Grouped citations are evaluated across the citation group.
- Obvious source-text errors may be flagged without inferring intent or proposing corrections.

## v7.2 source classification and link hygiene

- Review-section summaries are treated as secondary evidence, and original sources are prioritized for central claims.
- The source-evidence column is separated from analytical judgments.
- DOI values use canonical clickable URLs.
- Tracking parameters are removed from formal links.
- Results do not contain self-referential statements about the Skill or prompt.

## v7.3 traced original sources

- Original sources traced from review or background sections are shown as separate rows immediately after the currently cited source.
- Review evidence and original-source evidence remain separate.
- Each source receives its own alignment score.
- Original-source supplementation or replacement is raised only for central theories, key mechanisms, concept definitions, or priority claims.
  
<a name="chinese-version"></a>
## 中文

用于核查学术引用是否真实存在，以及文献原文能否支持当前引文位置承担的具体命题。

v7 根据实际测试中暴露的问题重新设计。

### 快速开始

1. 在 AI（推荐Chatgpt Thinking模式） 对话框 中粘贴 Skill 文件。
2. 在 对话框中输入：
```text
   通过这个Skill文件处理：
```
3. 在 对话框中粘贴需要核查的句子或段落，即有文内引用的段落
例如：
```text
I love learning very much, and it brings me joy(xxx.,2026).
```
4. 发送 - 等待
   
‼️. 想提高速度可以把带或不带链接的参考文献一并提交
```text
例如：xxx.,(2026) Good good study, Day day up.http://study.doi.orj/12.345.com
```
‼️. 无需提供PDF，AI完成检索后仍无法核验全文时，可以再补充PDF。

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

## v7.1 证据处理

- 用户只提供文内引用时，表格第一列补充完整书目信息和 DOI 或正式链接。
- 文献证据列支持原句证据、全文综合证据和全文核查后的不适合判断。
- 多篇文献共同引用时，按照整个引用组分配证据责任。
- 可以标记原文中直接可见的明显问题，但不能推测原意或提供修改方案。

## v7.2 来源分类与链接规范

- 文献综述中的既有研究概括归为二手证据，核心命题优先追溯原始来源。
- 文献证据列与适配性分析严格分开。
- DOI 使用可点击的标准 URL。
- 正式链接删除追踪参数。
- 结果中不再出现关于 Skill 或提示词的执行声明。

## v7.3 原始来源追溯

- 从综述或背景部分追溯到的原始来源，在同一核查表中另起一行，并紧接当前引用文献。
- 综述证据和原始来源证据严格分开。
- 两类文献分别评分。
- 只有核心理论、关键机制、概念定义或首创性主张，才在核查问题中说明原始来源是否应补充或替代当前引用。
