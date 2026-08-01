# FreshRSS Issue / PR トリアージ調査（全open・軽量パス）

> 更新: 2026-07-05。調査範囲を「最新100 issue」から **全 open issue + 全 open PR** に拡大。

- **調査範囲**: open issue **全611件**（#471〜#8976）＋ open PR **全75件**
- **方式**: ラベル + メタデータ（担当者 / 最終更新 / 紐付きPR）駆動の軽量パス。個別の深掘りは主要アクション対象に限定。
- **目的**: close / 返信 / 実装で open issue・PR を減らす。まず「近道」（第1章）から。

> ⚠️ タイトル・ラベル・メタデータからの机上判定。各項目の最終対応前に実物（コード/最新コメント）確認を推奨。

---

## 0. 全体像

### Issue ラベル構成（上位。1 issue に複数ラベル）

| ラベル | 件数 | ラベル | 件数 | ラベル | 件数 |
|---|---|---|---|---|---|
| Feature Request | **278** | Documentation | 43 | Bug (confirmed) 🐞 | 15 |
| help wanted | 116 | System care | 33 | I18n | 17 |
| UI | 82 | Support | 33 | View | 17 |
| Bug (unconfirmed) | 76 | UX | 31 | Not urgent | 17 |
| Feed problem | 61 | Security | 30 | Docker | 16 |
| Extension | 53 | API | 28 | SimplePie | 15 |
| Good first issue | 50 | | | Vote to close | 14 |

- ラベル無し 29件、担当者あり 44件。
- **Bug 合計 91件**（未確認76 + 確認15）。**Feature Request が全体の約45%**。

### 最終更新年（滞留度）

| 年 | ~2021 | 2022 | 2023 | 2024 | 2025 | 2026 |
|---|---|---|---|---|---|---|
| 件数 | 11 | 136 | 87 | 78 | 103 | 196 |

→ **最終更新 ≤2022 が 147件（24%）= 3年以上放置**。棚卸し（クローズ）の主対象。

---

## 1. 最優先アクション（openを減らす近道）

| 優先 | アクション | 対象 | 参照 |
|---|---|---|---|
| 🟢 | **紐付きPRのマージ → issue自動クローズ** | 26 issue | 2-A |
| 🟢 | **クローズ / 返信で片付く** | Vote to close 14 + Duplicate 2 + 超長期放置 11 | 2-B |
| 🟡 | **実装で潰す** | Good first issue（着手可能）40 + Bug (confirmed) 15 | 2-C / 2-D |
| 🟡 | **承認済みPRのマージ / 変更要求対応** | PR: APPROVED 4 + CHANGES_REQUESTED 2 | 3 |
| 🟠 | **大量バックログの棚卸し** | ≤2022 の 147件、Extension 53、Support 33 | 2-E |

---

## 2. Issue トリアージ

### 2-A. 対応PRが存在（マージで issue 自動クローズ）— 25件 🟢

