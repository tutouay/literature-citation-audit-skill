# Changelog

## v7.3

### English

1. Added a fixed presentation rule for original sources traced from review papers.
2. Required traced original sources to appear as separate rows immediately after the currently cited source.
3. Kept review evidence and original-source evidence separate.
4. Required separate alignment scores for review papers and original sources.
5. Limited citation-replacement issues to central theories, key mechanisms, concept definitions, and priority claims.
6. Prevented indefinite citation-chain tracing by prioritizing the most direct, earliest, and relevant source.

### 中文

1. 增加综述文献追溯原始来源后的固定呈现方式。
2. 原始来源必须在同一核查表中另起一行，并紧接当前引用文献。
3. 综述证据与原始来源证据严格分开。
4. 综述文献和原始来源分别评分。
5. 只有核心理论、关键机制、概念定义和首创性主张，才报告是否需要补充或替代原始来源。
6. 优先追溯最直接、最早且最相关的来源，避免无限追溯。

## v7.2

### English

1. Classified review-section summaries as secondary review evidence.
2. Required original-source tracing for central theoretical claims and mechanisms.
3. Separated source evidence from analytical judgments in the table.
4. Standardized DOI values as canonical clickable URLs.
5. Removed tracking parameters from formal reference links.
6. Clarified that ResearchGate and similar sites may provide access but cannot alone verify metadata.
7. Prohibited self-referential statements about the Skill, prompt, or execution process.

### 中文

1. 将综述部分对既有研究的概括归类为二手综述证据。
2. 核心理论命题和关键机制优先追溯原始来源。
3. 严格分离“文献证据”列和适配性分析。
4. DOI 统一使用可点击的标准 URL。
5. 正式参考链接删除追踪参数。
6. 明确 ResearchGate 等平台可以用于获取全文，但不能单独承担元数据核验。
7. 禁止输出关于 Skill、提示词和执行过程的自我声明。

## v7.1

### English

1. Renamed the first table column to bibliographic information and link.
2. Required reconstructed bibliographic information and DOI or official links when users provide only in-text citations.
3. Replaced the quotation-only column with a source-evidence column.
4. Added verbatim evidence, full-text synthesis, and no-support-found evidence types.
5. Prohibited vague “full” or “full text” labels without checked sections or page ranges.
6. Added grouped-citation responsibility rules.
7. Allowed minimal flags for directly observable errors without inferred intent or corrective rewriting.
8. Prevented forced quotations for wholly unsuitable sources.

### 中文

1. 第一列改为“文献信息与链接”。
2. 用户只提供文内引用时，必须补充完整书目信息和 DOI 或正式链接。
3. “文献中的原句”改为“文献证据”。
4. 增加原句证据、全文综合证据和未发现支持证据三种形式。
5. 禁止只写“全文”或“full”，必须标注实际核查章节或页码范围。
6. 增加多篇文献共同引用时的证据分配规则。
7. 允许最小化标记直接可见的问题，禁止推测原意和提供修改方案。
8. 文献完全不符合时，不再强行摘录无关句子。

## v7.0

### English

1. Rebuilt the skill around a short mandatory workflow and a final submission gate.
2. Added a minimum search requirement for constrained environments.
3. Added a full-text retrieval threshold with alternative retrieval routes.
4. Added a hard evidence gate before support judgments or scores.
5. Made full audit mode automatic for submitted passages.
6. Made complete bibliography entries optional.
7. Prohibited process narration, repeated confirmations, and unrequested language correction.
8. Required each score to map to a full-text quotation and page or section.
9. Added compliance test prompts.

### 中文

1. 重新设计核心执行流程和最终提交门槛。
2. 增加受限环境下的最低检索要求。
3. 增加全文检索完成条件和替代获取渠道。
4. 增加支持性判断和评分前的强制证据门槛。
5. 用户提交段落后自动进入完整核查。
6. 完整参考文献条目改为可选。
7. 禁止过程播报、重复确认和未经要求的语言修改。
8. 每个贴合率必须对应全文原句和页码或章节。
9. 增加合规测试指令。
