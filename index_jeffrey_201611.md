
[2016-11-01](https://github.com/silenceuncrio/diary/wiki/20161101_jeffrey)
---
- 寫完了 engineering notebook
- react 值得長期投資...
- 感覺現階段的 M300 還是先好好的使用 AngularJS 吧
- openvpn.c: redesign
- 今天幾乎都是在看 react

[2016-11-02](https://github.com/silenceuncrio/diary/wiki/20161102_jeffrey)
---
- 先看一點 react
- react
- react: add more examples

[2016-11-03](https://github.com/silenceuncrio/diary/wiki/20161103_jeffrey)
---
- 從 openvpn 的 CGI 再次回到 M300 的 AngularJS
- openvpn.cgi: implement

[2016-11-04](https://github.com/silenceuncrio/diary/wiki/20161104_jeffrey)
---
- javascript 也可以先用 webpack 編譯了...
- 轉換到 react 跑道的是可以從長計議
- openvpn.cgi: implement
- ipsec.cgi: implement - ipsec web page: implement

[2016-11-07](https://github.com/silenceuncrio/diary/wiki/20161107_jeffrey)
---
- 這禮拜要專心衝一下 M300 WEB UI
- follow ipsec 的配置  
- openvpn page
- 把 key 的管理部分拉回各個 connection 的 edit 畫面

[2016-11-08](https://github.com/silenceuncrio/diary/wiki/20161108_jeffrey)
---
- openvpn page
- openvpn.cgi: modify - openvpn page
- redux time...

[2016-11-09](https://github.com/silenceuncrio/diary/wiki/20161109_jeffrey)
---
- 來把 openvpn 的 key 的 info 和 download 做完
- openvpn page
- add share.service.js

[2016-11-10](https://github.com/silenceuncrio/diary/wiki/20161110_jeffrey)
---
- 來做 openvpn 的 security import
- openvpn.cgi: add - openvpn page
- react time...

[2016-11-11](https://github.com/silenceuncrio/diary/wiki/20161111_jeffrey)
---
- Mongoose - Embedded Web Server / Embedded Networking Library
- iweb: next generation web technology for icos
- icos_shm.cgi add - netmon.cgi: new

[2016-11-14](https://github.com/silenceuncrio/diary/wiki/20161114_jeffrey)
---
- netmon.cgi: implement - dualSim page: implement
- ddns.cgi: add - Dynamic DNS page: add
- dualSim page: modify
- dualSim page: modify
- ipsec web page: modify

[2016-11-15](https://github.com/silenceuncrio/diary/wiki/20161115_jeffrey)
---
- mongoose creates zombies, when using php-cgi, or any cgi program.. #679
- use angular.toJson() instead of JSON.stringify()
- syslog.cgi: add - logging page: add
- logging page: add really

[2016-11-16](https://github.com/silenceuncrio/diary/wiki/20161116_jeffrey)
---
- dualSim page: modify
- ipv6lan.cgi: add - lanIpv6 page: add
- icos_config.cgi: add - management_restart page: add
- system.cgi: modify - management_identification page: modify

[2016-11-17](https://github.com/silenceuncrio/diary/wiki/20161117_jeffrey)
---
- sntp.cgi 的 apply() 還沒做
- sntp.cgi: implement - timeAndDate page: implement
- lte.cgi: implement

[2016-11-18](https://github.com/silenceuncrio/diary/wiki/20161118_jeffrey)
---
- 一早起床對於不同的客戶有不同的 WEB UI 樣貌有了一些想法
- 買個雲端主機玩玩 - https://www.vultr.com/

[2016-11-21](https://github.com/silenceuncrio/diary/wiki/20161121_jeffrey)
---
- 這禮拜開始做 login 的部分
- add cookie_auth example
- remove the executable file
- the "cookie_auth" example: modify
- dualSim page: modify
- com.cgi: modify
- dhcp.cgi: implement
- lanst.cgi: implement
- dnat.cgi: implement - icos dnat service: modify
- dns_ext6.cgi: fix the apply problem

[2016-11-22](https://github.com/silenceuncrio/diary/wiki/20161122_jeffrey)
---
- 今天為了 monkeyjj 來找一下怎麼實作 網站註冊 的機制

[2016-11-23](https://github.com/silenceuncrio/diary/wiki/20161123_jeffrey)
---
- m300 pm 希望我這禮拜能先給出多國語言的檔案給業務
- logging page: modify
- top_digicomm page: complete the language key
- delete the pages folder
- menu page: complete the language key
- status page: complete the language key
- identification page: complete the language key
- comPorts page: fixed problem about wrong value of vcom.mode
- timeAndDate page: complete the language key
- comPorts page: complete the language key
- dualSim page
- alarm page - logging page - locale-en.json
- comPorts page: ui improvement
- wanPriority page: complete the language key
- dualSim page: complete the language key
- wanEthernet page: complete the language key
- Eric 拿了 6 片 5600 Ver:B3 給我

[2016-11-24](https://github.com/silenceuncrio/diary/wiki/20161124_jeffrey)
---
- 希望今天把 M300 多國語言的 language key 做完
- lanIpv4 page: complete the language key
- lanIpv6 page: complete the language key
- dynamicDns page: complete the language key
- rename "firewall_portForwarding" to "portForwarding"
- portForwarding page: complete the language key
- openvpn cgi: remove following fields from configuration
- openvpn page: complete the language key
- ipsec page: complete the language key
- dualSim page: modify
- add locale-de.json: language file for german

[2016-11-25](https://github.com/silenceuncrio/diary/wiki/20161125_jeffrey)
---
- 開完 M300 周會有一些事項要注意一下

[2016-11-28](https://github.com/silenceuncrio/diary/wiki/20161128_jeffrey)
---
- 繼續做 login/logout
- implement authentication

[2016-11-29](https://github.com/silenceuncrio/diary/wiki/20161129_jeffrey)
---
- review 昨天作的 login/logout
- update mongoose
- _api_logout() does not Set-Cookie: prevent the logout problem at web ui
- monkeyjj time

[2016-11-30](https://github.com/silenceuncrio/diary/wiki/20161130_jeffrey)
---
- 昨天下午到今天發生了一些讓我不得不改變習慣的事情
- M300 的開發環境 虛擬機 `m300_dev` 被我搞掛了...
- 把 m300 的開發環境 setup 好了

