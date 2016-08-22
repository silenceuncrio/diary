
[2016-08-01](https://github.com/silenceuncrio/diary/wiki/20160801_jeffrey)
---
- review
- 將 `kernel` 和 `rootfs` 燒錄到 NAND 去所需要的 tool
- `bitbake linux-mfgtool` - 包含我們需要的 tool
- VirtualBox - 介面卡 1 附加到 NAT - 介面卡 2 附加到 `僅限主機` 介面卡
- `svn up` update M300
- jammy 的 `000_enable_ENET_CLK_when_booting.patch`
- 為了之後的 NAND Flash boot 做了兩次 commit
- 月會
- 我們該提供什麼 image 讓 第三方 來做預燒的動作
- `imx-kobs` recipe - `bitbake imx-kobs`
- trace source code

[2016-08-02](https://github.com/silenceuncrio/diary/wiki/20160802_jeffrey)
---
- review
- trace `imx-kobs` recipe - main - init_main - padding_1k_in_head
- `rom_mtd_init()` - `v4_rom_mtd_init()`
- `rom_mtd_commit_structures()` - `v6_rom_mtd_commit_structures()`
- `write_boot_stream()`
- 好好了解 `write_boot_stream()` 的行為
- bitbake fsl-image-mfgtool-initramfs
- `<BUILD_DIR>` - `<IMX_KOBS_SRC>`
- 修改 `<IMX_KOBS_SRC>` - compile - 燒錄 - console 看到 debug information
- `fill_fcb()` - `imx-kobs` 怎麼來使用 `/dev/mtd0` 這一塊 NAND Flash
- MfgTool 被我弄亂了 - 燒錄完開不起來
- 之前 mfgtools 燒錄完開的起來
- 修改 `mx6ul_14x14_evk.h` - 讓 boot mtd 只占 3m - 原本是 64m
- 理論 - 複製一個 3m 的 image 從頭 燒錄到 NAND Flash 去 - 可以開機

[2016-08-03](https://github.com/silenceuncrio/diary/wiki/20160803_jeffrey)
---
- review
- 再確認 - 修改 `<IMX_KOBS_SRC>` - 燒錄 U-Boot image - 是否能開機
- 可以開機 - 放心 trace `imx-kobs` source code
- 如何透過網路將電腦上的檔案上傳到 M300
- 利用 `tftpboot` 從 `serverip` 上將 `test.bin` 複製到 address `0x80000000` 去
- 從 RAM address `0x80000000` 將 `test.bin` 複製到 NAND Flash address `0x01000000` 去
- `cmp` command
- 怎麼把 M300 RAM 裡某一段的內容再傳到 PC 上 - tftpput
- 將 RAM address `0x80000000` 裡 64 bytes 的 `test.bin` 利用 `tftpput` put 到 tftp server 上
- 理論 - `0x300000` 大的 `u-boot-all.bin` 寫入 NAND Flash - 開機
- `NAND read from offset 0 failed` - nand read.raw... OK
- 13 號板 - 玩第一個 page 觀察 OOB 的變化
- `FCBx` 用 read.raw/write.raw - `DBBTx` 和 `tmp_kobs_ng` 用 read/write
- 13 號板 - 開機成功 - 外包廠看到 SOP 可能 很不爽

[2016-08-04](https://github.com/silenceuncrio/diary/wiki/20160804_jeffrey)
---
- review
- nand 的 write 和 write.raw 對外包廠的燒錄來說是否有對應的方法可以實作
- 不用 MfgTool 燒錄 NAND Flash 的流程 - 麻煩 - 為了 MfgTool 留 USB Port
- 開始進行 web
- web `mini_httpd` - `index.html` 在 `/www` - source code 在 `M300\fsl-release-bsp\proscend\prosrc\www`
- 看 `index.html`
- 問 ariel 關於 share memory 中的 status 資訊 如何取得

[2016-08-05](https://github.com/silenceuncrio/diary/wiki/20160805_jeffrey)
---
- CGI 把 icos 細節藏起來 - 從 web 只看 RESTful API
- M300 meeting
- cgi class 101
- [Bootstrap 3 Tutorial](http://www.w3schools.com/bootstrap/)
- [Bootstrap Glyphicons](http://www.w3schools.com/bootstrap/bootstrap_glyphicons.asp)
- [Icon Font 的使用方式](http://www.oxxostudio.tw/articles/201406/css-icon-font.html) 加強一下知識
- [Bootstrap 3 Tutorial](http://www.w3schools.com/bootstrap/)
- 可以 利用 bootsrap 寫網頁

[2016-08-08](https://github.com/silenceuncrio/diary/wiki/20160808_jeffrey)
---
- review
- 整理 GitHub Index
- engineering notebook
- VirtualBox scp
- CGI Class 101 - cgi_1
- CGI Class 101 - cgi_2
- m300 webui
- bootstrap template
- MfgTool 多 USB Port 被 否決

[2016-08-09](https://github.com/silenceuncrio/diary/wiki/20160809_jeffrey)
---
- 準備 winston 協助 NAND Flash 開機 image 的板子
- `nand read.raw` 讀出 再寫回 nand flash
- 盤 將 `kernel` 和 `rootfs` 燒錄到 NAND 所需 tool
- `mtd-utils` recipe
- U-Boot 把 NAND Flash image dump 出來
- 修改 `mx6ul_14x14_evk.h` - image 2MB
- U-Boot - image dump - tftpput
- 萬事起頭難
- 7 個 page dump - 64, 128, 192, 256, 320, 384, 448
- 第 320 個 page - DBBT - 不是我想像的規則 - 放棄

[2016-08-10](https://github.com/silenceuncrio/diary/wiki/20160810_jeffrey)
---
- review
- Bad Linux ARM zImage magic
- 修改 `mx6ul_14x14_evk.h` - ${loadaddr} - ${fdt_addr}
- `boot` 改小 - 從 `4m` 改成 `2m`
- 把 0x200000 大小 的 `boot` 搞出來
- mtdinfo 怎麼用
- nanddump 怎麼用
- 研究 燒錄機 - ALL-100P
- PHT 表示 燒錄機 是 `FLASH-100`

[2016-08-11](https://github.com/silenceuncrio/diary/wiki/20160811_jeffrey)
---
- PHT - 隔壁電腦 `C:\Program Files\Hi-Lo\FLASH-100` 複製
- FLASH-100 User's Manual - SNAND8 Help
- 燒錄 0 ~ 15 這 16 個 block
- 拜託 morris 換 NAND Flash - 4 號板
- 致電 frank 詢問 NAND Flash 相關知識
- 4 號板 - 不可以開機

[2016-08-12](https://github.com/silenceuncrio/diary/wiki/20160812_jeffrey)
---
- 昨天下班前 ken 幫我換一片 NAND Flash
- 4 號板 - 請 PHT 幫我換 - 5 分鐘 - 厲害
- M300 開會 - 多了俄羅斯客戶
- 4 號板 開機成功
- 整理 術語
- 4 號板 第 5 個 block 沒有燒錄
- ken 幫我換的是 13 號板 - 可以開機
- 記錄 燒錄 過程
- 充實 bootstrap 知識
- 昨天 aaron 介紹 [zsh](https://github.com/robbyrussell/oh-my-zsh)
- 燒錄 NAND Flash 確認可行 - 公布 - 下禮拜
- 感覺 MfgTool 方便
- `cmp.b 80000000 81000000 10000`
