---
author: pawal
categories:
- Hacks
date: 2007-01-06T00:00:12Z
guid: http://pawal.blipp.com/hacks/galet-perl-misstag
id: 64
title: Galet Perl-misstag
url: /hacks/galet-perl-misstag
---

Så här brukar man skriva hashar i Perl:
<pre>my $hash = {
    key1 =&gt; 'foo',
    key2 =&gt; &bar,
    key3 =&gt; 'baz'
};</pre>
Nu är det så att man inte alltid vet hur funktionen &bar returnerar sitt data. Om man inte vet det kan det hända att ovanstående hash inte resulterar i den hash man tror att man ska få. Om &bar returnerar data med en <code>wantarray</code> så ska man veta att när man skriver funktionsanrop i en hash, så befinner man sig i <em>list-context</em>. Det betyder att man rätt som det är kan få två eller fler värden returnerade från funktionen &bar. Om man vet att skrivningen "=&gt;" i en hash bara är syntaktiskt socker för ett komma-tecken så betyder det att något så otroligt kan hända att key3 blir ett värde till en nyckel som returneras från &bar.

Allt detta låter naturligtvis helsnurrigt, men det är sant. Man kan hamna i många timmars felsökning, men nu har jag råkat ut för det flera gånger, så jag vet vad ska ska akta mig för... Egentligen kan man tycka att det är en bugg i Perl, och att "=&gt;" borde resultera i ett <em>scalar context</em>, men jag kan för lite Perl-internals för att tycka rätt saker.