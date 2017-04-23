---
author: pawal
date: 2010-12-03T10:32:11Z
guid: http://pawal.blipp.com/?p=13153
has_been_twittered:
- "yes"
id: 13153
tags:
- dns
- säkerhet
title: När DNS ljuger
url: /sakerhet/nar-dns-ljuger
---

Man kan väl minst sagt konstatera att DNS hamnat i fokus den senaste
veckan, inte minst i ljuset av Verisigns ompekningar av ett större
antal domäner, men också Wikileaks problem med att vara
tillgängliga. Senast ut med Wikileaks är att deras DNS-tjänst som
sköttes av <a href="http://www.everydns.com/">EveryDNS</a> <a
href="http://www.bbc.co.uk/news/world-us-canada-11907641">plockade
bort</a> wikileaks.org från sina namnservrar. Anledningen är att
namnservrarna utsattes för en DDoS-attack, vilket skulle få nästan
vilken leverantör som helst att ta bort det domännamn som är orsaken
till problemet, eftersom detta går ut över alla andra kunder.

Företaget <a href="http://www.renesys.com/">Renesys</a>, känt för sina
rapporter om olika aspekter av Internet, mer eller mindre bra, har i
en bloggpost <a
href="http://www.renesys.com/blog/2010/12/dns-when-governments-lie-2.shtml">skissat
på ett litet betygssystem</a> för hur DNS hanteras i olika länder. Vi
vet ju att man från operatörshåll i Sverige filtrerar visst
innehåll. Så hur illa är detta i Renesys betygssystem? Först listar
jag detta betygsystem här:

<dt>★★★★★</dt>
<p style="padding-left: 30px;">Entirely safe. Providers in this country respect DNS integrity and never rewrite DNS responses. Even if you mistype a domain, you get an obvious non-existent domain (NXDOMAIN) error message and not an advertisement. When asking questions you always receive the intended answers.</p>

<dt>★★★★</dt><p style="padding-left: 30px;">Mostly safe. <a href="http://en.wikipedia.org/wiki/DNS_hijacking#Use_by_ISPs">Providers in this country</a> are allowed to rewrite queries to unknown domains to make money, but otherwise they leave DNS alone.</p>

<dt>★★★</dt><p style="padding-left: 30px;">Use caution. In this country, DNS providers may be required to modify the recursive resolver responses in order to enforce local content laws.</p>

<dt>★★</dt><p style="padding-left: 30px;">Strong caution. In this country, ISPs may be required to modify the recursive resolver responses <em>in flight</em> in order to enforce local content laws. In other words, ISPs listen in on your requests and alter the responses, no matter which server you query.</p>

<dt>★</dt><p style="padding-left: 30px;">Danger. In this country, <em>root server responses</em> as well as recursive responses may be modified in flight, without warning, by any infrastructure providers.</p>

Så var hamnar Sverige på betygsskalan? Den filtrering som görs sker ju på frivillig basis, men där Rikskriminalen tar fram blocklistorna. Dessa blocklistor är dock inte offentliga. Jag skulle nog påstå att Sverige får ★★★★. Men detta kan ju snabbt ändras. Vi har ju inga lagar om att innehåll måste blockeras av operatörerna genom DNS.

Men som vanligt, kör din egen DNS om du inte litar på hur andra gör. Och använd DNSSEC för att detektera omskrivningar av DNS-svar. Vid DNSSEC-validering måste man dessvärre signera sina domäner med DNSSEC, och till en utbredd användning här har vi en bit kvar.