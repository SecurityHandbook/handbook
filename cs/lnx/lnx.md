# FAQ &ndash; OS Linux
Linux se díky svému minoritnímu zastoupení na desktopech těší řádově menší pozornosti hackerů nežli Windows, většina malware pro Linux je směřována na servery. Malware pro desktopové linuxové distribuce existuje &ndash; v mnohonásobně menším množství, ale existuje. Mimo jiné, exploit kity se poslední dobou snaží být co nejvíce multiplatformní a např. JS ransomware spolehlivě funguje i přes prohlížeč na Linuxu.

Tato sekce FAQ je určena běžným a středně pokročilým uživatelům. Sekci pro pokročilé naleznete [zde](https://faq.mople71.cz/cs/lnx/adv.php#lnx).

#### FAQ se dělí na několik sekcí:
- doporučené distribuce
- bezpečné nastavení OS
- vrstvy zabezpečení OS
- zabezpečení internetového prohlížeče

<br>

## Doporučené distribuce:
- Fedora: https://getfedora.org/cs/workstation/
- openSUSE: https://www.opensuse.org/
- Ubuntu: https://www.ubuntu.com/desktop

V sekci OS Linux naleznete tipy převážně pro distribuci <span class="green">Fedora</span>.

Fedora je nejlepší a nejbezpečnější volbou pro běžného uživatele, jelikož je již v základu špičkově zabezpečená. Používá GNOME, nabízí uživateli možnost snadné instalace Flatpak aplikací, obsahuje velmi robustní implementaci SELinux a má velmi vysoké standardy na své balíčky &ndash; všechny musí mít důležité mitigace proti memory corruption exploitům. Mimo technické funkce nabízí stabilní nejnovější SW a velmi rychle záplatuje objevené bezpečnostní zranitelnosti.

U některých kroků také naleznete pokyny pro distribuci Ubuntu, která je velmi populární, z hlediska bezpečnosti ovšem *mnohem* méně vhodná.

Chcete-li používat jinou distribuci, níže uvedené kroky můžete aplikovat i na ostatní distribuce, pouze si musíte zjistit správný syntax vaší distribuce a informace o kompatibilitě.

### Doporučené grafické prostředí:
Z bezpečnostního hlediska doporučuji [GNOME](https://www.gnome.org/), jelikož používá wayland místo X.org a podílí se na vývoji Flatpaku. Výjimku tvoří rozhraní *GNOME Classic*, které využívá primárně X.org &ndash; není tedy doporučeno.

<br><br><hr><br>

## Bezpečné nastavení OS:
### Oddělení /tmp oddílu během instalace a jeho bezpečné připojení:
Malware se často spouští z dočasných složek. Zakázání exekuce spustitelných souborů v dočasných složkách (konkrétně /tmp) tedy dokáže vyřadit z provozu mnoho rodin malware.

> Návod

- Při instalaci OS otevřete možnosti rozdělení disků.
- V sekci **Konfigurace úložiště** zvolte možnost <span class="green">Pokročilé uživatelské nastavení (Blivet-GUI)</span> a v levém horním rohu klikněte na <span class="green">Hotovo</span>.
- V levém sloupci zvolte disk, na který chcete OS instalovat a klikněte na tlačítko <span class="green">+</span> pro přidání oddílu.
- Jako **typ zařízení** vyberte <span class="green">Oddíl</span>.
- Do kolonky **velikost** zadejte <span class="blue">0,5 GiB</span>.
- Jako **souborový systém** zvolte <span class="green">ext4</span>, jako **label** zadejte *boot*, **přípojný bod** nastavte na "<span class="red">/boot</span>" a následně klikněte na tlačítko <span class="green">Budiž</span>.
<li style="list-style-type: none">![lnxtmp](https://faq.mople71.cz/img/cs/lnxtmp.png)</li>
- V pravém sloupci kliknutím označte **volné místo** a klikněte na tlačítko <span class="green">+</span> pro přidání dalšího oddílu.
- Jako **typ zařízení** vyberte <span class="green">Oddíl</span>.
- Do kolonky **velikost** zadejte velikost, kterou chcete vyhradit pro OS, akorát od ní odečtěte <span class="blue">4 GiB</span>.
- Jako **souborový systém** zvolte <span class="green">btrfs</span>, jako **přípojný bod** nastavte na "<span class="red">/</span>" a následně klikněte na tlačítko <span class="green">Budiž</span>.
<li style="list-style-type: none">![lnxtmp1](https://faq.mople71.cz/img/cs/lnxtmp1.png)</li>
- V pravém sloupci kliknutím označte **volné místo** a klikněte na tlačítko <span class="green">+</span> pro přidání dalšího oddílu.
- Jako **typ zařízení** vyberte <span class="green">Oddíl</span>.
- Do kolonky **velikost** zadejte <span class="blue">2,0 GiB</span> (budete muset přepnout jednotky na *GiB*).
- Jako **souborový systém** zvolte <span class="green">ext4</span>, jako **label** zadejte *tmp*, **přípojný bod** nastavte na "<span class="red">/tmp</span>" a následně klikněte na tlačítko <span class="green">Budiž</span>.
<li style="list-style-type: none">![lnxtmp2](https://faq.mople71.cz/img/cs/lnxtmp2.png)</li>
- V pravém sloupci kliknutím označte **volné místo** a klikněte na tlačítko <span class="green">+</span> pro přidání dalšího oddílu.
- Jako **typ zařízení** vyberte <span class="green">Oddíl</span>.
- V kolonce **velikost** ponechte původní hodnotu (měla by být <span class="blue">2047 MiB</span>).
- Jako **souborový systém** zvolte <span class="green">swap</span>, jako **label** zadejte *swap* a následně klikněte na tlačítko <span class="green">Budiž</span>.
- V levém horním rohu klikněte na <span class="green">Hotovo</span>.
- Rozložení disku potvrďte tlačítkem <span class="green">Přijmout změny</span>.
- Pokračujte v instalaci.
- Po úspěšné instalaci si otevřete <span class="green">Terminál</span>. Zadejte do něj následující příkaz:
<li style="list-style-type: none"><pre><code>sudo -i
dnf -y install nano
nano -\$ /etc/fstab</code></pre></li>
- V textovém souboru šipkami nalezněte řádek, který obsahuje "<span class="red">/tmp</span>". Řádek by měl vypadat následovně:
<li style="list-style-type: none"><pre><code>UUID=... /tmp           ext4    defaults     1 2</code></pre></li>
- Na řádku nalezněte slovo "<span class="green">defaults</span>" a a za něj dopište "<span class="red">,nodev,noexec,nosuid</span>". Fstab tedy bude vypadat následovně:
<li style="list-style-type: none">![lnxfstab](https://faq.mople71.cz/img/en/lnxfstab.png)</li>
- Stiskněte klávesovou zkratku <span class="green">Ctrl + X</span>. Pro uložení změn v souboru stiskněte tlačítko <span class="red">Y</span> a následně <span class="green">Enter</span>.
- Budete vráceni do konzole. Zadejte do ní následující příkazy:
<li style="list-style-type: none"><pre><code>exit
exit</code></pre></li>
- Restartujte OS.

<br>

### Zakázání IPv6:
Pokud nepoužíváte a nepotřebujete IPv6 (pokud nevíte, můžete to zjistit pomocí následujícího [testu](http://www.test-ipv6.cz/), je rozumné protokol vypnout pro snížení prostoru pro útok.

> Návod

- Otevřete si <span class="green">Terminál</span>. Zadejte do něj následující příkazy:
<li style="list-style-type: none"><pre><code>sudo -i
dnf -y install nano
nano /etc/default/grub</code></pre></li>
- Nalezněte řádek <span class="green">GRUB_CMDLINE_LINUX_DEFAULT</span> a před poslední uvozovku vepište "<span class="red"> ipv6.disable=1</span>". Řádek tedy bude vypadat nějak takto:
<li style="list-style-type: none"><pre><code>GRUB_CMDLINE_LINUX_DEFAULT="quiet splash ipv6.disable=1"</code></pre></li>
- Stiskněte klávesovou zkratku <span class="green">Ctrl + X</span>. Pro uložení změn v souboru stiskněte tlačítko <span class="red">Y</span> a následně <span class="green">Enter</span>.
- Budete vráceni do konzole. Zadejte do ní následující příkazy:
<li style="list-style-type: none"><pre><code>grub2-mkconfig -o /boot/grub2/grub.cfg
exit
exit</code></pre></li>
- Restartujte OS.

<br>

### Nastavení DNS:
Pokud vám zkratka DNS nic neříká, přečtěte si tento [krátký článek](https://www.nic.cz/page/312/o-domenach-a-dns/).

> Návod

- Otevřete si <span class="green">Nastavení</span> a klikněte na položku <span class="green">Síť</span>.
- V seznamu zvolte připojení, které používáte (Drátové/WiFi), a otevřete jeho nastavení.
<li style="list-style-type: none">![lnxnet](https://faq.mople71.cz/img/cs/lnxnet.png)
![lnxnet1](https://faq.mople71.cz/img/cs/lnxnet1.png)</li>
- Přepněte se do záložky IPv4 a v sekci **DNS** vypněte možnost <span class="green">Automatické</span>.
- Do řádku vepište následující DNS servery:
<li style="list-style-type: none"><pre><code>217.31.204.130,193.29.206.206</code></pre></li>
<li style="list-style-type: none">![lnxnet2](https://faq.mople71.cz/img/cs/lnxnet2.png)</li>
- Klikněte na tlačítko <span class="green">Použít</span> a nastavení zavřete.

<br><br><hr><br>

## Vrstvy zabezpečení OS:
### Firewall:
Firewall je velmi důležitá vrstva zabezpečení, která chrání OS před útoky ze sítě. *Poznámka na okraj: základem síťového zabezpečení v domácnosti je rozumný router.*

**<span class="fe">Fedora</span>** má v základu plně funkční firewall.

**<span class="os">openSUSE</span>** má v základu plně funkční firewall.

**<span class="ub">Ubuntu</span>** v základu nemá zapnutý firewall, je třeba jej zapnout příkazem:
<pre><code>sudo ufw enable</code></pre>

<br>

### MAC:
<abbr title="Mandatory Access Control">MAC</abbr> se stal důležitou součástí bezpečnostního modelu linuxových distribucí. Podrobné vysvětlení naleznete např. na [Wikipedii](https://cs.wikipedia.org/wiki/Mandatory_access_control).

**<span class="fe">Fedora</span>** používá implementaci **SELinux**.

**<span class="os">openSUSE</span>** používá implementaci **AppArmor**, MAC poskytující menší možnosti ochrany než např. SELinux.

**<span class="ub">Ubuntu</span>** používá implementaci **AppArmor**, MAC poskytující menší možnosti ochrany než např. SELinux.

<br>

### Virtualizace:
Virtualizace může být velmi bezpečný způsob ochrany před malware (záleží na způsobu implementace), jelikož odděluje požadovanou část OS od fyzického OS.

Nejčastější implementací virtualizace je **sandbox**. Existují dva druhy sandboxu:

- sandbox nativně integrovaný v aplikaci (např. Chromium)
- externí sandbox &ndash; např. Flatpak, firejail

Sandbox nativně integrovaný v aplikaci je nejúčinnější možností implementace sandboxu, jelikož je nastaven přesně na míru dané aplikaci.

Externí sandbox není zdaleka tak účinný jako sandbox integrovaný v aplikaci a při porovnání ponechává větší prostor pro exploitaci, ale stále může být vcelku účinný a přirozeně je nesrovnatelně lepší, nežli žádný sandbox.

Další možností virtualizace je **virtuální počítač**, kdy je místo aplikace oddělen celý OS. Tato metoda drasticky snižuje prostor pro exploitaci, snižuje ovšem také přívětivost, výkon a použitelnost. Jednoduché nastavení a používání virtuálního počítače umožňují následující aplikace:

- GNOME Boxes
- VirtualBox

> Konfigurace GNOME Boxes

- Stáhněte si obraz OS (ISO), který chcete virtualizovat.
- Otevřete si aplikaci <span class="green">Boxy</span>.
- V levém horním rohu aplikace klikněte na tlačítko <span class="green">Nový</span>.
- Klikněte na <span class="green">Vybrat soubor</span> a nalezněte požadovaný ISO soubor.
- Klikněte na tlačítko <span class="green">Přizpůsobit...</span>
- Nastavte požadované množství alokované paměti (pro 64-bitový OS alespoň 3 GiB) a místa na disku.
<li style="list-style-type: none">![gboxes](https://faq.mople71.cz/img/cs/gboxes.png)</li>
- Přesuňte se zpět a v pravém horním rohu klikněte na <span class="green">Vytvořit</span>.

<br>

### Flatpak:
Flatpak je nový způsob distribuce aplikací. Má za cíl odstranit chyby a nedostatky současné architektury &ndash; odděluje aplikace od sebe a částí OS, sjednocuje instalaci aplikací pro linuxové distribuce etc.

**<span class="fe">Fedora</span>** má **flatpak** předinstalovaný.

**<span class="os">openSUSE</span>** Flatpak předinstalovaný nemá, lze jej ovšem nainstalovat jednoduchým příkazem:
<pre><code>sudo zypper install flatpak</code></pre>

**<span class="ub">Ubuntu</span>** Flatpak předinstalovaný nemá, jelikož propaguje svou alternativu k Flatpaku &ndash; [Snap](https://www.ubuntu.com/desktop/snappy). Každopádně pokud se rozhodnete upřednostnit Flatpak před Snap (doporučeno), můžete jej nainstalovat následujícími příkazy:
<pre><code>sudo add-apt-repository ppa:alexlarsson/flatpak
sudo apt update
sudo apt install flatpak</code></pre>

<br>

> Návod k použití Flatpak

Několik aplikací můžete nalézt na [stránkách Flatpak](http://flatpak.org/apps.html) a většinu poté v repozitáři **Flathub**. Je důrazně doporučeno překliknout se do záložky <span class="green">Command Line</span> a příkazy provést ručně.

Nikdy před příkaz **flatpak** nedávejte <span class="red">sudo</span>. Flatpak si o autorizaci řekne sám, bude-li ji potřebovat.

- Nainstalované Flatpak aplikace vypíšete následujícím příkazem:
<li style="list-style-type: none"><pre><code>flatpak list</code></pre></li>
- Aplikace aktualizujete náledujícím příkazem:
<li style="list-style-type: none"><pre><code>flatpak update</code></pre></li>
- Dostupné aplikace v repozitáři vypíšete takto:
<li style="list-style-type: none"><pre><code>flatpak remote-ls <repozitář></code></pre></li>
- Instalaci aplikace z repozitáře je možno provést následovně:
<li style="list-style-type: none"><pre><code>flatpak install <repozitář> <název_aplikace></code></pre></li>
- Aplikaci poté můžete jednoduše odinstalovat:
<li style="list-style-type: none"><pre><code>flatpak uninstall <název_aplikace></code></pre></li>

#### Flathub:

Flathub je oficiální platforma pro distribuci Flatpak aplikací. Naleznete zde již vcelku obstojný počet aplikací, který se neustále rozšiřuje. Například **LibreOffice**, GIMP, Atom, Signal, VLC, Audacity, Blender, **Steam**, GeoGebra, Inkscape,...

> Nastavení repozitáře Flathub

- Otevřete si <span class="green">Terminál</span>. Zadejte do něj následující příkazy:
<li style="list-style-type: none"><pre><code>flatpak remote-add --if-not-exists gnome https://sdk.gnome.org/gnome.flatpakrepo
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo</code></pre></li>

> Instalace GNOME aplikací

Ve Flatpaku by správně měly být všechny aplikace ve výchozím nastavení, na to si ovšem budeme ještě muset chvíli počkat. (*Fedora 29?*)

Je vhodné mít ve Flatpaku alespoň rizikové aplikace jako **Evince** (prohlížeč PDF) nebo **Eye of GNOME** (prohlížeč obrázků). Také je dobrý nápad nainstalovat flatpak verzi GNOME prohlížeče **Epiphany**, který následně můžete odděleně používat pro citlivé věci jako bankovnictví apod.

- Otevřete si <span class="green">Terminál</span>. Odinstalujte původní aplikace:
<li style="list-style-type: none"><pre><code>sudo dnf -y remove eog</code></pre></li>
- Aplikace *Evince* odebrat nelze, jelikož poskytuje náhledy ve správci souborů a také náhledy tisku. Lze ovšem jednoduše odebrat jeho ikonu ze seznamu aplikací:
<li style="list-style-type: none"><pre><code>sudo rm /usr/share/applications/evince.desktop</code></pre></li>
- Nainstalujte flatpak verze aplikací:
<li style="list-style-type: none"><pre><code>flatpak install flathub org.gnome.Evince
flatpak install flathub org.gnome.eog
flatpak install flathub org.gnome.Epiphany</code></pre></li>
- Nyní nastavte zpět aplikace jako výchozí. Otevřete si <span class="green">Nastavení</span>.
- Rozklikněte kategorii **Podrobnosti** a následně zvolte podkategorii <span class="green">Výchozí aplikace</span>.
- Nastavte Flatpak verzi *Eye of GNOME* aplikací jako výchozí:
<li style="list-style-type: none">![lnxdapp](https://faq.mople71.cz/img/cs/lnxdapp.png)</li>
- Nalezněte libovolný **PDF** soubor. Klikněte na něj pravým tlačítkem a zvolte <span class="green">Otevřít jinou aplikací</span>.
- V seznamu zvolte Flatpak verzi **Prohlížeč dokumentů** a klikněte na tlačítko <span class="green">Vybrat</span>.
<li style="list-style-type: none">![lnxdapp1](https://faq.mople71.cz/img/cs/lnxdapp1.png)</li>

> Instalace LibreOffice

- Otevřete si <span class="green">Terminál</span>. Odinstalujte původní LibreOffice, které jsou součástí standardní instalace:
<li style="list-style-type: none"><pre><code>sudo dnf -y remove libreoffice*</code></pre></li>
- Nainstalujte flatpak verzi LibreOffice:
<li style="list-style-type: none"><pre><code>flatpak install flathub org.libreoffice.LibreOffice</code></pre></li>

> Instalace Steam

- Otevřete si <span class="green">Terminál</span>. Zadejte do něj následující příkaz:
<li style="list-style-type: none"><pre><code>flatpak install flathub com.valvesoftware.Steam</code></pre></li>
- Bude-li vám v průběhu nabídnut výběr mezi *gnome* a *flathub* repozitáři, zvolte <span class="green">flathub</span>.
- Spusťte Steam a doufejte, že vaše oblíbené hry jsou ve flatpaku funkční. Seznam otestovaných her naleznete [zde](https://github.com/flathub/com.valvesoftware.Steam/wiki/Tested-Games).

<br><br><hr><br>

## Zabezpečení internetového prohlížeče:
Z bezpečnostního hlediska doporučuji prohlížeč <span class="green">Chromium</span>. Používá špičkovou implementaci sandboxu a jeho kód je na velmi dobré úrovni. Celkově je v ohledu bezpečnosti v současném stavu dále než **Mozilla Firefox**. Prohlížeč **Epiphany** není nijak zvlášť zaměřený na bezpečnost, nehodí se tedy ke každodennímu používání. Můžete jej ovšem použít jako oddělený prohlížeč pro citlivé věci jako bankovnictví apod.

<!--- ./browsers.md -->

<br><br><hr>

<h3 class="nocol">To je vše. Stay safe! ![smile](https://mople71.cz/img/sm/smile.gif)</h3>
