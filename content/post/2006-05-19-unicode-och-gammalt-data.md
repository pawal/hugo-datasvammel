---
author: pawal
date: 2006-05-19T10:27:16Z
guid: http://pawal.blipp.com/linux/unicode-och-gammalt-data
id: 44
tags:
- linux
title: Unicode och gammalt data
url: /linux/unicode-och-gammalt-data
---

<img align="right" alt="Unicode" title="Unicode" class="alignright"
src="https://blipp.com/misc/unicode.png" />Jag har som jag <a
href="https://pawal.blipp.com/linux/utf-8-overallt">skrivit förut</a>
beslutat mig för att helt gå över till UTF-8. Mina desktop-miljöer kör
sedan dess helt och hållet UTF-8, men jag har fortfarande inte orkat
konvertera filsystemen. Vad jag dessutom upptäckte var en hel drös med
webbsidor som fortfarande är kodade i Latin-1. Vilket gör att det blir
jobbigt att uppdatera dem. Någon strategi för konvertering där har jag
inte ännu.

En lustig grej var hela min Apache-konfiguration på vic20, som globalt
tyckte att allting är Latin-1. Det gjorde det en aning jobbigt att
släppa <a href="https://www.gnuheter.com/">Planet Gnuheter</a> på samma
"nivå" som <a href="https://www.gnuheter.com/oldgnuheter.php">gamla
Gnuheter</a>, då den gamla kör Latin-1 och planeten kör UTF-8. Och det
fungerade inte att sätta HTML-headers *heller*. Den globala
Latin-1-inställningen tyckte man ju skulle vara lätt att byta ut mot
UTF-8, men det drabbade ju alla 40 webbplatser jag hostar... Så jag
slog helt enkelt av den globala teckenuppsättningsväljaren, och hoppas
att allt fungerar. Så Gnuheter.com kör blandat UTF-8 och Latin-1. Min
gamla usla hemsida får tills vidare köra Latin-1, men det gör det till
exempel jobbigt att sköta min fina <a
href="https://blipp.com/pawal/diary/">fotoblogg</a> eftersom den
bygger på att jag har ett script på min desktop som jag kan släppa
bilder på, och som frågar efter en bildbeskrivning. Detta görs förstås
i UTF-8 nu.

Och som lite extra grädde på moset så hanterar **fortfarande inte**
Perl-modulen DBD::mysql UTF-8. Undrar när MySQL tänker fixa det...