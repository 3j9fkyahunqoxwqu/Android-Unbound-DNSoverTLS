## Android-Unbound-DNSoverTLS
A guide which shows how to get Android with Unbound or Stubby and DNSoverTLS working together.

[![Twitter URL](https://img.shields.io/twitter/url/https/twitter.com/fold_left.svg?style=social&label=Follow%20%40CHEF-KOCH)](https://twitter.com/CKsTechNews)
[![Say Thanks!](https://img.shields.io/badge/Say%20Thanks-!-1EAEDB.svg)](https://saythanks.io/to/CHEF-KOCH)
[![Discord](https://discordapp.com/api/guilds/418256415874875402/widget.png)](https://discord.me/CHEF-KOCH)


Google's implementation in current Android versions 9+
--------------

* [RFC (7858)](https://tools.ietf.org/html/rfc7858)
* Google will use DNS over TLS which prevents the ISP from seen DNS request details. 
* 8.8.8.8 will be default (same as current)
* Requests are been encrypted over Port 853
* Prevents MITM
* [DNS over TLS support in Android P Developer Preview](DNS over TLS support in Android P Developer Preview)


How DNS over TLS Works
--------------

This new feature will be released in the Android P and could to secure your Internet traffic from network spoofing attacks at the DNS level. Just like Transport Layer Security (TLS) encrypted protocol secures HTTPS connections cryptographically, DNS-over-TLS dramatically enhances privacy and security with end-to-end authenticated DNS lookups.

This means DNS over TLS will virtually mask the website name you’re viewing, but don’t jump to the conclusion this will completely block these sites and metadata from your ISP, a hotly debated aspect of this protocol’s efficacy. Those initial queries you make to the DNS (entering a URL into your browser bar) will get their own encryption—TLS encryption, one of the protocols used in HTTPS—and they won’t be logged by the DNS.

DNS over TLS is not a solve-all: Enabling the protocol is not going to make your Android browsing completely anonymous from your Internet service provider (ISP)—for that, you’ll want to implement a virtual private network (VPN).


Do note that TLS over DNS will not lead to full privacy with the flip of a toggle. If a different DNS service provider you decide to connect to does opt to enable DNS over TLS, they’ll get your DNS traffic instead of your ISP. DNS requests will be encrypted, but the DNS over TLS server still gets to see your DNS traffic, though that alone might be a step above using your ISP’s servers without TLS over DNS. At least this way, your ISP won’t be able to attach your queries to the IP you’ve been assigned, and thus your name.

The handshake between servers via Server Name Indication (SNI) that allows for a connection to be established can still be seen by your ISP (and they can log it under your name). In order to fully hide yourself, then, you will need a VPN to route the DNS queries, which can otherwise be seen by your ISP, to a DNS over TLS server. As long as you trust your VPN provider, you should now be more hidden than ever on Android. So while this feature isn’t straightforwardly allowing you to be fully anonymous by virtue of having a DNS over TLS toggle, it does enable you to hide DNS requests from ISPs, and to hide requests and traffic if you are willing to put in some extra work.


Server Implementations
--------------

* [DNSCrypt-Wrapper](https://github.com/cofyc/dnscrypt-wrapper)

* Pre-build [Docker container](https://github.com/jedisct1/dnscrypt-server-docker) uses Unbound for DNS resolution and DNSCrypt-Wrapper to proxy dnscrypt.

* [Unbound](https://unbound.net/) by NLnetLabs, supports both DNS-over-TLS and DNSCrypt. Since Version 1.7.1 supports authentication of DNS-over-TLS using PKIX certificates!

* [dnsdist](https://dnsdist.org/) by PowerDNS, supports both DNS-over-TLS and DNSCrypt.

* [DoH-proxy](https://facebookexperimental.github.io/doh-proxy/) by Facebook, supports DNS-over-HTTP/2 (DoH).

* [rust-DoH](https://github.com/jedisct1/rust-doh) supports DNS-over-HTTP/2 (DoH).


Client
--------------

* [Cloudflare Running a DNS over HTTPS Client](https://developers.cloudflare.com/1.1.1.1/dns-over-https/cloudflared-proxy/)

* [Google Public DNS now offers DNS-over-HTTPS](https://groups.google.com/forum/#!topic/public-dns-discuss/rmZTtPAV430) DNSCrypt will not be supported because it's not an official RFC 


Implementation Status:
--------------

* Everything implemented in Android P except Unbound (the current situation will be discusses internally which caching mechanism will be used in the upcoming Android version).
* Google (Alphabet= released his official app called [Intra](https://getintra.org/?_escaped_fragment_=/) for Android 9 (Pie) which resolves DNS queries over DNS-over-HTTPS, it's backward compatible down to Android 4.0. The source code can be reviwed [here](https://github.com/Jigsaw-Code/intra).


Reference:

* https://medium.com/@JigsawTeam/introducing-intra-a-new-app-to-stop-dns-manipulation-f76de3f5d01
* https://security.googleblog.com/2018/04/dns-over-tls-support-in-android-p.html
* https://github.com/jedisct1/dnscrypt-proxy/issues/724
* https://github.com/laggardkernel/dnscrypt-proxy-magisk
* https://review.lineageos.org/#/q/topic:dnscrypt
* https://www.xda-developers.com/android-dns-over-tls-website-privacy/
* http://www.theregister.co.uk/2017/10/26/android_testing_dns_over_tls/
* https://dnsprivacy.org/wiki/
