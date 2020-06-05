# FAQ – OS Linux
Linux se díky svému minoritnímu zastoupení na desktopech v porovnání s OS Windows těší řádově menší pozornosti hackerů – většina malware pro Linux je směřována pouze na servery. Malware pro desktopové linuxové distribuce také existuje, akorát v mnohonásobně menším množství. Ačkoliv tedy je stav některých desktopových linuxových distribucí z pohledu bezpečnosti tristní, v praxi je riziko infikace nižší nežli u jiných OS. Moderní *exploit kity* jsou ovšem často multiplatformní a jejich počet roste. Dostatečné zabezpečení OS je proto nezbytné.

Tato sekce FAQ je určena běžným a středně pokročilým uživatelům. Sekci pro pokročilé naleznete [zde](https://securityhandbook.cz/cs/lnx/adv.php#lnx).

#### FAQ se dělí na několik sekcí:
- [Doporučené distribuce](#lnx1)
- [Základní bezpečnostní nastavení](#lnx2)
- [Ochrana proti malware](#lnx3)
- [Zabezpečení internetového prohlížeče](#lnx4)

<br>

## Doporučené distribuce:
- **<span class="fe">Fedora</span>**: https://getfedora.org/cs/workstation/
- **<span class="os">openSUSE</span>** (Leap): https://www.opensuse.org/#Leap
- **<span class="ub">Ubuntu</span>**: https://www.ubuntu.com/desktop

V sekci OS Linux naleznete tipy převážně pro distribuci **Fedora**.

**<span class="fe">Fedora</span>** je nejlepší volbou pro běžného uživatele, jelikož je v základu vcelku bezpečně nastavená. Používá GNOME, nabízí uživateli možnost snadné instalace Flatpak aplikací, obsahuje robustní implementaci SELinux a má velmi vysoké standardy na své balíčky – všechny musí mít důležité mitigace proti memory corruption exploitům. Mimo technické funkce nabízí stabilní nejnovější software. Jediný problém zmíněné distribuce jsou občasné pomalejší aktualizace webových prohlížečů z důvodu mnoha vlastních úprav (patchů), které je nutno pro každou novou verzi aktualizovat.

U některých kroků také naleznete pokyny pro distribuci **<span class="os">openSUSE</span>** a distribuci **<span class="ub">Ubuntu</span>**, která je velmi populární, z hlediska bezpečnosti ovšem o něco méně vhodná.

Většina obsažených informací je platná i pro jiné distribuce, pouze se bude lišit přesný postup aplikace různých kroků – syntax.

### Doporučené grafické prostředí:
Z bezpečnostního hlediska je rozumnou volbou prostředí [GNOME](https://www.gnome.org/), jelikož používá Wayland místo X.org a podílí se na vývoji Flatpaku. Výjimku tvoří rozhraní *GNOME Classic*, které využívá primárně X.org – není tedy doporučeno.

<br><br><hr><br>

## Základní bezpečnostní nastavení:
### Oddělení /tmp oddílu během instalace a jeho bezpečné připojení:
Malware se často spouští z dočasných složek. Zakázání exekuce spustitelných souborů v dočasných složkách (konkrétně /tmp) tedy dokáže vyřadit z provozu mnoho rodin malware.

> Návod

- Při instalaci OS otevřete možnosti rozdělení disků.
- V sekci **Konfigurace úložiště** zvolte možnost <span class="green">Pokročilé uživatelské nastavení (Blivet-GUI)</span> a v levém horním rohu klikněte na <span class="green">Hotovo</span>.
- V levém sloupci zvolte disk, na který chcete OS instalovat a klikněte na tlačítko <span class="green">+</span> pro přidání oddílu.
- Jako **typ zařízení** vyberte <span class="green">Oddíl</span>.
- Do kolonky **velikost** zadejte <span class="blue">0,5 GiB</span>.
- Jako **souborový systém** zvolte <span class="green">ext4</span>, jako **label** zadejte *boot*, **přípojný bod** nastavte na "<span class="red">/boot</span>" a následně klikněte na tlačítko <span class="green">Budiž</span>.
<li style="list-style-type: none">![lnxtmp](https://securityhandbook.cz/img/cs/lnxtmp.png)</li>
- V pravém sloupci kliknutím označte **volné místo** a klikněte na tlačítko <span class="green">+</span> pro přidání dalšího oddílu.
- Jako **typ zařízení** vyberte <span class="green">Oddíl</span>.
- Do kolonky **velikost** zadejte velikost, kterou chcete vyhradit pro OS, akorát od ní odečtěte <span class="blue">4 GiB</span>.
- Jako **souborový systém** zvolte <span class="green">btrfs</span>, jako **přípojný bod** nastavte na "<span class="red">/</span>" a následně klikněte na tlačítko <span class="green">Budiž</span>.
<li style="list-style-type: none">![lnxtmp1](https://securityhandbook.cz/img/cs/lnxtmp1.png)</li>
- V pravém sloupci kliknutím označte **volné místo** a klikněte na tlačítko <span class="green">+</span> pro přidání dalšího oddílu.
- Jako **typ zařízení** vyberte <span class="green">Oddíl</span>.
- Do kolonky **velikost** zadejte <span class="blue">2,0 GiB</span> (budete muset přepnout jednotky na *GiB*).
- Jako **souborový systém** zvolte <span class="green">ext4</span>, jako **label** zadejte *tmp*, **přípojný bod** nastavte na "<span class="red">/tmp</span>" a následně klikněte na tlačítko <span class="green">Budiž</span>.
<li style="list-style-type: none">![lnxtmp2](https://securityhandbook.cz/img/cs/lnxtmp2.png)</li>
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
<li style="list-style-type: none">![lnxfstab](https://securityhandbook.cz/img/en/lnxfstab.png)</li>
- Stiskněte klávesovou zkratku <span class="green">Ctrl + X</span>. Pro uložení změn v souboru stiskněte tlačítko <span class="red">Y</span> a následně <span class="green">Enter</span>.
- Budete vráceni do konzole. Zadejte do ní následující příkazy:
<li style="list-style-type: none"><pre><code>exit
exit</code></pre></li>
- Restartujte OS.

<br>

### Práce pod Běžným uživatelem:

OS Linux má dva typy uživatelských účtů: <span class="green">Běžný uživatel</span> a <span class="green">Správce</span>.

Z hlediska bezpečnosti je nezbytné provádět denní činnosti pod Běžným uživatelem, jelikož má omezená oprávnění, která jsou pro práci plně dostačující. Pokud se do OS i přes všechny vrstvy ochrany dostane malware, infikuje pouze uživatelský účet – na infikaci OS nebude mít potřebná oprávnění.

<div class="alert exclaim"><p><em class="icon-attention"></em>**Varování**<br>
Jedná se o naprostý základ zabezpečení OS, bez kterého jsou veškerá další opatření zbytečná.</p></div>

> Přidání účtu Správce a změna stávajícího uživatele na Běžného

- Otevřete si <span class="green">Nastavení</span>. Rozklikněte kategorii **Úživatelé**.
- Klikněte na <span class="green">Odemknout&#8230;</span> a zadejte své heslo.
- V horním pravém rohu zvolte možnost <span class="green">Přidat uživatele&#8230;</span>
- Zobrazí se dialog pro přidání uživatele. **Typ účtu** zvolte <span class="green">Správce</span>.
- Do textového pole *Celé jméno* název účtu Správce (např. **Admin**).
- V sekci **Heslo** zvolte možnost <span class="green">Nastavit heslo nyní</span> a zvolte pro něj silné bezpečné heslo.
- Tlačítkem <span class="green">Přidat</span> v horním pravém rohu účet vytvořte.
<li style="list-style-type: none">![lnxus](https://securityhandbook.cz/img/cs/lnxus.png)</li>
- Odhlaste se z vašeho účtu a přihlaste se jako **Admin**.
- Otevřete si <span class="green">Nastavení</span>. Rozklikněte kategorii **Úživatelé**.
- Klikněte na <span class="green">Odemknout&#8230;</span> a zadejte heslo administrátora.
- V seznamu uživatelů nalezněte svůj uživatelský účet, klikněte na něj a odeberte mu pravomoci <span class="green">Správce</span>.
<li style="list-style-type: none">![lnxus1](https://securityhandbook.cz/img/cs/lnxus1.png)</li>
- Odhlaste se z administrátorského účtu a přihlaste se zpět na svůj uživatelský účet.

<br>

### Bezpečné nastavení sítě:

> Nastavení DNS

Pokud vám zkratka DNS nic neříká, podívejte se na následující [jednoduchou stránku](http://www.jakfungujedns.cz/).

- Otevřete si <span class="green">Nastavení</span>.
- Rozklikněte položku <span class="green">Wi-Fi</span> nebo <span class="green">Síť</span> v závislosti na druhu vašeho připojení.
- V seznamu nalezněte příslušné spojení a otevřete jeho nastavení.
<li style="list-style-type: none">![lnxnet](https://securityhandbook.cz/img/cs/lnxnet.png)
![lnxnet1](https://securityhandbook.cz/img/cs/lnxnet1.png)</li>
- Přepněte se do záložky IPv4 a v sekci **DNS** vypněte možnost <span class="green">Automatické</span>.
- Do řádku vepište následující DNS servery:
<li style="list-style-type: none"><pre><code>193.17.47.1,185.43.135.1</code></pre></li>
<li style="list-style-type: none">![lnxnet2](https://securityhandbook.cz/img/cs/lnxnet2.png)</li>
- Pro *IPv6* aplikujte obdobný postup s následujícími servery:
<li style="list-style-type: none"><pre><code>2001:148f:ffff::1,2001:148f:fffe::1</code></pre></li>
- Klikněte na tlačítko <span class="green">Použít</span> a nastavení zavřete.

> Zakázání IPv6

Pokud nepoužíváte a nepotřebujete IPv6 (nejste-li si jistí, můžete využít následující [test](https://test-ipv6.cz/)), je rozumné protokol vypnout pro snížení prostoru pro útok.

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

### Další bezpečnostní nastavení:
- Vypněte AutoPlay/AutoRun:
  - Otevřete si <span class="green">Nastavení</span> a rozklikněte kategorii **Zařízení**.
  - Klikněte na položku <span class="green">Výměnná média</span>.
  - Zatrhněte možnost <span class="green">Nikdy se nedotazovat nebo spouštět programy na vloženém médiu</span>.
  <li style="list-style-type: none">![lnxar](https://securityhandbook.cz/img/cs/lnxar.png)</li>
- Vypněte sdílení:
  - Otevřete si <span class="green">Nastavení</span> a klikněte na položku <span class="green">Sdílení</span>.
  - Zkontrolujte, že je sdílení vypnuto, případně napravte.
  <li style="list-style-type: none">![lnxshare](https://securityhandbook.cz/img/cs/lnxshare.png)</li>

<br><br><hr><br>

## Ochrana proti malware:
Jako nejúčinnější metoda ochrany proti malware se osvědčila bezpečnostní konfigurace skládající se z více vrstev (*&bdquo;layered config&ldquo;*) – pokud selže jedna vrstva, nastupuje druhá. Samotný OS poskytuje jistou úroveň ochrany proti malware, která se liší v závislosti na distribuci. V základním nastavení ovšem většinou bohužel nejsou všechny bezpečnostní funkce zapnuty a/nebo korektně nastaveny.

<br>

### Aktualizace OS a SW:
Je důležité mít aktuální verzi veškerého SW, jelikož nové verze často opravují mnoho bezpečnostních chyb. Neaktuální SW je implicitně nebezpečný. Ve všech zmíněných distribucích slouží k aktualizaci SW vestavěná aplikace <span class="green">Software</span>, která kromě tradičních balíčků obstarává i aktualizaci flatpaků či firmware.

![lnxupd](https://securityhandbook.cz/img/cs/lnxupd.png)

<br>

### Firewall:
Firewall je velmi důležitá vrstva zabezpečení, která chrání OS před útoky ze sítě. *Poznámka na okraj: základem síťového zabezpečení v domácnosti je rozumný router.*

**<span class="fe">Fedora</span>** má v základu plně funkční firewall.

**<span class="os">openSUSE</span>** má v základu plně funkční firewall.

**<span class="ub">Ubuntu</span>** v základu nemá zapnutý firewall, je třeba jej zapnout příkazem:
<pre><code>sudo ufw enable</code></pre>

<br>

### MAC:
<abbr title="Mandatory Access Control">MAC</abbr> se stal důležitou součástí bezpečnostního modelu linuxových distribucí.

**<span class="fe">Fedora</span>** používá implementaci **SELinux**. **<span class="os">openSUSE</span>** a **<span class="ub">Ubuntu</span>** používají implementaci **AppArmor**, MAC poskytující menší možnosti ochrany nežli např. SELinux.

<br>

### Virtualizace:
Virtualizace může být velmi bezpečný způsob ochrany před malware v závislosti na způsobu implementace, jelikož odděluje požadovanou část OS od jeho zbytku. Standardních způsobů implementace virtualizace je několik:

- sandbox
- semivirtuální stroj (např. docker)
- virtuální stroj (VM; virtual machine)

#### Flatpak:
Sandbox je populární způsob implementace virtualizace. Existují dva druhy sandboxu:

- sandbox nativně integrovaný v aplikaci (např. *Chromium*)
- externí sandbox – např. **Flatpak**, *firejail*

Sandbox nativně integrovaný v aplikaci je nejúčinnější možností implementace sandboxu, jelikož je nastaven přesně na míru dané aplikaci. Externí sandbox nemusí být nutně účinný jako sandbox integrovaný v aplikaci, jelikož není dělaný přesně na míru určité aplikaci, a při porovnání může ponechat větší prostor pro exploitaci. Stále ovšem může být velmi účinný a přirozeně je mnohem lepší, nežli žádný sandbox.

<span class="green">Flatpak</span> je nový způsob distribuce aplikací. Má za cíl odstranit chyby a nedostatky současné architektury – odděluje aplikace od sebe a částí OS (obsahuje implementaci sandboxu), sjednocuje instalaci aplikací pro linuxové distribuce apod.

**<span class="fe">Fedora</span>** má **flatpak** předinstalovaný.

**<span class="os">openSUSE</span>** Flatpak předinstalovaný nemá, lze jej ovšem nainstalovat jednoduchým příkazem:
<pre><code>sudo zypper install flatpak</code></pre>

**<span class="ub">Ubuntu</span>** Flatpak předinstalovaný nemá, jelikož propaguje svou alternativu k Flatpaku – [Snap](https://www.ubuntu.com/desktop/snappy). Každopádně pokud se rozhodnete upřednostnit Flatpak před Snap (doporučeno), můžete jej nainstalovat následujícími příkazy:
<pre><code>sudo add-apt-repository ppa:alexlarsson/flatpak
sudo apt update
sudo apt install flatpak</code></pre>

<br>

> Návod k použití Flatpak

Většinu aplikací můžete nalézt v repozitáři [Flathub](https://flathub.org/home). Distribuce **<span class="fe">Fedora</span>** má svůj integrovaný [kontejnerový repozitář](https://registry.fedoraproject.org/). Flatpak balíčky lze spravovat pomocí vestavěné aplikace <span class="green">Software</span>.

Budete-li příkaz **flatpak** spouštět v terminálu, <span class="red">nikdy jej nespouštějte pod sudo</span>. Flatpak si o autorizaci případně požádá sám přes GNOME dialog. Níže naleznete základní terminálové příkazy pro správu flatpak aplikací.

- Výpis nainstalovaných aplikací:
<li style="list-style-type: none"><pre><code>flatpak list</code></pre></li>
- Aktualizace nainstalovaných aplikací:
<li style="list-style-type: none"><pre><code>flatpak update</code></pre></li>
- Výpis obsahu repozitáře – dostupných aplikací:
<li style="list-style-type: none"><pre><code>flatpak remote-ls <repozitář></code></pre></li>
- Instalace aplikace z repozitáře:
<li style="list-style-type: none"><pre><code>flatpak install <repozitář> <název_aplikace></code></pre></li>
- Odinstalace:
<li style="list-style-type: none"><pre><code>flatpak uninstall <název_aplikace></code></pre></li>

<span class="green">Flathub</span> je nejrozšířenější platforma pro distribuci Flatpak aplikací. Repozitář **fedora** již obsahuje část GNOME aplikací a některé populární aplikace jako *GIMP*, nicméně je stále v aktivním vývoji a ne všechny aplikace jsou v použitelném stavu.

> Přidání Flathub repozitáře

- Otevřete si <span class="green">Terminál</span>. Zadejte do něj následující příkaz:
<li style="list-style-type: none"><pre><code>flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo</code></pre></li>
- Aplikaci zavřete.
- Otevřete si <span class="green">Software</span>.
- Přesuňte se do záložky **Aktualizace** a v levém horním rohu spusťte kontrolu aktualizací.
- Po dokončení kontroly se přesuňte zpět do záložky **Procházet**.
- Aplikaci zavřete.

> Instalace GNOME aplikací

Ve Flatpaku by správně měly být všechny aplikace ve výchozím nastavení, na to si ovšem budeme ještě muset chvíli počkat. (*Fedora 34?*)

- Otevřete si <span class="green">Terminál</span>. Zadejte do něj následující příkazy:
<li style="list-style-type: none"><pre><code>sudo dnf -y remove eog evince epiphany
flatpak install fedora org.gnome.eog
flatpak install fedora org.gnome.Evince
flatpak install fedora org.gnome.Epiphany</code></pre></li>

> Instalace flatpak aplikace v GNOME Software

- Otevřete si <span class="green">Software</span>.
- Pomocí vyhledávání nalezněte a rozklikněte požadovanou aplikaci.
- V pravém horním rohu vyberte příslušný zdroj – Fedora / Flathub:
<li style="list-style-type: none">![lnxflat](https://securityhandbook.cz/img/cs/lnxflat.png)</li>
<div class="alert info"><p><em class="icon-info-circled"></em>**Info**<br>
Flatpak repozitář **Fedora** preferujte pouze u GNOME aplikací, aplikací <span class="red">GIMP</span> a <span class="red">Transmission</span>. Jinde preferujte **Flathub**.</p></div>
- Klikněte na <span class="green">Instalovat</span>.
- Instalace může trvat delší dobu v závislosti na vašem internetovém připojení, aplikace může vyžadovat runtime, která jsou objemná a musí se nejprve stáhnout.
- Po dokončení instalace aplikaci zavřete.

> Instalace flatpak LibreOffice

- Otevřete si <span class="green">Terminál</span>. Odinstalujte původní LibreOffice, které jsou součástí standardní instalace:
<li style="list-style-type: none"><pre><code>sudo dnf -y remove libreoffice*</code></pre></li>
- Nainstalujte flatpak verzi LibreOffice:
<li style="list-style-type: none"><pre><code>flatpak install flathub org.libreoffice.LibreOffice</code></pre></li>

<br>

#### Virtuální stroj:
Nejbezpečnější způsob virtualizace je emulace zařízení, kdy je virtualizován celý OS – za korektního nastavení a využití snapshotů. Po správné konfiguraci můžete virtuální stroj používat např. k vcelku bezpečnému brouzdání internetem.

Virtualizován může být libovolný OS jako Windows nebo linuxová distribuce. Pro virtualizaci OS Windows pro něj ovšem budete potřebovat dodatečnou licenci. Jednoduché nastavení a používání virtuálního počítače umožňují následující aplikace:

- [GNOME Boxes](https://wiki.gnome.org/Apps/Boxes)
- [VirtualBox](https://www.virtualbox.org/)

> Konfigurace GNOME Boxes

- Stáhněte si .iso obraz OS, který chcete virtualizovat.
- Otevřete si aplikaci <span class="green">Boxy</span>.
- Zobrazí-li se **Úvodní seznámení**, projděte jej a zavřete.
- V levém horním rohu aplikace vytvořte nový virtuální stroj.
- Klikněte na <span class="green">Soubor s obrazem operačního systému</span> a nalezněte požadovaný ISO soubor.
- Odmítněte případnou expresní instalaci.
- Upravte alokaci zdrojů tlačítkem <span class="green">Přizpůsobit</span>
- Přidělte virtuálnímu stroji alespoň *3 GiB* paměti a alespoň *22 GiB* místa na disku.
<li style="list-style-type: none">![gboxes](https://securityhandbook.cz/img/cs/gboxes.png)</li>
- Klikněte na <span class="green">Vytvořit</span>.
- Nainstalujte a nakonfigurujte OS. Následně jej vypněte.
- V seznamu na požadovaný virtuální stroj klikněte pravým tlačítkem a otevřete <span class="green">Vlastnosti</span>.
- Přesuňte se do záložky **Snímky**. Existuje-li již nějaký snapshot, ozubeným kolem vpravo otevřete jeho konfiguraci a smažte jej.
- Tlačítkem <span class="green">+</span> v dolním menu vytvořte nový snapshot.
- Ozubeným kolem vpravo otevřete jeho konfiguraci a tlačítkem <span class="green">Přejmenovat</span> si jej pojmenujte jako výchozí snapshot.
<li style="list-style-type: none">![gboxes1](https://securityhandbook.cz/img/cs/gboxes1.png)</li>
- Nyní můžete kdykoli virtuální stroj po jeho vypnutí snadno obnovit do výchozího stavu.
- Čas od času (např. 1x měsíčně) virtuální OS aktualizujte a vytvořte nový snapshot.

<br><br><hr><br>

## Zabezpečení internetového prohlížeče:
Z bezpečnostního hlediska lze doporučit prohlížeč <span class="green">Chromium</span>. Používá špičkovou implementaci sandboxu a jeho kód je na velmi dobré úrovni. Celkově je v ohledu bezpečnosti v současném stavu dále než **Mozilla Firefox**. Prohlížeč **GNOME Web (Epiphany)** není nijak zvlášť zaměřený na bezpečnost, nehodí se tedy ke každodennímu používání. Je možné jej ovšem použít jako oddělený prohlížeč pro citlivé věci jako bankovnictví apod. Prohlížeč **Brave** vychází z prohlížeče Chromium, v základu integruje blokování reklam a trackerů. Jeho sandbox aktuálně není na úrovni prohlížeče Chromium, i tak je ovšem solidní.

<!--- /browsers.md -->

<br><br><hr>

<h3 class="nocol">To je vše. Stay safe! ![smile](https://securityhandbook.cz/img/sm/smile.svg)</h3>
