# tango-audio
「単語ノート / 日語單字 Tango」App 的日文發音音檔 CDN（GitHub Pages 服務）。

**App 一個音檔都沒有內嵌，全部從這裡串流**（2026-07-26 起）。
所以換掉這裡的檔案 = 所有使用者立刻聽到新版，不必重新送審。
（App 端設定：`ios-tango/Resources/web/index.html` 的 `AUDIO_BASE` 指向本站、`BUNDLED_AUDIO` 為空。）

## 檔名

| 前綴 | 內容 | 產生方式 |
|---|---|---|
| `w_<id>` | 單字 | OpenAI `gpt-4o-mini-tts` nova（2026-08-01）／64k |
| `e_<id>` | 例句 1 | 同上 |
| `e2_`–`e5_<id>` | 例句 2–5 | VocalLab `Hina`（ja-JP）／32k — **N5+N4 已換，N3/N2/N1 仍是舊的 macOS Kyoko 16k** |

規格一律 mono 24kHz mp3。

## ⚠️ 容量天花板

GitHub Pages 單站上限 **1 GB**。目前約 630 MB；剩下的 N3/N2/N1 例句 2–5（32,316 檔）
全部升級後約 **849 MB**，還在線內——**但前提是新檔用 32k**。
用 64k 會膨脹到約 1,263 MB 直接撞牆（新檔比舊的 Kyoko 大 5 倍：位元率 4x × 時長 1.33x）。

生成腳本：`~/telegram-dutch/multilang/gen_audio_ja_vocallab.py`（預設 32k，manifest 可續跑）。
