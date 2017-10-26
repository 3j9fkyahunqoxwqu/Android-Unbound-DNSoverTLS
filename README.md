## Android-Unbound-DNSCrypt
A guide which shows how to get Android with Unbound and DNSCrypt working together

[![GitHub stars](https://img.shields.io/github/stars/badges/shields.svg?style=social&label=Star)](https://github.com/CHEF-KOCH/Android-Unbound-DNSCrypt)
[![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)
[![Say Thanks!](https://img.shields.io/badge/Say%20Thanks-!-1EAEDB.svg)](https://saythanks.io/to/CHEF-KOCH)



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
