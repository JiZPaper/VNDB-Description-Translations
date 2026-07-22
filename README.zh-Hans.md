<p align="center">
  <a href="./README.md">English</a> ·
  <strong>简体中文</strong> ·
  <a href="./README.zh-Hant.md">繁體中文</a> ·
  <a href="./README.ja.md">日本語</a> ·
  <a href="./README.ko.md">한국어</a>
</p>

# 将 VNDB 翻译到你的语言

这是一个翻译 VNDB 的项目。你可以提交 Pull Request 来翻译 VNDB 简介。它将被用于 PaperVN App 中，当然，所有人都可以使用这些译文。关于 PaperVN App 的更多信息，请查阅：https://github.com/JiZPaper/PaperVN-Localizations。

## 目录结构

```text
VNDBDescriptions/
├── en/
│   ├── visual-novels/020/v20424.json
│   └── characters/000/c123.json
├── zh-Hans/
│   ├── visual-novels/020/v20424.json
│   └── characters/000/c123.json
├── zh-Hant/
├── ja/
└── ko/
```

- `en` 是 VNDB API 返回的英文原文。
- `zh-Hans`、`zh-Hant`、`ja`、`ko` 是目标语言；也可以按 BCP 47 语言标签新增目录。
- `visual-novels` 保存视觉小说，`characters` 保存角色。
- 文件名使用 VNDB 的条目 ID，而不是标题。
- 为保持所有语言使用同一结构，英文文件的 `source` 与 `translation` 相同；目标
  语言文件保留 `source`，只改 `language` 和 `translation`。

## 如何翻译条目？

以 `Summer Pockets`（`v20424`）的简体中文翻译为例：

1. 拷贝 `en/visual-novels/020/v20424.json` 到
   `zh-Hans/visual-novels/020/v20424.json`，保持相同的相对路径。
2. 把 `language` 从 `en` 改为 `zh-Hans`。
3. 只把 `translation` 改成译文。保留 `source` 英文原文、
   `source_sha256`、`id`、`type` 和其他元数据。
4. 提交前确认 JSON 能正常解析，并且简介中的 `[spoiler]`、`[url]` 等 VNDB
   格式标记仍然成对、含义正确。

翻译文件示例：

```json
{
  "schema_version": 1,
  "id": "v20424",
  "type": "visual_novel",
  "name": "Summer Pockets",
  "original_name": "サマーポケッツ",
  "language": "zh-Hans",
  "source_language": "en",
  "source": "English description from VNDB...",
  "source_sha256": "68bd7b8cbffc2d330b0a641b77bc3536aae3d6681ef6621055bb543e06c09c92",
  "translation": "这里填写完整的译文……",
  "vndb_url": "https://vndb.org/v20424"
}
```

字段约束见 [`description.schema.json`](description.schema.json)。请勿把多个条目合并到
同一文件，也不要把机翻结果作为已完成人工译文批量提交。

## 原文更新

`source_sha256` 是 `source` UTF-8 文本的 SHA-256。英文原文件更新后，已有翻译
不会被同步脚本覆盖。审阅者应把目标语言文件的哈希与当前英文文件比较；不一致
表示 VNDB 原文在翻译完成后发生了变化，需要重新核对并更新该翻译文件中的
`source`、`source_sha256` 和 `translation`。

## 数据来源与许可

英文简介和相关元数据来自 [VNDB Kana API](https://api.vndb.org/kana)，受
[VNDB Data License](https://vndb.org/d17) 与 API 使用条款约束。PaperVN 是非官方
第三方项目，与 VNDB 不存在隶属关系，也未获得 VNDB 的官方背书。

