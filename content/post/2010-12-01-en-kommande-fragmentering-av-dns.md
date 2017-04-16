---
author: pawal
categories:
- DNS
- Hacks
- Svammel
date: 2010-12-01T22:34:44Z
guid: http://pawal.blipp.com/?p=12969
has_been_twittered:
- "yes"
id: 12969
title: En kommande fragmentering av DNS
url: /hacks/en-kommande-fragmentering-av-dns
---

Med anledningen av att den "amerikanska regeringen" (Immigration &amp; Customs Enforcement inom Department of Homeland Security) för snart en vecka bad Verisign peka om ett antal .com-domäner till en <a href="http://torrentfreak.com/u-s-government-seizes-bittorrent-search-engine-domain-and-more-101126/">spärrsida</a> liknande den som svenska ISP:er på frivillig basis implementerat mot barnpornografi, så har piratnördarna med <a href="http://p2pdns.baywords.com/2010/11/30/hello-world/">Peter Sunde</a> i spetsen skapat något slags initiativ för att bygga en P2P-baserad DNS-toppdomän, .p2p.

De krav (eller "mål") som man har med detta är att få till en toppdomän där innehållet inte går att filtrera på det sätt som gjorts ovan. Men för att ta ett mål i taget, från deras <a href="http://dot-p2p.org/index.php?title=Goals">wiki</a>:
<ul>
	<li>Undgå den "kontroll" som ICANN har idag. Ja, ICANN har inte särskilt mycket kontroll över ccTLD:er som t.ex. .se idag. De kan förstås tillsammans med <a href="http://www.ntia.doc.gov/">NTIA</a> ta bort .se från kartan, men det blir med största sannolikhet förhållandevis ganska komplicerade diplomatiska förhållanden mellan Sverige och USA då, samtidigt som ICANN förminskar sin egen roll genom minskat förtroende. Risken för detta är minimal. Att servera sina domäner under .com som drivs av ett amerikanskt företag har ju visat sig vara ödesdigert, men då borde slutsatsen vara att köra sina domäner under toppdomäner som har lagstiftning och myndigheter som man vet hur man uppför sig.</li>
	<li>Kryptera DNS-uppslagningarna genom mekanismer i P2P-lösningen. Visst, det är ju bra. Men allt som skjuts långt bort i nätet, och bygger på någon form av realtidskrypto sänker prestandan. Nu kan man ju argumentera för att med högre säkerhet och anonymitet, så kan man offra prestanda. Nu har P2P-nät mycket sämre prestanda än DNS ändå, så oavsett vad man gör så blir uppslagningarna långsammare än vanlig DNS. Dessutom vill man inte göra särskilt mycket avancerad krypto i sådana här protokoll, eftersom detta lätt leder till DoS-attacker riktade mot den som ska validera signaturer eller dekryptera information.</li>
	<li>Återanvända så mycket färdig bittorrent-kod som möjligt. Jag förstår inte varför detta ska vara ett mål, det känns som en teknikerlösning på ett teknikerproblem. Först designar man ett protokoll, sedan tittar man på om det finns färdig kod som kan lösa implementationsbiten.</li>
	<li>Stöd för .p2p i alla OS och applikationer, genom "open source". Ja, det är ju bra. Men det är inte så man designar protokoll. Man gör det genom att skriva extremt bra specifikationer som har flera oberoende implementationer, som faktiskt fungerar mellan varandra.</li>
	<li>Denna uppslagningsmekanism ska inte påverka det övriga DNS-systemet, och här vill man inte betraktas som ett malware. Bra. Men svårt att undvika, eftersom vem som helst kommer att prångla ut "Phree Warez for the .p2p-domainz!1!"-applikationer, eftersom detta inte kommer att ingå som en standardkomponent i ditt operativsystem.</li>
	<li>Zeroconf. Bra, men det är ju egentligen ingen protokollfråga, utan upp till den specifika applikationen att avgöra. Dessutom kan ju implementationen bara bli zeroconf i klientläge, knappast i den del som ska servera namn till .p2p-namnrymden.</li>
	<li>Uppslagningsmekanismen ska vara säker och krypterad (sista punkten, end2end...). Ja, why not. DNS är ju inte krypterat idag, även om det förekommit flera förslag på hur man gör detta. Och med DNSSEC kan du vara säker på att DNS-svaren inte är manipulerade.</li>
</ul>
Min betraktelse här är att kravspecifikationen på ett nytt DNS-liknande protokoll så här långt är väldigt luddiga. Det är en massa önskemål. Men ingen information om hur man publicerar namn, vilka nycklar man ska lita på, och vem som litar på vem. (Det finns något obegripligt om web-of-trust och GPG.) Men mycket <a href="http://dot-p2p.org/index.php?title=Distributed_decision_example">Alice and Bob</a> blir det.

Rick Falkvinge har ökat på förvirringen genom att hävda att <a href="http://rickfalkvinge.se/2010/12/01/cirkus/">DNS redan är fragmenterat</a>. Detta baserat på att man i Danmark har lagstiftat att operatörers resolvrar måste filtrera ut piratebay.org. Lösningen ovanför (vad den nu blir) kommer inte att lösa andra resolvrars DNS-filtrering. Här är lösningen givetvis att köra sin DNS-resolver själv. Men det måste man ju ändå om man ska få DNSSEC att skydda DNS-informationen hela vägen till klient-datorn. För det gör ni väl?

Jag är positiv till allt som utvecklar Internet och DNS. Men man löser inte diffusa problem med diffusa tekniska lösningar. Jag gissar att målet i förlängningen är att helt ersätta DNS, men att man vill börja med .p2p, eftersom det är något rimligare. Det är bra. Men då måste man modellera protokollet med vad DNS idag hanterar. Annars kommer det att bli något annat, och då ska man nog inte parasitera på DNS-namnrymden ens.