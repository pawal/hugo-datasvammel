---
author: pawal
tags:
- creeper
- mjukvara
- programmering
- php
date: 2010-03-01T10:18:48Z
guid: http://pawal.blipp.com/?p=183
has_been_twittered:
- "yes"
id: 183
jd_tweet_this:
- "yes"
title: Att smyga in funktioner
url: /mjukvara/att-smyga-in-funktioner
wp_jd_clig:
- http://cli.gs:80/nnXhe
wp_jd_target:
- http://pawal.blipp.com/mjukvara/att-smyga-in-funktioner?utm_campaign=UA-264167-1&utm_medium=twitter&utm_source=twitter
---

En enda liten skillnad i en uppgradering från PHP 5.3.0 till 5.3.1
gjorde att Creeper inte längre fungerade. Jag fick ett meddelande om
att Creeper inte längre visade några resultat, och det tog en stund
att komma på vad felet var, och varför det hade uppstått.

De finurliga människorna bakom PHP tycker att det är en bra idé att
föra in nya reserverade ord lite då och då. I Creeper har (numera
hade) jag en funktion som heter getHostname som hämtade hostnamn-delen
av HTTP-referern som jag vidarebehandlar. Om man lusläser <a
href="http://www.php.net/ChangeLog-5.php#5.3.1">changeloggen för PHP
release 5.3.1</a> hittar man denna obetydliga rad:

```sh
Added gethostname() to return the current system host name. (Ilia)
```

Maken till featurecreep har jag sällan skådat. Kan man inte hålla sig
till major-releaser innan man inför sådana här galenskaper? Hur gör
folk för att hålla sina PHP-applikationer stabila över tid, när marken
under dem gungar så här?