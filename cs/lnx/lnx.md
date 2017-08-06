# FAQ &ndash; OS Linux
Linux se díky svému minoritnímu zastoupení na desktopech těší řádově menší pozornosti hackerů nežli Windows, většina malware pro Linux je určena serverům. Malware pro desktopové linuxové distribuce ovšem existuje &ndash; sice v mnohonásobně menším množství, ale existuje. Mimo jiné, exploit kity se poslední dobou snaží být co nejvíce multiplatformní a např. JS ransomware spolehlivě funguje i přes prohlížeč na Linuxu.

Není tedy pravda, že malware na desktopový Linux neexistuje. Pouze máte o něco menší šanci, že na něj někdy narazíte. Pokud by se ovšem tak stalo, je dobré být předem připraven. V této sekci naleznete několik jednoduchých tipů na účinné zvýšení úrovně zabezpečení.

Tato sekce FAQ je určena běžným a středně pokročilým uživatelům.

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
Z bezpečnostního hlediska doporučuji <a href="https://www.gnome.org/">GNOME</a>, jelikož používá wayland místo X.org a podílí se na vývoji Flatpaku. Vyjímku tvoří rozhraní *GNOME Classic*, které využívá primárně X.org &ndash; není tedy doporučeno.

<br><br><hr><br>

## Bezpečné nastavení OS:
### Oddělení /tmp oddílu a jeho bezpečné připojení:
Malware se často spouští z dočasných složek. Zakázání exekuce spustitelných souborů v dočasných složkách (konkrétně /tmp) tedy dokáže vyřadit z provozu mnoho rodin malware.

> Návod

