# FAQ &ndash; OS Windows
Windows se jakožto nejrozšířenější desktopový OS těší velké pozornosti hackerů, jeho dostatečné zabezpečení je proto velmi důležité.
Jako nejúčinnější metoda ochrany proti malware se osvědčila bezpečnostní konfigurace skládající se z více vrstev (tzv. *layered config*) &ndash; pokud selže jedna vrstva, nastupuje druhá. Spousta běžných uživatelů spoléhá pouze na jednu tradiční vrstvu &ndash; antivir &ndash; což je z hlediska bezpečnosti tristní.
Samotný OS poskytuje jistou úroveň ochrany proti malware, která se liší v závislosti na verzi a edici OS. V základním nastavení ovšem nejsou všechny bezpečnostní funkce zapnuty a/nebo korektně nastaveny.
#### FAQ se dělí na několik sekcí:
- bezpečné nastavení OS
- vrstvy zabezpečení
- zabezpečení internetového prohlížeče
- doporučené bezpečnostní konfigurace

<br>

## Bezpečné nastavení OS
### Práce pod Standardním uživatelem:

OS Windows má dva typy uživatelských účtů: <span class="green">Standardní uživatel</span> a <span class="green">Správce</span>.

Z hlediska bezpečnosti je důležité pracovat pod Standardním uživatelem, jelikož má omezená oprávnění. Pokud se tedy do OS i přes všechna zdejší doporučení dostane malware, infikuje pouze uživatelský účet &ndash; na infikaci OS nemá potřebná oprávnění.
<span class="red">Jedná se o naprostý základ zabezpečení OS, bez kterého jsou veškerá další opatření naprosto zbytečná.</span>

> Přidání účtu Správce a změna stávajícího uživatele na Standardního:

