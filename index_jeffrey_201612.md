
[2016-12-01](https://github.com/silenceuncrio/diary/wiki/20161201_jeffrey)
---
- m300 我有一項要負責的 test case - multi language
- apply the top.html style from digicomm
- 來熟悉一下新的開發環境
- 發現 `MobaXterm` 比 `Cmder` 還好用
- `MobaXterm` 不只比 `Cmder` 還好用
- 清理 webcgi

[2016-12-02](https://github.com/silenceuncrio/diary/wiki/20161202_jeffrey)
---
- 今天來為 monkeyjj 做點事
- https://colorlib.com/wp/node-js-frameworks/
- 比 express 還要多星星的 https://github.com/meteor/meteor
- 跟著 meteor 的 tutorial 走了一遭

[2016-12-05](https://github.com/silenceuncrio/diary/wiki/20161205_jeffrey)
---
- ariel 表示我們 M300 web 的 apply modal 訊息要一致
- use the same behavior for apply button
- 要開始做 nand flash 相關的工作了
- ariel 希望我多國語言的繁體中文部分稍微作一些
- translate some chinese for demo purpose
- monkeyjj time

[2016-12-06](https://github.com/silenceuncrio/diary/wiki/20161206_jeffrey)
---
- m300 nand flash - 整理裡一下過去的情報
- monkeyjj time
- correct the calculate formula for megabyte
- 花了一些時間跟 meteor 相處
- build 出 SD Card 用的 image 但 U-Boot 要有 nand 這個 command 可以使用
- 先用克難的方式來套 `mx6ul_14x14_evk.h`
- 參考 [i.MX Linux User's Guide] - 4.3.4 Copy a bootloader image
- 感覺又卡在之前不了解的地方了
- 套 `mx6ul_14x14_evk.h` 的方式有誤
- 對新打回來 `NAND:  256 MiB` 的 m300 CPU board 做燒錄的動作

[2016-12-07](https://github.com/silenceuncrio/diary/wiki/20161207_jeffrey)
---
- 下午預計請假
- review 一下昨天做的
- 待會 m300 的 ui 第一次對外見客
- m300 對 dqa 功能面上的介紹還算順利

[2016-12-08](https://github.com/silenceuncrio/diary/wiki/20161208_jeffrey)
---
- 昨天修打檔車的結果
- 試著把最新的 code 利用 mfgtool 燒錄到 nand flash 去
- 我們目前的 dtb 整合 nand flash 的結果如下

[2016-12-09](https://github.com/silenceuncrio/diary/wiki/20161209_jeffrey)
---
- 昨天已修改了 dtb 讓 m300 能支援 nand flash
- ariel 希望我重新畫一下對於 2g nand flash 的 partition 規劃
- merge from "SIM_STATUS_T" type from "icos_shm.h"
- 利用 git 建一個 branch `nandflash`
- 修改 `sources\meta-proscend\recipes-core\prosrc\prosrc_0.1.bb`
- 找一下 `mtd-utils' 相對應的 bb file
- `mtd-utils` 相關的 log 可以在下面的 path 找到
- 當時缺少下述 tool 的問題目前已經知道怎麼回事了
- monkeyjj time

[2016-12-12](https://github.com/silenceuncrio/diary/wiki/20161212_jeffrey)
---
- engineering notebook
- 上禮拜為了 nand flash 做的應該先 commit 到我 git 的 branch `nandflash` 去
- 利用 `git log -2 -p` 來看最後兩次的 git log
- 為了下述的改變來製作 patch
- 上 commit 到 brach nandflash
- 繼續 patch 吧
- 盤一下我們之後需要將 `kernel` 和 `rootfs` 燒錄到 NAND 去所需要的 tool
- monkeyjj time
- 業務面希望在 12/23 下禮拜五寄 sample 給 digicomm
- 明天來把 `imx-kobs` 這個 recipe 也 build 進來目前的 nandflash branch

[2016-12-13](https://github.com/silenceuncrio/diary/wiki/20161213_jeffrey)
---
- 目前具備的 tool 已經可以把 `u-boot`, `kernel`, `dtb` 和 `rootfs` 燒錄到 nandflash 去
- 先來燒錄 uboot
- 重開機看看... ok
- 來燒錄 linux kernel 吧
- 來燒錄 rootfs 吧
- 再整理一次燒錄 rootfs 的步驟
- Erasing rootfs partition 之前先把後續動作需要的工具放到 `/tmp` 去
- 先做 `detach` 吧
- 跟 winston 聊了一下他是怎麼克服寫 rootfs 這個問題
- 新增 uboot 的 ubi command 需要修改 mx6ul_14x14_evk.h
- 就算 uboot 有了 ubi 的 command 也沒啥用
- winston 提到 uboot 的 ubi command 是為了看目前已使用的大小...
- 修改 mx6ul_14x14_evk.h 來達到我們未來的 dual image nand flash 配置
- uboot mtdparts 的問題有解

[2016-12-14](https://github.com/silenceuncrio/diary/wiki/20161214_jeffrey)
---
- review 一下昨天的足跡
- `<u-boot-imx>\include\configs\mx6ul_14x14_evk.h`
- 修改 `${loadaddr}` 和 `${fdt_addr}` 的值
- 看來可以試著把 rootfs 燒錄到另一個 mtd partition 去
- 來燒錄 rootfs 吧
- 確認一下有沒有 `tar` 相關的 recipe
- 似乎還需要 `bzip2` 這個 recipe
- 理論上把 `bootargs` 裡的 `ubi.mtd` 改成 7 應該就可以了
- 卡在一樣的地方
- 又卡住了 - Starting kernel ...
- 正常的訊息是這樣
- 只要在 uboot 做過 `saveenv` 就會導致開機時卡在 `Starting kernel ...`
- 昨天改了 `bootargs` 也做過 `saveenv` 並不會導致開機時卡 `Starting kernel ...`
- 確認 rootfs 是在 mtd4 的狀況下去清掉 mtd3 是否還能正常開機
- winston 提到之後還要克服的點

[2016-12-15](https://github.com/silenceuncrio/diary/wiki/20161215_jeffrey)
---
- `linux 去改 uboot 的 環境變數`
- fw_printenv: cannot execute binary file: Exec format error
- u-boot-fw-utils
- fw_printenv - `/etc/fw_env.config`

[2016-12-16](https://github.com/silenceuncrio/diary/wiki/20161216_jeffrey)
---
- review
- 參考 `<u-boot-imx>\README` 裡的說明
- 修改 `mtdparts` 讓 uboot env 這一塊也佔一個 mtd
- 配合新的 nand flash layout 來修改
- 配合新的 nand flash layout 來修改 mfgtool 的 `ucl2.xml`
- uboot 顯示 `*** Warning - bad CRC, using default environment`
- 使用 `fw_setenv` 把 `bootargs` 裡的 `ubi.mtd` 從 4(rootfs_a) 改成 9(rootfs_b)

[2016-12-19](https://github.com/silenceuncrio/diary/wiki/20161219_jeffrey)
---
- review
- Warning: Bad CRC, using default environment
- solve
- uboot env - bootargs

[2016-12-20](https://github.com/silenceuncrio/diary/wiki/20161220_jeffrey)
---
- review
- 解析 `burn the rootfs to NAND` 流程
- flash_erase /dev/mtd9 0 0
- ubiformat /dev/mtd9
- ubiattach /dev/ubi_ctrl -m 9
- ubimkvol /dev/ubi1 -Nrootfs -m
- mkdir -p /mnt/mtd9
- mount -t ubifs ubi1:rootfs /mnt/mtd9
- tar -jxv -C /mnt/mtd9 -f images/core-image-minimal-imx6ulevk.tar.bz2
- umount /mnt/mtd9
- http://www.linux-mtd.infradead.org/doc/ubi.html
- mfgtool - ucl2.xml - 讓 rootfs_a, rootfs_b, config_a 和 config_b 跟 ubi device 的關係先固定下來
- 使用 `ubiattach -m 5` 來 attach MTD device 5 (mtd5) to UBI 之後可看到 ubimkvol 的效果
- 再次的開機 除了 `ubi0` 看不到其他的 ubi device
- 需要一個地方來做 ubiattach 的動作
- 修改 `/etc/rc.local`
- 根據 uboot env 來決定到底是要 attach `config_a` 或 `config_b`
- patch `<u-boot-fw-utils>/tools/env/fw_env.config`
- git commit

[2016-12-21](https://github.com/silenceuncrio/diary/wiki/20161221_jeffrey)
---
- review
- 盤一下 `prosrc_0.1.bb` 和 `local.conf`
- 修 `<u-boot-imx>\include\configs\mx6ul_14x14_evk.h`
- 幫 `<u-boot-imx>\include\configs\mx6ul_14x14_evk.h` 上 patch
- git commit
- 寫 shell script
- 修改 `/etc/rc.local`
- 幫 m300 裝一下 `vim` 方便編輯 shell script
- 修改 `/etc/rc.local`


[2016-12-22](https://github.com/silenceuncrio/diary/wiki/20161224_jeffrey)
---
- review
- 把需要的 image 作打包
- 回憶之前買的 USB DAC - 使用 pcm2706
- 盤一下 firmware upgrade shell script 需要哪些動作
- Extract all files from images.tar
- burn the uboot to NAND
- burn the kernel to NAND
- burn the dtb to NAND
- burn the rootfs to NAND
- chnage uboot env
- commit
- 目前的 firmware upgrade shell script

[2016-12-23](https://github.com/silenceuncrio/diary/wiki/20161225_jeffrey)
---
- m300 開會
- 準備跟最新的 git 作整合 - 盤一下現況
- http://nvie.com/posts/a-successful-git-branching-model/

[2016-12-26](https://github.com/silenceuncrio/diary/wiki/20161226_jeffrey)
---
- review
- http://nvie.com/posts/a-successful-git-branching-model/
- 把之前做的部分手工整合到 `nandflash` 這個 brach
- 整 `fsl-release-bsp/sources/meta-proscend/recipes-core/prosrc/prosrc_0.1.bb`
- 參考之前 commit 的紀錄 - patch for u-boot-fw-utils since we need access uboot env from linux
- 修 `/meta-proscend/conf/distro/proscend-m300.conf b/meta-proscend/conf/distro/proscend-m300.conf`
- 整 `\M300_git\M300\sources\meta-fsl-arm\conf\machine\imx6ulevk.conf`
- 整 `M300_git/M300:<u-boot-imx>/include/configs/mx6ul_14x14_evk.h`
- `u-boot-fw-utils`
- 利用 `M300_git\M300\proscend\base_fs\default\rootfs` 整 `u-boot-fw-utils`
- 利用 `git status` 盤今天改了什麼
- commit
- engineering notebook
- 整合 `rc.local` - 配合新的 image 修改 mfgtool 的 `ucl2.xml`
- 改權限 - `chmod 775 FILE...` - - `fw_printenv`, `fw_setenv` 和 `FirmwareUpgrade.sh`
- 改 `imx6ul-14x14-evk.dts`
- 修正 `FirmwareUpgrade.sh` - 製作 firmware.tar - commit

[2016-12-27](https://github.com/silenceuncrio/diary/wiki/20161227_jeffrey)
---
- M300 team 就 KPI 這個主題開了會 - 結論
- review
- 修改 nfs 的設定
- 可以修改 `/www/app/` 的 source code 然後直接觀察結果
- 來寫 KPI
- 搞定 KPI
- efm bridge - 幫忙 upgrade 成 ACE 的版本 - 19 片 - 一片沒辦法插 power
- PHT 裝了 power 給我
- m300 - firmware upgrade web ui
- 從 cgi 用不會咬住的方法來呼叫 firmware upgrade 的 shell script

[2016-12-28](https://github.com/silenceuncrio/diary/wiki/20161228_jeffrey)
---
- review
- 改一隻 `/tmp/test.sh`
- `firmware.tar` 大於 20MB - 上傳就失敗了
- 利用 mongoose 在 iweb 寫個 upload file 的 api
- 成功把 2xMB 的 `firmware.tar` 傳到 m300 的 `/tmp/xxx.file` 去
- 把範例 `big_upload.c` 整到 `iweb.c` 去
- 成功上傳 2xMB 的 `firmware.tar` - `firmware.cgi` 呼叫 `/tmp/test.sh` 作事

[2016-12-29](https://github.com/silenceuncrio/diary/wiki/20161229_jeffrey)
---
- review
- 把 cgi 跟 shell script 接起來
- `FirmwareUpgrade.sh` - 一出錯就停下來 而且 讓使用者知道發生甚麼事
- m300 因為我明天請假所以提前在禮拜四開常態性的周會
- 目前已經可以透過 web 作 upgrade firmware 這件事了
- commit
- commit
- 製作 firmware.tar 目前手動流程如下




