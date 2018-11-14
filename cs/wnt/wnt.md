# FAQ &ndash; OS Windows
Windows se jakožto nejrozšířenější desktopový OS těší velké pozornosti hackerů, jeho dostatečné zabezpečení je proto nezbytné.

Podporovanou verzí Windows v následující sekci je **Windows 10 September 2018 Update** jakožto nejnovější OS s podporou do roku 2025. Obsažené informace jsou platné také pro **Windows 8.1 Update 3**. Starší verze OS Windows již postrádají důležité bezpečnostní mitigace/funkce a zanedlouho jim skončí &ndash; pokud již neskončil &ndash; cyklus rozšířené podpory. Majitelé starých verzí OS by proto měli přejít na novější OS, dovoluje-li jim to jejich HW. I přesto je většina obsažených informací platná i pro starší verze OS, pouze se bude lišit přesný postup aplikace různých kroků &ndash; přesný postup pro staré verze zde nebude uváděn.

Tato sekce FAQ je určena běžným a středně pokročilým uživatelům. Sekci pro pokročilé naleznete [zde](https://faq.mople71.cz/cs/wnt/adv.php#wnt).


#### FAQ se dělí na několik sekcí:
- [Základní bezpečnostní nastavení](#wnt1)
- [Ochrana proti malware](#wnt2)
- [Zabezpečení internetového prohlížeče](#wnt3)
- [Doporučené bezpečnostní konfigurace](#wnt4)

<br>

## Základní bezpečnostní nastavení
### Práce pod Standardním uživatelem:

OS Windows má dva typy uživatelských účtů: <span class="green">Standardní uživatel</span> a <span class="green">Správce</span>.

Z hlediska bezpečnosti je důležité pracovat pod Standardním uživatelem, jelikož má omezená oprávnění. Pokud se tedy do OS i přes všechna zdejší doporučení dostane malware, infikuje pouze uživatelský účet &ndash; na infikaci OS nemá potřebná oprávnění.

<div class="alert exclaim"><p><em class="icon-attention"></em>**Varování**<br>
Jedná se o naprostý základ zabezpečení OS, bez kterého jsou veškerá další opatření naprosto zbytečná.</p></div>

> Přidání účtu Správce a změna stávajícího uživatele na Standardního

- Otevřete si <span class="green">Nastavení</span>. Rozklikněte kategorii **Účty** a následně zvolte podkategorii <span class="green">Rodina a jiní uživatelé</span>.
- Klikněte na tlačítko <span class="green">Přidat do tohoto počítače někoho dalšího</span>.
<li style="list-style-type: none">![wntus](https://faq.mople71.cz/img/cs/wntus.png)</li>
- Otevře se dialog pro přidání nového uživatele. V levém dolním rohu klikněte na <span class="green">Nemám přihlašovací údaje této osoby</span>.
- V levém dolním rohu zvolte možnost <span class="green">Přidat uživatele bez účtu Microsoft</span>.
- Zadejte název účtu Správce (např. **Admin**) a zvolte pro něj silné zapamatovatelné heslo. Vyplňte bezpečnostní otázky a klikněte na <span class="green">Další</span>.
<li style="list-style-type: none">![wntus1](https://faq.mople71.cz/img/cs/wntus1.png)</li>
- V seznamu jiných uživatelů se zobrazí účet **Admin**. Klikněte na něj a následně zvolte <span class="green">Změnit typ účtu</span>.
<li style="list-style-type: none">![wntus2](https://faq.mople71.cz/img/cs/wntus2.png)</li>
- Zobrazí se dialog pro změnu typu účtu. Ze seznamu zvolte možnost <span class="green">Správce</span> a klikněte na <span class="green">OK</span>.
<li style="list-style-type: none">![wntus3](https://faq.mople71.cz/img/cs/wntus3.png)</li>
- Odhlaste se z vašeho účtu a přihlaste se jako **Admin**.
- Otevřete si <span class="green">Nastavení</span>. Rozklikněte kategorii **Účty** a následně zvolte podkategorii <span class="green">Rodina a jiní uživatelé</span>.
- V seznamu jiných uživatelů nalezněte svůj účet, klikněte na něj a následně zvolte <span class="green">Změnit typ účtu</span>.
- Zobrazí se dialog pro změnu typu účtu. Ze seznamu zvolte možnost <span class="green">Standardní uživatel</span> a klikněte na <span class="green">OK</span>.
- Přihlaste se zpět na svůj uživatelský účet.

> Přidání účtu Správce a změna stávajícího uživatele na Standardního (starší verze Windows)

- Otevřete si <span class="green">Nastavení</span>. Rozklikněte kategorii **Účty** a následně zvolte podkategorii <span class="green">Jiné účty</span>.
- Zvolte možnost <span class="green">Přidat účet</span>.
- Otevře se dialog pro přidání nového uživatele. V pravém dolním rohu klikněte na <span class="green">Přihlásit se bez účtu Microsoft</span>.
- Klikněte na tlačítko <span class="green">Místní účet</span>.
- Zadejte název účtu Správce (např. **Admin**) a zvolte pro něj silné zapamatovatelné heslo.
- Potvrďte přidání uživatele (<span class="green">Dokončit</span>).
- V seznamu dalších účtů se zobrazí účet **Admin**. Klikněte na něj a následně zvolte <span class="green">Upravit</span>.
<li style="list-style-type: none">![wntusleg](https://faq.mople71.cz/img/cs/wntusleg.png)</li>
- Zobrazí se dialog pro změnu typu účtu. Ze seznamu zvolte možnost <span class="green">Správce</span> a klikněte na <span class="green">OK</span>.
<li style="list-style-type: none">![wntusleg1](https://faq.mople71.cz/img/cs/wntusleg1.png)</li>
- Odhlaste se z vašeho účtu a přihlaste se jako **Admin**.
- Otevřete si <span class="green">Nastavení</span>. Rozklikněte kategorii **Účty** a následně zvolte podkategorii <span class="green">Jiné účty</span>.
- V seznamu dalších účtů nalezněte svůj účet, klikněte na něj a následně zvolte <span class="green">Upravit</span>.
- Zobrazí se dialog pro změnu typu účtu. Ze seznamu zvolte možnost <span class="green">Standardní uživatel</span> a klikněte na <span class="green">OK</span>.
- Přihlaste se zpět na svůj uživatelský účet.

<br>

### User Account Control:

*User Account Control* je důležitá součást bezpečnostního modelu OS od **Windows Vista**, kde se dočkala obrovské kritiky a ve Windows 7 proto byla v základním nastavení oslabena. Vypnutí UAC je z hlediska bezpečnosti sebevražda, naopak je doporučeno konfiguraci UAC nastavit na ještě přísnější úroveň.

> Nastavení UAC

- Stiskněte kláv. zkratku ![win](https://mople71.cz/img/icons/wkey.png) <span class="ks">+ R</span>, do textového pole zadejte:
<li style="list-style-type: none"><pre><code>useraccountcontrolsettings</code></pre>
a stiskněte **Enter**.</li>
- Otevře se konfigurace UAC. Zkontrolujte, že je nastavena na nejvyšší úroveň. Případně napravte.
<li style="list-style-type: none">![uac](https://faq.mople71.cz/img/cs/uac.png)</li>
- Klikněte na <span class="green">OK</span>.

<br>

### Bezpečné nastavení služeb a funkcí Windows:

<div class="alert info"><p><em class="icon-info-circled"></em>**Info**<br>
Pokročilejší si skript mohou upravit &ndash; je v něm několik zakomentovaných bezpečnostních opatření, které nemohou být aplikovány širokopásmově&#8230;</p></div>

![batch](https://mople71.cz/img/icons/bat.png) **SafeSVC**:
- Stáhněte si [SafeSVC](https://mople71.cz/safesvc.zip).
- Uložte a obsah archivu vyextrahujte <span class="blue">na Plochu</span>.
- Na skript jménem <span class="green">safesvc</span> klikněte pravým tlačítkem a zvolte možnost: ![admin](https://mople71.cz/img/icons/admin.png) **Spustit jako správce**.
- Nechte skript pracovat, na konci procesu vám řekne o souhlas k restartu OS.

> Nastavení SmartScreen (starší verze Windows)

- Stiskněte kláv. zkratku ![win](https://mople71.cz/img/icons/wkey.png) <span class="ks">+ R</span>, do textového pole zadejte:
<li style="list-style-type: none"><pre><code>smartscreensettings</code></pre>
a stiskněte **Enter**.</li>
- Otevře se nastavení SmartScreen filtru. Upravte jej dle obrázku:
<li style="list-style-type: none">![smartscreen](https://faq.mople71.cz/img/cs/smartscreen.png)</li>
- Klikněte na <span class="green">OK</span>.

<br>

### Bezpečné nastavení sítě:
> Konfigurace síťového adaptéru + DNS

- Stiskněte kláv. zkratku ![win](https://mople71.cz/img/icons/wkey.png) <span class="ks">+ R</span>, do textového pole zadejte:
<li style="list-style-type: none"><pre><code>ncpa.cpl</code></pre>
a stiskněte **Enter**.</li>
- Otevře se seznam síťových adaptérů. Klikněte na první adaptér (obvykle ethernet) pravým tlačítkem a zvolte možnost <span class="green">Vlastnosti</span>.
<li style="list-style-type: none">![wntnet](https://faq.mople71.cz/img/cs/wntnet.png)</li>
- V seznamu odškrtněte všechny nepotřebné položky. Běžným uživatelům stačí ponechat pouze <span class="green">Sdílení souborů a tiskáren v sítích Microsoft</span>, <span class="green">Protokol IP verze 4 (TCP/IPv4)</span> a <span class="green">Protokol IP verze 6 (TCP/IPv6)</span>.
- Pokud nesdílíte žádnou tiskárnu v síti a nepoužíváte IPv6 (pokud nevíte, zdali používáte IPv6, můžete to zjistil pomocí následujícího rychlého [online testu](http://www.test-ipv6.cz/)\), můžete pro vyšší bezpečnost ponechat zaškrtnutý pouze <span class="green">Protokol IP verze 4 (TCP/IPv4)</span>.
<li style="list-style-type: none">![wntnet1](https://faq.mople71.cz/img/cs/wntnet1.png)</li>
- Klikněte na **Protokol IP verze 4 (TCP/IPv4)** a zvolte možnost <span class="green">Vlastnosti</span>.
<li style="list-style-type: none">![wntnet2](https://faq.mople71.cz/img/cs/wntnet2.png)</li>

<div class="alert success"><p><em class="icon-ok-circled"></em>**Úspěch**<br>
Potenciálně nebezpečné protokoly jsou nyní vypnuty. Dále nastavíme bezpečné DNS servery.</p></div>

- Pokud nevíte, co DNS je, přečtěte si tento [krátký článek](https://www.nic.cz/page/312/o-domenach-a-dns/).
- Doporučuji použít DNSSEC. Ale můžete si vybrat z mnoha DNS serverů, zde je pár příkladů:
<li style="list-style-type: none"><pre><code>CZ.NIC DNSSEC:        217.31.204.130, 193.29.206.206
Adguard DNS:          176.103.130.130, 176.103.130.131
OpenDNS:              208.67.222.222, 208.67.220.220</code></pre></li>
- Po zvolení DNS serverů se přepněte zpět do okna Vlastností IPv4 protokolu.
- Klikněte na <span class="green">Použít následující adresy serverů DNS</span> a do kolonek vepište vámi zvolené DNS.
<li style="list-style-type: none">![wntnet3](https://faq.mople71.cz/img/cs/wntnet3.png)</li>
- Klikněte na tlačítko <span class="green">Upřesnit&#8230;</span>
- V horním panelu se přesuňte do záložky **WINS** a zvolte možnost <span class="green">Zakázat rozhraní NetBIOS nad protokolem TCP/IP</span>.
<li style="list-style-type: none">![wntnet4](https://faq.mople71.cz/img/cs/wntnet4.png)</li>
- Klikněte na <span class="green">OK</span>.
- Klikněte na <span class="green">OK</span> a okno zavřete.

<div class="alert exclaim"><p><em class="icon-attention"></em>**Varování**<br>
Pro dosáhnutí kýženého efektu je nutné kompletní postup aplikovat pro všechny síťové adaptéry v seznamu (obvykle WLAN).</p></div>

<br>

### Další bezpečnostní nastavení:

- Vypněte Usnadnění přístupu na přihlašovací obrazovce &ndash; součást skriptu **SafeSVC**.
- Vypněte AutoPlay:
    - Otevřete si <span class="green">Nastavení.</span> Rozklikněte kategorii **Zařízení** a následně zvolte podkategorii <span class="green">Automatické přehrávání</span>.
    - Automatické přehrávání vypněte.
    <li style="list-style-type: none">![autoplay](https://faq.mople71.cz/img/cs/autoplay.png)</li>
- Vypněte Remote Assistance:
    - Stiskněte kláv. zkratku ![win](https://mople71.cz/img/icons/wkey.png) <span class="ks">+ R</span>, do textového pole zadejte:
    <li style="list-style-type: none"><pre><code>sysdm.cpl</code></pre>
a stiskněte **Enter**.</li>
    - Zobrazí se Vlastnosti systému.
    - Přesuňte se do záložky **Vzdálený přístup** a <span style="color: #BF0000">odstraňte</span> zatržítko u položky <span class="green">Povolit připojení vzdálené pomoci k tomuto počítači</span>.
    <li style="list-style-type: none">![sysdm](https://faq.mople71.cz/img/cs/sysdm.png)</li>
    - Klikněte na <span class="green">OK</span>.

<br><br><hr><br>

## Ochrana proti malware
Jako nejúčinnější metoda ochrany proti malware se osvědčila bezpečnostní konfigurace skládající se z více vrstev (*&bdquo;layered config&ldquo;*) &ndash; pokud selže jedna vrstva, nastupuje druhá. Spousta běžných uživatelů stále spoléhá pouze na jednu tradiční vrstvu &ndash; antivirus &ndash; což je z hlediska bezpečnosti tristní.

Samotný OS poskytuje jistou úroveň ochrany proti malware, která se liší v závislosti na verzi a edici OS. V základním nastavení ovšem bohužel nejsou všechny bezpečnostní funkce zapnuty a/nebo korektně nastaveny.

Vrstev existuje mnoho, níže jsou zmíněny pouze vrstvy vyhodnoceny jako důležité.

- antivirus / antimalware
- firewall
- anti-exploit
- anti-executable
- virtualizace
- &#8230;

<br>

### Aktualizace OS a SW:

Je důležité mít aktuální verzi veškerého SW, jelikož nové verze často opravují mnoho bezpečnostních chyb. Neaktuální děravý SW je implicitně nebezpečný.

Windows by se měly ve výchozím nastavení aktualizovat samy (v edici *Home* automatické aktualizace dokonce nelze vypnout). Mnohé důležité aplikace (např. prohlížeče) se obvykle aktualizují automaticky.

Pro kontrolu aktualizací ostatního SW můžete použít např. aplikaci <span class="green">Kaspersky Software Updater</span>, která vás v případě neaktuálního SW upozorní a umožní jeho aktualizaci &ndash; automatické aktualizace ovšem teoreticky mohou způsobit problémy. Návod ke *Kaspersky Software Updater* naleznete v sekci [Ostatní aplikace](#wnt2.4).

> Kontrola nastavení aktualizací OS (starší verze Windows)

- Stiskněte kláv. zkratku ![win](https://mople71.cz/img/icons/wkey.png) <span class="ks">+ R</span>, do textového pole zadejte:
<li style="list-style-type: none"><pre><code>wuapp</code></pre>
a stiskněte **Enter**.</li>
- V levém panelu klikněte na tlačítko <span class="green">Změnit nastavení</span>.
- Zkontrolujte, že **důležité aktualizace** mají zvolenou možnost <span class="green">Instalovat aktualizace automaticky (doporučeno)</span>, případně napravte.
- Zkontrolujte, že je <span style="color: #BF0000">odstraněné</span> zatržítko u možnosti <span class="green">Získávat doporučené aktualizace stejným způsobem jako důležité aktualizace</span>, případně napravte.
- Klikněte na <span class="green">OK</span> a okno zavřete.

<br>

### Windows Defender:
Windows Defender je komplexní řešení, jenž kompletně pokrývá následující vrstvy zabezpečení: **antimalware**, **firewall**, **anti-exploit**. Dále zasahuje i do jiných vrstev jako *anti-ransomware* atd.

#### Ochrana proti tradičnímu malware:
Antivirus nebo antimalware (AV/M) je uživateli chápán jako základní vrstva zabezpečení, která sama o sobě stačí k zabezpečení OS. Tato teze již ovšem nějakou dobu není pravdivá.

> Rozebrání problematiky antivirů

Tradiční mechanismus antiviru pracuje na bázi databáze &ndash; detekuje známý malware, jejichž otisk má v databázi. Tento systém má vcelku očividnou slabinu &ndash; pokud otisk pro malware neexistuje, antivir jej nevyhodnotí jako škodlivý.
Další technologií je tzv. *heuristika*, kdy je škodlivost kódu vyhodnocována na základě jeho aktivit po spuštění (vzorek je zpravidla testován v izolovaném prostředí &ndash; sandboxu). Tato technologie má také slabinu &ndash; škodlivost je posuzována na základě předvolených pravidel a indikací, které u vzorku pozoruje. Pokud malware provede činnost, která není zaznamenána heuristickým systémem jako škodlivá, antivir jej nevyhodnotí jako škodlivý. Tvůrci malware tedy používají různé postupy, aby heuristickou detekcí jejich kód prošel.

Další problém antivirů je ten, že většina z nich je stará &ndash; mají starý kód, který je tak komplexní, že jej vývojáři nepřepisují, pouze záplatují a přidávají nové funkce. V důsledku je mnoho antivirů náchylných na hackerské útoky staré 10 let.

Z výše uvedených důvodů tedy není bezpečné mít antivirus jako hlavní &ndash; natož jedinou &ndash; vrstvu zabezpečení. Antivirus ovšem má v bezpečnostní konfiguraci místo.

<span class="green">Windows Defender</span> integrovaný ve **Windows 8.1 Update 3** a **Windows 10** dosáhl úrovně, kdy dostatečně pokrývá tradiční vrstvu zabezpečení. Již tedy není nutné instalovat antivirus třetí strany, jehož kvalita kódu je řádově menší a s OS mnohdy provádí oproti integrovanému řešení naprosté šílenosti.

> Porovnání Windows Defender a AV/M řešení třetích stran

Do příchodu **Windows 8.1 Update 3** byla AV/M řešení třetích stran brána jako nutné zlo, jelikož být bez žádného AV/M řešení je výrazně horší, nežli být s AV/M řešením třetí strany, a OS tehdy neobsahoval použitelné vestavěné AV/M řešení. S příchodem **Windows 10** byl <span class="green">Windows Defender</span> z velké části přepsán a s každou novou verzí OS se dočkává vylepšení. V aktuálním stavu se jedná o kvalitní moderní AV/M řešení.

Ostatní AV/M řešení nejsou vestavěná v OS &ndash; kvalita jejich kódu nemusí (může) být na úrovni zbytku OS, s každým řádkem kódu navíc se ovšem zvětšuje prostor pro exploitaci. Na rozdíl od <span class="green">Windows Defender</span> nejsou korektně integrovány do OS &ndash; operují proto na bázi hacku a zásahu do bezpečnostního modelu OS (a aplikací jako internetových prohlížečů). V porovnání s integrovaným řešením navíc zpravidla postrádají/nevyužívají moderní mitigace proti exploitaci, které mají všechny systémové aplikace.

Detekce <span class="green">Windows Defender</span> je na velmi dobré úrovni. Jedná se o výchozí AV/M řešení na instalacích aktuálních verzí OS &ndash; počet uživatelů zvyšuje šanci zachytit nový malware. Implementuje vyspělý cloudový systém, díky kterému nabízí užitečné pokročilé funkce (např. *block on first sight*).

<div class="alert info"><p><em class="icon-info-circled"></em>**Tip**<br>
Používáte-li lokální uživatelský účet bez propojení s účtem Microsoftu, *Windows Defender* bude zobrazovat varování o nezabezpečení účtu. Zmíněného varování se snadno zbavíte otevřením **Centra zabezpečení v programu Windows Defender** a kliknutím na **Zavřít** v sekci *Ochrana účtu*.<br>
![wdmsa](https://faq.mople71.cz/img/cs/wdmsa.png)</p></div>

> Ochrana před viry a hrozbami &ndash; nastavení

- Otevřete si <span class="green">Centrum zabezpečení v programu Windows Defender</span>.
- Přesuňte se do kategorie **Ochrana před viry a hrozbami** a otevřete <span class="green">Nastavení ochrany před viry a hrozbami</span>.
- Zkontrolujte konfiguraci ochrany a případně opravte:
<li style="list-style-type: none">![wd](https://faq.mople71.cz/img/cs/wd.png)</li>

> Řízení aplikací a prohlížečů &ndash; nastavení

- Přesuňte se do kategorie **Řízení aplikací a prohlížečů**.
- Zkontrolujte konfiguraci SmartScreen filtru a případně opravte:
<li style="list-style-type: none">![wd1](https://faq.mople71.cz/img/cs/wd1.png)</li>

> Zabezpečení zařízení &ndash; nastavení

- Přesuňte se do kategorie **Zabezpečení zařízení**.
- V sekci **Izolace jádra** otevřete <span class="green">Podrobnosti o izolaci jádra</span>.
- Zkontrolujte konfiguraci virtualizace a případně opravte:
<li style="list-style-type: none">![wd2](https://faq.mople71.cz/img/cs/wd2.png)</li>
- Potvrďte případný restart OS.

> Konfigurace Řízeného přístupu ke složkám

- Přesuňte se do kategorie **Ochrana před viry a hrozbami** a otevřete <span class="green">Ochranu před ransomwarem</span>.
- Zapněte <span class="green">Řízený přístup ke složkám</span> a následně otevřete <span class="green">Chráněné složky</span>.
<li style="list-style-type: none">![wd3](https://faq.mople71.cz/img/cs/wd3.png)</li>
- Kliknutím na <span class="green">Přidat chráněnou složku</span> přidejte na seznam veškeré důležité osobní složky na disku, které nejsou v seznamu.

> Povolení aplikace v Řízeném přístupu ke složkám (příklad: Kaspersky Software Updater)

- Při instalaci aplikací budete muset dočasně **Řízený přístup ke složkám** zakázat.
- Otevřete <span class="green">povolené aplikace v Řízeném přístupu ke složkám</span>.
<li style="list-style-type: none">![wd3b](https://faq.mople71.cz/img/cs/wd3b.png)</li>
- Klikněte na <span class="green">Přidat povolenou aplikaci</span>. Zvolte možnost <span class="green">Procházet všechny aplikace</span>.
<li style="list-style-type: none">![wd4](https://faq.mople71.cz/img/cs/wd4.png)</li>
- Nalezněte **Kaspersky Software Updater** a přidejte postupně jeho spustitelné programy na seznam.
- **Řízený přístup ke složkám** následně opětovně povolte.

<br>

Ve verzi OS **Windows 8.1 Update 3** obsahuje <span class="green">Windows Defender</span> méně funkcí, stále se ovšem jedná o nejlepší volbu. Pro nižší verze OS poté existuje substituce Defenderu &ndash; [Microsoft Security Essentials](https://www.microsoft.com/cs-cz/download/details.aspx?id=5201).

> Ochrana před viry a hrozbami &ndash; nastavení (starší verze Windows)

- Otevřete si <span class="green">Windows Defender</span>.
- Přesuňte se do záložky **Nastavení** a zvolte podkategorii <span class="green">Ochrana v reálném čase</span>.
- Zkontrolujte zatržítko u volby <span class="green">Zapnout ochranu v reálném čase</span>.
- Přesuňte se do podkategorie **Upřesnit**. Zkontrolujte konfiguraci ochrany a případně opravte:
<li style="list-style-type: none">![wdleg](https://faq.mople71.cz/img/cs/wdleg.png)</li>
- Přesuňte se do podkategorie **Komunita MAPS**. Zkontrolujte konfiguraci ochrany a případně opravte:
<li style="list-style-type: none">![wdleg1](https://faq.mople71.cz/img/cs/wdleg1.png)</li>
- Přesuňte se do podkategorie **Správce** a zkontrolujte zatržítko u volby <span class="green">Zapnout tuto aplikaci</span>.
- Případné změny uložte a aplikaci zavřete.

<br>

#### Firewall:

Firewall je velmi důležitá vrstva zabezpečení, která chrání OS před útoky ze sítě. Windows obsahují vestavěný <span class="green">Windows Defender Firewall</span> (WDF), který je na velmi dobré úrovni a plně dostačující. *Poznámka na okraj: základem síťového zabezpečení v domácnosti je rozumný router.*

**Windows Defender Firewall** je v základu nastaven na blokování příchozí komunikace, která není explicitně povolena. Chcete-li posunout bezpečnost na výrazně vyšší úroveň, je nutné nastavit FW na blokování veškeré odchozí komunikace, která není explicitně povolena. V nejnovější verzi Windows je ovšem taková konfigurace značně problematická, návod proto naleznete pouze v [FAQ pro pokročilé](https://faq.mople71.cz/cs/wnt/adv.php#wnt1).

Firewall aplikace třetích stran jako <span class="red">Comodo Firewall</span> jsou důrazně nedoporučeny.

<br>

### Ochrana proti exploitaci:
Každý kód obsahuje minimálně jednu chybu. Toho zneužívají *exploity*, které tyto chyby zneužívají.

Windows využívají velké množství nejmodernějších mitigací, exploitace samotného OS je tedy velmi nákladná. Některé aplikace (např. *Google Chrome*) jsou z hlediska mitigací proti exploitům také na velmi vysoké úrovni. Pak jsou zde ovšem aplikace, které žádné mitigace neimplementují/nevyužívají, a někdy je bohužel užívání takových aplikací nezbytné. V takovém případě existují anti-exploit řešení, která umí exploitaci těchto aplikací ztížit.

Od verze **Windows 10 Fall Creators Update** je schopnost mitigace aplikací třetích stran integrována přímo v OS, rozhraní pro konfiguraci poskytuje Windows Defender.

> Konfigurace celosystémových anti-exploit mitigací

- Otevřete si <span class="green">Centrum zabezpečení v programu Windows Defender</span>.
- Přesuňte se do kategorie **Řízení aplikací a prohlížečů**.
- Sjeďte na konec stránky a otevřete <span class="green">Nastavení Ochrany Exploit Protection</span>.
<li style="list-style-type: none">![wd5](https://faq.mople71.cz/img/cs/wd5.png)</li>
- Zkontrolujte konfiguraci celosystémových mitigací a případně opravte:
<li style="list-style-type: none">![wd6](https://faq.mople71.cz/img/cs/wd6.png)</li>

> Konfigurace anti-exploit mitigací pro jednotlivé aplikace (příklad: VoodooShield)

- V horním panelu se přesuňte do záložky **Nastavení programu**.
- Klikněte na <span class="green">Přidat program, který chcete přizpůsobit</span> a <span class="green">Zvolit přesnou cestu k souboru</span>.
<li style="list-style-type: none">![wd7](https://faq.mople71.cz/img/cs/wd7.png)</li>
- Nalezněte a zvolte požadovanou aplikaci, kterou chcete mitigovat.
<li style="list-style-type: none">![wd8](https://faq.mople71.cz/img/cs/wd8.png)</li>
- Upravte konfiguraci dle obrázku:
<li style="list-style-type: none">![wd9](https://faq.mople71.cz/img/cs/wd9.png)</li>
- Klikněte na tlačítko <span class="green">Použít</span>.

> Konfigurace anti-exploit mitigací pro Microsoft Office

- V horním panelu se přesuňte do záložky **Nastavení programu**.
- Klikněte na <span class="green">Přidat program, který chcete přizpůsobit</span> a zvolte <span class="green">Přidat podle názvu aplikace</span>.
- Do textového pole zadejte:
<li style="list-style-type: none"><pre><code>WINWORD.EXE</code></pre></li>
- Upravte konfiguraci dle obrázku:
<li style="list-style-type: none">![wd10](https://faq.mople71.cz/img/cs/wd10.png)</li>
- Klikněte na tlačítko <span class="green">Použít</span>.
- Obdobný způsob proveďte pro aplikaci MS Excel:
<li style="list-style-type: none"><pre><code>EXCEL.EXE</code></pre></li>
- Obdobný způsob proveďte pro aplikaci MS PowerPoint:
<li style="list-style-type: none"><pre><code>POWERPNT.EXE</code></pre></li>

<br>

#### Ochrana proti exploitaci starších verzí Windows:
- [Microsoft Enhanced Mitigation Experience Toolkit](https://support.microsoft.com/cs-cz/help/2458544/the-enhanced-mitigation-experience-toolkit) (EMET; Windows 8.1 Update 3 a níže)
- [HitmanPro.Alert](https://www.hitmanpro.com/en/alert.aspx) (HMP.A)

<span class="red">EMET</span> je anti-exploit řešení od MS určeno pro **starší verze OS**, které anti-exploit mitigace nemají integrovány.

> Instalace a konfigurace EMET (starší verze Windows)

- Stáhněte si nejnovější verzi [EMET](https://aka.ms/emetdownload).
- Aplikaci nainstalujte.
- V průběhu instalace se zobrazí okno se základním nastavením aplikace. Zvolte možnost <span class="green">Use Recommended Settings</span> a klikněte na <span class="green">Finish</span>.
<li style="list-style-type: none">![emet](https://faq.mople71.cz/img/en/emet.png)</li>
- Otevřete si <span class="green">EMET GUI</span>.
- V horním menu EMET klikněte na tlačítko <span class="green">Apps</span>.
- Zobrazí se seznam mitigovaných aplikací, pro přidání nové klikněte na tlačítko <span class="green">Add Application</span>.
<li style="list-style-type: none">![emet1](https://faq.mople71.cz/img/en/emet1.png)</li>
- Nalezněte a zvolte požadovanou aplikaci, kterou chcete mitigovat.
<li style="list-style-type: none">![wd8](https://faq.mople71.cz/img/cs/wd8.png)</li>
- Upravte konfiguraci dle obrázku:
<li style="list-style-type: none">![emet2](https://faq.mople71.cz/img/en/emet2.png)</li>
- Po dokončení nastavení všech aplikací zkontrolujte nastavení mitigací, případně opravte dle obrázku:
<li style="list-style-type: none">![emet3](https://faq.mople71.cz/img/en/emet3.png)</li>
- Klikněte na <span class="green">OK</span> a zavřete EMET spolu s vyskakovacím oknem, které se objeví.

<div class="alert info"><p><em class="icon-info-circled"></em>**Info**<br>
Jaké další aplikace mitigovat? Veškerý rizikový SW třetí strany – např. VLC, 7-Zip, PDF prohlížeč, Steam apod.</p></div>

**TIP pro rychlou konfiguraci aplikace:**
- Pro rychlou konfiguraci aplikace danou aplikaci nejprve spusťte.
- Otevřete si <span class="green">EMET GUI</span>.
- V listu běžících procesů nalezněte danou aplikaci, klikněte na ni pravým tlačítkem a zvolte možnost <span class="green">Configure Process&#8230;</span>
- Otevře se nastavení aplikací s nově přidanou zvolenou aplikací, pro kterou následně nakonfigurujte mitigace, a klikněte na <span class="green">OK</span>.
<li style="list-style-type: none">![emet4](https://faq.mople71.cz/img/en/emet4.png)</li>

<br>

<span class="red">HitmanPro.Alert</span> je placená aplikace, která nabízí komplexní zabezpečení včetně mitigací proti exploitům. Investice do něj má smysl u starších verzí OS, verze **Windows 10 Fall Creators Update** a novější ovšem mají většinu hlavních funkcí HMP.A integrovanou v OS.

> Instalace a konfigurace HMP.A (starší verze Windows)

- Stáhněte si [HMP.A](https://www.hitmanpro.com/en/alert.aspx).
- Aplikaci nainstalujte, ponechte doporučené nastavení a možnost skenu po instalaci.
- Aplikaci otevřete.
- Klikněte na ozubené kolo v pravém horním rohu a zvolte možnost <span class="green">Advanced interface</span>.
- Následně v dolní části klikněte na možnost **Safety notification** a zvolte možnost <span class="green">At application start</span>.
<li style="list-style-type: none">![hmpa](https://faq.mople71.cz/img/en/hmpa.png)</li>
- Následně klikněte na kategorii <span class="green">Risk reduction</span> a zapněte všechny její funkce, které nejsou vypnuté. Funkce, které již jsou zapnuté, ponechte na výchozím nastavení.
- Při otevření prohlížeče nebo jiné chráněné aplikace se při ponechání myši na pár sekund na kraji jejího okna  zobrazí ohraničení, které signalizuje, že HMP.A chrání danou aplikaci a také ukazuje, které funkce HMP.A jsou pro danou aplikaci zapnuté. Mimo jiné se objeví notifikace o zapnutí ochrany pro danou aplikaci.
<li style="list-style-type: none">![hmpa1](https://faq.mople71.cz/img/en/hmpa1.png)</li>
<li style="list-style-type: none">![hmpa2](https://faq.mople71.cz/img/en/hmpa2.png)</li>
- Při zachycení útoku HMP.A školivou aplikaci ukončí a zobrazí následující hlášku:
<li style="list-style-type: none">![hmpa3](https://faq.mople71.cz/img/en/hmpa3.png)</li>

<div class="alert success"><p><em class="icon-ok-circled"></em>**Tip**<br>
Více informací můžete nalézt v [manuálu](https://www.hitmanpro.com/en-us/medialibrary/Microsites/SurfRight/Resources/HitmanPro-Alert-Getting-Started.pdf) [EN].</p></div>

<br>

### Anti-executable:
Anti-executable je velmi účinná vrstva ochrany. Jak název napovídá, anti-executable řešení zabraňuje spouštění spustitelných souborů, tedy i malware.

Většina řešení funguje na principu *whitelistu* &ndash; má nastaveno, které spustitelné soubory povolit, a při spuštění neznámého souboru zobrazí uživateli dialog pro povolení/zakázání, případně souboru rovnou zabraní ve spuštění. Nastavení whitelistu není úkol pro běžné uživatele, existují ovšem i řešení, která umí whitelist vytvořit s minimem uživatelské interakce.

#### Přehled anti-executable řešení:
- [NVT Anti-AutoExec](https://www.novirusthanks.org/products/anti-autoexec/)
- [VoodooShield](https://voodooshield.com/) (VS)
- [NVT ExeRadarPro](https://www.novirusthanks.org/products/exe-radar-pro/) (NVT ERP)
- [AppLocker](https://technet.microsoft.com/cs-cz/library/dd759117.aspx)
- [Software Restrtiction Policies](https://technet.microsoft.com/cs-cz/library/hh831534.aspx) (SRP)

<span class="red">NVT Anti-AutoExec</span> je drobná aplikace, která automaticky zabraňuje šíření USB malware. Stačí nainstalovat a ochrana je aktivní bez jakékoli interakce.

<span class="red">VoodooShield</span> je nejpřívětivější anti-executable a vhodná volba pro obyčejné uživatele, pro profesionální nasazení z důvodů implementace ochrany již ne. Kromě placené verze poskytuje i bezplatnou pro nekomerční využití, která poskytuje srovnatelnou ochranu, akorát nenabízí možnost rozšířené konfigurace &ndash; což běžného uživatele nemusí trápit. V základu je aplikace nakonfigurována bezpečně. Bohužel (zatím) nenabízí české rozhraní.

> Instalace a konfigurace VoodooShield

- Stáhněte si [VoodooShield](https://voodooshield.com/#download).
- Aplikaci nainstalujte.
- Vyčkejte na dokončení konfigurace aplikace a při dotázání zvolte <span class="green">Application Whitelisting Mode</span>. Uvítací okno následně zavřete.
- Klikněte pravým tlačítkem na ikonu aplikace v hlavním panelu a vyberte možnost <span class="green">Hide</span>, čímž skryjete widget aplikace z pracovního prostoru.
- Klikněte pravým tlačítkem na ikonu aplikace v hlavním panelu a zvolte mód <span class="green">Training</span>.
<li style="list-style-type: none">![vs](https://faq.mople71.cz/img/en/vs.png)</li>
- Nyní se VoodooShield učí aplikace, které používáte, a povoluje je. V tréninkovém módu postupně spusťte všechny aplikace, které používáte. Ideální je v tréninkovém módu PC používat jeden den, aby VoodooShield vše stihl zapsat.
- Po ukončení tréninku VoodooShield klikněte pravým tlačítkem na ikonu aplikace v hlavním panelu a zvolte mód <span class="green">Always On</span>.
<li style="list-style-type: none">![vs1](https://faq.mople71.cz/img/en/vs1.png)</li>

<div class="alert success"><p><em class="icon-ok-circled"></em>**Úspěch**<br>
Nyní máte plně funkční anti-executable ochranu aplikace VoodooShield. Když budete chtít instalovat libovolnou aplikaci, zvolte <strong>Disable/Install Mode</strong>.</p></div>

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

<span class="red">AppLocker</span> je anti-executable integrovaný ve Windows v edicích **Ultimate**, **Education** a **Enterprise**. Umožňuje ovládání spustitelných souborů, skriptů, DLL knihoven, MSI instalátorů a ModernUI (metro) aplikací. Poskytuje vcelku slušnou ochranu, na druhou stranu existují známé způsoby jeho obejití.

<span class="red">Software Restriction Policy</span> je funkčně velmi omezený anti-executable dostupný ve všech edicích Windows. Umožňuje ovládání spustitelných souborů a skriptů. Jeho pravidla jsou ovšem vázána na proces *explorer.exe*, který je vlastněn uživatelem, není tedy ideální k profesionálnímu nasazení.

<br>

### Virtualizace:
Virtualizace může být velmi bezpečný způsob ochrany před malware (záleží na způsobu aplikace), jelikož odděluje požadovanou část OS od fyzického OS. Základních možností aplikace virtualizace je několik.

- virtuální stroj (VM; virtual machine)
- částečná virtualizace OS
- sandbox &ndash;

#### Virtuální stroj:
Nejbezpečnější způsob virtualizace je emulace virtuálního zařízení, kdy je virtualizován celý OS &ndash; za korektního nastavení a využití snapshotů. Po správné konfiguraci můžete virtuální stroj používat např. k vcelku bezpečnému brouzdání internetem.

Virtualizován může být libovolný OS jako Windows nebo linuxová distribuce. Pro virtualizaci OS Windows pro něj ovšem budete potřebovat dodatečnou licenci. Přehled populárních řešení naleznete níže:

- [Hyper-V](https://docs.microsoft.com/cs-cz/virtualization/hyper-v-on-windows/about/)
- [VMware Workstation Player](https://www.vmware.com/go/downloadworkstationplayer)
- [VirtualBox](https://www.virtualbox.org/)
- &#8230;

<span class="red">Hyper-V</span> je integrované řešení ve Windows v edicích **Pro** a **Enterprise**.

<span class="red">VMware Workstation Player</span> je bezplatný virtualizační software, který je oproti své placené mutaci značně funkčně omezený.

<span class="red">VirtualBox</span> je nejpopulárnější bezplatné open-source řešení, které umožňuje důležitou konfiguraci bezpečnostních funkcí jako snapshotů. Není ideální k profesionálnímu nasazení.

> Příklad vytvoření VM s linuxovou distribucí pomocí VirtualBox

- Stáhněte si [VirtualBox](https://www.virtualbox.org/wiki/Downloads).
- Aplikaci nainstalujte.
- Po otevření aplikace v horním menu klikněte na tlačítko <span class="green">Nový</span>.
- V dolním panelu zvolte <span class="green">Expertní režim</span>.
- Zvolte název VM a požadovaný OS. Následně určete velikost paměti OS a tlačítkem <span class="green">Vytvořit</span> otevřete dialog k vytvoření virtuálního pevného disku.
- Zvolte jeho velikost (alespoň *20 GB*) a vytvořte jej.
- Upravte nastavení VM dle potřeby a následně virtuální stroj spusťte. Vyberte bootovací disk požadovaného OS a klikněte na tlačítko <span class="green">Spustit</span>.
- Nainstalujte a nakonfigurujte OS. Po úspěšné konfiguraci pro požadované účely virtuální stroj vypněte.
- V pravém horním menu rozklikněte nabídku **Machine Tools** a zvolte <span class="green">Snímky</span>.
<li style="list-style-type: none">![vbox](https://faq.mople71.cz/img/cs/vbox.png)</li>
- Tlačítkem <span class="green">Take</span> vytvořte nový snapshot virtuálního stroje.
- Snapshot pojmenujte a klikněte na <span class="green">OK</span>.
<li style="list-style-type: none">![vbox1](https://faq.mople71.cz/img/cs/vbox1.png)</li>
- Při následujícím vypnutí virtuálního stroje nastavte automatické obnovení vytvořeného snapshotu.
- Čas od času (např. 1x měsíčně) virtuální OS aktualizujte a vytvořte nový snapshot.

<br>

#### Částečná virtualizace OS:
Implementací částečné virtualizace OS je mnoho. Může spočívat ve virtualizaci jádra či jiné části OS, nebo např. ve vrácení změn v OS při restartu ([Shadow Defender](http://www.shadowdefender.com/),&#8230;).

Od verze **Windows 10 September 2018 update** je částečná virtualizace implementována v OS. Konfigurace je možná pomocí <span class="green">Centra zabezpečení v programu Windows Defender</span> v sekci **Zabezpečení zařízení**.

<br>

#### Sandbox:
U sandboxu velmi záleží na implementaci, např. bezplatné řešení [Sandboxie](https://www.sandboxie.com/) poskytující externí sandbox pro aplikace, je spíše na hraní. Windows implementují svůj vestavěný sandbox (*AppContainer*), pokročilejší virtualizaci integrují ve verzích pro firemní sféru.

> Instalace a konfigurace Sandboxie

- Stáhněte si [Sandboxie](https://www.sandboxie.com/DownloadSandboxie).
- Aplikaci nainstalujte a projděte úvodním tutoriálem.
- Otevřete **Ovládání Sandboxie**.
- Klikněte pravým tlačítkem na **Sandbox DefaultBox** a zvolte možnost <span class="green">Nastavení Sandboxu</span>.
<li style="list-style-type: none">![sbie](https://faq.mople71.cz/img/cs/sbie.png)</li>
- V pravém panelu rozbalte možnost **Vymazat** a klikněte na <span class="green">Smazat pracovní soubory</span>.
- Zatrhněte možnost <span class="green">Automaticky smazat obsah Sandboxu</span> a klikněte na <span class="green">OK</span>.
<li style="list-style-type: none">![sbie1](https://faq.mople71.cz/img/cs/sbie1.png)</li>

<br>

### Ostatní aplikace:
Užitečné aplikace, které nelze zařadit pod určitou vrstvu zabezpečení.

#### Doporučené ostatní aplikace:
- [Kaspersky Software Updater](https://www.kaspersky.com/free-software-updater) (KSU)
- [Unchecky](https://unchecky.com/)
- [HashTab](http://implbits.com/products/hashtab/)

> Instalace a konfigurace Kaspersky Software Updater

- Stáhněte si [Kaspersky Software Updater](https://www.kaspersky.com/downloads/thank-you/free-software-updater).
- Máte-li nastavený **Řízený přístup ke složkám** ve <span class="green">Windows Defender</span>, dočasně jej po dobu instalace vypněte.
- Odsouhlaste všechny podmínky a aplikaci nainstalujte.
- Po startu aplikace otevřete nastavení kliknutím na ozubené kolo v levém dolním rohu.
- Ujistěte se, že **režim vyhledávání aktualizací** je nastaven na <span class="green">Úplné vyhledávání</span>.
- Zvolte si požadovaný čas vyhledávání aktualizací, časový interval ponechte na *jednou týdně*.
- Odeberte zatržítko u položky <span class="green">Chci, aby mi společnost Kaspersky Lab zasílala zprávy s novinkami a speciálními nabídkami</span>.
<li style="list-style-type: none">![ksu](https://faq.mople71.cz/img/cs/ksu.png)</li>
- Nastavení uložte a vraťte se zpět na úvodní obrazovku aplikace.
- Klikněte na <span class="green">Vyhledat aktualizace</span>.
- Kaspersky Software Updater zobrazí dostupné aktualizace vašich aplikací. Aktualizaci můžete provést ručně přes stránky výrobce, nebo pomocí KSU kliknutím na tlačítko <span class="green">Aktualizovat</span>.
- Aplikaci zavřete. Marketingovou řečnickou otázku v horní liště aplikace okázale ignorujte.
<li style="list-style-type: none">![ksu1](https://faq.mople71.cz/img/cs/ksu1.png)</li>
- Aplikaci pravděpodobně budete muset povolit v **Řízeném přístupu ke složkám**, který nyní opětovně zapněte. Návod [zde](#wnt2.1).

<div class="alert info"><p><em class="icon-info-circled"></em>**Info**<br>
Ačkoli je *Kaspersky Software Updater* kvalitní aplikace, automatická aktualizace aplikací otevírá prostor problémům. Na druhou stranu se jedná o menší zlo v porovnání s neaktuálními aplikacemi. Pokud tedy takto konfigurujete OS člověku, který si s PC nerozumí a nebude aplikace aktualizovat, povolení automatických aktualizací zvažte.</p></div>

> Instalace a konfigurace Unchecky

- Stáhněte si [Unchecky](https://unchecky.com/files/unchecky_setup.exe).
- Aplikaci nainstalujte.
- Otevřete rozhraní aplikace a přesuňte se do sekce **Nastavení**.
- Vypněte zobrazování ikony v oznamovací oblasti a klikněte na <span class="green">Použít</span>.
<li style="list-style-type: none">![un](https://faq.mople71.cz/img/cs/un.png)</li>

> Instalace a konfigurace HashTab

- Stáhněte si [HashTab](http://implbits.com/products/hashtab/).
- Aplikaci nainstalujte.
- Nalezněte libovolný soubor na disku a otevřete jeho **Vlastnosti**.
- V horním panelu se přesuňte do záložky **File Hashes** a klikněte na tlačítko <span class="green">Settings</span>.
<li style="list-style-type: none">![ht](https://faq.mople71.cz/img/en/ht.png)</li>
- Upravte konfiguraci dle obrázku a klikněte na <span class="green">OK</span>.
<li style="list-style-type: none">![ht1](https://faq.mople71.cz/img/en/ht1.png)</li>

<br><br><hr><br>

## Zabezpečení internetového prohlížeče
- bezpečnější nastavení (vypnutí nebezpečných funkcí, ideálně vč. javascriptu)
- blokování reklamy
- oddělení prohlížeče od dat a fyzického OS (sandbox &lt; VM &lt; live OS)

> Porovnání prohlížečů z ohledu bezpečnosti

Všechny prohlížeče jsou po korektním nastavení relativně bezpečné, velmi důležitým faktorem je také samotný uživatel. Níže v sekci naleznete návody na zabezpečení **Google Chrome**, **Microsoft Edge**, **Mozilla Firefox** a **Internet Explorer**, z důvodu jejich dominantního postavení.

Ze zmíněných prohlížečů jsou na vrcholu <span class="green">Microsoft Edge</span> a <span class="green">Chromium</span>, případně jeho proprietární varianta [Google Chrome](https://www.google.com/chrome/browser/index.html).

<span class="green">Chrome / Chromium</span> využívá špičkovou implementaci vestavěného sandboxu OS (LP-AC). Také integruje všechny moderní mitigace včetně **CFG**, což je významné plus.

<span class="green">Microsoft Edge</span> je nový a moderní prohlížeč využívající implementaci vestavěného sandboxu OS (AC). Používá moderní mitigace jako **CFG**, což je významné plus.

<span class="red">Mozilla Firefox</span>. Tento prohlížeč z hlediska zabezpečení v porovnání s ostatními zmíněnými prohlížeči stále o něco zaostává. Oproti svým konkurentům má starý kód nižší kvality a postrádá moderní mitigace proti exploitaci. Na druhou stranu již integruje solidní implementaci sandboxu a tvrdě pracuje na nápravě.

Prohlížeč **Internet Explorer** již není v aktivním vývoji, jeho používání tedy není pro denní užití doporučeno.

<br>

<!--- ./browsers.md -->

<br><br><hr><br>

## Doporučené bezpečnostní konfigurace
Zde naleznete několik příkladů bezpečnostních konfigurací. Není tedy je slovo od slova kopírovat, stačí se inspirovat. Na druhou stranu níže zmíněné příklady konfigurací jsou plně funkční a relativně účinné. Pokud byste chtěli příklad aplikovat, počítá se s prostudováním celé sekce OS Windows v FAQ &ndash; hlavně návodů na jednotlivé programy &ndash; a aplikací zmíněných doporučení.

#### Bezplatná konfigurace pro BFU, který neumí anglicky (např. prarodiče):
> Konfigurace

- OS &ndash; Windows **10 September 2018 Update**
- bezpečné nastavení OS &ndash; **kompletní**
- AV/M &ndash; **Windows Defender**
- FW &ndash; **Windows Defender Firewall**
- anti-exploit &ndash; **Windows Defender Exploit Guard**
- anti-executable &ndash; **NVT Anti-AutoExec**
- virtualizace &ndash; **integrovaná v OS**
- internetový prohlížeč &ndash; **MS Edge**, **Google Chrome** / **Brave**
- zabezpečení prohlížeče &ndash; **kompletní**
- užitečné aplikace &ndash; **Unchecky**, **Kaspersky Software Updater**
- konfigurace pro pokročilé &ndash; dle znalostí

Je nutné proškolit BFU, jak se má chovat na PC a na internetu. Bezpečně nastavit OS. **MS Edge** používat pro bankovní účely a podobné citlivé věci, **Google Chrome** či **Brave** pro běžné brouzdání.

<br>

#### Bezplatná konfigurace pro středně pokročilého, který umí anglicky:
> Konfigurace

- OS &ndash; Windows **10 September 2018 Update** / **8.1 Update 3**
- bezpečné nastavení OS &ndash; **kompletní**
- AV/M &ndash; **Windows Defender**
- FW &ndash; **Windows Defender Firewall**
- anti-exploit &ndash; **Windows Defender Exploit Guard** / **EMET**
- anti-executable &ndash; **VoodooShield**, **NVT Anti-AutoExec**
- virtualizace &ndash; **integrovaná v OS**, **virtuální stroj**
- internetový prohlížeč &ndash; **MS Edge**, **Chromium** / **Brave**
- zabezpečení prohlížeče &ndash; **kompletní**
- užitečné aplikace &ndash; **Kaspersky Software Updater**, **HashTab**
- konfigurace pro pokročilé &ndash; dle znalostí

<br><br><hr>

<h3 class="nocol">To je vše. Stay safe! ![smile](https://mople71.cz/img/sm/smile.svg)</h3>
