
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


[2016-07-07](https://github.com/silenceuncrio/diary/wiki/20160707_jeffrey)
---
- 發 mail 問 AVNET 的 FAE 有關 U-Boot 設定成 NAND Boot 的 issue
- web server 需要 dropbear 加密 先記錄
- alarm sensor 警報器 零用金申請單  
- 整理 GitHub diary index
- proposal - [m300_proposal_kernel_mtd_driver_jeffrey](https://docs.google.com/document/d/1x5xbzFECeaXqY8-4UOipQe0_otIxEahNb2KOkXdM0D4/edit?usp=sharing)
- alarm sensor
- proposal - [m300_proposal_uboot_burn_image_nand_flash_jeffrey](https://docs.google.com/document/d/1AcyShTN-VFRmFzJbiWmrYZ-BnU4y-JdyK-j_B9B8JmY/edit?usp=sharing)
- AVNET 的 FAE 回信
- 幫忙 寄 `M300 Kick Off Meeting`
- 發現 `bitbake u-boot-imx` 出錯 - source code 權限有些被改成 root
- `Freescale Yocto Project User's Guide` - `5.5 U-Boot configuration`  
- machine configuration - `M300\fsl-release-bsp\sources\meta-fsl-arm\conf\machine\imx6ul14x14ddr3arm2.conf`
- machine configuration - `conf\machine\imx6ulevk.conf`
- `u-boot-fw-utils_2015.01.bb`
- `u-boot-ls1_2015.01.bb`
- `u-boot.inc`
- `bitbake u-boot-imx -c compile -vf` 會呼叫 `u-boot.inc` 的 do_compile ()
- 警報器 隔壁庫房 測試

[2016-07-08](https://github.com/silenceuncrio/diary/wiki/20160708_jeffrey)
---
- 颱風假一天

[2016-07-11](https://github.com/silenceuncrio/diary/wiki/20160711_jeffrey)
---
- mail proposal ariel
- M300 meeting 延到明天十點
- trace `bitbake u-boot-imx -c compile -vf` 流程
- `do_compile ()`
- `do_compile ()`...
- `do_compile ()` - 修改 來 trace `UBOOT_CONFIG` 在 `local.conf` 有無 定義 `nand` 的 影響
- `do_compile ()` - 修改
- `oe_runmake` `oe_runmake_call`
- `imx6ulevk.conf` - 修改
- `do_compile ()` - 修改
- `mx6ul_14x14_evk_defconfig`
- `Freescale Yocto Project User's Guide` - `5.5 U-Boot configuration` - `U-Boot type = NAND`

[2016-07-12](https://github.com/silenceuncrio/diary/wiki/20160712_jeffrey)
---
- alarm sensor - `print("Alarm Detect!")` - 順便點燈
- M300 meeting - schedule 順延 十月底
- 聲音偵測 SoC - BelaSigna R281
- review 昨天 實驗 過程 加強 YOCTO 認識
- review 昨天 足跡
- 整理 方便 說故事 - `<YOCTO_DIR>` `<BUILD_DIR>` `<UBOOT_DIR>`
- `<UBOOT_DIR>/configs/mx6ul_14x14_evk_nand_config` - 新增
- `CONFIG_SYS_EXTRA_OPTIONS="...,SYS_BOOT_NAND"` - compile-time - `CONFIG_SYS_BOOT_NAND` flag
- 實驗 - UBOOT_CONFIG = "sd" - UBOOT_CONFIG = "nand"
- 幫助 實驗 順利 情報
- 實驗 - `UBOOT_CONFIG = "sd"` - `UBOOT_CONFIG = "nand"`
- 整理 alarm sensor code - 可能 config
- 隔壁庫房 試 alarm sensor
- `UBOOT_CONFIG = "nand"` - log - 沒有 build `ubifs` 格式 rootfs
- `<BUILD_DIR>/conf/local.conf` - `MACHINE ??= 'imx6ul14x14ddr3arm2'` - `bitbake core-image-minimal`

[2016-07-13](https://github.com/silenceuncrio/diary/wiki/20160713_jeffrey)
---
- review
- charlie alarm sensor prototype 進 會議室
- 昨晚 - log - 還是 沒有 `ubifs` 字眼 - 自己 誤會
- alram sensor 等 簡單 UI 控制 
- MfgTool 找 ubifs 相關 線索 - ubifs 跟 rootfs 沒有 關係
- `MACHINE` 改回 `imx6ulevk` - 執行 `bitbake core-image-minimal`
- 示波器 看 alarm sensor 
- [How-To use NAND boot on i.MX6UL EVK board](https://community.nxp.com/docs/DOC-236994) - MfgTool 相關 部分
- rayson nelson 致電 拿 一串燈
- eric nelson 交換 聖誕燈串 情報
- [How-To use NAND boot on i.MX6UL EVK board](https://community.nxp.com/docs/DOC-236994) - [mx6ul_14x14_evk.h](https://community.nxp.com/servlet/JiveServlet/download/236994-2-304575/mx6ul_14x14_evk.h.zip)

[2016-07-14](https://github.com/silenceuncrio/diary/wiki/20160714_jeffrey)
---
- review - recipe - u-boot-imx - bitbake task - do_compile
- `M300\fsl-release-bsp\sources\meta-fsl-arm\` - `meta-fsl-arm` layer
- `bitbake-layers show-layers` - 看 M300 layers - `M300/fsl-release-bsp/sources/` 簡化 成 `<POKY_DIR>`
- `<POKY_DIR>/meta-fsl-arm/conf/layer.conf` 是 `meta-fsl-arm layer` 的 `configuration file`
- `<POKY_DIR>\meta-fsl-arm\conf\machine\imx6ulevk.conf` - 不知道 怎麼 被 吃進去
- `<POKY_DIR>\meta-fsl-arm\conf\machine\imx6ulevk.conf` - 細節 算了
- `<POKY_DIR>/poky/meta/recipes-bsp/u-boot/u-boot_2015.01.bb` - 解析
- `<POKY_DIR>/poky/meta/recipes-bsp/u-boot/u-boot.inc` - 解析
- `addtask deploy before do_build after do_compile` - 解析
- `<POKY_DIR>\meta-fsl-bsp-release\imx\meta-bsp\recipes-bsp\u-boot\u-boot-imx_2015.04.bb` - 追蹤
- morris 表示 明天 料備齊後 送 打件廠 - 下禮拜三 回來 算快
- [Yoctco Project Mega-Manual](http://www.yoctoproject.org/docs/2.1/mega-manual/mega-manual.html) - [Chapter 20. A Closer Look at the Yocto Project Development Environment](http://www.yoctoproject.org/docs/2.1/mega-manual/mega-manual.html#closer-look) - [20.1. User Configuration](http://www.yoctoproject.org/docs/2.1/mega-manual/mega-manual.html#user-configuration)

[2016-07-15](https://github.com/silenceuncrio/diary/wiki/20160715_jeffrey)
---
- review
- follow [user configuration] - `<POKY_DIR>` `<BUILD_DIR>` `<UBOOT_DIR>`
- alarm sensor 綜合 情報
- `<POKY>/meta-fsl-arm/conf/machine/imx6ulevk.conf` - 修改
- 永鈦鑫 世宏 來訪 - 今年九月 知道 要不要繼續
- 看一下 永鈦鑫 和 昇頻 這兩間網通產業公司
- ariel 聊 目前 處境  
- ariel 拿 i.MX6UL demo board
- proscend 目錄 `make menuconfig` - 取消 ndisk - 不然 build 不過
- M300 - `bitbake linux-imx -c devshell` - `make menuconfig` - 確認 `iptables` 有關 選項
- 解掉 `iptables` 的 issue - commit
- 不能 使用 busybox 的 `ps` 而是要 使用 完整功能 的 `procps`
- 確認 是否有 `procps` recipe

[2016-07-18](https://github.com/silenceuncrio/diary/wiki/20160718_jeffrey)
---
- 安裝 `procps` 到 M300 的 image 上
- 開機 出錯 `[ -f /etc/sysctl.conf ] && sysctl -p -e >&-`
- 修改 `do_install_append ()` - 沒有 install
- `<POKY_DIR>/poky/meta/recipes-extended/procps/procps_3.3.10.bb` - 解析
- 修改 `/etc/rc.local` - 拿掉 `[ -f /etc/sysctl.conf ] && sysctl -p -e >&-` - commit
- engineering notebook
- M300 板子 禮拜三 回來
- [BitBake User Manual](http://www.yoctoproject.org/docs/2.1/bitbake-user-manual/bitbake-user-manual.html) - [Appendix A. Hello World Example](http://www.yoctoproject.org/docs/2.1/bitbake-user-manual/bitbake-user-manual.html#hello-world-example)
- [BitBake User Manual](http://www.yoctoproject.org/docs/2.1/bitbake-user-manual/bitbake-user-manual.html) - [Appendix A. Hello World Example](http://www.yoctoproject.org/docs/2.1/bitbake-user-manual/bitbake-user-manual.html#hello-world-example)
- 基本 BitBake Hello World 架構
- [From Bitbake Hello World to an Image](http://hambedded.org/blog/2012/11/24/from-bitbake-hello-world-to-an-image/)

[2016-07-19](https://github.com/silenceuncrio/diary/wiki/20160719_jeffrey)
---
- `bitbake.conf` 在 `<POKY_DIR>/poky/meta/conf` 目錄
- `core-image-minimal` 是個 `recipe`
- [From Bitbake Hello World to an Image](http://hambedded.org/blog/2012/11/24/from-bitbake-hello-world-to-an-image/)
- [The Linux Command Line: A Complete Introduction](https://www.amazon.com/Linux-Command-Line-Complete-Introduction/dp/1593273894/ref=sr_1_2?ie=UTF8&qid=1468904908&sr=8-2&keywords=shell+script)
- review M300 web
- [異種國度](http://acg.gamer.com.tw/acgDetail.php?s=83148) - Alienation
- [The Linux Command Line: A Complete Introduction](https://www.amazon.com/Linux-Command-Line-Complete-Introduction/dp/1593273894/ref=sr_1_2?ie=UTF8&qid=1468904908&sr=8-2&keywords=shell+script)

[2016-07-20](https://github.com/silenceuncrio/diary/wiki/20160720_jeffrey)
---
- cpu board 打件 回來
- `Boot Device` 為 `NAND` - console 沒任何訊息
- MfgTool 燒錄 code
- MfgTool `Jumping to OS image.` 停住 - MXS NAND: DMA read error
- M300 CPU Board 1 號 - 3 號 和 4 號
- 4 號板 `Boot Device` 為 `MicroSD` - 開機 - iCOS 跑起來了
- 早上做的事 換成 公板
- [[U-Boot] MXS NAND: DMA read error](https://patchwork.ozlabs.org/patch/153071/)
- pioneer 分享 openvpn 在 vpn router 上的實作
- `mx6ul_14x14_evk.h` DMA 相關部分拿掉 - build 不過
- M300 console 是公頭 - 兩個公頭之間 杜邦線
- 出錯的點 - `<UBOOT_DIR>/drivers/mtd/nand/mxs_nand.c`
- 套用 [How-To use NAND boot on i.MX6UL EVK board](https://community.nxp.com/docs/DOC-236994) 的 `mx6ul_14x14_evk.h` - PASS
- 修改 `ucl2.xml` - 大步前進
- M300 的 kernel 和 rootfs 一起燒

[2016-07-21](https://github.com/silenceuncrio/diary/wiki/20160721_jeffrey)
---
- 找出 `mx6ul_14x14_evk.h` 修改的關鍵點
- 做完整的 MfgTool burn image - [2016-07-21-MfgTool.log](https://gist.github.com/silenceuncrio/917bc8a24a2c3c8b3bc6a08e1c10cc83) - nand 開機 看不到 console 任何訊息
- [NAND BOOT fail on iMX6UL](https://community.nxp.com/message/640692)
- `i.MX 6UltraLite Applications Processor Reference Manual` - `Chapter 8 System Boot`
- BOOT_CFG1[1:0] - Nand_Row_address_bytes - Row Address Cycle
- M300 Web UI Proposal meeting
- [反及閘快閃記憶體（NAND Flash Memory）簡介](http://bbs.hwrf.com.cn/downpcbe/NAND%20Flash%20Memory-9386.pdf)
- MX30LF1G18AC - 2 個 `Row address` - `BOOT_CFG1[1:0]` = `2'b01`
- morris 幫忙改 - 開機 console 沒 任何訊息

[2016-07-22](https://github.com/silenceuncrio/diary/wiki/20160722_jeffrey)
---
- 寫 KPI
- M300 meeting - aaron 確定 八月一號 報到
- 繼續 NAND Flash 問題
- 套用 [How-To use NAND boot on i.MX6UL EVK board](https://community.nxp.com/docs/DOC-236994) 的 `mx6ul_14x14_evk.h`
- 將 U-Boot 燒錄到 NAND Flash - `kobs-ng init -x -v --chip_0_device_path=/dev/mtd0 $FILE`
- 試 MfgTool - `L3.14.52_1.1.0_ga-mfg-tools.tar.gz`
- MXIC FAE Frank 電話
- winston 示範 怎麼看 code 有寫到 NAND Flash 去
- `0x87800000` address - RAM 裡面的 U-Boot
- `local.conf` `UBOOT_CONFIG = "nand"` - SD Card 開機 - U-Boot 有 `nand` command 可以使用

[2016-07-25](https://github.com/silenceuncrio/diary/wiki/20160725_jeffrey)
---
- review
- 安裝 Yocto project cross-compilation toolchain
- 整理問題 尋求協助
- 在 論壇 https://community.nxp.com/docs/DOC-236994 發問
- 看 i.MX6UL boot 相關 部分
- BOOT_CFG2[4:3] 的 shipped value 為 2'b00
- morris 3 號板 BOOT_CFG2 改成 0x00 - 開機 挑戰失敗
- U-Boot - `fuse`

[2016-07-26](https://github.com/silenceuncrio/diary/wiki/20160726_jeffrey)
---
- AVNET CPU 公板 emmc 開機
- Frank 回信
- 致電 mike
- imximage.cfg u-boot.bin u-boot.imx
- `<UBOOT_SRC>` 另存 `<UBOOT_SRC_NAND>`
- `u-boot.imx` SD Card - `<UBOOT_SRC>` 或 `<UBOOT_SRC_NAND>` 可以 從 SD Card 開機
- 研究 GPIO 點燈
- 觀察 `<UBOOT_SRC>/board/freescale/mx6ul_14x14_ddr3_arm2/imximage.cfg` DCD

[2016-07-27](https://github.com/silenceuncrio/diary/wiki/20160727_jeffrey)
---
- review
- 配合 winston 步調 準備環境
- 點燈 參考 `26.4.3.2 GPIO Write Mode`
- 知道 暫存器 點燈 後 - 寫成 assembly 塞到 uboot 去
- 把 `50`, `51` 和 `52` 通通點亮
- 通通點亮 `test.c` - `arm-poky-linux-gnueabi-gcc test.c -S` 得到 `test.s`
- 寫到 `<UBOOT_SRC>/arch/arm/cpu/armv7/start.S`
- NAND Flash 開機 - les #50, #51, #53 亮了

[2016-07-28](https://github.com/silenceuncrio/diary/wiki/20160728_jeffrey)
---
- trace 從 U-Boot 的 start.s 出發 經過的路
- `start.S` - `crt0.S` - `board_f.c` 的 `board_init_f()`
- init_sequence_f[] - console_init_f - 我要把陣亡的點找出來
- NAND Falsh 的 U-Boot 直接開起來了
- NAND Flash 開機 4 號 - 6 號 無法從 NAND Flash 開機 - 4 號板子 bad block 消失
- 14 號板子 實驗 - `nand scrub.chip` - erase all factory set bad blocks - NAND Flash 開機 成功
- 復健

[2016-07-29](https://github.com/silenceuncrio/diary/wiki/20160729_jeffrey)
---
- 完整 image 燒錄 - 開起來了
- M300 meeting
- 整理 日記 寫 index
- 什麼是 OOB
- [SLC Nand Flash driver](http://afttnote.blogspot.tw/2015/01/slc-nand-flash-driver.html)
- recipes used to build a manufacturing tool image
- VirtualBox `study_ubuntu_16` 只有 16 GB
- 建 80 GB VirtualBox `ubuntu_16`
- 安裝 samba - YOCTO - build image - `bitbake linux-mfgtool`


