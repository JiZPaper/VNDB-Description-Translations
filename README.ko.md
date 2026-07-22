<p align="center">
  <a href="./README.md">English</a> ·
  <a href="./README.zh-Hans.md">简体中文</a> ·
  <a href="./README.zh-Hant.md">繁體中文</a> ·
  <a href="./README.ja.md">日本語</a> ·
  <strong>한국어</strong>
</p>

# 여러분의 언어로 VNDB 번역하기

VNDB 소개글을 번역하기 위한 프로젝트입니다. Pull Request를 제출하여 번역에 참여할 수 있습니다. 번역문은 PaperVN 앱에서 사용되며, 물론 누구나 이용할 수 있습니다. PaperVN 앱에 관한 자세한 내용은 https://github.com/JiZPaper/PaperVN-Localizations 에서 확인하세요.

## 디렉터리 구조

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

- `en`에는 VNDB API가 반환한 영어 원문을 저장합니다.
- `zh-Hans`, `zh-Hant`, `ja`, `ko`는 번역 대상 언어입니다. BCP 47 언어 태그에 따라 새 언어 디렉터리를 추가할 수도 있습니다.
- `visual-novels`에는 비주얼 노벨을, `characters`에는 캐릭터를 저장합니다.
- 파일 이름에는 제목 대신 VNDB 항목 ID를 사용합니다.
- 모든 언어에서 동일한 구조를 유지하기 위해 영어 파일의 `source`와 `translation` 값은 같게 합니다. 대상 언어 파일에서는 `source`를 유지하고 `language`와 `translation`만 변경합니다.

## 항목은 어떻게 번역하나요?

`Summer Pockets`(`v20424`)의 중국어 간체 번역을 예로 들면 다음과 같습니다.

1. `en/visual-novels/020/v20424.json`을
   `zh-Hans/visual-novels/020/v20424.json`으로 복사하고 동일한 상대 경로를 유지합니다.
2. `language`를 `en`에서 `zh-Hans`로 변경합니다.
3. `translation`만 번역문으로 변경합니다. `source`의 영어 원문,
   `source_sha256`, `id`, `type` 및 기타 메타데이터는 그대로 유지합니다.
4. 제출하기 전에 JSON이 정상적으로 파싱되는지 확인하고, 소개글 안의 `[spoiler]`, `[url]`
   같은 VNDB 형식 마커가 올바르게 짝을 이루며 의미가 유지되는지 확인합니다.

번역 파일 예시:

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

필드 제약 조건은 [`description.schema.json`](description.schema.json)을 참고하세요. 여러 항목을 하나의 파일로 합치지 말고, 기계 번역 결과를 사람이 번역을 완료한 것처럼 대량으로 제출하지 마세요.

## 원문 업데이트

`source_sha256`는 `source` UTF-8 텍스트의 SHA-256 해시입니다. 영어 원문 파일이 업데이트되어도 동기화 스크립트는 기존 번역을 덮어쓰지 않습니다. 검토자는 대상 언어 파일의 해시를 현재 영어 파일과 비교해야 합니다. 해시가 일치하지 않으면 번역 완료 후 VNDB 원문이 변경되었다는 뜻입니다. 이 경우 번역 파일의 `source`, `source_sha256`, `translation`을 다시 검토하고 업데이트해야 합니다.

## 데이터 출처 및 라이선스

영어 소개글과 관련 메타데이터는 [VNDB Kana API](https://api.vndb.org/kana)에서 가져오며, [VNDB Data License](https://vndb.org/d17)와 API 이용 약관의 적용을 받습니다. PaperVN은 비공식 타사 프로젝트이며, VNDB와 제휴 관계가 없고 VNDB의 공식적인 승인도 받지 않았습니다.
