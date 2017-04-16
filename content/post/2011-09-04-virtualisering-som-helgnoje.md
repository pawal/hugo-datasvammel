---
author: pawal
categories:
- Linux
- Mjukvara
- Virtualisering
date: 2011-09-04T21:23:35Z
guid: http://pawal.blipp.com/?p=28494
has_been_twittered:
- "yes"
id: 28494
title: Virtualisering som helgnöje
url: /linux/virtualisering-som-helgnoje
---

<p>Jag har börjat roa mig med att lära mig mycket om virtualisering. Dvs, att köra låtsasdatorer inuti mina servrar. Fast virtualisering är inte så mycket på låtsas längre, det är en av de snabbast framväxande marknaderna på Internet. Och jag är väl en av de få en inte har köpt en <strong>VPS</strong> (Virtual Private Server) för att köra mina tjänster på. Jag har riktig hårdvara. Med ett riktigt nät. Det finns virtuella nät också.</p>
<p>Först måste jag erkänna att jag trodde det var väldigt enkelt att köra virtualisering. Och det är det ju också på ytan, ända tills man vill börja göra lite mer intressanta saker med virtualisering.</p>
<p>Den första frågan man ställer sig när man vill börja köra lite virtuella maskiner är förstås vilken virtualiseringprogramvara man vill köra (eller "<a href="http://en.wikipedia.org/wiki/Hypervisor">hypervisor</a>"). Den självklara plattformen att köra hypervisor på är för mig idag Linux. Det finns lite att välja bland, men själv kom jag att fundera på <a href="http://xen.org/">Xen</a>, <a href="http://www.virtualbox.org/">VirtualBox</a> eller nånting jag aldrig tittat på, <a href="http://www.linux-kvm.org/page/Main_Page">Qemu-KVM</a>. VirtualBox har jag kört litegrann på min MacOS-maskin för att snabbt och enkelt testa lite saker under andra operativsystem. Men aldrig för att permanent köra en virtuell server. Vad jag visste är dock att <a href="http://en.wikipedia.org/wiki/Kernel-based_Virtual_Machine">KVM</a> finns i Linux-kärnan sedan ett par år tillbaka, och det har känts som om det är den tekniken som utvecklas mest just nu. Så jag bestämde mig för att titta närmare på Qemu och KVM.</p>
<p>Steg ett var att titta närmare på Qemu och komma underfund med hur det fungerade. För att skapa en virtuell maskin måste man först skapa en image att installera ett operativsystem på. Qcow2 är det image-format som man vill använda idag för att köra virtuella servrar. Mycket arbete pågår för att förbättra tekniken för hur virtualiserade operativsystem fungerar på dessa images, både vad gäller hur de växer i storlek med att den virtuella maskinen använder diskytan, men också prestandan kan förbättras både i den virtuella maskinen och i hypervisorn.</p>
<p>Hur som helst, skapa en 10GB qcow2-image med följande kommando:</p>
<blockquote><p>
twobot$~&gt;qemu-img create -f qcow2 foo.img 10G
Formatting 'foo.img', fmt=qcow2 size=10737418240 encryption=off cluster_size=0
</p>
</blockquote>
<p>Man kan ha krypterade images, vilket ju är trevligt. Med AES-kryptering och ett långt lösenord borde det dessutom bli riktigt säkert.</p>
<p>Vad gäller dessa images i övrigt så verkar det finnas en del trevliga verktyg baserade på <em>libguestfs</em> att jobba med för att titta inuti dem. Med <strong>guestfish</strong> kan du manipulera filer direkt i en disk-image. Det är praktiskt om man vill duplicera många images, och därefter anpassa varje image med exempelvis hostnamn och annat. Görs lämpligast när maskinen inte körs förstås. Med <em>guestmount</em> används FUSE för att montera valt filsystem i en image direkt i det lokala filsystemet.</p>
<p>När man vill bygga sina virtuella servrar så vill man förstås att de ska få sina IP-adresser ut mot Internet, och inte bara vara lokalt åtkomliga från hypervisorn. Default-inställningen verkar vara att köra på väldigt lokala IP-adresser. I Linux kan man dock skapa ett <em>bridge</em>-interface för att hänga på de virtuella instanserna på det externa interfacet. Så i stället för att konfigurera eth0 som vanligt konfigurerar man upp sin br0 såhär:</p>
<blockquote><p>
auto br0
iface br0 inet static
      bridge_ports eth0
      bridge_stp off
      bridge_fd 0
      bridge_maxwait 0
      address 192.168.0.2
      netmask 255.255.255.0
      network 192.168.0.0
      gateway 192.168.0.1
      broadcast 192.168.0.255
      up ifconfig br0 add 2001:16d8:dead::dead/64
</p>
</blockquote>
<p>och sedan ersätter man sin eth0 såhär:</p>
<blockquote><p>
auto eth0
iface eth0 inet manual
</p>
</blockquote>
<p><strong>br0</strong> blir då statiskt konfigurerad. Hypervisorn kan dock köra en DHCP-server så att de virtuella servrarna får en automatiskt konfigurerad IP-adress. (Exemplet ovan är en Debian.)</p>
<p>Nu har vi en image och ett nätverk som är rätt konfigurerat. Då återstår bara att installera ett operativsystem. Mitt första försök använde qemu direkt för att installera operativsystemet. Man konfigurerar upp qemu för att montera på en cdrom, eftersom så fort man kör igång qemu så är det ju en virtuell maskin man startar.</p>
<blockquote><p>
sudo qemu -enable-kvm -k sv -ctrl-grab -hda foo.img -m 1024 -net nic,macaddr=DE:AD:BE:EF:A7:A2 -net tap,ifname=tap2 -monitor pty -vnc 0.0.0.0:1 -name foo-dator -cdrom debian-testing-i386-businesscard.iso -boot d
</p>
</blockquote>
<p>Tyvärr verkar det som om man måste köra qemu som root för att kunna köra mot bridge-interfacet. Kör man qemu såhär så når man den via VNC på den första lediga porten (VNC körs från port 5900 och uppåt). Anlut och se datorn boota upp, och förhoppningsvis boota från cdrom. Sedan när du installerat operativsystemet är det bara att boota om och köra igång det installerade systemet.</p>
<p>Vill man inte köra <strong>qemu</strong>-kommandona för hand kan man istället välja att köra ytterligare ett abstraktionslager högre upp. Det finns antagligen flera. Jag vet att Ubuntu har baserat något på <strong>virsh</strong> för att via grafiska gränssnitt för att konfigurera upp qemu, och förmodligen har alla OS sina verktyg. Virsh är dock ett CLI som verkar vanligt, och motsvarande qemu-kommando är detta:</p>
<blockquote><p>
virt-install --connect qemu:///system --virt-type kvm --accelerate --name demo --ram 1024 --disk path=debian.img,size=10,format=qcow2 -w bridge:br0 --mac=DE:AD:BE:EF:A7:A2 --graphics vnc,listen=0.0.0.0,keymap=sv,password='foo' --noautoconsole --cdrom debian-testing-i386-businesscard.iso
</p></blockquote>
<p>Det är viktigt att sätta olika MAC-adresser för de virtuella nätverksgränssnitten, annars kommer de att kollidera på ditt LAN. Hur som helst, poängen med att köra virsh framför qemu direkt är att du får ett management-lager ovanpå qemu som har koll på vilka virtuella maskiner som finns tillgängliga, vilka som är igång, hur mycket CPU de drar, och så vidare. Dessutom blir det enklare att skapa kloner av en maskin du kan utgå ifrån för att skapa nya projekt.</p>
<p>Jag inser vid det här laget att jag skulle kunna skriva tio bloggposter till, så det kommer jag att göra. Kan du inte slita dig från att lära dig så vet jag inte riktigt var man ska börja läsa. Men själv sitter jag och pluggar <a href="http://www.linux-kvm.org/page/KVM_Forum_2011">presentationerna från KVM-konferensen</a> som var nu i augusti. Och jag har inte ens börjat skriva om user-mode-linux som jag tycker är väldigt trevligt. Eller virtuella nätverk.</p>
<p>Med ett oerhört kommersiellt intresse för virtualisering har jag insett att det händer oerhört mycket inom det här området. Mycket går givetvis mot att klämma in fler och fler virtuella maskiner i en och samma hypervisor för att kunna sälja till fler kunder, men också mot management och monitoring. Men det är ju intressant även för mig, som vill kunna använda min hårdvara till roliga saker också.</p>
<p>Vad har ni för erfarenheter av virtualisering?</p>