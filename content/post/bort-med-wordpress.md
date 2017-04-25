---
author: pawal
date: 2017-04-25T20:16:29+02:00
tags:
- wordpress
- php
- letsencrypt
- kakor
title: Bort med Wordpress och PHP
url: /svammel/bort-med-wordpress
---

Mitt *nyårslöfte* i år var att bli av med Wordpress. Ja, tro det eller
ej, men den typen av nyårslöften kan jag i alla fall försöka hålla.

Anledningen till att få bort Wordpress är relativt enkel, den gör det
inte enkelt för mig att blogga. Jag skriver helst inte text i
fancy-schmancy-verktyg, utan gärna rått i en ren texteditor i format
som Markdown. Dessutom börjar det bli rätt hårigt att underhålla
verktyg som Wordpress eftersom man måste stå på tårna och uppgradera
så fort det kommer en ny version eller sårbarhet. Att dessutom få
Wordpress att inte sätta några *kakor* är också rätt krångligt.

Så därför har jag letat efter vettiga verktyg för att generera
statiska webbsajter. Och jag har hittat ett,
[Hugo](https://gohugo.io/). Väldigt lätt att hantera, och kan rendera
hela den här bloggen på *cirka 160ms* på den maskin där jag kör
den. Det är ganska fort. Så snabbt bloggar inte jag, vilket märks om
man tittar på [mina inlägg](/post/). Mest intensivt bloggade jag
kanske mellan 2005 och 2008.

Dessutom ville jag stöka om på mitt hemmanät, och exponera några
tjänster ut, bl.a. över HTTP(S). Då fick jag bygga om lite för att
skapa en extern HTTP-proxy. Denna proxy genererar dessutom [Let's
Encrypt](https://letsencrypt.org/)-certifikat för de tjänster som
behöver det, och sedan skickar de in trafiken till tjänster som hostas
i kvm:er. Nu är proxyn en Nginx, och jag använder
[acmetool](https://github.com/hlandau/acme) för att underhålla
certifikaten. Dock blev jag sugen på att använda
[Caddy](https://caddyserver.com/) som proxyserver istället, då den
dels verkar riktigt bra, och dels har inbyggt stöd för Let's Encrypt.

Den här bloggen genereras på samma gamla Wordpress-instans, men nu som
statisk HTML. Det går som jag nämnt väldigt fort att rendera sajten
statiskt. Men som bonus har jag minimera ytan för sårbarheter
avsevärt. Buggar i PHP, Wordpress eller alla dessa Wordpress-tillägg
behöver jag inte längre bry mig om. Och backup kan jag mycket enkelt
göra genom att lagra källan till bloggen som ett git-repo, och
publicera helt öppet på
[Github](https://github.com/pawal/hugo-datasvammel). Eftersom inget i
denna backup innehåller några hemliga element är detta trivialt.

Det var svårare att göra backup med en Wordpress-instans eftersom
Wordpress lagrar data i två skilda världar, dels MySQL (redan där
borde jag ha avvecklat Wordpress för länge sen), och dels i
filsystemet. Och inte nog med det lagras det ju också lösenord där,
för saker som administratörer, användare och inloggning till MySQL.

Men att byta från Wordpress till något annat är inte helt enkelt,
särskilt inte om man vill bevara gammalt innehåll. Nu finns det en del
verktyg för att dra ut innehåll ur en gammal Wordpress - men inte
direkt till en Hugo-instans. Det gick dock att dra ut det som
Jekyll-data, och för Hugo finns det en Jekyll-importer, så det blev
lösningen den här gången. Det betyder dock inte att allt innehåll
dyker upp felfritt.

Att gå in och manuellt granska och anpassa innehållet var faktiskt det
som tog mest tid. Wordpress använder ju HTML som markup, vilket
Markdown faktiskt hanterar.

När man går igenom en dump som den jag gjorde från min Wordpress, som
varit igång sedan 2005 (12 år!) så märker man hur mycket som ändrats
under ytan på Wordpress. Inlägg som gjorts har formatterats på en
uppsjö olika sätt. Nu har jag inte ändrat all HTML till Markdown, för
det orkar jag inte, och det mesta fungerar ändå. Men att göra ett
försök till att genomföra en konvertering med automatik vore dömt att
misslyckas.

Så, nu återstår bara att skapa ett enklare flöde för publicering av
nya inlägg. Läser ni det här har jag åtminstone gjort ett lyckat
första försök.

Helt borta från PHP är jag inte, det finns ju
bl.a. [Gnuheter](https://www.gnuheter.com) som behöver en del
vård. Och [Creeper](https://gnuheter.com/creeper/) behöver en hel del
uppdateringar ändå.

Nu saknar jag ingenting från Wordpress egentligen. Men det innehåll
som inte följde med den här konverteringen var *kommentarer*. Skönt
egentligen. Det vanliga är att man sätter upp Disqus tillsammans med
Hugo för att slippa egen teknik, men jag vill inte ladda alltför många
externa resurser till denna sajt. Jag känner inte till Discus
egentliga affärsmodell, eller ens vem som äger dem. Ett lockande
alternativ är att använda Github Issues som kommentarer, som [Don
Williamson skrivit om](http://donw.io/post/github-comments/). Men
egentligen behövs de inte tycker jag.

Eller vad tycker du..?
