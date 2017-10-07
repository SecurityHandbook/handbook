# FAQ &ndash; OS Linux
Linux se díky svému minoritnímu zastoupení na desktopech těší řádově menší pozornosti hackerů nežli Windows, většina malware pro Linux je určena serverům. Malware pro desktopové linuxové distribuce ovšem existuje &ndash; sice v mnohonásobně menším množství, ale existuje. Mimo jiné, exploit kity se poslední dobou snaží být co nejvíce multiplatformní a např. JS ransomware spolehlivě funguje i přes prohlížeč na Linuxu.

Není tedy pravda, že malware na desktopový Linux neexistuje. Pouze máte o něco menší šanci, že na něj někdy narazíte. Pokud by se ovšem tak stalo, je dobré být předem připraven. V této sekci naleznete několik jednoduchých tipů na účinné zvýšení úrovně zabezpečení.

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
Pokud nepoužíváte a nepotřebujete IPv6 (pokud nevíte, můžete to zjistit pomocí následujícího [testu](http://www.test-ipv6.cz/), je rozumné protokol vypnout pro snížení prostoru pro útok.

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
Pokud vám zkratka DNS nic neříká, přečtěte si tento [krátký článek](https://www.nic.cz/page/312/o-domenach-a-dns/).

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
<abbr title="Mandatory Access Control">MAC</abbr> se stal důležitou součástí bezpečnostního modelu linuxových distribucí. Podrobné vysvětlení naleznete např. na [Wikipedii](https://cs.wikipedia.org/wiki/Mandatory_access_control).

**<span class="fe">Fedora</span>** používá implementaci **SELinux**.

**<span class="os">openSUSE</span>** používá implementaci **AppArmor**, MAC poskytující menší možnosti ochrany než např. SELinux.

**<span class="ub">Ubuntu</span>** používá implementaci **AppArmor**, MAC poskytující menší možnosti ochrany než např. SELinux.

<br>

### Virtualizace:
Virtualizace může být velmi bezpečný způsob ochrany před malware (záleží na způsobu implementace), jelikož odděluje požadovanou část OS od fyzického OS.

Nejčastější implementací virtualizace je **sandbox**. Existují dva druhy sandboxu:

- sandbox nativně integrovaný v aplikaci (např. Chromium)
- externí sandbox &ndash; např. Flatpak

Sandbox nativně integrovaný v aplikaci je nejúčinnější možností implementace sandboxu, jelikož je nastaven přesně na míru dané aplikaci.

Externí sandbox není zdaleka tak účinný jako sandbox integrovaný v aplikaci a při porovnání ponechává větší prostor pro exploitaci, ale stále může být vcelku účinný a přirozeně je nesrovnatelně lepší, nežli žádný sandbox.

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

> Instalace Flatpak verze LibreOffice

- Odinstalujte současnou verzi LibreOffice, máte-li nějakou nainstalovanou.
- Otevřete si <span class="green">Terminál</span>. Zadejte do něj následující příkazy:
<li style="list-style-type: none"><pre><code>flatpak remote-add --if-not-exists gnome https://sdk.gnome.org/gnome.flatpakrepo
wget https://download.documentfoundation.org/libreoffice/flatpak/latest/LibreOffice.flatpak
flatpak install --bundle LibreOffice.flatpak</code></pre></li>
- Na všechny otázky odpovězte kladně.

> Flathub

Flathub je oficiální platforma pro distribuci Flatpak aplikací. Naleznete v ní vcelku malý počet aplikací, který se bude pouze zvyšovat. Například Audacity, Corebird, Blender, **Steam**, GeoGebra, Inkscape, Warmux,...

#### Steam:
- Otevřete si <span class="green">Terminál</span>. Zadejte do něj následující příkazy:
<li style="list-style-type: none"><pre><code>flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
flatpak install flathub com.valvesoftware.Steam</code></pre></li>
- Bude-li vám v průběhu nabídnut výběr mezi *gnome* a *flathub* repozitáři, zvolte <span class="green">flathub</span>.
- Spusťte Steam a doufejte, že vámi oblíbené hry jsou ve flatpaku funkční. Seznam otestovaných her naleznete [zde](https://github.com/flathub/com.valvesoftware.Steam/wiki/Tested-Games).

> Instalace GNOME aplikací

GNOME poskytuje flatpak verzi pro většinu svých aplikací. Ve Flatpaku by správně měly být všechny aplikace ve výchozím nastavení, na to si ovšem budeme ještě muset chvíli počkat. (*Fedora 28?*)

Je důležité ve Flatpaku mít alespoň nejrizikovější aplikace &ndash; **Evince** (prohlížeč PDF) a **Eye of GNOME** (prohlížeč obrázků).

- Otevřete si <span class="green">Terminál</span>. Zadejte do něj následující příkazy:
<li style="list-style-type: none"><pre><code>flatpak remote-add --if-not-exists gnome https://sdk.gnome.org/gnome-apps.flatpakrepo
flatpak update
flatpak install flathub org.gnome.eog
flatpak install gnome-apps org.gnome.Evince</code></pre></li>
- Následně můžete odebrat původní verzi *Eye of GNOME*:
<li style="list-style-type: none"><pre><code>sudo dnf remove eog</code></pre></li>
- Původní verze *Evince* odebrat nelze, jelikož poskytuje náhledy ve správci souborů a také náhledy tisku. Lze ovšem jednoduše odebrat jeho ikonu ze seznamu aplikací:
<li style="list-style-type: none"><pre><code>sudo rm /usr/share/applications/evince.desktop</code></pre></li>
- Otevřete si <span class="green">Nastavení</span>. Rozklikněte kategorii **Podrobnosti** a následně zvolte podkategorii <span class="green">Výchozí aplikace</span>.
- Nastavte Flatpak verzi *Eye of GNOME* aplikací jako výchozí:
<li style="list-style-type: none">![lnxdapp](https://faq.mople71.cz/img/cs/lnxdapp.png)</li>
- Nalezněte libovolný **PDF** soubor. Klikněte na něj pravým tlačítkem a zvolte <span class="green">Otevřít jinou aplikací</span>.
- V seznamu zvolte Flatpak verzi **Prohlížeč dokumentů** a klikněte na tlačítko <span class="green">Vybrat</span>.
<li style="list-style-type: none">![lnxdapp1](https://faq.mople71.cz/img/cs/lnxdapp1.png)</li>

<br><br><hr><br>

## Zabezpečení internetového prohlížeče:
Z bezpečnostního hlediska doporučuji prohlížeč <span class="green">Chromium</span>. Používá špičkovou implementaci sandboxu a jeho kód je na velmi dobré úrovni. Celkově je v ohledu bezpečnosti mnohem dále než **Mozilla Firefox**.

<!--- ./browsers.md -->

<br><br><hr>

<h3 class="nocol">To je vše. Stay safe! ![smile](https://mople71.cz/img/sm/smile.gif)</h3>
