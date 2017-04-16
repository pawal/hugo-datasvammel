---
author: pawal
categories:
- Hacks
- Identitet
- Säkerhet
date: 2014-09-24T14:00:41Z
guid: http://pawal.blipp.com/?p=37684
id: 37684
title: Tvåfaktorautentisering är lätt
url: /hacks/tvafaktorautentisering-ar-latt
---

Jag slog precis på tvåfaktorautentisering här på min blogg. Det tog ungefär tre minuter.

Om du vill slippa all teori omkring så gör man så här:
<ol>
	<li>Installera <a href="https://fedorahosted.org/freeotp/">FreeOTP</a> på din telefon.</li>
	<li>Ladda ner tillägget <a href="https://wordpress.org/plugins/two-factor-auth/">Two Factor Auth</a> till din Wordpress.</li>
	<li>Om den inte fungerar, installera php5-mcrypt och se till att den fungerar i din installation.</li>
	<li>Klicka på Two Factor Auth i win Wordpress-meny och aktivera TOTP.</li>
	<li>Läs av QR-koden med FreeOTP på telefonen.</li>
	<li>Logga ut från Wordpress.</li>
	<li>Logga in på Wordpress med ditt vanliga lösenord. Nu får du frågan om OTP-koden.</li>
	<li>Generera koden i telefonen med FreeOTP och skriv in den i Wordpress.</li>
</ol>
Så enkelt är det. Inga dyra RSA-dosor, inga SMS, och inga engångslösenord nedskrivna på en lapp.

Nästa blogginlägg får bli teorin kring denna lösning.