---
author: pawal
categories:
- Identitet
- Mjukvara
- Säkerhet
date: 2010-01-26T20:57:08Z
guid: http://pawal.blipp.com/?p=177
id: 177
jd_tweet_this:
- "yes"
title: Lathet och OpenID
url: /identitet/lathet-och-openid
wp_jd_clig:
- http://cli.gs:80/Yq4GT
wp_jd_target:
- http://pawal.blipp.com/identitet/lathet-och-openid?utm_campaign=UA-264167-1&utm_medium=twitter&utm_source=twitter
---

Jag ville ha en OpenID-inloggning. En egen. Detta har dröjt ett tag, eftersom jag inte har orkat leta efter vettiga implementationer av en OpenID-server. Och så har naturligtvis andra saker prioriterats.

Men idag fick jag ork att leta lite efter om det fanns några genvägar. Och jag ville inte använda lösenord, utan hellre klient-certifikat från <a href="http://cacert.org/">cacert.org</a>. Så vid en snabb sökning så hittade jag tjänsten <a href="https://certifi.ca/">certifi.ca</a> som just enbart är en OpenID-provider för folk med cacert. Prima. Men jag ville ju inte egentligen knyta upp mig mot deras tjänst, utan ta höjd för att köra på egen hand framöver. Så vad jag gjorde var att skaffa konto hos certifi.ca, och sedan så la jag till följande på min blipp.com-domän:
<pre>&lt;link rel="openid.server" href="http://certifi.ca/_serve" /&gt;
&lt;link rel="openid.delegate" href="http://certifi.ca/pawal" /&gt;
</pre>
Det innebär att jag numera kan använda blipp.com som ett OpenID, men styra själv vilken OpenID-provider jag vill använda. Och jag har testat detta mot lite allt möjligt, bland annat slashdot.org och dopplr.com. Båda dessa tjänster stöder dessutom att man i efterhand kan knyta sitt OpenID mot sitt befintliga konto.