---
author: pawal
date: 2014-06-24T22:49:25Z
guid: http://pawal.blipp.com/?p=37670
id: 37670
tags:
- dns
- öppen källkod
title: Många alternativa programvaror för DNS
url: /dns/manga-alternativa-programvaror-for-dns
---

Nästan alla kör <a href="http://www.isc.org/downloads/bind/">BIND</a>
från <a href="http://www.isc.org/">ISC</a> för sin DNS. Så är det
bara. Men det finns många nya alternativa namnservrar som är minst
lika bra, och som inte lider av det kod-arv som BIND 9 gör. BIND har
skrivits om från grunden två gånger i modern tid, först från BIND 4
till BIND 8, och sedan till BIND 9. Ett tredje försök har gjorts under
de senaste åren från ISCs sida, nämligen med det <a
href="https://ripe68.ripe.net/presentations/208-The_Decline_and_Fall_of_BIND_10.pdf">havererade
BIND 10-projektet</a>. ISC har dock varit väldigt öppna med hur och
varför projektet havererade, och det är bara att konstatera att vi
kommer att få dras med BIND 9 ett väldigt långt tag framöver.


![Knot-DNS](https://www.knot-dns.cz//images/logo.svg)

Men under de senaste åren har ett par riktigt bra alternativ till BIND
tagits fram av andra aktörer. Min favorit för auktoritativ DNS är <a
href="https://www.knot-dns.cz/">Knot DNS</a> från <a
href="http://www.nic.cz/">CZ.NIC</a>. Som också ISC själva säger,
framtida DNS-innovation kommer sannolikt att komma från andra aktörer
än ISC. Ett av de nuvarande problemen med BIND är att den försöker
göra <em>allt</em>. Den är både <em>auktoritativ namnserver</em>, och
<em>cacheande resolver</em>, och säkert mycket annat också
samtidigt. Knot DNS är "nästan bara" en auktoritativ namnserver. Men i
nuvarande versioner har de även lagt till online-signering för DNSSEC,
och kommer att i version 1.6 komma närmare <a
href="http://www.opendnssec.org/">OpenDNSSEC</a> vad gäller
hanteringen för nyckelsigneringspolicy - något som andra
DNS-programvaror saknar helt. Man håller också på att byta från
OpenSSL till GnuTLS, dels av <a
href="http://heartbleed.com/">kända</a> <a
href="http://opensslrampage.org/">anledningar</a>, och dels för att
GnuTLS har betydligt bättre stöd för <a
href="http://en.wikipedia.org/wiki/PKCS_11">PKCS#11</a>, något som
krävs om man vill använda <a
href="http://en.wikipedia.org/wiki/Hardware_security_module">HSM:er</a>. Vidare
har man även möjlighet att köra sina egna moduler för att utföra
dynamisk hantering av DNS-svar, och för IPv6 kan man exempelvis också
dynamiskt generera <em>reverse</em>-svaren för IP-adresserna. Se gärna
<a
href="https://ripe68.ripe.net/presentations/262-KNOT-20140514-RIPE68.pdf">presentationen</a>
från RIPE68.

Själv har jag kört Knot DNS ett långt tag på en av mina egna
namnservrar. Den är både betydligt enklare att konfigurera, men den
har också betydligt bättre prestanda än BIND. Något som jag förvisso
inte har något större behov av, eftersom mina domäner inte drar
särskilt mycket trafik. Som ett alternativ till Knot DNS finns också
självklart <a href="http://www.nlnetlabs.nl/projects/nsd/">NSD 4</a>
från <a href="http://www.nlnetlabs.nl/">NLNet Labs</a>, som har
funnits betydligt längre, och används kanske mest av TLD:er idag - men
också <a href="http://www.yadifa.eu/">Yadifa</a> från <a
href="http://www.eurid.eu/">EURid</a>.

<img class="aligncenter" src="http://unbound.net/gx/unbound-250.png" alt="Unbound" width="250" height="125" />

För att köra en <em>cacheande resolver</em> så kan man med fördel
använda <a href="http://unbound.net/">Unbound</a>, också från NLNet
Labs. Unbound har också givetvis fördelarna med att den är betydligt
enklare att konfigurera, och har betydligt högre prestanda än BIND. En
cacheande resolver kör man med fördel med DNSSEC påslaget för
DNSSEC-validering, så nära de tjänster man har som behöver lita på DNS
(det är i princip samtliga internet-tjänster).

Om man känner sig lite osäker på att behöva byta från BIND kan man
kanske titta på antalet <a
href="https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=ISC+BIND">kända
sårbarheter</a>... Och som med alla monokulturer, de är sårbara för
breda attacker. Därför är det också bra att börja köra alternativa
programvara. Gärna på någon udda  CPU-arkitektur, så att inte alla kör
Intel.

**(Jag har fullständigt medvetet inte skrivit om programvaror som inte är öppen källkod.)**
