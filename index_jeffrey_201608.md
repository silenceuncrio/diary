
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


[2016-08-15](https://github.com/silenceuncrio/diary/wiki/20160815_jeffrey)
---
- 再確認一片燒錄好的 NAND Flash
- 14 號板 開起來 - ariel 小會議室 報告 好消息
- dual image 優先 priority
- Free Bootstrap Admin Dashboard - Siminta
- BOOTSTRAP SIDE MENU TEMPLATE - metismenu.js
- [65+ Best Free Bootstrap Admin Templates](http://www.cssauthor.com/bootstrap-admin-templates/)
- 估 schedule
- schedule list 放到 mantis
- `Web server+HTTPS`

[2016-08-16](https://github.com/silenceuncrio/diary/wiki/20160816_jeffrey)
---
- bootstrap 和 mentismenu
- 套 M300 的 menu tree
- [Twitter bootstrap 3 admin template](https://github.com/bopoda/ace)
- 從 bootstrap 加 mentismenu 開始

[2016-08-17](https://github.com/silenceuncrio/diary/wiki/20160817_jeffrey)
---
- 單純的記錄一下目前的工作環境
- winston 在廁所主動問我最近怎麼樣
- chrome `開發人員工具` - trace css
- Bootstrap-Admin-Theme-3-master
- side-menu-metis`
- 比較喜歡 `Bootstrap-Admin-Theme-3-master`

[2016-08-18](https://github.com/silenceuncrio/diary/wiki/20160818_jeffrey)
---
- 請 明天的假
- DigiComm logo
- bootstrap 搭配 logo 的技巧
- 調整 bootstrap 原本的配色
- 大概掌握了 navbar 加上 logo 的作法
- bootstrap vertical menu 的技巧

[2016-08-22](https://github.com/silenceuncrio/diary/wiki/20160822_jeffrey)
---
- review
- 參考 [DigiComm](http://www.digicomm.de/) 配合 logo 來設計上排的選單
- 目前在 `D:\m300\web\digicomm` 已做出了雛形

[2016-08-23](https://github.com/silenceuncrio/diary/wiki/20160823_jeffrey)
---
- engineering notebook
- 參考 [DigiComm](http://www.digicomm.de/) 的配色
- SVN update 完發現 compile error
- 目前 bootstrap 版型大架構

[2016-08-24](https://github.com/silenceuncrio/diary/wiki/20160824_jeffrey)
---
- digicomm 的 logo 換了底色 跟 bootstrap 的 `.navbar-inverse` 一樣
- 參考 [Bootstrap List Groups](http://www.w3schools.com/bootstrap/bootstrap_list_groups.asp)
- 參考 [Bootstrap Tables](http://www.w3schools.com/bootstrap/bootstrap_tables.asp)
- SVN clone 一份新的
- Samba server - root 的權限讓我蠻困擾的
- 修改 Samba 設定 - jeffrey 的權限
- chechout 反覆做了三次
- 安排表單的輸入版面

[2016-08-25](https://github.com/silenceuncrio/diary/wiki/20160825_jeffrey)
---
- 昨天 compile 出錯 - ubuntu 裝回 14 版
- ubuntu 14 - 再試一次 samba - 果然失敗
- 挑戰一下 nfs - window 10 NFS client - 找不到
- 太依賴 Source Insight 嗎?
- checkout m300 的 source code 超慢
- checkout 完成 - compile prosrc recipe
- compile opensrc 出錯 - 解決方法
- 為了 `ndisc6-1.0.3` 需要在 ubuntu_15 做兩件事

[2016-08-26](https://github.com/silenceuncrio/diary/wiki/20160826_jeffrey)
---
- 恢復到正常開工的狀態
- 開響 第一砲 - Revision: 425 - Add "CGI Class 101"
- m300 meeting
- 配合 john 包裝 `wanstcfg.c` 的 CGI
- `iweb` - 相當滿意的作品

[2016-08-29](https://github.com/silenceuncrio/diary/wiki/20160829_jeffrey)
---
- review
- commit - Revision: 444 - Add lanst.cgi
- 思考 [AngularJS AJAX - $http](http://www.w3schools.com/angular/angular_http.asp) 
- 注意 [AngularJs $http.post() does not send data](http://stackoverflow.com/t ns/19254029/angularjs-http-post-does-not-send-data) 這個 issue
- commit - 今天的成果

[2016-08-30](https://github.com/silenceuncrio/diary/wiki/20160830_jeffrey)
---
- john 分享 ubuntu 14.04 怎麼來啟動 samba - 真的可以
- commit - Modify lanst.html - Modify lanst.cgi
- commit - Refactoring iweb API - Modify lanst.c - Modify wanst.c
- commit - Refactoring iweb API, lanst.cgi, wanst.cgi - Add wanst.html
- trace 目前 login 機制
- WDBG() function 開啟 - 費不少功夫
- commit - Refactoring wanst.html

[2016-08-31](https://github.com/silenceuncrio/diary/wiki/20160831_jeffrey)
---
- `lanst.html` form input 格式檢查
- [AngularJS Form Validation](http://www.w3schools.com/angular/angular_validation.asp)
- [8 Example(s) of Ng-Pattern](http://learnkode.com/Examples/Angular/Ng-Pattern)
- [RegExp](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/x 
- CGI 裡如果也需要比對 regular expression 的話
- commit - Improve lanst.html
- [bootstrap form validation done right in angularjs/)](http://blog.yodersolutions.com/s ap-form-validation-done-right-in-angularjs/)
- 為了 `wanst.html` 有跟原設計者 john 聊了一下


