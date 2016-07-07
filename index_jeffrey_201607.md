
[2016-07-04](https://github.com/silenceuncrio/diary/wiki/20160704_jeffrey)
---
- 下午 九十秒的題目 倖存者偏差
- 默念一遍 夠撐 90 秒
- engineering notebook
- review M300
- 月會 90 秒演講 順利
- 重新安裝 M300 開發環境
- window m300_develop 掛載 網路磁碟
- Ubuntu svn command checkout
- checkout 完畢
- M300 build process 停在下面的畫面超過十五分鐘
- 放棄 Ubuntu 16.04
- 安裝 Ubuntu 14.04
- 安裝 subversion
- checkout build code 

[2016-07-05](https://github.com/silenceuncrio/diary/wiki/20160705_jeffrey)
---
- 看 昨天 build 的怎樣 沒裝 gawk
- 還是有錯 該裝的 Yocto Project host packages 裝一裝
- 順利 build image 中
- morris 麥可風 輸出端 加一顆電容
- M300 build 有錯誤 proscend make menuconfig 連不上 samba Ubuntu 14.04 問題 試 Ubuntu 15.10 samba
- ariel M300 demoboard web
- m300_ubuntu_15 samba 運作正常 shit! Ubuntu 14.04
- ariel 表示 NAND Flash boot 比較優先  
- m300_ubuntu_15 checkout build image
- 大會議 alarm sensor 實驗
- M300 還再 build
- `M300/fsl-release-bsp/proscend' 要先 make menuconfig 取消勾選 `LTE` module
- 安裝 host packages
- build 過了 Source Insight trace code
- webcfg.c InitWeb() 找不到 mgmt_init_iptables





[2016-07-06](https://github.com/silenceuncrio/diary/wiki/20160706_jeffrey)
---
- M300 開機 web module init `Error: /etc/mini_httpd.conf not exist!`
- web 起來了 `ifconfig eth0 up`
- 網頁可以正常顯示了
- boot device 設定成 QSPI 卻可以從 SD Card 開機 morris R324 NAND_DATA0
- [issue]ariel 表示 網頁的帳密太簡單
- demo board 先拿給 ariel
- svn update conflict tf
- ariel 小紙條 `我用最近的 code 怎麼 web server 沒起來?`
- [How-To use NAND boot on i.MX6UL EVK board](https://community.nxp.com/docs/DOC-236994)
- mx6ul_14x14_evk_nand_defconfig
- Linux DTB modification and build
- jammy 已經準備好 dtb file
- 禮拜五要提出 `kernel: EMMC/NAND MTD Driver` 的 proposal
- `u-boot : burn image - NAND flash` 這個 proposal 也要提出來
- alarm sensor






