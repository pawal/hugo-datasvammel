---
author: pawal
date: 2006-04-07T08:09:37Z
guid: http://pawal.blipp.com/hacks/cuteoverloadaptcha
id: 36
tags:
- hacks
title: CuteoverloadAPTCHA
url: /hacks/cuteoverloadaptcha
---

<img align="right" class="alightright" title="Kitten" alt="Kitten" src="http://blipp.com/misc/kitten.jpg" />

För att skydda innehåll eller på annat sätt verifiera att en användare
på en webbtjänst är en människa så finn det en teknik som kallas <a
href="http://en.wikipedia.org/wiki/Captcha">CAPTCHA</a>. Det står för
<em><strong>C</strong></em>ompletely
<em><strong>A</strong></em>utomated <em><strong>P</strong></em>ublic
<em><strong>T</strong></em>uring Test to tell
<em><strong>C</strong></em>omputers and
<em><strong>H</strong></em>umans <em><strong>A</strong></em>part. En
klassisk CAPTCHA ser ut ungefär såhär: <div align="left"
style="text-align: center"><img title="CAPTCHA" alt="CAPTCHA"
class="aligncenter" src="http://blipp.com/misc/captcha.png" /></div>
Uppgiften är att i en textruta skriva in de tecken som står i
grafiken. För att en sådan CAPTCHA ska vara bra, och förhindra
datorprogram från att lätt kunna analysera bilden så att man kan
utföra automatiska attacker, så ska denna text vara i princip
oläsbar. Ju mer oläsbar desto bättre skydd mot automatisk analys av
innehållet.

Jag snubblade precis över en riktigt rolig, <a
href="http://cuteoverload.com/">Cute Overload</a>-inspirerad teknik,
<a href="http://www.thepcspy.com/articles/security/the_cutest_humantest_kittenauth">KittenAuth</a>!

Den går ut på att bland en massa bilder på söta djur, klicka på de tre
som är söta kattungar. Tekniken finns att testa <a
href="http://www.thepcspy.com/kittenauthtest">här</a>, och lyckas man
identifiera kattungarna får man svaret <strong><span
class="ponies">OMG PONIES!!! YOU CLICKED 3
KITTENS!!!!!!</span></strong> Om detta skyddar bättre mot automatiska
attacker låter jag vara osagt, men det känns spontant jobbigare för
datorer att känna igen kattungar än alfabetet.