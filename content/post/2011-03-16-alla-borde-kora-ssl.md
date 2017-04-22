---
author: pawal
tags:
- creeper
- integritet
- säkerhet
date: 2011-03-16T16:13:02Z
guid: http://pawal.blipp.com/?p=18726
has_been_twittered:
- "yes"
id: 18726
title: Alla borde köra SSL
url: /integritet/alla-borde-kora-ssl
---

Nu när det till och med går att köra både Facebook och Twitter
krypterat med hjälp av SSL tycker jag att de flesta argument mot att
köra SSL på sin webbplats faller. Det största argument som framhålls
är att det kräver så mycket av webbservern. Det var säkert sant för 10
år sedan. Processorerna har utvecklats sedan dess och har numera bra
funktioner för att även hjälpa till med de kryptooperationer som
krävs. Ett annat vanligt argument är att det är dyrt. Det är det
inte. Ifall man inte tycker att gratis är dyrt.

Jag vill gärna föregå med gott exempel, men tyvärr är det lite
svårt. Helst av allt vill jag göra en 302 redirect från HTTP till
HTTPS på alla mina webbplatser, men den enda jag har lyckats göra det
med gott resultat på är <a
href="https://vic20.blipp.com/">vic20.blipp.com</a>. Både blipp.com
och gnuheter.com har jag slagit på SSL för. Problemet där beskrivs på
engelska som "<a
href="http://www.imperialviolet.org/2011/02/11/originpoisoning.html">origin
poisioning</a>". Som bloggare använder man gärna resurser på andra
webbplatser, och dessa andra webbplatser saknar tyvärr ofta stöd för
SSL. Vilket innebär att om man surfar till den här bloggen, <a
href="https://pawal.blipp.com/">pawal.blipp.com</a> över SSL så får
man inte det skinande fina hänglåset som markör som visar att sajten
man surfar till är säker. Jag använder nämligen resurser hos
exempelvis Flickr för att hämta några bilder. Flickr har inte stöd för
SSL.

Men för att komma en liten bit på vägen så har jag för er som vill
köra SSL hela vägen, sett till att ha stöd för det på Creeper. Så om
man länkar till bilden med "https" istället, så funkar det bra. Jag
har lagt till detta som en liten instruktion på <a
href="http://gnuheter.com/creeper/howto">howto-sidan</a> för
Creeper. Så ni som kör Creeper och läser detta, kan ni prova att byta
ut era länkar? Då kan jag se om det blir något problem med att köra
det på min sida. Det borde som sagt inte krävas särskilt mycket extra
CPU för detta, och jag har en hel del CPU över om det ändå skulle göra
det.

För är det så att du fortfarande länkar osäkra resurser på din
webbsida så kan den som vill avlyssna trafiken hos läsaren fortfarande
se vilka sidor användaren är inne på, även om inte klartexten på
sajten går att läsa. Jag tycker att vi kan höja kvaliteten på den
svenska webben nu, och göra läsaren lite extra trygg. <em>Inte minst
så att datalagringsdirektivet blir ännu lite mer tandlöst.</em> För
varför konstra med nya krypton och p2p-nät, när vi inte ens lyckas
skydda den befintliga infrastrukturen med de verktyg som faktiskt
finns tillgängliga?

(Certifikat som fungerar helt gratis hittar du bl.a. hos <a
href="https://www.startssl.com/">startssl.com</a>.)