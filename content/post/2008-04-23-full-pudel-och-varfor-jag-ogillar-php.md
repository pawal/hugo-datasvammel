---
author: pawal
date: 2008-04-23T05:09:22Z
guid: http://pawal.blipp.com/?p=107
id: 107
tags:
- creeper
- php
title: Full pudel och varför jag ogillar PHP
url: /creeper/full-pudel-och-varfor-jag-ogillar-php
---

PHP är ett väldigt trevligt språk när man ska utveckla någonting kort
och enkelt för webben. Som att till exempel utveckla en applikation
som Creeper.

Creeper har dock med tiden börjat få lite problem med prestandan,
vilket jag löst på olika sätt, bland annat genom att använda XCache
för att inte låta PHP kompilera om varje PHP-sida för varje ynka
request. Vad jag också provat att optimera är denna kodsnutt (och nu
blir det tekniskt):

```php
      Array(
        min => 3256002816, # ip2long('194.18.169.0'),
        max => 3256003583, # ip2long('194.18.171.255'),
        name => 'Försvarets Radioanstalt FRA',
        short => 'forsvaret'
      )
```

Det jag optimerat är alltså att ta bort funktionen
<code>ip2long()</code> för att se om detta ger någon
prestandavinst. Det är dock oklart hittills om det lett till någon
förändring. Annat än <b>detta</b>:

<code>ip2long()</code> returnerar det heltal som finns i min och max
ovan. Problemet med PHP:s variabelhantering är att man aldrig vet
vilken datatyp som används. Hade jag kunnat bestämma att max och min
skulle vara <em>unsigned 32-bitars integers</em> hade detta
fungerat. Nu blir det unsigned int om jag använder
<code>ip2long()</code> men inte om jag skriver in heltalet i koden
själv. Efter att ha letat runt en stund verkar det som om
<code>heltal+0</code> hade fungerat och gett mig en <em>unsigned 32
bit integer</em>, men nu vågar jag inte prova detta utan har
konverterat tillbaka koden till att använda <code>ip2long()</code>.

Konsekvensen av allt detta då? Jo, alla myndigheter vars IP-adresser
fyllt ut alla 32 bitar har blivit minustal. Detta gör att alla
jämförelser med tal som jag sedan konverterar med
<code>ip2long()</code>, dvs tal jag får via klientens IP-adress, inte
fungerar eftersom värdena helt förändrats. Så då har alltså dessa
myndigheter sett ut att försvinna från Creeper. Vi får se om loggen
fylls upp av lite mer korrekt information nu.

Jag trodde naturligtvis att min kod fungerade utmärkt efter denna
optimering och konstaterade att en <code>serialize()</code> på min
array med IP-adresser gav samma resultat (den innehöll samma tal
åtminsone). Detta är dock ett projekt jag aldrig skrivit några
automatiserade tester på. Hade jag gjort det hade jag hittat detta fel
omgående.

Någon som har ett förslag på ett *bättre programmeringsspråk*
att skriva enkla små webbapplikationer med? Perl har jag god
erfarenhet av, men det blir snabbt knöligt att få in en massa
Perl-applikationer i en Apache som driver ett 50-tal webbsajter.
