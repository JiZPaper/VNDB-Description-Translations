<p align="center">
  <a href="./README.md">English</a> ·
  <a href="./README.zh-Hans.md">简体中文</a> ·
  <strong>繁體中文</strong> ·
  <a href="./README.ja.md">日本語</a> ·
  <a href="./README.ko.md">한국어</a>
</p>

# 將 VNDB 翻譯成你的語言

本專案旨在翻譯 VNDB 簡介。你可以透過提交 Pull Request 參與翻譯。譯文將用於 PaperVN App，所有人也都可以使用。若要進一步瞭解 PaperVN App，請參閱：https://github.com/JiZPaper/PaperVN-Localizations。

## 目錄結構

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

- `en` 是 VNDB API 傳回的英文原文。
- `zh-Hans`、`zh-Hant`、`ja`、`ko` 是目標語言；你也可以依照 BCP 47 語言標籤新增其他目錄。
- `visual-novels` 存放視覺小說，`characters` 存放角色。
- 檔名使用 VNDB 的條目 ID，而不是標題。
- 為了讓所有語言維持相同結構，英文檔案的 `source` 與 `translation` 內容相同；目標語言檔案則保留 `source`，只修改 `language` 和 `translation`。

## 如何翻譯條目？

以下以 `Summer Pockets`（`v20424`）的簡體中文翻譯為例：

1. 將 `en/visual-novels/020/v20424.json` 複製到
   `zh-Hans/visual-novels/020/v20424.json`，並維持相同的相對路徑。
2. 將 `language` 從 `en` 改為 `zh-Hans`。
3. 只將 `translation` 改為譯文。請保留 `source` 中的英文原文、
   `source_sha256`、`id`、`type` 和其他中繼資料。
4. 提交前，請確認 JSON 能正常解析，且簡介中的 `[spoiler]`、`[url]` 等 VNDB
   格式標記仍正確成對並保留原意。

翻譯檔案範例：

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

欄位限制請參閱 [`description.schema.json`](description.schema.json)。請勿將多個條目合併到同一個檔案，也不要把機器翻譯結果當作已完成的人工譯文大量提交。

## 原文更新

`source_sha256` 是 `source` UTF-8 文字的 SHA-256 雜湊值。英文原文檔案更新後，同步指令碼不會覆寫現有譯文。審閱者應比較目標語言檔案與目前英文檔案中的雜湊值；若不一致，表示 VNDB 原文在翻譯完成後有所變更，需要重新核對並更新翻譯檔案中的 `source`、`source_sha256` 和 `translation`。

## 資料來源與授權

英文簡介和相關中繼資料來自 [VNDB Kana API](https://api.vndb.org/kana)，並受 [VNDB Data License](https://vndb.org/d17) 與 API 使用條款規範。PaperVN 是非官方第三方專案，與 VNDB 並無關聯，也未獲得 VNDB 的官方認可。

