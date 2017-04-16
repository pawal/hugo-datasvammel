---
author: pawal
categories:
- Integritet
- Journalister
- Säkerhet
date: 2007-02-21T11:18:20Z
guid: http://pawal.blipp.com/integritet/svt-skickar-sin-e-post-utomlands
id: 68
title: SVT skickar sin e-post utomlands
url: /integritet/svt-skickar-sin-e-post-utomlands
---

Rubriken kanske inte är så uppseendeväckande vid första anblicken. Men det borde den vara. Skickar någon ett litet mail till SVT, kanske med tips om en het nyhet eller liknande, så skickas det nämligen en sväng via Westerham, Kent i England, efter att ha passerat London en sväng. Mottagare av e-posten är emailfiltering.co.uk, ett företag som säljer hantering av e-post.

<pre>svt.se.    2581    IN MX 10    mx1-svt-se.emailfiltering.com.
svt.se.    2581    IN MX 20    mx2-svt-se.emailfiltering.com.
svt.se.    2581    IN MX 30    mx3-svt-se.emailfiltering.com.</pre>

I ljuset av diverse <a href="http://www.svd.se/dynamiskt/blogg/did_14548472.asp?ID=2817">FRA-diskussioner</a> om avlyssning osv, blir det extra bekymmersamt eftersom tyngdpunkten kommer att ligga på trafik som går utanför Sveriges gränser. Extra grädde på moset får man eftersom trafiken till svt.se numera också kan avlyssnas av utländsk underrättelsetjänst.

Nu är det så att man normalt sett inte vet vilken väg trafiken mellan två datorer tar, men när man explicit skickar okrypterad e-post via utlandet har man knappast tänkt på någon personlig integritet alls. Slutsatsen man lätt drar av detta är att man borde kryptera all e-post som är det minsta känslig. Det har vi vetat länge, men risken för att bli avlyssnad inom Sverige har ju hittills varit relativt begränsad.

<em>Uppdatering:</em> TT rapporterar via <a href="http://www.svd.se/dynamiskt/inrikes/did_14677149.asp">SVD</a>, <a href="http://www.gp.se/gp/jsp/Crosslink.jsp?d=361&a=328091">GP</a> och <a href="http://hd.se/ekonomi/2007/02/21/myndighet-kan-faa-laesa-svt-mejl/">hd.se</a> om detta.