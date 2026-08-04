# sounds/ — 効果音・BGM の置き場

ここに音を置くと、ゲーム内の合成音が自動で差し替わります。
**置いていないものは合成音のまま**鳴るので、1本ずつ追加しても壊れません。

詳しい発注内容は **[../SOUND_SPEC.md](../SOUND_SPEC.md)** を見てください。

## ファイル名（固定）

### 効果音

```
tap.mp3            phase_clash.mp3    win.mp3      gauge.mp3     tierup.mp3   end.mp3
                   phase_pinch.mp3    lose.mp3     bonus.mp3     rankup.mp3   button.mp3
                   phase_rally.mp3                               master.mp3
                   phase_finish.mp3
```

### BGM

```
bgm_title.mp3      bgm_battle.mp3
```

## 最優先の3本

この3本だけでも体感が変わります。

1. **`tap.mp3`** — 60ms以内。連打で最大5個重なるので、短く・軽く・耳に痛くないこと
2. **`win.mp3`** — 1戦ごとに必ず鳴る。派手すぎないこと
3. **`rankup.mp3`** — 階級昇格。いちばん気持ちいい音

形式は MP3 / 44.1kHz、ピークは -3dBFS 前後、**先頭の無音は必ず削る**こと。
