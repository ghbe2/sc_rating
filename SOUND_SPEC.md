# しゅがけレーティング — サウンド要件

> 音を用意する人向けの発注書。
> **ファイルを `sounds/` に置くだけで差し替わります。** 置いていない音は現行の合成音のまま鳴るので、
> 1つずつ順番に差し替えても壊れません。全部揃うまで待つ必要はありません。

---

## 0. 共通仕様

| 項目 | 指定 |
|---|---|
| 形式 | **MP3**（第一候補）。iOS Safari / Android Chrome の両方で確実に鳴る |
| サンプルレート | 44.1kHz |
| ビットレート | SE = 128kbps / BGM = 160kbps 程度（軽さ優先） |
| チャンネル | SE = モノラルで可 / BGM = ステレオ |
| 音量 | **ピークを -3dBFS 前後に正規化**。ゲーム側でさらに 0.8 倍（BGM は 0.35 倍）します |
| 無音 | **先頭の無音を必ず削る**。連打音は先頭無音が数十msあるだけで「遅れて聞こえる」 |
| 置き場所 | `しゅがけレーティング/sounds/` |

**音の方向性**: このゲームは砂糖モチーフのバカゲーです。シリアスな効果音ではなく、
**軽い・甘い・少し安っぽい**方向。ファミコン〜ゲームボーイ的なピコピコに、
砂糖のシャリッとした質感（グラニュー糖をこぼす、飴を噛む）が混ざる感じを想定しています。
`DotGothic16` のドット文字と同じ温度感です。

---

## 1. 効果音（SE）— 14ファイル

ファイル名は固定です。変えたい場合は `index.html` の `CONFIG.sfx.files` を書き換えてください。

### 最優先（この3つだけでも体感が変わる）

| ファイル名 | 場面 | 長さ | 内容の指定 |
|---|---|---|---|
| `tap.mp3` | **タップ1回ごと** | **60ms 以内** | 最重要。連打で最大5個まで重なって鳴ります。**短く・軽く・耳に痛くない**こと。砂糖の粒がぶつかる「チッ」「ポッ」程度。ピッチは固定でOK（現在は合成音側で半音ずつ上げていますが、ファイルを置くとピッチ変化は無くなります。変化が欲しい場合は相談してください） |
| `win.mp3` | 決着カットで自分に **WIN** が出る | 0.4〜0.8秒 | 勝利の確定音。派手すぎないこと（1戦ごとに必ず鳴るため、40戦聴いても飽きない範囲） |
| `rankup.mp3` | **階級昇格**（グラニュー級→ザラメ級 等） | 1.2〜2.0秒 | いちばん気持ちいい音。上昇するファンファーレ |

### バトル中

| ファイル名 | 場面 | 長さ | 内容の指定 |
|---|---|---|---|
| `phase_clash.mp3` | 押し合い開始（拮抗） | 0.3秒 | 「始まった」合図。中立的 |
| `phase_pinch.mp3` | **ピンチ**（相手に押し込まれる／画面が赤くなる） | 0.4〜0.7秒 | 不穏。ただし絶望的にはしない（このゲームに敗北は存在しません） |
| `phase_rally.mp3` | 逆転（押し返す） | 0.4〜0.7秒 | 反撃の合図。上向き |
| `phase_finish.mp3` | 押し切り（決着直前） | 0.4〜0.7秒 | 畳みかけ。テンポを上げる |

### 決着〜リザルト

