---
author: pawal
categories:
- DFRI
- Integritet
- Säkerhet
date: 2015-01-30T10:34:07Z
guid: http://pawal.blipp.com/?p=37687
id: 37687
tags:
- övervakning
- dfri
- integritet
- iops
- wifi
title: MAC-adresser är personuppgifter?
url: /integritet/mac-adresser-ar-personuppgifter
---

*Den här artikeln är skriven till ett annat forum och är skriven för
<a href="https://www.dfri.se/">DFRI:s</a> räkning, men publicerades
aldrig.*

En mobiltelefon med Wifi påslagen skickar ut en unik signal som går
att avlyssna med enkel utrustning. Några som lyssnar på dessa signaler
är Bumbee Labs, som byggt ett system kallat IOPS. Syftet med systemet
är att mäta rörelsemönster i stadskärnor, och just nu testas det i
Västerås och Borås.

{{% flickr "IOPS" "IOPS antenn" "https://www.flickr.com/photos/pawal/15131281523/" "https://c1.staticflickr.com/8/7519/15131281523_729ed7a525_k.jpg" %}}

I systemet sparas telefonens unika identitet, den så kallade
<a href="http://sv.wikipedia.org/wiki/Hashfunktion">MAC-adressen</a>,
samt vilka platser den befunnit sig på och vid vilken
tidpunkt. Bumbee Labs hävdar att de inte sparar telefonens
MAC-adress, utan bara en kod som motsvarar den, och att det inte går
att räkna ut i efterhand vilken MAC-adress koden motsvarar.

Forskning visar dock att det lätt går att <a href="http://webpolicy.org/2014/03/19/questionable-crypto-in-retail-analytics/">göra baklängesberäkningar</a> för att ta reda på vilken
MAC-adress som koden motsvarar. Men egentligen spelar det ingen roll. Genom att över
tid titta på hur en telefon rör sig går det ändå att lista ut vilken
individ som äger den, oavsett om MAC-adressen är tydligt utskriven
eller bara motsvaras av en kod.

Det är också möjligt att missbruka systemet åt andra hållet. Genom att
själv ta reda på en persons MAC-adress och se vilken kod den motsvarar
i systemet kan man i datan sedan följa hur personen, tidigare eller i
framtiden, rör sig.

Att avidentifiera data är med andra ord ingen lätt uppgift. Tyvärr har
Bumbee Labs hittills inte gett oss någon information som tyder på att
de lyckats. Tvärtom har flera av deras uttalanden fått oss att tvivla
på att de förstår det grundläggande problemet.

När nu systemet byggs ut i stadskärnorna och efterfrågas av fler
städer, skapas alltså en gigantisk databas över inidviders nationella
rörelsemönster.

Vi tror inte att Bumbee Labs har för avsikt att övervaka individer,
men det blir ändå konsekvensen av systemet. Faktum är att alla typer
av storskalig datainsamling kan användas för att kartlägga individer
om inte all data är helt avidentifierad.

Vi anser inte att det är fel i sig att samla in statistik över
besöksströmmar, men insamlandet måste ske på ett sätt som inte kränker
människors grundläggande rätt till integritet.

Vi anser också att ett minimikrav på ett sådant system är transparens,
där alla som vistas i områden där kartläggningar pågår kan ta del av
den tekniska lösningen, källkod till systemet, databasinnehåll och den
statistik som tas fram. Utan dessa möjligheter kan vi inte veta om
systemet faktiskt lever upp till att skydda vår integritet. Istället
är vi hänvisade till uppgifter från företaget som ligger bakom.

Vår förhoppning är även att MAC-adresser, likt IP-adresser, som lagras
på det här sättet klassas som personuppgifter och behandlas
därefter. Allra minst ska det finnas tydliga skyltar om att
MAC-adresserna samlas in, i likhet med vad som gäller för
övervakningskameror.Något som är trivialt att bygga ut IOPS-systemet
med är att fånga upp fler av de signaler som läcker ut samma väg som
MAC-adressen. Många telefoner sänder också ut så kallade SSID:s för
att snabbt koppla upp sig till nät kan vara tillgängliga. Dessa SSID:s
kan avslöja var personen bor, vilket hotell man bott på och personens
arbetsplats. Detta har demonstrerats i system som <a href="http://www.sensepost.com/blog/7557.html">Snoopy</a> och
<a href="http://dangerousprototypes.com/2013/08/10/creepydol-wifi-surveillance-project-debuts-at-blackhatdefcon/">CreepyDOL</a>. Dessa
system kopplar effektivt ihop mobiltelefoninnehavarens MAC-adress med
andra databaser, och kan därmed med lite tur lätt identifiera en
individs hemvist. Det är trivialt för Bumbee Labs att bygga ut IOPS
med den här typen av funktionalitet. MAC-adressen blir en effektiv
länk mot andra databaser som effektivt kan identifiera individer. Det
är också lätt för andra som spanar efter en MAC-adress - arbetsgivare,
polis eller kriminella organisationer - att fråga Bumbee Labs om
rörelsemönster för en viss mobiltelefon. Särskilt problematiskt blir
detta då de inte redovisar hur företaget skyddar sin databas eller hur
länge de sparar data om din telefons rörelsemönster.