| issue | 対応PR | タイトル |
|---|---|---|
| [#8953](https://github.com/FreshRSS/FreshRSS/issues/8953) | [#8969](https://github.com/FreshRSS/FreshRSS/pull/8969) | Sort/order parameters bleed into navigation links |
| [#8941](https://github.com/FreshRSS/FreshRSS/issues/8941) | [#8942](https://github.com/FreshRSS/FreshRSS/pull/8942) | ログイン失敗時にIP記録 |
| [#8759](https://github.com/FreshRSS/FreshRSS/issues/8759) | [#8764](https://github.com/FreshRSS/FreshRSS/pull/8764) | 戻るボタンで記事を閉じる |
| [#8744](https://github.com/FreshRSS/FreshRSS/issues/8744) | [#8745](https://github.com/FreshRSS/FreshRSS/pull/8745) | API "Your News" star同期 |
| [#8699](https://github.com/FreshRSS/FreshRSS/issues/8699) | [#8843](https://github.com/FreshRSS/FreshRSS/pull/8843) | srcsetからimg src復元 |
| [#8551](https://github.com/FreshRSS/FreshRSS/issues/8551) | [#8943](https://github.com/FreshRSS/FreshRSS/pull/8943) | reader viewに共有ボタン |
| [#8514](https://github.com/FreshRSS/FreshRSS/issues/8514) | [#8523](https://github.com/FreshRSS/FreshRSS/pull/8523) | 大量entryでのSQL遅延 |
| [#8407](https://github.com/FreshRSS/FreshRSS/issues/8407) | [#8503](https://github.com/FreshRSS/FreshRSS/pull/8503) | OIDCがhttpでcallback |
| [#8362](https://github.com/FreshRSS/FreshRSS/issues/8362) | [#8365](https://github.com/FreshRSS/FreshRSS/pull/8365) | Docker rootless |
| [#8349](https://github.com/FreshRSS/FreshRSS/issues/8349) | [#8354](https://github.com/FreshRSS/FreshRSS/pull/8354) | h2c (HTTP/2) |
| [#7659](https://github.com/FreshRSS/FreshRSS/issues/7659) | [#8687](https://github.com/FreshRSS/FreshRSS/pull/8687) | カテゴリ内フィード手動並べ替え |
| [#7628](https://github.com/FreshRSS/FreshRSS/issues/7628) | [#8965](https://github.com/FreshRSS/FreshRSS/pull/8965) | README self-hosted整理 |
| [#7035](https://github.com/FreshRSS/FreshRSS/issues/7035) | [#7036](https://github.com/FreshRSS/FreshRSS/pull/7036) | カテゴリ内フィード数表示 |
| [#6049](https://github.com/FreshRSS/FreshRSS/issues/6049) | [#8983](https://github.com/FreshRSS/FreshRSS/pull/8983) | Dynamic OPMLでカテゴリ生成（**自PR**） |
| [#4913](https://github.com/FreshRSS/FreshRSS/issues/4913) | [#8903](https://github.com/FreshRSS/FreshRSS/pull/8903) | カテゴリの可視性オプション |
| [#3662](https://github.com/FreshRSS/FreshRSS/issues/3662) | [#8615](https://github.com/FreshRSS/FreshRSS/pull/8615) | 拡張管理のCancelボタン |
| [#5016](https://github.com/FreshRSS/FreshRSS/issues/5016) / [#5583](https://github.com/FreshRSS/FreshRSS/issues/5583) / [#4335](https://github.com/FreshRSS/FreshRSS/issues/4335) / [#3885](https://github.com/FreshRSS/FreshRSS/issues/3885) / [#3658](https://github.com/FreshRSS/FreshRSS/issues/3658) / [#3141](https://github.com/FreshRSS/FreshRSS/issues/3141) / [#2900](https://github.com/FreshRSS/FreshRSS/issues/2900) / [#2371](https://github.com/FreshRSS/FreshRSS/issues/2371) / [#1989](https://github.com/FreshRSS/FreshRSS/issues/1989) | 各PR | **古いPR（Draft/停滞）で紐付くもの** — マージ可否は要確認 |

> 補足: **#8983 / #8985 は私の提出中PR**（#8984→#6470・#8986→#8540 はマージ済みで削除）。#4728(→#4335), #6848(→#3885), #3053(→#2900), #3517(→#3141), #5816(→#2371) 等は長期Draft/停滞で「即マージ可能」ではない（3-C/3-D参照）。

### 2-B. クローズ / 返信で片付く候補 🟢

**Vote to close（クローズ投票済み）— 14件**（要最終確認 → クローズ）
[#4832](https://github.com/FreshRSS/FreshRSS/issues/4832), [#4221](https://github.com/FreshRSS/FreshRSS/issues/4221), [#3823](https://github.com/FreshRSS/FreshRSS/issues/3823), [#3764](https://github.com/FreshRSS/FreshRSS/issues/3764), [#3697](https://github.com/FreshRSS/FreshRSS/issues/3697), [#3598](https://github.com/FreshRSS/FreshRSS/issues/3598), [#3199](https://github.com/FreshRSS/FreshRSS/issues/3199), [#2695](https://github.com/FreshRSS/FreshRSS/issues/2695), [#2293](https://github.com/FreshRSS/FreshRSS/issues/2293), [#2187](https://github.com/FreshRSS/FreshRSS/issues/2187), [#2003](https://github.com/FreshRSS/FreshRSS/issues/2003), [#1644](https://github.com/FreshRSS/FreshRSS/issues/1644), [#1256](https://github.com/FreshRSS/FreshRSS/issues/1256), [#811](https://github.com/FreshRSS/FreshRSS/issues/811)

**Duplicate — 2件**: [#5177](https://github.com/FreshRSS/FreshRSS/issues/5177)（ghacks feed）, [#4684](https://github.com/FreshRSS/FreshRSS/issues/4684)（タイトル接頭辞、#4335と重複）

**超長期放置（最終更新 2021年以前）— 11件**（多くは質問/環境依存 → 返信 or クローズ）
[#1662](https://github.com/FreshRSS/FreshRSS/issues/1662)(2017), [#1854](https://github.com/FreshRSS/FreshRSS/issues/1854)(2018), [#2392](https://github.com/FreshRSS/FreshRSS/issues/2392)(2019), [#2432](https://github.com/FreshRSS/FreshRSS/issues/2432)(2019), [#2640](https://github.com/FreshRSS/FreshRSS/issues/2640)(2019), [#3384](https://github.com/FreshRSS/FreshRSS/issues/3384)(2021), [#3188](https://github.com/FreshRSS/FreshRSS/issues/3188)(2021), [#3884](https://github.com/FreshRSS/FreshRSS/issues/3884)(2021), [#3971](https://github.com/FreshRSS/FreshRSS/issues/3971)(2021), [#3688](https://github.com/FreshRSS/FreshRSS/issues/3688)(2021), [#4066](https://github.com/FreshRSS/FreshRSS/issues/4066)(2021)

### 2-C. Good first issue（未担当・PR無し = 着手可能）— 39件 / 全50件 🟡

**実コード寄り（着手候補）**: [#7954](https://github.com/FreshRSS/FreshRSS/issues/7954) keycodeホットキー, [#7648](https://github.com/FreshRSS/FreshRSS/issues/7648) 重複購読警告, [#7594](https://github.com/FreshRSS/FreshRSS/issues/7594) loglevel調整, [#6034](https://github.com/FreshRSS/FreshRSS/issues/6034) cron無し自動更新, [#6158](https://github.com/FreshRSS/FreshRSS/issues/6158) About画面カスタム, [#4560](https://github.com/FreshRSS/FreshRSS/issues/4560) フィード毎IPv4強制, [#4999](https://github.com/FreshRSS/FreshRSS/issues/4999) フィード毎エンクロージャ表示

**docsのみ**: [#7331](https://github.com/FreshRSS/FreshRSS/issues/7331) Fever APIドキュメント, [#4818](https://github.com/FreshRSS/FreshRSS/issues/4818) CRON_MIN記述誤り

**i18n翻訳タスク（コードでなく翻訳者募集）**: [#6842](https://github.com/FreshRSS/FreshRSS/issues/6842)(EL), [#6841](https://github.com/FreshRSS/FreshRSS/issues/6841)(CS), [#6353](https://github.com/FreshRSS/FreshRSS/issues/6353)(OC), [#6349](https://github.com/FreshRSS/FreshRSS/issues/6349)(ID), [#6332](https://github.com/FreshRSS/FreshRSS/issues/6332)(HE) — 実装ではないので着手対象外。

> 残りの GFI（#8183 SQLite export, #6830 PHP8.4 CSSセレクタ, #6135/#6136/#6139 メモリ最適化 等）は「good first」ラベルだが中規模。ラベルを鵜呑みにせず要スコープ確認。

### 2-D. Bug (confirmed) — 15件（実装候補）🟡

[#8976](https://github.com/FreshRSS/FreshRSS/issues/8976) proxyでfavicon未取得, [#8795](https://github.com/FreshRSS/FreshRSS/issues/8795) Custom CSS不安定, [#8569](https://github.com/FreshRSS/FreshRSS/issues/8569) media:group, [#7299](https://github.com/FreshRSS/FreshRSS/issues/7299) 共有ショートカット, [#5850](https://github.com/FreshRSS/FreshRSS/issues/5850) gitバージョン誤表示, [#5674](https://github.com/FreshRSS/FreshRSS/issues/5674) show-in-category絞り込み, [#5201](https://github.com/FreshRSS/FreshRSS/issues/5201) 特定feedがUI破壊, [#4835](https://github.com/FreshRSS/FreshRSS/issues/4835) SliderのURL, [#4564](https://github.com/FreshRSS/FreshRSS/issues/4564) Global viewのFav, [#3670](https://github.com/FreshRSS/FreshRSS/issues/3670) テーマ不具合, [#3462](https://github.com/FreshRSS/FreshRSS/issues/3462) memory_limit, [#1820](https://github.com/FreshRSS/FreshRSS/issues/1820) 無意味な更新警告

> [#5583](https://github.com/FreshRSS/FreshRSS/issues/5583), [#5016](https://github.com/FreshRSS/FreshRSS/issues/5016), [#3658](https://github.com/FreshRSS/FreshRSS/issues/3658) は既にPR有（2-A）。

### 2-E. バックログ（大分類・件数サマリ）🟠

| 分類 | 件数 | メモ |
|---|---|---|
| **Feature Request** | 278 | 下の内訳表参照。大半は長期バックログ |
| **Bug (unconfirmed)** | 76 | 再現確認待ち。再現不可はクローズ |
| **Feed problem** | 61 | 多くは対象サイト側要因（403/429/エンコード）。共通対策できるものだけ機能化 |
| **Extension** | 53 | 多くは「拡張で対応すべき」= コア対象外/クローズ候補 |
| **Documentation** | 43 | docs追記・整理 |
| **Security** | 30 | TOTP/Passkey/OIDC 等（大規模設計含む） |
| **Support** | 33 | 質問系。返信でクローズ可のものが多い |

**Feature Request 内訳（共起ラベル別）**: UI 55, Extension 22, UX 19, View 16, System care 14, Security 11, Article filter 10, Documentation 9, API 9, Bulk action 8, Sharing 8, Theme 8, Shortcuts 6, CLI 5。

GitHubフィルタ例:

- 未確認バグ: `is:issue is:open label:"Bug (unconfirmed)"`
- クローズ投票: `is:issue is:open label:"Vote to close"`
- 3年以上放置: `is:issue is:open updated:<2023-01-01`

---

## 3. PR トリアージ（全75件）

内訳: Draft 22 / 非Draft・レビュー待ち 53。レビュー状態: APPROVED 4 / CHANGES_REQUESTED 2 / 未決 69。

### 3-A. APPROVED（マージ候補）🟢

- [#8383](https://github.com/FreshRSS/FreshRSS/pull/8383) Mark as Readに時間オプション
- [#7107](https://github.com/FreshRSS/FreshRSS/pull/7107) UserCSSにカスタムURL
- [#7288](https://github.com/FreshRSS/FreshRSS/pull/7288) 埋め込み動画/音声プレビュー（Draft）
- [#3659](https://github.com/FreshRSS/FreshRSS/pull/3659) フィード追加時にキャッシュクリア（Draft）

### 3-B. CHANGES_REQUESTED（作者対応待ち）🟡

- [#5816](https://github.com/FreshRSS/FreshRSS/pull/5816) 画像lazy loadingをhtml属性へ（#2371紐付き）
- [#5671](https://github.com/FreshRSS/FreshRSS/pull/5671) font-familyに日本語追加

### 3-C. 長期放置（最終更新 2024-2025）→ 棚卸し 🟠

- [#7092](https://github.com/FreshRSS/FreshRSS/pull/7092)(2025) Readeck共有, [#6958](https://github.com/FreshRSS/FreshRSS/pull/6958)(2024) Hoarder統合, [#6754](https://github.com/FreshRSS/FreshRSS/pull/6754)(2024) 有料統合(Draft), [#3896](https://github.com/FreshRSS/FreshRSS/pull/3896)(2025) Service Worker, [#3053](https://github.com/FreshRSS/FreshRSS/pull/3053)(2024) 拡張システム更新(Draft), [#1760](https://github.com/FreshRSS/FreshRSS/pull/1760)(2025) GitHub更新(Draft、8年放置)

### 3-D. Draft / WIP — 22件

作者に継続意思を確認し、無反応はクローズ（グリッドビュー #6848、全体レイアウト刷新 #6047、TT-RSS JSON #5584 等の大規模WIP含む）。

---

## 4. 次の一手（推奨）

1. **即効（openを最も減らす）**: 2-A の26 issue のうち活発なPRをマージ → issue も自動クローズ。3-A の承認済み4 PRもマージ。
2. **棚卸し**: 2-B（Vote to close 14 + Duplicate 2 + 超長期放置 11）を確認してクローズ。≤2022 の147件は定期的に一括レビュー。
3. **実装**: 2-C（着手可能 GFI・実コード寄り）と 2-D（confirmed bug）から、未着手・小規模を選んでPR化。
4. **返信のみ**: Support 33・質問系 issue に回答してクローズ。

> 本レポートはラベル/メタデータ駆動の軽量パス。個別対応の前に必ずコード/最新コメントで裏取りすること。