- Otevřete si <span class="green">Nastavení</span>. Rozklikněte kategorii **Účty** a následně zvolte podkategorii <span class="green">Rodina a jiní uživatelé</span>.
- Klikněte na tlačítko <span class="green">Přidat do tohoto počítače někoho dalšího</span>.
<li style="list-style-type: none">![wntus](https://faq.mople71.cz/img/cs/wntus.png)</li>
- Otevře se dialog pro přidání nového uživatele. V levém dolním rohu klikněte na <span class="green">Nemám přihlašovací údaje této osoby</span>.
- V levém dolním rohu zvlote možnost <span class="green">Přidat uživatele bez účtu Microsoft</span>.
- Zadejte název účtu Správce (např. **Admin**) a zvolte pro něj silné zapamatovatelné heslo.
- V seznamu jiných uživatelů se zobrazí účet **Admin**. Klikněte na něj a následně zvolte <span class="green">Změnit typ účtu</span>.
<li style="list-style-type: none">![wntus1](https://faq.mople71.cz/img/cs/wntus1.png)</li>
- Zobrazí se dialog pro změnu typu účtu. Ze seznamu zvolte možnost <span class="green">Správce</span> a klikněte na <span class="green">OK</span>.
<li style="list-style-type: none">![wntus2](https://faq.mople71.cz/img/cs/wntus2.png)</li>
- Odhlaste se z vašeho účtu a přihlaste se jako **Admin**.
- Otevřete si <span class="green">Nastavení</span>. Rozklikněte kategorii **Účty** a následně zvolte podkategorii <span class="green">Rodina a jiní uživatelé</span>.
- V seznamu jiných uživatelů nalezněte svůj účet, klikněte na něj a následně zvolte <span class="green">Změnit typ účtu</span>.
- Zobrazí se dialog pro změnu typu účtu. Ze seznamu zvolte možnost <span class="green">Standardní uživatel</span> a klikněte na <span class="green">OK</span>.
- Přihlaste se zpět na svůj uživatelský účet.

> Přidání účtu Správce (starší verze Windows):

- Stiskněte kláv. zkratku ![win](https://mople71.cz/img/wkey.png) <span class="ks">+ R</span>, do textového pole zadejte:
<li style="list-style-type: none"><pre><code>control userpasswords</code></pre>
a stiskněte **Enter**.</li>
- Otevře se nastavení uživatelského účtu. Klikněte na možnost <span class="green">Spravovat jiný účet</span> a vytvořte Standardní účet s omezenými oprávněními, ze kterého můžete prohlížet internet apod.

<br>

### Aktualizace OS a SW

Je důležité mít aktuální verzi veškerého SW, jelikož nové verze často opravují mnoho bezpečnostních chyb. Neaktuální děravý SW je implicitně nebezpečný.

Windows by se měly ve výchozím nastavení aktualizovat samy (v edici Home automatické aktualizace dokonce nelze vypnout). Mnohé důležité aplikace (např. prohlížeče) se obvykle aktualizují automaticky.

Pro kontrolu aktualizací ostatního SW můžete použít aplikaci <span class="green">Heimdal Free</span>, která běží na pozadí a upozorní vás v případě neaktuálního SW, případně jej sama aktualizuje, automatické aktualizace ovšem teoreticky mohou způsobit problémy. Návod k *Heimdal Free* naleznete v sekci [Ostatní aplikace](#win2.6).

> Kontrola nastavení aktualizací OS (starší verze Windows):

- Stiskněte kláv. zkratku ![win](https://mople71.cz/img/wkey.png) <span class="ks">+ R</span>, do textového pole zadejte:
<li style="list-style-type: none"><pre><code>wuapp</code></pre>
a stiskněte **Enter**.</li>
- V levém panelu klikněte na tlačítko <span class="green">Změnit nastavení</span>.
- Zkontrolujte, že **důležité aktualizace** mají zvolenou možnost <span class="green">Instalovat aktualizace automaticky (doporučeno)</span>, případně napravte.
- Zkontrolujte, že je <span style="color: #BF0000">odstraněné</span> zatržítko u možnosti <span class="green">Získávat doporučené aktualizace stejným způsobem jako důležité aktualizace</span>, případně napravte.
- Klikněte na <span class="green">OK</span> a okno zavřete.

<br>

### User Account Control

User Account Control je důležitá součást bezpečnostního modelu OS od Windows Vista, kde se dočkala obrovské kritiky a ve Windows 7 proto byla v základním nastavení oslabena. Vypnutí UAC je z hlediska bezpečnosti sebevražda. Naopak je doporučeno nastavení UAC upravit na ještě přísnější úroveň.

> Nastavení UAC:

- Stiskněte kláv. zkratku ![win](https://mople71.cz/img/wkey.png) <span class="ks">+ R</span>, do textového pole zadejte:
<li style="list-style-type: none"><pre><code>useraccountcontrolsettings</code></pre>
a stiskněte **Enter**.</li>
- Otevře se nastavení UAC. To změňte na nejvyšší možnost.
<li style="list-style-type: none">![uac](https://faq.mople71.cz/img/cs/uac.png)</li>
- Klikněte na <span class="green">OK</span>.

<br>

### Vypnutí nebezpečných služeb a funkcí Windows

![idea](https://mople71.cz/img/sm/idea.gif) Pokročilejší si skript mohou upravit &ndash; je v něm několik zakomentovaných bezpečnostních opatření, které nemohou být aplikovány širokopásmově...

![batch](https://mople71.cz/img/bat.png) **SafeSVC**:
- Stáhněte si [SafeSVC](https://mople71.cz/safesvc.zip).
- Uložte a obsah archivu vyextrahujte <span class="blue">na Plochu</span>.
- Na skript jménem <span class="green">safesvc</span> klikněte pravým tlačítkem a zvolte možnost: ![admin](https://mople71.cz/img/admin.png) **Spustit jako správce**.
- Nechte skript pracovat, na konci procesu vám řekne o souhlas k restartu OS.

#### Bezpečné nastavení sítě:
> Konfigurace síťového adaptéru + DNS

- Stiskněte kláv. zkratku ![win](https://mople71.cz/img/wkey.png) <span class="ks">+ R</span>, do textového pole zadejte:
<li style="list-style-type: none"><pre><code>ncpa.cpl</code></pre>
a stiskněte **Enter**.</li>
- Otevře se seznam síťových adaptérů. Klikněte na první adaptér (obvykle ethernet) pravým tlačítkem a zvolte možnost <span class="green">Vlastnosti</span>.
<li style="list-style-type: none">![wntnet](https://faq.mople71.cz/img/cs/wntnet.png)</li>
- V seznamu odškrtněte všechny nepotřebné položky. Běžným uživatelům stačí ponechat pouze <span class="green">Sdílení souborů a tiskáren v sítích Microsoft</span>, <span class="green">Protokol IP verze 4 (TCP/IPv4)</span> a <span class="green">Protokol IP verze 6 (TCP/IPv6)</span>.
- Pokud nesdílíte žádnou tiskárnu v síti a nepoužíváte IPv6 (pokud nevíte, zdali používáte IPv6, můžete to zjistil pomocí následujícího rychlého [online testu](http://www.test-ipv6.cz/)\), můžete pro vyšší bezpečnost ponechat zaškrtnutý pouze <span class="green">Protokol IP verze 4 (TCP/IPv4)</span>.
<li style="list-style-type: none">![wntnet1](https://faq.mople71.cz/img/cs/wntnet1.png)</li>
- Klikněte na **Protokol IP verze 4 (TCP/IPv4)** a zvolte možnost <span class="green">Vlastnosti</span>.
<li style="list-style-type: none">![wntnet2](https://faq.mople71.cz/img/cs/wntnet2.png)</li>

![arrow](https://mople71.cz/img/sm/arrow.gif) <span class="green">Nyní nastavíme bezpečné DNS servery.</span>
- Pokud nevíte, co DNS je, přečtěte si tento [krátký článek](https://www.nic.cz/page/312/o-domenach-a-dns/).
- Doporučuji použít DNSSEC. Ale můžete si vybrat z mnoha DNS serverů, zde je pár příkladů:
<li style="list-style-type: none"><pre><code>CZ.NIC DNSSEC:        217.31.204.130, 193.29.206.206
Adguard DNS:          176.103.130.130, 176.103.130.131
OpenDNS:              208.67.222.222, 208.67.220.220</code></pre></li>
- Po zvolení DNS serverů se přepněte zpět do okna Vlastností IPv4 protokolu.
- Klikněte na <span class="green">Použít následující adresy serverů DNS</span> a do kolonek vepište vámi zvolené DNS.
<li style="list-style-type: none">![wntnet3](https://faq.mople71.cz/img/cs/wntnet3.png)</li>
- Klikněte na <span class="green">OK</span> a okno zavřete.

![arrow](https://mople71.cz/img/sm/arrow.gif) <span class="green">Stejný postup aplikujte pro všechny síťové adaptéry v seznamu (obvykle WLAN).</span>

<br>

### Ostatní bezpečnostní nastavení

- Vypněte Usnadnění přístupu na přihlašovací obrazovce &ndash; součást skriptu **SafeSVC**.
- Vypněte AutoPlay:
    - Otevřete si <span class="green">Nastavení.</span> Rozklikněte kategorii **Zařízení** a následně zvolte podkategorii <span class="green">Automatické přehrávání</span>.
    - Klikněte na tlačítko <span class="green">Přidat do tohoto počítače někoho dalšího</span>.
    - Automatické přehrávání vypněte.
    <li style="list-style-type: none">![autoplay](https://faq.mople71.cz/img/cs/autoplay.png)</li>
- Vypněte Remote Assistance:
    - Stiskněte kláv. zkratku ![win](https://mople71.cz/img/wkey.png) <span class="ks">+ R</span>, do textového pole zadejte:
    <li style="list-style-type: none"><pre><code>sysdm.cpl</code></pre>
a stiskněte **Enter**.</li>
    - Zobrazí se Vlastnosti systému.
    - Přesuňte se do záložky **Vzdálený přístup** a odstraňte zatržítko u položky <span class="green">Povolit připojení vzdálené pomoci k tomuto počítači</span>.
    <li style="list-style-type: none">![sysdm](https://faq.mople71.cz/img/cs/sysdm.png)</li>
    - Klikněte na <span class="green">OK</span>.

<br><br><hr><br>

## Vrstvy zabezpečení OS Windows:
- antivirus / antimalware
- firewall
- anti-executable
- anti-exploit
- virtualizace
- užitečné aplikace

Vrstev zabezpečení existuje mnohem více a spousta lidí jich kombinuje desítky dohromady. Osobně to považuji za nerozumné, kombinování příliš mnoho vrstev zvětšuje prostor pro exploitaci a ve finále má spíše opačný účinek. Cílem by mělo být použít co nejméně aplikací třetích stran k dosáhnutí účinného zabezpečení. Níže si rozebereme jednotlivé vrstvy.

<br>

### Antivirus / Antimalware:
Antivirus nebo antimalware (AV/M) je uživateli chápán jako základní vrstva zabezpečení, která stačí k zabezpečení OS. To již ovšem není tak úplně pravda.

> Rozebrání problematiky antivirů

Tradiční mechanismus antiviru funguje na bázi databáze (někdy také nazýváno podpisy) &ndash; detekuje známý malware, jejichž otisk má v databázi. V dnešní době již antiviry mají tzv. heuristiku, kdy spustitelný soubor vyhodnocují na základě jeho aktivit po spuštění (obvykle vzorek testují v izolovaném prostředí &ndash; sandboxu). Tato metoda ovšem není ani z daleka dokonalá ze dvou důvodů. Zaprvé, tato metoda stále detekuje malware na základě předvolených pravidel, které u vzorku pozoruje. Pokud vzorek provede škodlivou akci, která ale není v heuristickém systému daného antiviru označena jako škodlivá, heuristika vyhodnotí vzorek jako neškodný. Zadruhé, mnoho vzorků malware je schopno poznat, že je spuštěno v sandboxu a žádné škodlivé aktivity neprovést. V takovém případě bude vzorek také vyhodnocen jako neškodný.
Další problém antivirů je ten, že většina z nich je stará &ndash; mají starý kód který je tak komplexní, že jej vývojáři nebudou přepisovat, pouze záplatovat a nabalovat na něj nové funkce. Z tohoto důvodu je mnoho antivirů náchylných na hackerské postupy klidně 10 let staré.
Z výše uvedených důvodů tedy není bezpečné mít antivirus jako hlavní &ndash; natož jedinou &ndash; vrstvu zabezpečení. Antivirus ovšem stále má v bezpečnostní konfiguraci místo.

<span class="green">Windows Defender</span> integrovaný ve **Windows 8.1 Update 3** a **Windows 10** dosáhl úrovně, kdy dostatečně pokrývá tradiční vstrvu zabezpečení. Již tedy není nutné instalovat antivirus třetí strany, jehož kvalita kódu je řádově menší a v OS mnohdy provádí v porovnání s integrovaným řešením naprosté šílenosti.

Ve verzi OS **Windows 10 Fall Creators Update** se <span class="green">Windows Defender</span> dočkal výrazného zlepšení. Mimo jiné nově nabízí možnost nastavení *chráněných složek*, do kterých je následně zakázán přístup podezřelým procesům (tzv. *Řízený přístup ke složkám*) a GUI pro ovládání *anti-exploit mitigací* implementovaných v samotném OS (více informací k tomuto naleznete v sekci [anti-exploit](#win2.4)\).

> Ochrana před viry a hrozbami &ndash; nastavení

- Otevřete si <span class="green">Centrum zabezpečení v programu Windows Defender</span>.
- Přesuňte se do kategorie **Ochrana před viry a hrozbami** a otevřete <span class="green">Nastavení ochrany před viry a hrozbami</span>.
- Zkontrolujte konfiguraci ochrany a případně opravte:
<li style="list-style-type: none">![wd](https://faq.mople71.cz/img/cs/wd.png)</li>

> Řízení aplikací a prohlížečů &ndash; nastavení

- Přesuňte se do kategorie **Řízení aplikací a prohlížečů**.
- Zkontrolujte konfiguraci SmartScreen filtru a případně opravte:
<li style="list-style-type: none">![wd3](https://faq.mople71.cz/img/cs/wd3.png)</li>

> Konfigurace Řízeného přístupu ke složkám

- Přesuňte se do kategorie **Ochrana před viry a hrozbami** a otevřete <span class="green">Nastavení ochrany před viry a hrozbami</span>.
- Zapněte <span class="green">Řízený přístup ke složkám</span> a následně otevřete <span class="green">Chráněné složky</span>.
<li style="list-style-type: none">![wd1](https://faq.mople71.cz/img/cs/wd1.png)</li>
- Klikněte na <span class="green">Přidat chráněnou složku</span>.
- Nalezněte svojí složku **Dokumenty** v levém panelu, zvolte ji a následně klikněte na <span class="green">Vybrat složku</span>.
<li style="list-style-type: none">![wd2](https://faq.mople71.cz/img/cs/wd2.png)</li>
- Obdobným způsobem přidejte na seznam veškeré důležité osobní složky na disku.

> Povolení aplikace v Řízeném přístupu ke složkám (příklad: Heimdal Free)

- Při instalaci některých aplikací budete muset dočasně **Řízený přístup ke složkám** zakázat.
- Otevřete <span class="green">Povolené aplikace v Řízeném přístupu ke složkám</span>.
<li style="list-style-type: none">![wd1b](https://faq.mople71.cz/img/cs/wd1b.png)</li>
- Klikněte na <span class="green">Přidat povolenou aplikaci</span>.
<li style="list-style-type: none">![wd1c](https://faq.mople71.cz/img/cs/wd1c.png)</li>
- Nalezněte **Heimdal Free** a přidejte postupně jeho spustitelné programy na seznam.
<li style="list-style-type: none">![hf2](https://faq.mople71.cz/img/en/hf2.png)</li>
- **Řízený přístup ke složkám** následně opětovně povolte.

<br>

Pro nižší verze Windows lze instalaci antiviru třetí strany pochopit, jelikož OS nemá integrované AV/M řešení.

> Doporučené antiviry pro Windows 8 a níže

#### Bezplatná řešení:
- [Sophos Home](https://www.sophos.com/en-us/lp/sophos-home.aspx) &ndash; anglické rozhraní, špičková administrace
- [Microsoft Security Essentials](https://www.microsoft.com/cs-cz/download/details.aspx?id=5201) &ndash; české rozhraní, substituce Defenderu pro Windows 7 a Windows Vista
- [Bitdefender Free](https://www.bitdefender.com/solutions/free.html) &ndash; anglické rozhraní

#### Placená řešení:
- [Emsisoft Anti-Malware](https://www.emsisoft.com/en/software/antimalware/) &ndash; anglické rozhraní
- [F-Secure](https://www.f-secure.com/en/web/home_global/safe?icid=1526) &ndash; české rozhraní
- [Bitdefender](https://www.bitdefender.com/solutions/internet-security.html) &ndash; anglické rozhraní, existuje i [česká verze](https://www.bitdef.cz/)

<br>

### Firewall:

Firewall je velmi důležitá vrstva zabezpečení, která chrání OS před útoky ze sítě. Windows obsahují vestavěný <span class="green">Windows Firewall</span> (WF), který je na velmi dobré úrovni a plně dostačující (spousta AV/M produktů přestala vyvíjet vlastní FW a maximálně nabízet alternativní rozhraní pro Windows Firewall). *Poznámka na okraj: základem síťového zabezpečení v domácnosti je rozumný router.*

Základní nevýhoda WF pro běžné uživatele je absence jakéhokoli intuitivního rozhraní. Velmi jednoduché rozhraní naleznete v <span class="green">Centru zabezpečení v programu Windows Defender</span>.

<span class="red">Comodo Firewall</span>. Velmi oblíbená alternativa. Ano, je intuitivnější a obsahuje HIPS. Na druhou stranu, osobně důrazně nedoporučuji jakýkoli produkt od firmy **Comodo**.

**Windows Firewall** je v základu nastaven na blokování příchozí komunikace, která není explicitně povolena. Chcete-li posunout bezpečnost na výrazně vyšší úroveň, je dobrý nápad nastavit FW na blokování veškeré odchozí komunikace, která není explicitně povolena. V nejnovější verzi Windows je ovšem takové nastavení problematické, a návod proto naleznete pouze v FAQ pro pokročilé.

<br>

### Anti-executable:
Anti-executable je jedna z nejúčinnějších vrstev ochrany. Jak napovídá název, anti-executable řešení zabraňuje spuštění malware.

Správný anti-executable funguje na principu *whitelistu* &ndash; má nastaveno, které spustitelné soubory povolit, a při spuštění neznámého souboru zobrazí uživateli dialog pro povolení/zakázání, případně souboru rovnou zabraní spustit se. Nastavení whitelistu není úkol pro běžné uživatele, existují ovšem i řešení, která umí whitelist vytvořit prakticky bez uživatelské interakce.

#### Přehled anti-executable řešení:
- [VoodooShield](https://voodooshield.com/) (VS)
- [NVT Anti-AutoExec](http://www.novirusthanks.org/products/anti-autoexec/)
- [AppGuard](https://www.appguard.us/personal/#purchase) (AG)
- [NVT ExeRadarPro](http://www.novirusthanks.org/products/exe-radar-pro/) (NVT ERP)
- [AppLocker](https://technet.microsoft.com/cs-cz/library/dd759117.aspx)
- [Software Restrtiction Policies](https://technet.microsoft.com/cs-cz/library/hh831534.aspx) (SRP)

<span class="red">VoodooShield</span> je nejpřívětivější anti-executable a nejlepší volba pro obyčejné uživatele. Kromě placené verze poskytuje i bezplatnou pro nekomerční využití, která poskytuje srovnatelnou ochranu, akorát nenabízí možnost rozšířené konfigurace, což běžnému uživateli nevadí. V základu je nakonfigurován bezpečně. Bohužel zatím nenabízí české rozhraní.

> Instalace a konfigurace VoodooShield

- Stáhněte si [VoodooShield](https://voodooshield.com/#download).
- Aplikaci nainstalujte.
- Vyčkejte na dokončení konfigurace aplikace a při dotázání zvolte <span class="green">Application Whitelisting Mode</span>. Uvítací okno následně zavřete.
- Klikněte pravým tlačítkem na ikonu aplikace v hlavním panelu a vyberte možnost <span class="green">Hide</span>, čímž skryjete widget aplikace z pracovního prostoru.
- Klikněte pravým tlačítkem na ikonu aplikace v hlavním panelu a zvolte mód <span class="green">Training</span>.
<li style="list-style-type: none">![vs](https://faq.mople71.cz/img/en/vs.png)</li>
- Nyní se VoodooShield učí aplikace, které používáte, a povoluje je. V tréninkovém módu postupně spusťte všechny aplikace, které používáte. Ideální je v tréninkovém módu PC používat jeden den, aby VoodooShield vše stihl zapsat.
- Po ukončení tréniku VoodooShield klikněte pravým tlačítkem na ikonu aplikace v hlavním panelu a zvolte mód <span class="green">Always On</span>.
<li style="list-style-type: none">![vs1](https://faq.mople71.cz/img/en/vs1.png)</li>

![arrow](https://mople71.cz/img/sm/arrow.gif) <span class="green">To je vše, nyní máte plně funkční anti-executable ochranu aplikace VoodooShield. Když budete chtít instalovat libovolnou aplikaci, zvolte **Disable/Install Mode**.</span>

#### Ukázky a poznatky z provozu:
(obrázky jsou pouze ilustrativní)

- Když VS zablokuje neznámou, ale možná bezpečnou aplikaci, zobrazí následující bublinu:
<li style="list-style-type: none">![vs2](https://faq.mople71.cz/img/en/vs2.png)</li>
- Pokud chcete aplikaci povolit, na bublinu klikněte a v následujícím okně zvolte možnost <span class="green">Install</span>.
<li style="list-style-type: none">![vs3](https://faq.mople71.cz/img/en/vs3.png)</li>
- Když VS zablokuje aplikaci, kterou detekuje alespoň 1 antivirový produkt nebo VoodooAI jako malware, zobrazí následující bublinu:
<li style="list-style-type: none">![vs4](https://faq.mople71.cz/img/en/vs4.png)</li>
- Zde je povolení o pár kliků delší. Klikněte na bublinu, v následujícím okně zvolte možnost <span class="green">Allow False Positive</span> a odsouhlaste veškerá vyskakovací okna.
<li style="list-style-type: none">![vs5](https://faq.mople71.cz/img/en/vs5.png)</li>
- Po povolení aplikace a provedení vámi požadované akce se vždy přesvědčte, že VS běží v módu <span class="green">Always On</span>.

<br>

<span class="red">NVT Anti-AutoExec</span> je drobná aplikace, která automaticky zabraňuje šíření USB malware. Stačí nainstalovat a ochrana je aktivní bez jakékoli interakce.

<span class="red">AppGuard</span> je profesionální anti-executable určený převážně pro firemní sféru, je ovšem dostupný i v domácí verzi. Jeho nastavení je vcelku komplikované a přizpůsobené pro odborníky.

<span class="red">AppLocker</span> je anti-executable integrovaný ve Windows v edicích Ultimate, Education a Enterprise. Umožňuje ovládání spustitelných souborů, skriptů, DLL knihoven, MSI instalátorů a ModernUI (metro) aplikací. Poskytuje vcelku slušnou ochranu, na druhou stranu existují známé způsoby jeho obejití.

<span class="red">Software Restriction Policy</span> je velmi funkčně omezený anti-executable dostupný ve všech edicích Windows. Umožňuje ovládání spustitelných souborů a skriptů. Jeho pravidla jsou ovšem vázána na proces *explorer.exe*, který je vlastněn uživatelem, není tedy ideální k použití v profesionálním prostředí.

<br>

### Anti-exploit:
Každý kód obsahuje minimálně jednu chybu. Toho zneužívají exploity šířící se internetem. Anti-exploit aplikace přicházejí s mitigacemi, které mají za cíl znemožnit využití jednoduchých způsobů exploitace a proces exploitace výrazně ztížit.

Windows využívají velké množství mitigací a exploitace samotného OS a aplikací OS je tedy velmi nákladná. Některé aplikace (např. Chrome) jsou také na velmi vysoké úrovni a jejich exploitace je nákladná. Jsou zde ovšem aplikace, které žádné anti-exploit mitigace nepoužívají a někdy je používání těchto aplikací nezbytné. V takovém případě existují anti-exploit řešení, která umí exploitaci zmíněných aplikací výrazně ztížit.

#### Přehled anti-exploit řešení:
- Windows Defender Exploit Protection (Windows 10 Fall Creators Update a výše)
- [Microsoft Enhanced Mitigation Experience Toolkit](https://technet.microsoft.com/en-us/security/jj653751) (EMET; Windows 10 November Update a níže)
- [HitmanPro.Alert](https://www.hitmanpro.com/en/alert.aspx) (HMP.A)

Od verze **Windows 10 Fall Creators Update** jsou anti-exploit mitigace implementovány přímo do OS. Konfiguraci mitigací umožňuje *GUI* vestavěného AV/M řešení <span class="green">Windows Defender</span>.

> Konfigurace celosystémových anti-exploit mitigací

- Otevřete si <span class="green">Centrum zabezpečení v programu Windows Defender</span>.
- Přesuňte se do kategorie **Řízení aplikací a prohlížečů**.
- Sjeďte na konec stránky a otevřete <span class="green">Nastavení Exploit Protection</span>.
<li style="list-style-type: none">![wd4](https://faq.mople71.cz/img/cs/wd4.png)</li>
- Zkontrolujte konfiguraci celosystémových mitigací a případně opravte:
<li style="list-style-type: none">![wd5](https://faq.mople71.cz/img/cs/wd5.png)</li>

> Konfigurace anti-exploit mitigací pro jednotlivé aplikace (příklad: VoodooShield)

- V horním panelu se přesuňte do záložky **Nastavení programu**.
- Klikněte na <span class="green">Přidat program, který chcete přizpůsobit</span>.
<li style="list-style-type: none">![wd6](https://faq.mople71.cz/img/cs/wd6.png)</li>
- Nalezněte a zvolte požadovanou aplikaci, kterou chcete mitigovat.
<li style="list-style-type: none">![wd7](https://faq.mople71.cz/img/cs/wd7.png)</li>
- Upravte konfiguraci dle obrázku:
<li style="list-style-type: none">![wd8](https://faq.mople71.cz/img/cs/wd8.png)</li>
- Klikněte na tlačítko <span class="green">Použít</span>.

<br>

<span class="red">EMET</span> je anti-exploit řešení od MS určeno pro **starší verze OS**, které nemají anti-exploit mitigace integrovány.

> Instalace a konfigurace EMET (starší verze Windows)

- Stáhněte si nejnovější verzi [EMET](https://technet.microsoft.com/en-us/security/jj653751).
- Aplikaci nainstalujte, licenci odsouhlaste tlačítkem <span class="green">I Agree</span>.
- V průběhu instalace se zobrazí okno se základním nastavením aplikace. Zvolte možnost <span class="green">Use Recommended Settings</span> a klikněte na <span class="green">Finish</span>.
<li style="list-style-type: none">![emet](https://faq.mople71.cz/img/en/emet.png)</li>
- Po dokončení instalace otevřete EMET dvojitým poklepáním na jeho ikonu na hlavním panelu.
<li style="list-style-type: none">![emet1](https://faq.mople71.cz/img/en/emettray.png)</li>

![idea](https://mople71.cz/img/sm/idea.gif) <span class="green">Nyní máte nainstalovaný EMET v základní konfiguraci. Dále musíte nastavit ochranu pro všechny rizikové aplikace.</span>

- V horním menu EMET klikněte na tlačítko <span class="green">Apps</span>.
- Zobrazí se seznam aplikací chráněných EMETem, pro přidání nové klikněte na tlačítko <span class="green">Add Application</span>.
<li style="list-style-type: none">![emet2](https://faq.mople71.cz/img/en/emet2.png)</li>
- Otevře se okno průzkumníka Windows, v něm nalezněte aplikaci, kterou chcete mitigovat pomocí EMET a potvrďte ji. Tento proces opakujte pro všechny aplikace.

![idea](https://mople71.cz/img/sm/idea.gif) Jaké aplikace mitigovat? Všechny internetové prohlížeče, PDF čtečky, aplikace pracující s archivy (7-zip apod.), přehrávače hudby (VLC), LibreOffice, Steam atd. Veškerý rizikový SW třetí strany. Pokud se ve složce aplikace nachází více spustitelných souborů, mitigujte všechny (kromě odinstalátorů).

![emet3](https://faq.mople71.cz/img/cs/emet3.png)
- Pro více rizikovější síťový SW &ndash; webové prohlížeče, Java, Flash, Steam apod. &ndash; zaškrtněte v seznamu <span style="color: #008000">všechny</span> možnosti mitigace kromě <span class="green">Fonts</span>.
- Pro méně rizikový SW nemusíte zatrhávat mitigace <span class="green">EAF+</span> a <span class="green">ASR</span>. ASR může způsobovat pády aplikací.
<li style="list-style-type: none">![emet4](https://faq.mople71.cz/img/en/emet4.png)</li>
- Po dokončení nastavení všech aplikací zkontrolujte nastavení mitigací, případně opravte dle obrázku:
<li style="list-style-type: none">![emet5](https://faq.mople71.cz/img/en/emet5.png)</li>
- Klikněte na <span class="green">OK</span> a zavřete EMET spolu s vyskakovacím oknem, které se objeví.

![idea](https://mople71.cz/img/sm/idea.gif) **TIP pro rychlou konfiguraci aplikace:**
- Pro rychlou konfiguraci aplikace danou aplikaci nejprve spusťte.
- Otevřete <span class="green">EMET GUI</span>.
- V listu běžících procesů nalezněte danou aplikaci, klikněte na ni pravým tlačítkem a zvolte možnost <span class="green">Configure Process...</span>
- Otevře se nastavení aplikací s nově přidanou zvolenou aplikací, pro kterou následně nakonfigurujte mitigace, a klikěnte na <span class="green">OK</span>.
<li style="list-style-type: none">![emet6](https://faq.mople71.cz/img/en/emet6.png)</li>

<br>

<span class="red">HitmanPro.Alert</span> je placená aplikace, která nabízí komplexní zabezpečení včetně mitigací proti exploitům. Je to velmi solidní SW a investice do něj má smysl u starších verzí OS. Verze **Windows 10 Fall Creators Update** a novější mají většinu hlavních funkcí HMP.A integrovanou v OS, nejedná se tedy již o *&bdquo;must-have&ldquo;*.

> Instalace a konfigurace HMP.A

- Stáhněte si [HMP.A](https://www.hitmanpro.com/en/alert.aspx).
- Aplikaci nainstalujte, ponechte doporučené nastavení a možnost skenu po instalaci.
- Aplikaci otevřete.
- Klikněte na ozubené kolečko v pravém horním rohu a zvolte možnost <span class="green">Advanced interface</span>.
- Následně v dolní části klikněte na možnost **Safety notification** a zvolte možnost <span class="green">At application start</span>.
<li style="list-style-type: none">![hmpa](https://faq.mople71.cz/img/en/hmpa.png)</li>
- Následně klikněte na kategorii <span class="green">Risk reduction</span> a zapněte všechny její funkce, které nejsou vypnuté. Funkce, které již jsou zapnuté, ponechte na výchozím nastavení.
- Při otevření prohlížeče nebo jiné chráněné aplikace se při ponechání myši na pár sekund na kraji jejího okna  zobrazí ohraničení, které signalizuje, že HMP.A chrání danou aplikaci a také ukazuje, které funkce HMP.A jsou pro danou aplikaci zapnuté. Mimo jiné se objeví notifikace o zapnutí ochrany pro danou aplikaci.
<li style="list-style-type: none">![hmpa1](https://faq.mople71.cz/img/en/hmpa1.png)</li>
<li style="list-style-type: none">![hmpa2](https://faq.mople71.cz/img/en/hmpa2.png)</li>
- Při zachycení útoku HMP.A školivou aplikaci ukončí a zobrazí následující hlášku:
<li style="list-style-type: none">![hmpa3](https://faq.mople71.cz/img/en/hmpa3.png)</li>

![idea](https://mople71.cz/img/sm/idea.gif) Více se dozívte v [manuálu](https://www.hitmanpro.com/en-us/medialibrary/Microsites/SurfRight/Resources/HitmanPro-Alert-Getting-Started.pdf?la=en).

<br>

### Virtualizace:
Virtualizace může být velmi bezpečný způsob ochrany před malware (záleží na způsobu aplikace), jelikož odděluje požadovanou část OS od fyzického OS.

#### Možnosti virtualizace:
- virtuální počítač &ndash; [VirtualBox](https://www.virtualbox.org/), [VMware Player](https://my.vmware.com/en/web/vmware/free#desktop_end_user_computing/vmware_workstation_player/12_0),...
- lehká virtualizace OS &ndash; [Shadow Defender](http://www.shadowdefender.com/)
- sandbox &ndash; [Sandboxie](https://www.sandboxie.com/)

Nejbezpečnější způsob virtualizace je virtuální počítač při korektním nastavení a aplikaci snapshotů. Lehká virtualizace OS spočívá ve vrácení změn v OS při restartu, může být velmi užitečná proti např. ransomware. U sandboxu velmi záleží na implementaci, bezplatné řešení Sandboxie poskytující externí sandbox pro aplikace, je spíše na hraní.

> Instalace a konfigurace Sandboxie

- Stáhněte si [Sandboxie](https://www.sandboxie.com/index.php?DownloadSandboxie).
- Aplikaci nainstalujte a projděte úvodním tutoriálem.
- Otevřete **Ovládání Sandboxie**.
- Klikněte pravým tlačítkem na **Sandbox DefaultBox** a zvolte možnost <span class="green">Nastavení Sandboxu</span>.
<li style="list-style-type: none">![sbie](https://faq.mople71.cz/img/cs/sbie.png)</li>
- V pravém panelu rozbalte možnost **Vymazat** a klikněte na <span class="green">Smazat pracovní soubory</span>.
- Zatrhněte možnost <span class="green">Automaticky smazat obsah Sandboxu</span> a klikněte na <span class="green">OK</span>.
<li style="list-style-type: none">![sbie1](https://faq.mople71.cz/img/cs/sbie1.png)</li>

<br>

### Ostatní aplikace:
Užitečné aplikace, které nespadají ani pod jednu kategorii vrstev zabezpečení.

#### Doporučené ostatní aplikace:
- [Heimdal Free](https://heimdalsecurity.com/en/products/heimdal-free)
- [Unchecky](https://unchecky.com/)
- [HashTab](http://implbits.com/products/hashtab/)

> Instalace a konfigurace Heimdal Free

- Stáhněte si [Heimdal Free](https://heimdalsecurity.com/en/products/heimdal-free/thank-you).
- Máte-li nastavený **Řízený přístup ke složkám** ve <span class="green">Windows Defender</span>, dočasně jej po dobu instalace vypněte.
<li style="list-style-type: none">![wd1a](https://faq.mople71.cz/img/cs/wd1a.png)</li>
- Aplikaci nainstalujte. (**I want to activate Heimdal FREE**)
- V konfiguraci ponechte zapnuté pouze <span class="green">Software Update Notifications</span>.
<li style="list-style-type: none">![hf](https://faq.mople71.cz/img/en/hf.png)</li>
- Zapněte monitorování všech dostupných aplikací a případně i automatickou aktualizaci.
- Pro změnu nastavení &ndash; např. po instalaci nové aplikace, kterou *Heimdal Free* zatím nemonitoruje &ndash; otevřete **Heimdal Free** a přesuňte se do záložky <span class="green">Patching System</span>.
<li style="list-style-type: none">![hf1](https://faq.mople71.cz/img/en/hf1.png)</li>
<li style="list-style-type: none">![idea](https://mople71.cz/img/sm/idea.gif) Ačkoli je **Heimdal Free** velmi kvalitní aplikace, automatická aktualizace aplikací otevírá prostor problémům. Na druhou stranu se jedná o menší zlo v porovnání s neaktuálními aplikacemi. Pokud tedy takto konfigurujete OS člověku, který si s PC nerozumí a nebude aplikace aktualizovat, automatickou aktualizaci možná zapněte.</li>
- Aplikaci povolte v **Řízeném přístupu ke složkám**, který následně opětovně povolte. Návod [zde](#win2.1).

> Instalace a konfigurace HashTab

- Stáhněte si [HashTab](http://implbits.com/products/hashtab/).
- Aplikaci nainstalujte.
- Nalezněte libovolný soubor na disku a otevřete jeho **Vlastnosti**.
- V horním panelu se přesuňte do záložky **File Hashes** a klikněte na tlačítko <span class="green">Settings</span>.
<li style="list-style-type: none">![hashtab](https://faq.mople71.cz/img/en/hashtab.png)</li>
- Upravte konfiguraci dle obrázku a klikněte na <span class="green">OK</span>.
<li style="list-style-type: none">![hashtab1](https://faq.mople71.cz/img/en/hashtab1.png)</li>

<br><br><hr><br>

## Zabezpečení internetového prohlížeče:
- bezpečnější nastavení (vypnutí nebezpečných funkcí, ideálně vč. javascriptu)
- blokování reklamy
- oddělení prohlížeče od dat a fyzického OS (sandbox &lt; VM &lt; live OS)

> Porovnání prohlížečů z ohledu bezpečnosti

Všechny prohlížeče jsou po korektním nastavení relativně bezpečné, nejvíce také záleží na vás. Proto zde rozeberu pouze teoretické zabezpečení prohlížečů z hlediska mitigací exploitů apod. Níže v sekci naleznete návody na zabezpečení **Mozilla Firefox**, **Internet Explorer**, **Google Chrome** a **Microsoft Edge** kvůli jejich dominantnímu postavení.

Ze zmíněných prohlížečů bych doporučil <span class="green">Microsoft Edge</span> a <span class="green">Chromium</span>, případně jeho proprietární variantu [Google Chrome](https://www.google.com/chrome/browser/index.html). S prohlížečem **Internet Explorer** není zásadní problém, na druhou stranu již není v aktivním vývoji.

<span class="red">Mozilla Firefox</span>. Tento prohlížeč z hlediska zabezpečení nelze doporučit, v porovnání s ostatními zmíněnými prohlížeči výrazně zaostává. Má starý kód výrazně nižší kvality nežli Edge či Chromium a postrádá základní mitigace proti exploitům (v poslední době se toto snaží dohánět implementací sandboxu prohlížeče Chromium). Externí sandbox typu Sandboxie nedosahuje zdaleka takové kvality jako vestavěný sandbox.

<span class="green">Chrome(ium)</span> používá vestavěný sandbox velmi dobré kvality. Také nabízí možnost využití vestavěného sandboxu ve Windows (AppContainer). Nové verze jsou kompilovány s **CFG**, což je významné plus.

<span class="green">Microsoft Edge</span> je nový a moderní prohlížeč využívající špičkovou implementaci sandboxu. Používá nejmodernější mitigace jako **CFG**, což je významné plus.

<br>

<!--- ./browsers.md -->

<br><br><hr><br>

## Doporučené bezpečnostní konfigurace:
Zde naleznete několik příkladů bezpečnostních konfigurací. Není tedy je slovo od slova kopírovat, stačí se inspirovat. Na druhou stranu níže zmíněné příklady konfigurací jsou plně funkční a relativně účinné. Pokud byste chtěli příklad aplikovat, počítá se s prostudováním celé sekce OS Windows v FAQ &ndash; hlavně návodů na jednotlivé programy &ndash; a aplikací zmíněných doporučení.

#### Bezplatná konfigurace pro BFU, který neumí anglicky (např. prarodiče):
> Konfigurace

- OS &ndash; Windows 10 Fall Creators Update
- bezpečné nastavení OS &ndash; **kompletní**
- AV/M &ndash; **Windows Defender**
- FW &ndash; **Windows Firewall**
- anti-exploit &ndash; **Windows Defender**
- anti-executable &ndash; **NVT Anti-AutoExec**
- virtualizace &ndash; **nic**
- internetový prohlížeč &ndash; **MS Edge** / **Google Chrome**
- zabezpečení prohlížeče &ndash; **kompletní**
- užitečné aplikace &ndash; **Unchecky**, **Heimdal Free**
- konfigurace pro pokročilé &ndash; dle znalostí

Je nutné proškolit BFU, jak se má chovat na PC a na internetu. Bezpečně nastavit OS (hlavně účet s omezeným oprávněním). V případě instalace 3-P internetového prohlížeče používat MS Edge pro bankovní účely a podobné citlivé věci. *Heimdal Free* nastavit na tichou automatickou aktualizaci aplikací. Samozřejmě, pokud zvládáte pokročilou konfiguraci popisovanou v FAQ pro pokročilé, úroveň zabezpečení můžete velmi výrazně zvýšit.

![arrow](https://mople71.cz/img/sm/arrow.gif) Tato konfigurace by při správném použití měla spolehlivě zabránit malware infekci.

<br>

#### Bezplatná konfigurace pro středně pokročilého, který umí anglicky:
> Konfigurace

- OS &ndash; Windows **10** / **8.1 Update 3**
- bezpečné nastavení OS &ndash; **kompletní**
- AV/M &ndash; **Windows Defender**
- FW &ndash; **Windows Firewall**
- anti-exploit &ndash; **Windows Defender** / **EMET**
- anti-executable &ndash; **VoodooShield**, **NVT Anti-AutoExec**
- virtualizace &ndash; **Sandboxie**
- internetový prohlížeč &ndash; **MS Edge** / **Google Chrome**
- zabezpečení prohlížeče &ndash; **kompletní**
- užitečné aplikace &ndash; **Unchecky**, **HashTab**
- konfigurace pro pokročilé &ndash; dle znalostí

![arrow](https://mople71.cz/img/sm/arrow.gif) Tato konfigurace by při správném použití měla spolehlivě zabránit malware infekci.

<br><br><hr>

<h3 class="nocol">To je vše. Stay safe! ![smile](https://mople71.cz/img/sm/smile.gif)</h3>
