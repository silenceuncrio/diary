
[2017-02-02](https://github.com/silenceuncrio/diary/wiki/20170202_jeffrey)
---
- 過完農曆年的第一天上班 先 review 一下
- Proposal - Fine Tune Firmware Built and Upgrade
- `Fine Tune Firmware Built and Upgrade` 的工作我已經完成了一半
- 家裡二手的 EPSON EMP-TW700 投影機常常看個半小時就關機

[2017-02-03](https://github.com/silenceuncrio/diary/wiki/20170203_jeffrey)
---
- 看來沒有睡飽這件事實在會多了很高的意外風險...
- 修改 proscend/prosrc/icos/script/FirmwareUpgrade.sh

[2017-02-06](https://github.com/silenceuncrio/diary/wiki/20170206_jeffrey)
---
- review
- 目前 `FirmwareUpgrade.sh` 如下
- 再來要套 proscend 既有的 `MCSV Upgrade Rule`
- 看來有必要調整一下  `FirmwareUpgrade.sh` 輸出 log 的方式
- 目前考慮的方案是採用 `jq` 這個工具
- 明天要好好地來整理一下 `FirmwareUpgrade.sh`

[2017-02-07](https://github.com/silenceuncrio/diary/wiki/20170207_jeffrey)
---
- 來 refactoring 一下 `FirmwareUpgrade.sh`
- 動手做就會有熟悉度了...
- 筑波科技 派人來介紹 `NE3000` - LTE 測試儀器
- 目前 `FirmwareUpgrade.sh` 成果如下

[2017-02-08](https://github.com/silenceuncrio/diary/wiki/20170208_jeffrey)
---
- `FirmwareUpgrade.sh` 在一開始做事的時候就填入一個 timestamp
- 從 linux 帶出去的 timestamp 會由 javascript 來解析
- web 的 `Dual SIM` page 的 `Connect` 按鈕按下去之後應該刷新一下才會變成其他的按鈕...
- `Fine Tune Firmware Built and Upgrade`... 完工

[2017-02-09](https://github.com/silenceuncrio/diary/wiki/20170209_jeffrey)
---
- review
- ariel 表示 GPS 的 icos module 會提供 經度 和 緯度 給我
- web 的 `Dual SIM` page 的 `Connect` 按鈕按下去之後應該刷新一下才會變成其他的按鈕

[2017-02-10](https://github.com/silenceuncrio/diary/wiki/201702010_jeffrey)
---
- `Dual SIM page` - 'Connect' 按鈕需要修正一下
- m300 週會
- 紀錄一下昨天下班前接到的新需求
- 四月底前我有四個工作項目
- morris 量完 pull low 的時間表示不夠
- 發現 `GPIO5-IO7` 這根腳不能去做 mux mode 的設定


