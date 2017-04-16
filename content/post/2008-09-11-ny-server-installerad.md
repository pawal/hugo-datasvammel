---
author: pawal
categories:
- Creeper
- Hårdvara
- Linux
date: 2008-09-11T01:00:52Z
guid: http://pawal.blipp.com/?p=126
id: 126
title: Ny server installerad
url: /hardvara/ny-server-installerad
---

Nu har jag installerat en helt sprillans ny Quad Core Xeon-maskin för den server bland annat tjänsten Creeper kör på.

Som ni förmodligen har märkt under sommaren så har Creeper och andra tjänster jag kör haft märklig nertid under vissa perioder. Detta har berott på att servern som jag kört allting på har mått allt sämre. Med min nya fina hårdvara borde dessa problem vara åtgärdade. Den gamla trotjänaren hade körts i drygt 4,5 år, så det var Verkligen Dags för en uppgradering på hårdvarufronten.

Själva flytten av innehållet i maskinen börjar jag få rutin på. Den gamla maskinen kraschade dock två gånger under flytten, så det långsamma momentet att flytta <code>/home</code> var det som verkligen tog tid. Det enda uppenbara felet med uppstarten av den nya hårdvaran var SASL-autentiseringen för Postfix. Det tog en stund att felsöka. Men annars verkar ju allting flyta på bra.

Nu får jag nog sova en stund.

Och sluta fundera på vad jag har missat. Vilka cron-job kördes egentligen? Och så vidare...

<strong>Just det!</strong> Nu finns det prestanda nog så att Creeper ska kunna klara av <em>ännu flera övervakare</em>! Har du ännu inte börjar spåra dina besökare med Creeper är det nog dags nu... Jag vill se vad den nya hårdvaran klarar av!