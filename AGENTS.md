# 跑台機分享版：GitHub 公開發布

本資料夾是公開儲存庫 https://github.com/hsiehtzuchi/block1-micro-quiz 的本機副本（2026-10-06 建）。使用者只把跑台機分享給同學，筆記不放 GitHub。

- 儲存庫只放 `README.md`（給同學看的使用說明，GitHub 首頁會顯示）、本檔、`.gitignore`。
- 測驗檔本身放在 **Release** 附件：`Block1_Micro_Quiz.html`（約 84 MB）與 `Block1_Micro_Quiz.zip`（約 63 MB）。附件檔名用英數字，GitHub 會把附件檔名裡的中文去掉。
- 來源是 `~/Downloads/Block1_Micro_跑台測驗_分享版.html`（由 `../micro_quiz_all_20261005/build_all.py` 產生，key `b1micro_quiz_share_v1`，不讀使用者自己的紀錄）。不要放整合版。
- `dist/` 是上傳前的暫存，不進 git。
- 不能用 GitHub Pages 當網頁直接開：Pages 是 https，EBM 線上玻片是 http，會被當成混合內容擋掉。所以要下載後用本機檔案開。
- 使用者已知道分享版內含共筆圖與 EBM 玻片截圖的版權風險，決定照原樣公開（2026-10-06）。

## 更新（重建分享版之後）

```bash
cd ~/"Desktop/大四上/00_學習系統/tmp/micro_quiz_github"
cp ~/Downloads/Block1_Micro_跑台測驗_分享版.html dist/Block1_Micro_Quiz.html
(cd dist && rm -f Block1_Micro_Quiz.zip && zip -q -9 Block1_Micro_Quiz.zip Block1_Micro_Quiz.html)
gh release create v$(date +%Y%m%d-%H%M) dist/Block1_Micro_Quiz.zip dist/Block1_Micro_Quiz.html --title "$(date +%Y-%m-%d) 版" --notes "<改了什麼、題數>"
```

- 發新版用新的 tag，README 的連結指向 `releases/latest`，會自動變成最新版。
- 發布前確認：分享版已跑過 `safari_check`；檔案標題的題數正確；key 是 `b1micro_quiz_share_v1`。
