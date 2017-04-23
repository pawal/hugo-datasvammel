---
author: pawal
date: 2006-11-13T22:24:18Z
guid: http://pawal.blipp.com/hacks/spam-spam-spam-och-bildanalys
id: 60
tags:
- hacks
- spam
title: Spam, spam, spam, och bildanalys
url: /hacks/spam-spam-spam-och-bildanalys
---

De senaste veckorna har mängden spam som min stackars SpamAssassin
inte lyckats märka upp korrekt ökat väldigt mycket. Dessa spam som
verkar vara skrivna av en blivande vogonpoet innehåller förutom
rappakalja även en bild. Denna bild innehåller det egentliga
meddelandet, oftast text som ska locka till köp av så kallade <i>penny
stocks</i>. Man kan väl lugnt säga att jag tröttnade på att trycka på
delete-knappen, och istället letade efter en lösning. Och det fanns
en! Så nu är jag en lycklig användare av <a
href="http://fuzzyocr.own-hero.net/">FuzzyOcr</a>, en plugin till
SpamAssassin som gör en bildanalys av bilden, och kollar om den
innehåller förbjudna ord (gissa vilka). FuzzyOcr använder sig av
bildigenkänningsprogrammet <a
href="http://jocr.sourceforge.net/">gocr</a> som jag tidigare
lyckosamt använt för att tolka telefonnummer på Blocket.

I övrigt verkar spam-mängden bara öka och öka. Och min server-CPU
jobbar mer och mer för att känna igen de spam som till slut hamnar i
min skräpkorg. Ju fler människor med bra bandbredd och dålig säkerhet
på sina Windows-installationer, desto fler spam. I väntan på en bra
lösning för att helt få bukt med spam kan man flukta in och se hur
dålig affär man kan göra med <i>penny stocks</i> hos <a
href="http://www.spamstocktracker.com/">Spam Stock Tracker</a>.