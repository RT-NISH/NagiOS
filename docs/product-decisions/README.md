# NAGI Product Decisions — 決定済み仕様の保管庫

**目的:** チャット上で合意したNAGIの製品挙動・AIポリシー・ユーザー体験を、消えないMarkdownとして継続蓄積する。

**作成日:** 2026-10-25  
**管理場所:** `docs/product-decisions/`  
**対象:** 0.2以降の製品判断（実装前の要求を含む）

## このフォルダの使い方

- **原則、1テーマ1ファイル。** 会話で方針が固まったら対象ファイルを追加・更新する。1冊の巨大な仕様書に追記し続けない。
- 各ファイルには **決定事項／未確定事項／適用バージョン／関連文書／変更履歴** を区別して記録する。
- 状態は `CONFIRMED`（ユーザー合意済み）、`PROVISIONAL`（暫定値・提案）、`SUPERSEDED`（後の決定に置換）を使う。**「決定済み」の内容だけを確定仕様として扱う。**
- 決定を変更するときは旧内容を無言で上書きせず、変更日と理由を追記する。
- ChatGPTの記憶、別チャットの文脈、ローカルの一時出力を唯一の正本にしない。Gitのcommitで履歴を残す。
- ここへの記載は**機能が実装済みであることや、release / workstream activationを許可することを意味しない**。
- 秘密鍵・パスワード・個人情報そのものは、仕様の例としても書き込まない。

## ファイル一覧

| ID | テーマ | 状態 | 最終決定 |
|---|---|---|---|
| DEC-001 | [AIの自律性とAction](DEC-001-agent-autonomy-actions.md) | CONFIRMED | 2026-10-25 |
| DEC-002 | [クラウドAI・外部情報共有](DEC-002-cloud-ai-data-sharing.md) | CONFIRMED | 2026-10-25 |
| DEC-003 | [Memoryの機密分類と所有範囲](DEC-003-memory-classification.md) | CONFIRMED | 2026-10-25 |
| DEC-004 | [Memory保存・学習・自然忘却](DEC-004-memory-learning-forgetting.md) | CONFIRMED（一部数値は暫定） | 2026-10-25 |
| DEC-005 | [Files・AlbertとMemoryの連動](DEC-005-files-albert-memory-lifecycle.md) | CONFIRMED（一部パラメータは暫定） | 2026-10-25 |
| DEC-006 | [日常利用シナリオ](DEC-006-daily-use-scenarios.md) | CONFIRMED | 2026-10-25 |
| DEC-007 | [ロードマップ・版境界との整合](DEC-007-roadmap-alignment.md) | REVIEW NOTE | 2026-10-25 |

新しいテーマは [TEMPLATE.md](TEMPLATE.md) を複製して追加する。

## 既存文書との役割分担

- `docs/decisions/`: カーネル、権限、IPCなどの**技術的なArchitecture Decision Record (ADR)**。
- `docs/product-decisions/`（本フォルダ）: **ユーザーと決めた製品挙動／機能要求／プライバシー／体験**。
- `docs/Nagi_OS_0.1_Codex_Implementation_Spec.md`: 0.1の実装仕様。
- `docs/Nagi_OS_0.2_Codex_Implementation_Spec.md`: 0.2 Platform Foundationの実装仕様とGate。
- `docs/Nagi_OS_0.3_Architecture_Roadmap.md`: main上の0.3将来Architecture（2026-10-25時点では従来版）。
- `docs/workstreams/`、`.dev/workstreams.json`: 個別実装と進捗の正本。

2026-10-25にユーザーが提供した `Nagi_OS_0.3_Architecture_Roadmap_Revised.md` と `Nagi_OS_0.4+_Multi-Agent_Organization_Roadmap.md` は本フォルダの内容を整合させる参照資料。**本記録を追加するだけで、それらの改訂ファイルがGitHub mainへ自動反映されたわけではない**。

## 将来の追加手順

1. 会話で決める（決定した選択肢と例外まで明確にする）。
2. 同じテーマのMDに追記し、なければ新規MDを作る。
3. 確定事項と数値案・実装検証待ちを分ける。
4. READMEの索引を更新し、docs専用ブランチでcommit・レビュー後にmergeする。
5. 後続の0.3 Implementation Specなどへ正式に移す際、参照元IDと受入条件を付ける。

**原則:** Memoryに覚えさせるのではなく、仕様をファイルに残す。