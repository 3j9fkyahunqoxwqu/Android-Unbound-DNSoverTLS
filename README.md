## Android-Unbound-DNSoverTLS
A guide which shows how to get Android with Unbound / Stubby and DNSoverTLS working together.

[![Twitter URL](https://img.shields.io/twitter/url/https/twitter.com/fold_left.svg?style=social&label=Follow%20%40CHEF-KOCH)](https://twitter.com/FZeven)
[![Say Thanks!](https://img.shields.io/badge/Say%20Thanks-!-1EAEDB.svg)](https://saythanks.io/to/CHEF-KOCH)
[![Discord](https://discordapp.com/api/guilds/204394292519632897/widget.png)](https://discord.me/NVinside)


Google's implementation (in future Android versions)
--------------

* [RFC (7858)](https://tools.ietf.org/html/rfc7858)
* Google will use DNS over TLS which prevents the ISP from seen DNS request details. 
* 8.8.8.8 will be default (same as current)
* Requests are been encrypted over Port 853
* Prevents MITM


Reference:

* https://github.com/jedisct1/dnscrypt-proxy/issues/724
* https://github.com/laggardkernel/dnscrypt-proxy-magisk
* https://review.lineageos.org/#/q/topic:dnscrypt
* https://www.xda-developers.com/android-dns-over-tls-website-privacy/
* http://www.theregister.co.uk/2017/10/26/android_testing_dns_over_tls/