| ファイル名 | 場面 | 長さ | 内容の指定 |
|---|---|---|---|
| `lose.mp3` | WIN の0.5秒後に**相手側に LOSE** が出る | 0.5〜1.0秒 | 相手が負ける音。**間抜けに崩れる**方向（オチとして）。悲壮にしない |
| `gauge.mp3` | ランクゲージが伸びる | 0.2〜0.4秒 | 加算の手応え |
| `bonus.mp3` | **連勝ボーナス ×2**（3連勝目以降、毎回鳴る） | 0.3〜0.5秒 | `gauge.mp3` と重ならず聞き分けられること。ボーナスなので上向き・きらびやか |
| `tierup.mp3` | 甘さレベル上昇（グラニュー級3→2 等、階級内の昇格） | 0.6〜1.0秒 | `rankup.mp3` の小さい版。同系統の音色で、規模だけ小さく |
| `master.mp3` | **糖蜜級 到達／RATING 解禁**（1シーズンに1回だけ） | 2.0〜3.5秒 | 最大の見せ場。ここだけ思い切り派手にしてよい |
| `end.mp3` | シーズン終了（手が止まった） | 1.0〜2.0秒 | **敗北音にしないこと。** 花道・区切りの音。少し気の抜けた終わり方が正解 |
| `button.mp3` | ボタン押下（もう一度戦う／やめる 等） | 80ms 以内 | 素っ気なくてよい |

---

## 2. BGM — 2ファイル（任意）

ループ再生します。**ループ点で無音やプツッというノイズが出ないよう、末尾と先頭を繋げてください。**

| ファイル名 | 場面 | 長さ | 内容の指定 |
|---|---|---|---|
| `bgm_title.mp3` | タイトル画面 | 20〜40秒ループ | 軽く、待たせない |
| `bgm_battle.mp3` | **バトル〜決着〜リザルト**（戦闘中ずっと） | 40〜90秒ループ | 1回のプレイで数分間鳴り続けます。**主張しすぎないこと**。SEが上に乗るので中音域を空けてもらえると助かります |

最終成績画面は**無音**にしてあります（`end.mp3` を聴かせるため）。ここにもBGMが欲しい場合は
`CONFIG.bgm.files.result` にファイル名を入れれば鳴ります。

---

## 2-B. Suno で BGM を作る場合

### 共通設定

| 項目 | 設定 |
|---|---|
| モード | **Custom**（Simple だと歌が入る） |
| Instrumental | **ON**（必須） |
| モデル | v4.5+ / v5 |
| 長さ | 2分程度で生成し、**あとから32〜64小節を切り出す**（そのまま使わない） |
| 生成回数 | 各3〜5テイク。ループに耐える「淡々とした」テイクを選ぶ |

**Exclude Styles**（除外欄）には共通でこれを入れてください:

```
vocals, singing, lyrics, spoken word, fade in, fade out, ambient intro,
breakdown, half-time, sub bass, applause, sound effects, silence
```

`fade in / fade out / ambient intro` の除外が重要です。**Suno は放っておくと必ず静かな入りと
フェードアウトを付けます**が、ループBGMではどちらも邪魔になります。

---

### `bgm_battle.mp3` — 本命

一番長く聴かせる曲です。**主張しすぎないこと**を最優先にしてください。
1プレイで何十回もループし、その上に効果音が全部乗ります。

```
Upbeat chiptune power-pop, 8-bit square wave lead with punchy live drums,
bright major key, 158 BPM, candy-colored and playful, driving eighth-note
bassline, glockenspiel sparkle accents, mid-range left open for sound effects,
constant energy with no breakdown or drop, steady loopable groove,
retro handheld game battle theme
```

- **BPM 155〜165** を狙ってください。押し合いのフェーズが0.9〜1.5秒刻みなので、そのくらいが合います
- `no breakdown or drop` と `constant energy` を必ず入れること。**曲中で静かになる箇所があると、
  そこがループに当たったときバトルの熱が落ちます**
- `mid-range left open` は効果音の帯域を空けてもらうための指定です

### `bgm_battle.mp3` — 別案（もっとバカゲー寄り）

上が「ちゃんとしすぎ」と感じたらこちら。

```
Hyperactive J-pop chiptune, ska-punk offbeat guitar stabs, 8-bit arpeggios,
brass hits, 172 BPM, absurdly cheerful, comedic and slightly unhinged,
tight snare rolls, candy shop energy, no vocals, loopable game battle theme
```

### `bgm_title.mp3`

