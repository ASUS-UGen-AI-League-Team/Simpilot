# 繁中快速操作

1. 使用 Python 3.13（本次參考版本 3.13.9），依 README 建立 `.venv`，安裝 `requirements.txt`。
2. 執行 `start_workbench.cmd`，或 `python -X utf8 local_app.py`。
3. 按頁首「載入五配方範例」。不用 Google 登入，也不用 H: 或原電腦的路徑。
4. 到低 q 資料檢查，核對時間 1490–1499、兩段、q 頻帶 0–0.11，再按「計算低 q 平均並檢查五個配方」。
5. 到模型設定，選擇 kernel；範例預選 Linear、RBF、Matérn 3/2，固定搭配平均值與線性基準。
6. 查看曲線後勾選確認、填寫判讀紀錄，再開始訓練。結果頁有回歸圖、留一預測點與模型比較。
7. 執行產物在 `runtime/`。每次執行有自己的資料夾，歷史清單可確認後逐筆刪除。

純命令列也可執行：

```sh
python run_example.py --out runtime
```

q*、M、低 q 保留各自的目標定義。這五份資料對 q* 可能無法通過峰值篩查，請以實際診斷解讀。完整功能與限制見英文 README、FEATURES.md 及 DATA_AND_METHODS.md。

這是獨立的發佈副本，未包含私人 raw 資料、Google 憑證、既有模型／報告或 Git 歷史。請僅上傳此資料夾內容；對外公開前仍需確認合作資料及程式的授權條款。詳細安全檢查結果見 SECURITY_REVIEW.md。
