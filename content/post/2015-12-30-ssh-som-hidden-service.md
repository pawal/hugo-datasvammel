---
author: pawal
categories:
- Hacks
- Linux
- Säkerhet
- Svammel
date: 2015-12-30T02:45:06Z
guid: https://pawal.blipp.com/?p=37716
id: 37716
title: SSH som hidden service
url: /linux/ssh-som-hidden-service
---

<img class="alignnone alignright" src="https://www.torproject.org/images/onion.jpg" alt="" width="78"height="118" />Efter dagens presentationer på 32c3 om Tor, <a
href="https://media.ccc.de/v/32c3-7322-tor_onion_services_more_useful_than_you_think">Tor
Onion Services, More Useful Than You Think</a>, och <a
href="https://media.ccc.de/v/32c3-7307-state_of_the_onion">State of
the Onion</a>, så beslöt jag mig för att börja lägga till alla mina
egna (mest privata) tjänster som hidden services.

Instruktionerna för att <a
href="https://www.torproject.org/docs/tor-hidden-service.html.en">skapa
en konfiguration för sin hidden service</a> är rätt bra, och rätt
enkla om man vill dölja en webbtjänst. Men om man vill använda
t.ex. en SSH-klient för att ansluta till sin SSH-service så får man
söka rätt ordentligt på nätet för att ta reda på hur man gör.

Så här är snabb-snabb-instruktionerna för hur man skapar sin
SSH-tjänst som en hidden service på en debian/ubuntu-maskin - kör som
_root_:

```sh
apt-get install tor
```

Lägg till följande i din konfiguration i /etc/tor/torrc:

```sh
HiddenServiceDir /var/lib/tor/ssh_hidden_service/
HiddenServicePort 22 127.0.0.1:22
```

Sedan kör du

```sh
systemctl reload tor.service
```

Du hittar din .onion-adress genom att köra
```sh
cat /var/lib/tor/ssh_hidden_service/hostname
```

Nu har du alltså en SSH uppsatt som en hidden service. **Bra! Men hur ansluter man?**

Jo, såhär. Man lägger till följande proxy-information i sin
.ssh/config, förutsatt att ens socks-proxy för Tor körs på port 9050
(vilket är default):

```sh
Host *.onion
ProxyCommand /usr/bin/nc -xlocalhost:9050 -X5 %h %p
```

Nu ska man alltså helt utan problem kunna köra ett ssh-kommando för att ansluta till en .onion-adress:

```sh
ssh pawal@exempelhash123.onion
```

Om du har en massa maskiner bakom NAT underlättar ju även det här att
komma åt dem, även om det blir en hel del extrahopp över Tor-nätet på
vägen.

**En fotnot:** Den här bloggen är även tillgänglig på
<a href="http://hxrni7witdpetpuf.onion/">http://hxrni7witdpetpuf.onion/</a>,
men pga hur Wordpress <a href="https://codex.wordpress.org/Changing_The_Site_URL">fungerar</a>
så är det väldigt mycket jobb att få till det så att länkar och
bilder går .onion-adresserna istället för att läcka ut till den
vanliga sajten.