タイトルは数秒しか見ないので、短く・軽く。

```
Gentle chiptune waltz-pop, soft square and triangle wave leads, music box and
glockenspiel, warm major key, 124 BPM, sweet and slightly wistful, sparse
arrangement, cute retro handheld title screen theme, calm but inviting, loopable
```

`slightly wistful`（少し物悲しい）を入れているのは、**このゲームが「無意味な数字を無意味な尺度で
順位付けする」風刺**だからです。全面的に楽しいだけの曲より、ほんの少し翳りがある方が最終成績の
偽ランキングに効きます。強すぎたら外してください。

---

### 生成後の処理（ここを省くとループが破綻します）

1. **切り出し**: 一番おいしい32〜64小節を選び、**小節頭で正確に切る**。
   158BPM の32小節なら約48.6秒
2. **繋ぎの確認**: 切り出した音声を2つ並べて再生し、継ぎ目が不自然でないか聴く
3. **音量**: ピークを **-6dBFS 前後**に。効果音より下に敷くので、SE（-3dBFS）より低めにします
4. **書き出し**: MP3 / 44.1kHz / 160kbps

### ⚠ ループの継ぎ目について（技術的な制約）

**MP3 は仕様上、必ず先頭と末尾に無音のパディングが入ります。** そのため
`<audio loop>` でループさせると、繋ぎ目で数十ミリ秒の「プツッ」という空白が出ます。
これは音源の作り方では消せません。

現実的な対処は次のどれかです。

- **A. 継ぎ目を目立たせない曲にする**（推奨・追加実装なし）
  ループ末尾をシンバルやリバーブの余韻で終わらせる。ドラムのフィルで終わらせると、
  わずかな空白が「タメ」に聞こえて気にならなくなります。**Suno のプロンプトに
  `ending with a cymbal swell` を足す**と狙いやすいです
- **B. ゲーム側を Web Audio に切り替える**（完全な無縫ループになる）
  こちらで実装できます。ただし `fetch` を使うため **GitHub Pages 上でしか動かず**、
  ローカルの `file://` では従来方式にフォールバックします

**まずは A で試してください。** 気になるようなら B を実装します。

---

## 3. 鳴るタイミングの全体像

1戦のあいだに何がどの順で鳴るかです。**通常勝利で約9〜13秒、昇格を挟むと最大17秒**です。

```
[バトル]  phase_clash ─ tap tap tap… ─ phase_pinch ─ tap… ─ phase_rally ─ tap… ─ phase_finish
              ↓
[決着]    win ────(0.5秒)──── lose
              ↓
[リザルト] （1.0秒 間）→ gauge （+ bonus / 3連勝目以降は毎回）
              ↓
          昇格するなら → tierup または rankup または master
              ↓
          ボタンが出て停止（自動では進みません）→ button
```

シーズン終了時のみ `end` が鳴り、BGMは止まります。

---

## 4. 実装側の仕組み（音を作る人は読まなくて大丈夫です）

- `CONFIG.sfx.files` / `CONFIG.bgm.files` にファイル名を定義
- 起動後、最初のユーザー操作で `Sfx.load()` が全ファイルの読み込みを試行
- **読み込めたものだけ**がファイル再生に切り替わり、失敗したものは既存の合成音のまま
- `tap` のみ5個のプールを持ち、連打で重なって鳴る
- `HTMLAudioElement` を使用（`fetch` + `decodeAudioData` は `file://` で CORS に阻まれ、
  ローカルで動作確認できなくなるため）

### 音量を変えたいとき

```js
CONFIG.sfx.volume = 0.8;   // 効果音（0〜1）
CONFIG.bgm.volume = 0.35;  // BGM（0〜1）
```

### 音を止めたいとき

```js
CONFIG.sfx.enabled = false;   // 効果音ファイルを使わず合成音に戻す
CONFIG.bgm.enabled = false;   // BGM を鳴らさない
CONFIG.audio.enabled = false; // 合成音も含めて全部止める
```