- Při instalaci OS otevřete možnosti rozdělení disků.
- Zvolte možnost <span class="green">Ruční nastavení rozdělení</span> a v levém horním rohu klikněte na <span class="green">Hotovo</span>.
- Rozklikněte nabídku **schémat rozdělení** a zvolte <span class="green">Standardní oddíl</span>.
- Klikněte na tlačítko <span class="green">+</span> dole pro přidání oddílu.
- Do kolonky velikost zadejte plnou velikost disku/velikost, kterou chcete vyhradit pro Fedoru, akorát od ní odečtěte <span class="blue">4 GiB</span>.
<li style="list-style-type: none">![tmp1](https://faq.mople71.cz/img/cs/tmp1.png)</li>
- Přípojný bod zvolte "<span class="red">/</span>" a klikněte na <span class="green">Přidat bod připojení</span>.
- Klikněte na tlačítko <span class="green">+</span> dole pro přidání oddílu.
- Přípojný bod zvolte "<span class="red">/tmp</span>".
- Do požadované kapacity zadejte "<span class="blue">2 GiB</span>" a klikněte na <span class="green">Přidat bod připojení</span>.
- Klikněte na tlačítko <span class="green">+</span> dole pro přidání oddílu.
- Přípojný bod zvolte "<span class="red">swap</span>"
- Do požadované kapacity zadejte "<span class="blue">2 GiB</span>" a klikněte na <span class="green">Přidat bod připojení</span>.
- V levém horním rohu klikněte na Hotovo a následně na Přijmout změny.
- Pokračujte v instalaci.
- Po úspěšné instalaci si otevřete <span class="green">Terminál</span>. Zadejte do něj následující příkaz:
<li style="list-style-type: none"><pre><code>sudo -i
dnf -y install nano
gedit /etc/fstab</code></pre></li>
- V textovém souboru šipkami nalezněte řádek, který obsahuje "<span class="red">/tmp</span>". Řádek by měl vypadat následovně:
<li style="list-style-type: none"><pre><code>UUID=... /tmp           ext4    defaults   1   2</code></pre></li>
- Na řádku nalezněte slovo "<span class="green">defaults</span>" a a za něj dopište "<span class="red">,nodev,noexec,nosuid</span>". Fstab tedy bude vypadat následovně:
<li style="list-style-type: none">![fstab](https://faq.mople71.cz/img/en/fstab.png)</li>
- V horním pravém rohu klikněte na tlačítko <span class="green">Uložit</span>. Aplikaci zavřete a následně zavřete i konzoli.

<br>

### Zakázání IPv6:
Pokud nepoužíváte a nepotřebujete IPv6 (pokud nevíte, můžete to zjistit pomocí následujícího <a href="http://www.test-ipv6.cz/" target="_blank">testu</a>), je rozumné protokol vypnout pro snížení prostoru pro útok.

> Návod

- Otevřete si <span class="green">Terminál</span>. Zadejte do něj následující příkazy:
<li style="list-style-type: none"><pre><code>sudo -i
dnf -y install nano
nano /etc/default/grub</code></pre></li>
- Nalezněte řádek <span class="green">GRUB_CMDLINE_LINUX_DEFAULT</span> a před poslední uvozovku vepište "<span class="red"> ipv6.disable=1</span>". Řádek tedy bude vypadat nějak takto:
<li style="list-style-type: none"><pre><code>GRUB_CMDLINE_LINUX_DEFAULT="quiet splash ipv6.disable=1"</code></pre></li>
- Stiskněte klávesovou zkratku <span class="green">Ctrl + X</span>. Pro uložení změn v sobouru stiskněte tlačítko <span class="red">Y</span> a následně <span class="green">Enter</span>.
- Budete vráceni do konzole. Zadejte do ní následující příkazy:
<li style="list-style-type: none"><pre><code>grub2-mkconfig -o /boot/grub2/grub.cfg
exit
exit</code></pre></li>
- Restartujte OS.

<br>

### Nastavení DNS:
Pokud vám zkratka DNS nic neříká, přečtěte si tento <a href="https://www.nic.cz/page/312/o-domenach-a-dns/" target="_blank">krátký článek</a>.

> Návod

- Otevřete si <span class="green">Nastavení</span> a klikněte na položku <span class="green">Síť</span>.
- V seznamu zvolte připojení, které používáte (Drátové/WiFi), a otevřete jeho nastavení.
<li style="list-style-type: none">![lnxnet](https://faq.mople71.cz/img/cs/lnxnet.png)</li>
- Přepněte se do záložky IPv4 a vypněte možnost <span class="green">Automatické DNS</span>.
- Do kolonky **Server** vepište:
<li style="list-style-type: none"><pre><code>217.31.204.130</code></pre></li>
- Klikněte na tlačítko <span class="green">+</span> pod kolonkou **Server**.
- Objeví se další kolonka Server, do ní vepište:
<li style="list-style-type: none"><pre><code>193.29.206.206</code></pre></li>
<li style="list-style-type: none">![lnxnet1](https://faq.mople71.cz/img/cs/lnxnet1.png)</li>
- Klikněte na tlačítko <span class="green">Použít</span> a Nastavení zavřete.
<li style="list-style-type: none">![idea](https://mople71.cz/img/sm/idea.gif) Další doporučené DNS servery:</li>
<li style="list-style-type: none"><pre><code>Adguard DNS:         176.103.130.130, 176.103.130.131
OpenDNS:             208.67.222.222, 208.67.220.220</code></pre></li>

<br><br><hr><br>

## Vrstvy zabezpečení OS:
### Antivirus:
Just kidding.

<br>

### Firewall:
Firewall je velmi důležitá vrstva zabezpečení, která chrání OS před útoky ze sítě. *Poznámka na okraj: základem síťového zabezpečení v domácnosti je rozumný router.*

**<span class="fe">Fedora</span>** má v základu plně funkční firewall.

**<span class="os">openSUSE</span>** má v základu plně funkční firewall.

**<span class="ub">Ubuntu</span>** v základu nemá zapnutý firewall, je třeba jej zapnout příkazem:
<pre><code>sudo ufw enable</code></pre>

<br>

### MAC:
<abbr title="Mandatory Access Control">MAC</abbr> se stal důležitou součástí bezpečnostního modelu linuxových distribucí. Podrobné vysvětlení naleznete např. na <a href="https://cs.wikipedia.org/wiki/Mandatory_access_control" target="_blank">Wikipedii</a>.

**<span class="fe">Fedora</span>** používá implementaci **SELinux**.

**<span class="os">openSUSE</span>** používá implementaci **AppArmor**, MAC poskytující menší možnosti ochrany než např. SELinux.

**<span class="ub">Ubuntu</span>** používá implementaci **AppArmor**, MAC poskytující menší možnosti ochrany než např. SELinux.

<br>

### Virtualizace:
Virtualizace může být velmi bezpečný způsob ochrany před malware (záleží na způsobu implementace), jelikož odděluje požadovanou část OS od fyzického OS.

Zde budou rozebírány implementace **sandboxu**. Implementací existuje několik:

- sandbox nativně integrovaný v aplikaci (např. Chromium)
- externí sandbox &ndash; Flatpak, firejail

Sandbox nativně integrovaný v aplikaci je nejúčinnější možností implementace sandboxu, jelikož je nastaven přesně na míru dané aplikaci.

Externí sandbox není zdaleka tak účinný jako sandbox integrovaný v aplikaci a ponechává výrazně větší prostor pro exploitaci, ale stále je mnohonásobně lepší, než žádný sandbox.

**Flatpak** je rozebírán v následující sekci.

#### Firejail:
Firejail je solidní aplikace umožňující sandbox rizikových aplikací &ndash; pro spoustu z nich má předdefinované profily (např. Empathy, Evince, Filezilla, Firefox, Chrome, Chromium, HexChat, KMail, Opera, Pidgin, Transmission, Rhythmbox, SeaMonkey, Skype, Spotify, Steam, Thunderbird, Totem, VLC,...).

Důrazně doporučuji upřednostnit **Flatpak**, kde je to možné.

![idea](https://mople71.cz/img/sm/idea.gif) Používate-li aplikaci s integrovaným sandboxem jako např. **Chrome/ium**, rozhodně ji nesandboxujte pomocí firejail, integrovaný sandbox je řádově účinnější.

> Instalace Firejail

- Otevřete si <span class="green">Terminál</span>. Zadejte do něj následující příkazy:
<li style="list-style-type: none"><pre><code>sudo -i
dnf copr enable heikoada/firejail
dnf clean metadata && dnf check-update
dnf install firejail
chmod u+s /usr/bin/firejail</code></pre></li>

> Návod k použití Firejail

- Následující příkaz budete (bohužel) muset vždy spustit po aktualizaci aplikace firejail:
<li style="list-style-type: none"><pre><code>sudo chmod u+s /usr/bin/firejail</code></pre></li>
- Následujícím příkazem nastavíte automatické spouštění všech podporovaných aplikací v běžném sandboxu, pokud nainstalujete zbrusu novou podporovanou aplikaci, musíte příkaz zopakovat:
<li style="list-style-type: none">![exclaim](https://mople71.cz/img/sm/exclaim.gif) Máte-li nainstalovanou aplikaci **Chromium** / **Google Chrome**, před použitím následujícího příkazu ji musíte nejprve odinstalovat a po použití příkazu následně opět nainstalovat.</li>
<li style="list-style-type: none"><pre><code>sudo firecfg</code></pre></li>
- Aplikaci můžete spustit v sandboxu zadáním následujícího příkazu do konzole:
<li style="list-style-type: none"><pre><code>firejail nazev_aplikace
např. firejail firefox</code></pre></li>
- Tím spustíte Firefox v přednastaveném profilu &ndash; Firefox má z osobních složek přístup pouze k Ploše a Staženým souborům, data zůstávají na disku i po ukončení sandboxu => vhodné pro každodenní využití.
- Chcete-li, aby se aplikace spustila v prázdném sanboxu, který se po ukončení aplikace celý smaže, můžete použít následující příkaz:
<li style="list-style-type: none"><pre><code>firejail --private nazev_aplikace
např. firejail --private firefox</code></pre></li>
- Tato možnost se hodí v případě, kdy potřebujete otevřit rizikovou stránku, na kterou byste museli dočasně snížit bezpečnostní nastavení prohlížeče a mohli tak rizikovat kompromitaci profilu vašeho prohlížeče.
- V takovém případě se hodí znát příkaz, který Firefox spustí ve zmíněném sandboxu jako nový proces &ndash; jinak je nemožné mít otevřeno více Firefoxů ve více sandboxech.
<li style="list-style-type: none"><pre><code>firejail --private nazev_aplikace
např. firejail --private firefox</code></pre></li>
- Libovolnou aplikaci také můžete spustit bez přístupu k internetu použitím jednoduchého příkazu:
<li style="list-style-type: none"><pre><code>firejail --net=none nazev_aplikace
např. firejail --net=none evince</code></pre></li>

![idea](https://mople71.cz/img/sm/idea.gif) Více užitečných příkazů naleznete na <a href="https://firejail.wordpress.com/" target="_blank">oficiálních stránkách aplikace</a>.

<br>

### Flatpak:
Flatpak je nový způsob distribuce aplikací. Má za cíl odstranit chyby a nedostatky současné architektury &ndash; odděluje aplikace od sebe a částí OS, unifikuje instalaci aplikací pro linuxové distribuce apod.

**<span class="fe">Fedora</span>** má balíček **flatpak** předinstalovaný.

**<span class="os">openSUSE</span>** Flatpak předinstalovaný nemá, lze jej ovšem nainstalovat jednoduchým příkazem:
<pre><code>sudo zypper install flatpak</code></pre>

**<span class="ub">Ubuntu</span>** Flatpak předinstalovaný nemá, jelikož propaguje svou alternativu k Flatpaku &ndash; <a href="https://www.ubuntu.com/desktop/snappy" target="_blank">Snap</a>. Každopádně pokud se rozhodnete používat raději Flatpak než Snap, můžete jej nainstalovat následujícími příkazy:
<pre><code>sudo add-apt-repository ppa:alexlarsson/flatpak
sudo apt update
sudo apt install flatpak</code></pre>

<br>

> Návod k použití Flatpak

Několik dostupných aplikací naleznete zde: <a href="http://flatpak.org/apps.html" target="_blank">http://flatpak.org/apps.html</a>

Pokud ve vaší distribuci nebude fungovat odkaz na stáhnutí, překlikněte se do záložky <span class="green">Command Line</span> a postupujte dle instrukcí.

Flatpak aplikace lze aktualizovat následujícím příkazem:
<pre><code>flatpak update</code></pre>

#### LibreOffice:
- Odinstalujte současnou verzi LibreOffice.
- Otevřete si <span class="green">Terminál</span>. Zadejte do něj následující příkazy:
<li style="list-style-type: none"><pre><code>flatpak remote-add --if-not-exists gnome https://sdk.gnome.org/gnome.flatpakrepo
wget http://download.documentfoundation.org/libreoffice/flatpak/latest/LibreOffice.flatpak
flatpak install --bundle LibreOffice.flatpak</code></pre></li>
- Na všechny otázky odpovězte kladně.

> Flathub

Flathub je oficiální platforma pro distribuci Flatpak aplikací. Naleznete v ní vcelku malý počet aplikací, který se bude pouze zvyšovat. Například Audacity, Corebird, Blender, **Steam**, GeoGebra, Inkscape, Warmux,...

#### Steam:
- Otevřete si <span class="green">Terminál</span>. Zadejte do něj následující příkazy:
<li style="list-style-type: none"><pre><code>flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
flatpak install flathub com.valvesoftware.Steam
</code></pre></li>
- Bude-li vám v průběhu nabídnut výběr mezi *gnome* a *flathub* repozitáři, zvolte <span class="green">flathub</span>.
- Spusťte Steam a doufejte, že vámi oblíbené hry jsou ve flatpaku funkční. Seznam otestovaných her naleznete <a href="https://github.com/flathub/com.valvesoftware.Steam/wiki/Tested-Games" target="_blank">zde</a>.

<br><br><hr><br>

## Zabezpečení internetového prohlížeče:
Z bezpečnostního hlediska doporučuji prohlížeč <span class="green">Chromium</span>. Používá špičkovou implementaci sandboxu a jeho kód je na velmi dobré úrovni. Celkově je v ohledu bezpečnosti mnohem dále než **Mozilla Firefox**.

<!--- ./browsers.md -->

<br><br><hr>

<h3 class="nocol">To je vše. Stay safe! ![smile](https://mople71.cz/img/sm/smile.gif)</h3>
