<p align="center">
  <strong>English</strong> ·
  <a href="./README.zh-Hans.md">简体中文</a> ·
  <a href="./README.zh-Hant.md">繁體中文</a> ·
  <a href="./README.ja.md">日本語</a> ·
  <a href="./README.ko.md">한국어</a>
</p>

# Translate VNDB into Your Language

This project is dedicated to translating VNDB descriptions. You can submit a Pull Request to help translate them. The translations will be used in the PaperVN App, and anyone is welcome to use them. For more information about the PaperVN App, see: https://github.com/JiZPaper/PaperVN-Localizations.

## Directory Structure

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

- `en` contains the original English text returned by the VNDB API.
- `zh-Hans`, `zh-Hant`, `ja`, and `ko` are target languages. You may also add directories using other BCP 47 language tags.
- `visual-novels` contains visual novels, while `characters` contains characters.
- File names use VNDB entry IDs rather than titles.
- To keep the same structure across all languages, `source` and `translation` contain identical text in English files. Target-language files retain `source` and modify only `language` and `translation`.

## How Do I Translate an Entry?

Using the Simplified Chinese translation of `Summer Pockets` (`v20424`) as an example:

1. Copy `en/visual-novels/020/v20424.json` to
   `zh-Hans/visual-novels/020/v20424.json`, preserving the same relative path.
2. Change `language` from `en` to `zh-Hans`.
3. Replace only `translation` with the translated text. Keep the original English text in `source`, as well as `source_sha256`, `id`, `type`, and all other metadata.
4. Before submitting, make sure the JSON parses successfully and that VNDB markup such as `[spoiler]` and `[url]` remains properly paired and retains its intended meaning.

Example translation file:

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

See [`description.schema.json`](description.schema.json) for field constraints. Do not combine multiple entries into a single file, and do not bulk-submit machine-generated translations as completed human translations.

## Source Updates

`source_sha256` is the SHA-256 digest of the UTF-8 text in `source`. When an English source file is updated, the synchronization script will not overwrite an existing translation. Reviewers should compare the hash in the target-language file with the current English file. A mismatch means that the VNDB source changed after the translation was completed; the translation file's `source`, `source_sha256`, and `translation` must then be reviewed and updated.

## Data Source and License

The English descriptions and related metadata come from the [VNDB Kana API](https://api.vndb.org/kana) and are subject to the [VNDB Data License](https://vndb.org/d17) and the API terms of use. PaperVN is an unofficial third-party project. It is not affiliated with or endorsed by VNDB.

