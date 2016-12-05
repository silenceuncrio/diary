
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


