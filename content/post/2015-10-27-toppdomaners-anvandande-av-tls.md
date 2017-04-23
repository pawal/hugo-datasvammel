---
author: pawal
date: 2015-10-27T20:17:42Z
guid: https://pawal.blipp.com/?p=37711
id: 37711
tags:
- dns
- säkerhet
- svammel
- domäner
title: Toppdomäners användande av TLS
url: /sakerhet/toppdomaners-anvandande-av-tls
---

Jag gjorde en snabb körning på hur det ser ut med TLS hos våra
toppdomäner i världen. Med den nuvarande tillväxten av nya toppdomäner
har vi idag 1082 delegerade toppdomäner i root, och det växer sakta
tills dess att ICANN har delegerat alla nya toppdomäner.

Eftersom vi vill att TLS ska finnas på alla webbsajter är det
intressant att se hur toppdomäner skyddar sin kommunikation med
allmänheten. Så min första enkla analys är att helt enkelt se vilken
URL man registrerat hos IANA, och se om de har https som default. IANA
har en WHOIS-databas för toppdomänerna där man kan registrera sin
webbsida. Detta har 1010 av 1082 toppdomäner gjort, dvs 93% av alla
toppdomäner.

Men sedan kommer det lite nedslående resultatet. Tittar jag efter
https i resultatet så är det bara 23 registryn som registrerat en
webbsida med HTTPS:

|TLD | URL
|:---|:---
am.|https://www.amnic.net/
ar.|https://nic.ar
bank.|https://www.ftld.com/
bw.|https://registry.nic.net.bw
cfa.|https://www.cfainstitute.org
cloud.|https://www.getdotcloud.com
fi.|https://domain.fi
frl.|https://registreer.frl
id.|https://register.pandi.or.id
iq.|https://registrar.cmc.iq
jo.|https://www.dns.jo/login.aspx
lds.|https://www.lds.org
lidl.|https://www.nic.lidl
mo.|https://www.monic.mo
mp.|https://get.mp/
mt.|https://www.nic.org.mt/
nl.|https://www.sidn.nl/
schwarz.|https://www.nic.schwarz
trust.|https://nccgroupdomainservices.com
xn--j1amh.|https://namestore.u-registry.com
xn--tckwe.|https://www.verisigninc.com
xn--y9a3aq.|https://www.amnic.net/
zm.|https://registry.zicta.zm</blockquote>

Dvs, enbart 2% av alla toppdomäner har registrerat en webbsida som
skyddas av HTTPS. En närmare analys ger förhoppningsvis ett bättre
resultat, då man kanske glömt att registrera en webbsida med https
istället för http.

Script:

https://gist.github.com/anonymous/efe3f122c0e091868ff2

Hela resultatet hos <a href="http://pastebin.com/ZMd7WkeV">Pastebin</a>.

&nbsp;