---
author: pawal
categories:
- DNS
- IETF
- Integritet
- Säkerhet
date: 2014-05-21T14:28:52Z
guid: http://pawal.blipp.com/?p=37667
id: 37667
title: DNS Privacy &#8211; krypterad DNS
url: /ietf/dns-privacy-krypterad-dns
---

I en serie poster tänkte jag nu framöver posta lite mer renskrivna texter om DNS från mina anteckningar på olika internet-konferenser. Jag hoppas detta kan vara till glädje för någon som är intresserad av vad som händer i DNS-världen.

DNS har funnits i drift i över 25 år. Det är bara under de senaste 15 åren som säkerhet i protokollet diskuterats, och 2005 gick RFC:erna för DNSSEC genom IETF. Men kravet i protokollet för att skydda den personliga integriteten har aldrig funnits - förrän under det senaste året.

Med anledning av Edward Snowdens avslöjanden så har IETF sakta börjat se över de protokoll som IETF i någon form ansvarar för, och med publiceringen av <a style="color: #4183c4;" href="https://tools.ietf.org/html/rfc6973" rel="noreferrer">RFC 6973</a>, "Privacy Considerations for Internet Protocols" så kan man säga att arbetet satt igång på allvar. Inom IETF har man också satt upp en mailinglista för att diskutera "pervasive surveillance" med ett lite bredare perspektiv, <a style="color: #4183c4;" href="https://www.ietf.org/mailman/listinfo/perpass" rel="noreferrer">perpass@ietf.org.</a>

Gamla protokoll designades i en annan tidsålder, innan övervakning var på agendan. Dessa protokoll läcker mycket för mycket metadata (och data). Men det finns många begränsningar i dessa protokoll som kan förhindra eller försvåra att man gör tillägg för att gynna den personliga integriteten såsom latency, stabilitet och att protokollen blivit universella.

En DNS-fråga avslöjar vem som frågar, och vad som frågas efter. Detta underminerar säkerheten i andra protokoll, som till exempel HTTPS. Vad finns då i qname-delen av en DNS-fråga? "www.political-party.example", eller "_bittorrent-tracker._tcp.domain.example" - MPAA kan vara intresserade. "le-pc-de-pascal.domain.example" - personlig information, eller t.ex. PGP-nycklar i DNS. Helt enkelt saker som avslöjar saker om ditt internet-beteende som de protokoll du använder dig av normalt kanske skyddar - men där informationen skickas i klartext i DNS. Detta beteende i DNS vill man ju ändra på.

Vi behöver en lösning för att skydda informationen "on the wire" och "på servern". Resolvrar kan också läcka information genom t.ex. sysadmins, och en cache innehåller också all denna information i klartext. Att skydda DNS-informationen på protokollnivå kräver dock ändå olika lösningar, en för att skydda klient-kommunikationen mot en resolver, och en annan för att skydda kommunikationen från en resolver till auktoritativa namnservrar.

Från att ha diskuterats på perpass flyttade diskussionen till dnsop, och nu är flyttad till en egen dnsprivacy-lista. Det finns en möjlig lösning implementerad (men inga andra), DNSoverTLSoverTCP. Ingen officiell working group ännu, men vem som helst kan ändå posta förslag till IETF.

Problem statement: <a href="http://tools.ietf.org/html/draft-bortzmeyer-dnsop-dns-privacy-02">draft-bortzmeyer-dnsop-dns-privacy</a> - problemet behöver dokumenteras innan man kan lösa det...

Minimizing the qname - fulla frågenamnet behöver inte skickas till auktoritativa namnservrar högre upp i hierarkin. Detta går att implementera i Unbound och BIND, men ingen har gjort det ännu. Påverkar DNS-OARC och DITL, eftersom informationen att göra forskning på minskar. Vilket ju också är lite av poängen...

Tyvärr förekommer det alldeles för lite diskussion om dessa förslag på listorna, och intresset verkar lågt (trots riktigt stora möten på IETF). Att förändra DNS är också väldigt svårt.

Efter förra helgens DNS-OARC-möte skickade Paul Vixie ett mail till IETF:s dnsop-arbetsgrupp och uttalat sitt stöd för minimering av innehållet i frågorna, så det arbetet kanske tar lite fart igen.