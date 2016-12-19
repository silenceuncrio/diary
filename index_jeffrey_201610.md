
[2016-10-03](https://github.com/silenceuncrio/diary/wiki/20161003_jeffrey)
---
- review
- porting openvpn 的 `nwebmain.c` 的 `createServerCert()` 和 `createSharedkey()`

[2016-10-04](https://github.com/silenceuncrio/diary/wiki/20161004_jeffrey)
---
- monkeyjj 的雲端 server 目前先不考慮
- monkeyjj 應該用最省力的方式來實作後台  
- PHP, MySQL and AngularJS CRUD Tutorial – Step by Step Guide!
- Modify openvpn.c: add support for following actions:
- PHP and MySQL CRUD Tutorial for Beginners – Step By Step Guide
- PHP, MySQL and AngularJS CRUD Tutorial – Step by Step Guide
- Modify openvpn.cgi: change the value of following key base on original openvpn design:
- PHP AngularJS CRUD with Search and Pagination Example From Scratch

[2016-10-06](https://github.com/silenceuncrio/diary/wiki/20161006_jeffrey)
---
- 原本在 vpn 機種實作的 openvpn 的 CGI 實在是做了太多不適合在 CGI 做的事情
- 目前 m300 在瀏覽器上打 192.168.1.1 後會開啟 rpAuth.html
- 追一下 Request URL:http://192.168.1.1/cgi-bin/z_web.cgi?module=sysadmin&act=getSetting
- Modify system.cgi
- calculate the sysUpTime before display to user
- 來做 `z_web.cgi?module=systime&act=getSetting`
- Add sntp.cgi
- PHP CRUD Tutorial (part 1)

[2016-10-07](https://github.com/silenceuncrio/diary/wiki/20161007_jeffrey)
---
- 感覺今天可以針對 web 來 refactoring 一下
- Add dnat.cgi
- modify "firewall_portForwarding" web page


[2016-10-11](https://github.com/silenceuncrio/diary/wiki/20161011_jeffrey)
---
- review
- engineering notebook
- modify "firewall_portForwarding" web page
- `icos_shm.c` 裡的 _lte_dpip_all()
- Modify icos_shm.cgi
- index.html - status.html - management_administration page
- dnat.cgi: apply function return ok for testing
- comPorts page: change layout style

[2016-10-12](https://github.com/silenceuncrio/diary/wiki/20161012_jeffrey)
---
- icos_shm.c: use done_shm, not the done_status
- index.html - app.controller.js - status.html
- font-awesome - index.html
- custom-digicomm.css - index.html
- index.html

[2016-10-13](https://github.com/silenceuncrio/diary/wiki/20161013_jeffrey)
---
- 今天試著再為了 m300 web 的 nav-tab 分頁找找看有沒有更合適的 solution
- 參考 w3schools 的 Bootstrap Collapse
- change the overall layout style
- change the overall layout style
- custom-digicomm.css: less is more
- dhcp.cgi: CGI for MODULE_DHCP

[2016-10-14](https://github.com/silenceuncrio/diary/wiki/20161014_jeffrey)
---
- 今天再 review 一下整個 web 的架構
- change the layout style
- change the layout style
- add index_nobrand.html for common use
- use image to denote the signal level
- change the images used to denote the signal level
- change the overall layout style

[2016-10-17](https://github.com/silenceuncrio/diary/wiki/20161017_jeffrey)
---
- 早上 john 找我討論 log 的 web ui
- engineering notebook
- add the footer page via ng-include at index.html
- rearrange the resource folder
- rearrange top.html and bottom.html

[2016-10-18](https://github.com/silenceuncrio/diary/wiki/20161018_jeffrey)
---
- jweb API for user to implement CGI more easily
- ipsec.c: CGI for MODULE_IPSEC
- ipsec.c: CGI for MODULE_IPSEC
- icos_shm.cgi: use jweb api

[2016-10-19](https://github.com/silenceuncrio/diary/wiki/20161019_jeffrey)
---
- review
- sntp.cgi: 
- 目前 CGI 使用的 jweb API 已經有能力回傳非 200 的 http status code
- refactoring the jweb API
- refactoring the management_administration page
- sntp.cgi
- comp.cgi - vcomp.cgi
- connmgr.cgi
- lte.cgi - icos_msg.cgi - dualSim page
- dualSim page

[2016-10-20](https://github.com/silenceuncrio/diary/wiki/20161020_jeffrey)
---
- 這幾天 commit 了不少
- icos_shm.cgi - icos_msg.cgi
- pppoe.c: CGI for MODULE_PPPOE
- dns_ext6.c: CGI for MODULE_DNS_EXT6
- wanst.cgi
- wanEthernet page

[2016-10-21](https://github.com/silenceuncrio/diary/wiki/20161021_jeffrey)
---
- management_administration page: remove the `Domain Name` field
- dhcp.cgi and lanst.cgi - lanIpv4 page
- sntp.cgi - timeAndDate page
- timeAndDate page: update current time every second on browser side

[2016-10-24](https://github.com/silenceuncrio/diary/wiki/20161024_jeffrey)
---
- review
- top_digicomm.html and top_nobrand.html
- management_identification.html
- change the function name "VPN" to "Open VNP" at WEB UI
- ipsec page

[2016-10-25](https://github.com/silenceuncrio/diary/wiki/20161025_jeffrey)
---
- 繼續打造 IPSec 的 web UI
- ipsec page

[2016-10-27](https://github.com/silenceuncrio/diary/wiki/20161027_jeffrey)
---
- ipsec page 總算長到了一個自己覺得還算清爽的 config 畫面
- ipsec page

[2016-10-28](https://github.com/silenceuncrio/diary/wiki/20161028_jeffrey)
---
- 繼續 IPSec 的 WEB UI
- ipsec page
- ipsec page

[2016-10-31](https://github.com/silenceuncrio/diary/wiki/20161031_jeffrey)
---
- 今天悠哉一點 看個 react


