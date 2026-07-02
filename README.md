# Literature Citation Audit Skill

[English](#english) | [中文](#中文)

## English

A reusable skill for checking whether academic references actually support the claims assigned to them.

Version 6 uses adaptive language output. The skill asks the user to select an output language before the first audit.

- English material with English output uses no translation section and a four-column evidence table.
- Material in another language is translated into the selected output language.
- All headings, judgments, audit issues, and metadata findings use the selected language.
- A user intake form asks for the output language, citation style, and audit materials, including options for incomplete bibliographic information.

### Files

| File | Purpose |
|---|---|
| `SKILL.md` | English instruction file |
| `SKILL.zh-CN.md` | Chinese instruction file |
| `INPUT_TEMPLATE.md` | English user intake form |
| `INPUT_TEMPLATE.zh-CN.md` | Chinese user intake form |
| `CHANGELOG.md` | Version history |

The two skill files contain equivalent audit logic. Install one language version in a given AI environment.

## 中文

用于核查学术文献是否真实存在，以及文献原文能否支持当前引文位置承担的具体命题。

v6 根据用户选择动态确定语言和表格结构。

- 英语材料使用英语输出时，不设置翻译部分，核查表使用四列。
- 材料语言与输出语言不同时，翻译成用户选择的语言。
- 标题、判断、核查问题和参考文献信息均使用用户选择的语言。
- 新增用户材料填写模板，先确认输出语言和参考文献格式。没有完整参考文献条目时，也可以提交已有的作者、年份、题名、DOI 或链接。

### 文件

| 文件 | 用途 |
|---|---|
| `SKILL.md` | 英文指令文件 |
| `SKILL.zh-CN.md` | 中文指令文件 |
| `INPUT_TEMPLATE.md` | 英文用户材料模板 |
| `INPUT_TEMPLATE.zh-CN.md` | 中文用户材料模板 |
| `CHANGELOG.md` | 版本记录 |

两份 Skill 的核查逻辑相同。一个 AI 环境中选择一份安装即可。


## Citation-style handling

The user may select APA 7, Chicago, Harvard, IEEE, Vancouver, a journal-specific style, a custom style, or metadata verification without formatting review. The skill does not assume APA by default.

## 参考文献格式处理

用户可以选择 APA 7、Chicago、Harvard、IEEE、Vancouver、目标期刊格式、自定义格式，或只核对书目信息。Skill 不再默认采用 APA。
