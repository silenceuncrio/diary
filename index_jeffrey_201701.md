
[2017-01-03](https://github.com/silenceuncrio/diary/wiki/20170103_jeffrey)
---
- review - engineering notebook
- 上禮拜四下班前還有寫 `bfirmware.sh` 和 `bimage.sh`
- 上禮拜四還跟 develop 做了整合
- aaron 上禮拜參考 redux.js.org 跟 m300 作了一些整合
- 重新進入 docker 的方法
- 發現 FirmwareUpgrade.sh 的權限忘了修改
- 從 develop 跟 nandflash 作 merge
- 幫 m300 成員作 mfgtool flash firmware
- 整理一下 dokuwiki 文件
- 幫 nobrand 換了背景

[2017-01-04](https://github.com/silenceuncrio/diary/wiki/20170104_jeffrey)
---
- firmware uprade 的 progress bar - bootatrap 有現成的可以用
- firmware.js
- 大概估了一下 firmware upgrade 所需的時間 - 96 秒
- firmware upgrade 的 progress bar 做完囉

[2017-01-05](https://github.com/silenceuncrio/diary/wiki/20170105_jeffrey)
---
- 沒有把 rootfs 變成 read only
- rootfs read-only 在 `/etc/rc.local` 改 - `icosconfig bootinit` 會出錯
- 把 firmware upgrade 的 `reset` 鈕拿掉
- 今天傍晚 release 前該做的事已完成
- 把 nobrand 的 logo 稍微變大一點點
- 修改 `FirmwareUpgrade.sh` 時又改了檔案權限造成 m300 無法執行 - 網路芳鄰
- use json_object_new_int64 to keep the month_tx and month_rx

[2017-01-06](https://github.com/silenceuncrio/diary/wiki/20170106_jeffrey)
---
- m300 終於要迎接第一次的 release 了
- M300 經緯度 - wev ui google map
- 協助處理 apple 開發者帳號續約事宜
- m300 上的 nodejs 一直 build 不過
- aaron 示範 `jq` 搭配 `curl` 存取原本的 cgi - CLI 原型

[2017-01-09](https://github.com/silenceuncrio/diary/wiki/20170109_jeffrey)
---
- 周末停電 - 重新進入 docker
- review - engineering notebook
- 讓 bootenv 整齊
- 熟悉 u-boot 的 hush shell
- 更新 uboot env - 重新編譯 uboot - 直接刷新 uboot env MTD partition
- 拆解 uboot env `bootargs`
- 幫忙把一些 m300 cpu board 作 mfgtool flash firmware
- firmware upgrade 兩個問題
- 有一片 m300 cpu board web upgrade 在 90% umount 階段時自己重開機
- 明天跟生產單位會討論一下 m300 生產的問題
- aaron 告知 m300 的 GitLab 新增了兩個 project
- 目前 uboot env - 只要控制 `actfirm` 便可決定是 `rootfs_a` 或 `rootfs_b`

[2017-01-10](https://github.com/silenceuncrio/diary/wiki/20170110_jeffrey)
---
- m300 介紹會議 - web 需要修改
- meeting minute
- 盤開會的文件 - `M300產測程式`
- 跟生產單位開會順利 - 追加的工作可不少

[2017-01-11](https://github.com/silenceuncrio/diary/wiki/20170111_jeffrey)
---
- `M300 user manual modifications for 1/13(Fri) release` - `hotfix/user_manual` branch
- 搞定 `Status Bar` - `Logo Icon in status bar`
- commit
- Reset button in every page: Remove

[2017-01-12](https://github.com/silenceuncrio/diary/wiki/20170112_jeffrey)
---
- ieee 802.1ag 加 itu-t y.1731
- 把 IEEE 802.1ag 和 ITU-T Y.1731 扛下來 - 12 周
- firmware upgrade 還有 issue 要考慮
- 搞定 dual image

[2017-01-13](https://github.com/silenceuncrio/diary/wiki/20170113_jeffrey)
---
- 直接把 `m300_v1.1_012C000000129880.tar` 解開到 mfgtool 去燒錄程式
- uboot一開始就把系統燈點亮 - `bootdelay` 改短更好
- m300 週會 - Dual Images 結論 - 不要只給一次機會
- 搭配這一版的 uboot env 我們也要修正 `FirmwareUpgrade.sh`

[2017-01-16](https://github.com/silenceuncrio/diary/wiki/20170116_jeffrey)
---
- 早上遲到 - review 和寫 engineering notebook
- 結合 dual image 和 sys led 整理 uboot env
- 目前要完成 `Fine Tune Firmware Built and Upgrade`
- 安排一下怎麼來檢查檔案的完整性
- 檢查檔案的完整性
- 產生 firmware 的時候還要考慮到 MCSV 的資訊
- 盤 https://github.com/silenceuncrio/diary/blob/master/index_jeffrey_201612.md
- 我們 firmware 裡面的 MCSV 資訊需要保護 - 對稱加密 - openssl

[2017-01-17](https://github.com/silenceuncrio/diary/wiki/20170117_jeffrey)
---
- review
- 整理 github - index_jeffrey_201701.md
- Fine Tune Firmware Built and Upgrade

[2017-01-18](https://github.com/silenceuncrio/diary/wiki/20170118_jeffrey)
---
- 幫 john 把切不回好的 application 的 m300 急救一下
- 來把 modal 的機制換一下
- 全部的 modal 都換掉
- login 和 logout 也套 sweetalert
- 法國客戶 CXR 會後決議 m300 上的 IEEE 802.1ag 和 ITU-T Y.1731 需求 取消

[2017-01-19](https://github.com/silenceuncrio/diary/wiki/20170119_jeffrey)
---
- review
- 我們 firmware 裡面的 MCSV 資訊需要保護
- m300 的 hardware mcsv 與 software mcsv 可以參考之前 john 分享的情報
- m300 的 hardware mcsv 可從 `/tmp/etc/sysinfo.txt` 取得
- 準備一下 proposal
- 把 rootfs 轉成 read-only 會出錯

[2017-01-20](https://github.com/silenceuncrio/diary/wiki/20170120_jeffrey)
---
- 繼續昨天的修改前先盤一下
- FirmwareUpgrade.sh
- uboot_env.sh
- commit 時要寫什麼呢
- git push... ok
- 加了 gps 的 web page
- 把預設的位置改到公司來
- mfgtool flashing firmware 後是沒有 `/home/log` 的... 要注意阿...

[2017-01-23](https://github.com/silenceuncrio/diary/wiki/20170123_jeffrey)
---
- review
- Fine Tune Firmware Built and Upgrade 還有兩個 issue
- 跟 ariel 稍微 sync 一下
- 和 ariel 以及 aaron 討論 `rootfs read-only 後導致某些 icos module 初始化異常` 的 issue
- winston 希望知道我之前 efm bridge 最後跟 actelis co 端達到甚麼樣的狀態
- 找出當時最後的一封 mail 轉發給 winston - 是由 pioneer 在當時下的一步公司從來沒有的好棋
- ariel 提出 web ui firmware upgrade 的問題
- `Fine Tune Firmware Built and Upgrade` 的 proposal 已完成
- 來進行 `rootfs read-only 後導致某些 icos module 初始化異常` 的 issue
- 不做 `/bin/mkdir -p /tmp/var` 和 `mount /tmp/var /var`
- aaron 找到 yocto 本身就有的 `Read-Only Root Filesystem` 功能
- 明天要回台中一趟

[2017-01-25](https://github.com/silenceuncrio/diary/wiki/20170125_jeffrey)
---
- 一早來 ariel 找我討論一下 M300 的 issue
- morris 請我幫忙用 mfgtool 燒錄 六片 M300
- M300 法國 CXR 客戶有提供我們 M300 WEB UI 的法語檔案
- 幫忙把 法文 加入目前 M300 的多國語系架構

[2017-01-26](https://github.com/silenceuncrio/diary/wiki/20170126_jeffrey)
---
- 早上來 morris 告知昨天幫他燒錄的那六片 M300 怎麼開機還是那麼久才會閃燈
- 原來 morris 準備的哪幾片要出 sample 的
- 跟 ariel 討論一下早上 morris 的需求 - `閃燈快一點這件事能夠在一燒錄完就有了`
- 可以來 patch 了
- git commit
- 過年後需要跟產線單位 demo 一下怎麼使用 mfgtool

