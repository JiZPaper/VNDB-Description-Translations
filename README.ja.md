<p align="center">
  <a href="./README.md">English</a> ·
  <a href="./README.zh-Hans.md">简体中文</a> ·
  <a href="./README.zh-Hant.md">繁體中文</a> ·
  <strong>日本語</strong> ·
  <a href="./README.ko.md">한국어</a>
</p>

# VNDBをあなたの言語に翻訳する

これはVNDBの紹介文を翻訳するためのプロジェクトです。Pull Requestを送ることで翻訳に参加できます。翻訳はPaperVN Appで使用されますが、もちろんどなたでも利用できます。PaperVN Appの詳細については、https://github.com/JiZPaper/PaperVN-Localizations をご覧ください。

## ディレクトリ構成

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

- `en` にはVNDB APIから返される英語の原文を保存します。
- `zh-Hans`、`zh-Hant`、`ja`、`ko` は翻訳先の言語です。BCP 47言語タグに従って、新しい言語のディレクトリを追加することもできます。
- `visual-novels` にはビジュアルノベル、`characters` にはキャラクターを保存します。
- ファイル名にはタイトルではなく、VNDBのエントリIDを使用します。
- すべての言語で同じ構成を維持するため、英語ファイルでは `source` と `translation` の内容を同一にします。翻訳先言語のファイルでは `source` を維持し、`language` と `translation` だけを変更します。

## エントリを翻訳するには？

`Summer Pockets`（`v20424`）の簡体字中国語訳を例に説明します。

1. `en/visual-novels/020/v20424.json` を
   `zh-Hans/visual-novels/020/v20424.json` にコピーし、相対パスを同一に保ちます。
2. `language` を `en` から `zh-Hans` に変更します。
3. `translation` だけを翻訳文に変更します。`source` の英語原文、
   `source_sha256`、`id`、`type`、その他のメタデータは変更しないでください。
4. 提出前に、JSONとして正常に解析できること、および紹介文内の `[spoiler]`、`[url]`
   などのVNDB書式マーカーが正しく対応し、その意味が保たれていることを確認してください。

翻訳ファイルの例：

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

フィールドの制約については、[`description.schema.json`](description.schema.json)を参照してください。複数のエントリを同じファイルにまとめないでください。また、機械翻訳の結果を、人手による翻訳が完了したものとして一括提出しないでください。

## 原文の更新

`source_sha256` は、`source` のUTF-8テキストに対するSHA-256ハッシュです。英語の原文ファイルが更新されても、同期スクリプトが既存の翻訳を上書きすることはありません。レビュアーは、翻訳先言語ファイルのハッシュを現在の英語ファイルと比較してください。両者が一致しない場合、翻訳完了後にVNDBの原文が変更されたことを意味します。その場合は、翻訳ファイル内の `source`、`source_sha256`、`translation` を再確認して更新する必要があります。

## データの出典とライセンス

英語の紹介文と関連するメタデータは[VNDB Kana API](https://api.vndb.org/kana)から取得され、[VNDB Data License](https://vndb.org/d17)およびAPIの利用規約が適用されます。PaperVNは非公式の第三者プロジェクトであり、VNDBと提携しておらず、VNDBの公式な承認も受けていません。

