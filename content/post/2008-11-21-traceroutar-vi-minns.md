---
author: pawal
date: 2008-11-21T18:02:57Z
guid: http://pawal.blipp.com/?p=133
id: 133
tags:
- ipv6
title: Traceroutar vi minns
url: /ipv6/traceroutar-vi-minns
---

Jag sitter just nu på hotellrummet i Minneapolis, där IETF just nu
pågår. Jag har packat färdigt och är på väg till flygplatsen, men har
några minuter på mig. Så varför inte kolla vad det är för nät jag
sitter på?

<pre>randombot$~&gt;traceroute6 vic20.blipp.com
traceroute6 to vic20.blipp.com (2001:16d8:ff00:2a9::2) from 2001:df8::64:21f:5bff:fec4:a415, 30 hops max, 12 byte packets
 1  2001:df8:0:64::3  2.893 ms  15.19 ms  2.083 ms
 2  2001:df8:0:4::2  2.817 ms  1.828 ms  2.441 ms
 3  2001:468:1900:5::2  1.868 ms  1.935 ms  2.458 ms
 4  ge-2-0-0.2054.rtr.chic.net.internet2.edu  205.72 ms  202.649 ms  202.527 ms
 5  so-1-3-0.0.rtr.newy32aoa.net.internet2.edu  42.037 ms  42.07 ms  42.86 ms
 6  2001:450:2008:21::1  96.719 ms  101.818 ms  107.693 ms
 7  2001:450:2002:17::2  192.795 ms  197.35 ms  192.935 ms
 8  v1316-r84.cr0-r87.hy-sto.se.ip6.p80.net  193.431 ms  196.41 ms  192.908 ms
 9  sixxs-hy-demarc0.cust.ip6.p80.net  193.71 ms  193.279 ms  193.783 ms
10  cl-682.sto-01.se.sixxs.net  194.929 ms  197.617 ms  194.349 ms</pre>

Jämför med IPv4-motsvarigheten:

<pre>randombot$~&gt;traceroute vic20.blipp.com
traceroute to vic20.blipp.com (217.75.101.38), 64 hops max, 40 byte packets
 1  rtra-guestroom.meeting.ietf.org (130.129.64.2)  4.332 ms  3.237 ms  1.644 ms
 2  telecomb-gr-01-v152.ggnet.umn.edu (192.35.86.218)  2.230 ms  1.681 ms  1.446 ms
 3  mtc-gr-01-ten-3-1.northernlights.gigapop.net (146.57.252.134)  1.479 ms  2.085 ms  3.525 ms
 4  66.162.50.105 (66.162.50.105)  5.412 ms  3.790 ms  5.023 ms
 5  peer-02-so-0-0-0-0.chcg.twtelecom.net (66.192.244.20)  14.303 ms  13.342 ms  14.251 ms
 6  port80.ge-2-0-0.407ar1.ARN1.gblx.net (207.138.144.102)  137.025 ms  137.357 ms  136.748 ms
 7  ge1-0.dr1.hy-sto.se.p80.net (217.75.108.8)  137.143 ms  137.557 ms  137.212 ms
 8  fw1.webtajm.net (217.75.101.2)  137.868 ms  137.602 ms  138.350 ms
 9  vic20.blipp.com (217.75.101.38)  138.253 ms  139.151 ms  138.188 ms</pre>

Det finns några detaljer som skiljer dessa båda traceroutar
åt. Förutom det uppenbara att det är två olika protokoll vi pratar
om. En av sakerna är ju antalet hopp på väg till destinationen. För
IPv4 är det nio hopp, medan det för IPv6 är 10 hopp. Men det är bara
en illusion, på destinationen vic20.blipp.com kör jag nämligen en
IPv6-tunnel från <a href="https://www.sixxs.net/">sixxs.net</a>,
vilket innehär att från sixxs.net-tunneln kör IPv4 hela vägen in till
min vic20. Så antalet riktiga hopp har jag helt enkelt ingen aning om,
eller vilken väg mina IPv4-paket egentligen färdas.

En annan sak som skiljer är baklängesuppslagningen på
IP-adresserna. För IPv4-versionen är det bara en IP-adress som saknar
baklängesuppslagning. På IPv6-versionen är det fem! Och det är
ovanligt bra. Jag inbillar mig att situationen långsamt blir bättre,
ju mer folk bryr sig om sina IPv6-nät.

Ytterligare en sak som skiljer är latensen. Den skiljer sig inte så
hemskt mycket åt. Det är på en IPv6-länk som jag får lång svarstid, i
övrigt så ligger ju tunnlad IPv6 självklart något högre än IPv4.

Nej, dags att ta sig till flygplatsen.