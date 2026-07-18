# Sellwell Domestic Data Hub — Public JSON Feed

Sellwell 国内市場データハブ向けの**公開用 JSON フィード**。
Atlas が生成・更新し、Smith が sellwell.jp で読む受け渡し口。

- **Repo**: `moriit-provenans/sellwell-domestic-datahub-feed`（Public）
- **発足**: 2026-07-18（REQ-SMITH-20260718-002 Phase 0 採択・案B）
- **姉妹**: `prove-global-data-hub-feed`（海外・PROVE）。本Repoは国内・Sellwell専用（混在禁止）

```
├─ README.md
├─ _catalog.json           … フィード一覧
├─ _manifest.json          … 全体メタ・最終更新
├─ metrics_dict.json       … metric_id 台帳（jp.*）
├─ industries.json         … JSIC ↔ slug ↔ 表示名
├─ theme_tags.json         … 横断テーマタグ17
├─ as_of_manifest.json     … 系列ごとの as_of / still_valid
├─ subsidies/active.json   … jGrants 公募中（日次予定）
├─ timeseries/             … 指標時系列（Phase 1〜）
├─ sellwell_exclusive/     … J1-J3（Smith投入）
└─ schema/                 … JSON Schema
```

## 原則

1. 各レコードに `schema_version` / `as_of_date` / `still_valid_2026` / `source` / `retrieved_at` / `veritas` を必須（REQ-SMITH-20260718-001 準拠）
2. 業界キーは **JSIC中分類**（`industry_id`）。表示は `industry_slug`
3. テーマ横断は `theme_tags[]`（複数JSICの合成定義は `theme_tags.json`）
4. DataLake・Secrets・セルYAMLは本Repoに含めない（公開JSONのみ）
5. スキーマ破壊的変更は `schema_version` を上げて Smith と合意

## 更新頻度（予定）

| ソース | cron |
|---|---|
| e-Stat系 | 週次 |
| jGrants | 毎日 |
| 日銀CGPI | 週次 |
| Sellwell独自(J) | Smith更新時 |

## 参照

- Phase 0: `UDX事業/atlas/from_atlas/2026-07-18_REQ-SMITH-20260718-002_phase0_domestic_datahub.md`
- 構想: `UDX事業/projects/sellwell_revival/71_domestic_datahub_concept_20260718.md`
