# FAQ – OS Windows
Windows se jakožto nejrozšířenější desktopový OS těší velké pozornosti hackerů, jeho dostatečné zabezpečení je proto nezbytné.

Podporovanými verzemi Windows v této sekci jsou <span class="green">Windows 10 May 2020 Update</span> jakožto aktuální verze OS a **Windows 8.1 Update 3**. Starší verze OS již postrádají důležité bezpečnostní mitigace/funkce a nejsou podporovány, jejich uživatelé by proto přejít na novější verzi, dovoluje-li to HW.

Tato sekce FAQ je určena běžným a středně pokročilým uživatelům. Sekci pro pokročilé naleznete [zde](https://securityhandbook.cz/cs/wnt/adv.php#wnt).


#### FAQ se dělí na několik sekcí:
- [Základní bezpečnostní nastavení](#wnt1)
- [Ochrana proti malware](#wnt2)
- [Zabezpečení internetového prohlížeče](#wnt3)
- [Doporučené bezpečnostní konfigurace](#wnt4)

<br>

## Základní bezpečnostní nastavení
### Práce pod Standardním uživatelem:

OS Windows má dva typy uživatelských účtů: <span class="green">Standardní uživatel</span> a <span class="green">Správce</span>.

Z hlediska bezpečnosti je nezbytné provádět denní činnosti pod Standardním uživatelem, jelikož má omezená oprávnění, která jsou pro práci plně dostačující. Pokud se do OS i přes všechny vrstvy ochrany dostane malware, infikuje pouze uživatelský účet – na infikaci OS nebude mít potřebná oprávnění.

<div class="alert exclaim"><p><em class="icon-attention"></em>**Varování**<br>
Jedná se o naprostý základ zabezpečení OS, bez kterého jsou veškerá další opatření zbytečná.</p></div>

> Přidání účtu Správce a změna stávajícího uživatele na Standardního

- Otevřete si <span class="green">Nastavení</span>. Rozklikněte kategorii **Účty** a následně zvolte podkategorii <span class="green">Rodina a jiní uživatelé</span>.
- Klikněte na tlačítko <span class="green">Přidat do tohoto počítače někoho dalšího</span>.
<li style="list-style-type: none">![wntus](https://securityhandbook.cz/img/cs/wntus.png)</li>
- Otevře se dialog pro přidání nového uživatele. V levém dolním rohu klikněte na <span class="green">Nemám přihlašovací údaje této osoby</span>.
- V levém dolním rohu zvolte možnost <span class="green">Přidat uživatele bez účtu Microsoft</span>.
- Zadejte název účtu Správce (např. **Admin**) a zvolte pro něj silné bezpečné heslo. Vyplňte bezpečnostní otázky a klikněte na <span class="green">Další</span>.
<li style="list-style-type: none">![wntus1](https://securityhandbook.cz/img/cs/wntus1.png)</li>
- V seznamu jiných uživatelů se zobrazí účet **Admin**. Klikněte na něj a následně zvolte <span class="green">Změnit typ účtu</span>.
<li style="list-style-type: none">![wntus2](https://securityhandbook.cz/img/cs/wntus2.png)</li>
- Zobrazí se dialog pro změnu typu účtu. Ze seznamu zvolte možnost <span class="green">Správce</span> a klikněte na <span class="green">OK</span>.
<li style="list-style-type: none">![wntus3](https://securityhandbook.cz/img/cs/wntus3.png)</li>
- Odhlaste se z vašeho účtu a přihlaste se jako **Admin**.
- Otevřete si <span class="green">Nastavení</span>. Rozklikněte kategorii **Účty** a následně zvolte podkategorii <span class="green">Rodina a jiní uživatelé</span>.
- V seznamu jiných uživatelů nalezněte svůj účet, klikněte na něj a následně zvolte <span class="green">Změnit typ účtu</span>.
- Zobrazí se dialog pro změnu typu účtu. Ze seznamu zvolte možnost <span class="green">Standardní uživatel</span> a klikněte na <span class="green">OK</span>.
- Odhlaste se z administrátorského účtu a přihlaste se zpět na svůj uživatelský účet.

> Přidání účtu Správce a změna stávajícího uživatele na Standardního (starší verze Windows)

- Otevřete si <span class="green">Nastavení</span>. Rozklikněte kategorii **Účty** a následně zvolte podkategorii <span class="green">Jiné účty</span>.
- Zvolte možnost <span class="green">Přidat účet</span>.
- Otevře se dialog pro přidání nového uživatele. V pravém dolním rohu klikněte na <span class="green">Přihlásit se bez účtu Microsoft</span>.
- Klikněte na tlačítko <span class="green">Místní účet</span>.
- Zadejte název účtu Správce (např. **Admin**) a zvolte pro něj silné bezpečné heslo.
- Potvrďte přidání uživatele (<span class="green">Dokončit</span>).
- V seznamu dalších účtů se zobrazí účet **Admin**. Klikněte na něj a následně zvolte <span class="green">Upravit</span>.
<li style="list-style-type: none">![wntusleg](https://securityhandbook.cz/img/cs/wntusleg.png)</li>
- Zobrazí se dialog pro změnu typu účtu. Ze seznamu zvolte možnost <span class="green">Správce</span> a klikněte na <span class="green">OK</span>.
<li style="list-style-type: none">![wntusleg1](https://securityhandbook.cz/img/cs/wntusleg1.png)</li>
- Odhlaste se z vašeho účtu a přihlaste se jako **Admin**.
- Otevřete si <span class="green">Nastavení</span>. Rozklikněte kategorii **Účty** a následně zvolte podkategorii <span class="green">Jiné účty</span>.
- V seznamu dalších účtů nalezněte svůj účet, klikněte na něj a následně zvolte <span class="green">Upravit</span>.
- Zobrazí se dialog pro změnu typu účtu. Ze seznamu zvolte možnost <span class="green">Standardní uživatel</span> a klikněte na <span class="green">OK</span>.
- Odhlaste se z administrátorského účtu a přihlaste se zpět na svůj uživatelský účet.

<br>

### User Account Control:

*User Account Control* je důležitá součást bezpečnostního modelu již OS od **Windows Vista**, kde se dočkala obrovské kritiky ze strany uživatelů a v novějších verzích OS je od té doby ve výchozím nastavením oslabena. Je důrazně doporučeno konfiguraci UAC zvýšit na nejpřísnější úroveň.

> Nastavení UAC

- Stiskněte kláv. zkratku ![win](https://securityhandbook.cz/img/icons/wkey.png) <span class="ks">+ R</span>, do textového pole zadejte:
<li style="list-style-type: none"><pre><code>useraccountcontrolsettings</code></pre>
a stiskněte **Enter**.</li>
- Otevře se konfigurace UAC. Posuvník nastavte na nejvyšší úroveň.
<li style="list-style-type: none">![uac](https://securityhandbook.cz/img/cs/uac.png)</li>
- Klikněte na <span class="green">OK</span>.

<br>

### Bezpečné nastavení služeb a funkcí Windows:

![batch](https://securityhandbook.cz/img/icons/bat.png) **WinSecOpt**:
- Stáhněte si [WinSecOpt](https://github.com/lhajn/WNT_scripts/releases/download/v1/winsecopt_cs.zip).
- Uložte a obsah archivu vyextrahujte <span class="blue">na Plochu</span>.
- Na skript jménem <span class="green">winsecopt</span> klikněte pravým tlačítkem a zvolte možnost: ![admin](https://securityhandbook.cz/img/icons/admin.png) **Spustit jako správce**.
- Nechte skript pracovat, na konci procesu vám řekne o souhlas k restartu OS.

> Nastavení SmartScreen (starší verze Windows)

- Stiskněte kláv. zkratku ![win](https://securityhandbook.cz/img/icons/wkey.png) <span class="ks">+ R</span>, do textového pole zadejte:
<li style="list-style-type: none"><pre><code>smartscreensettings</code></pre>
a stiskněte **Enter**.</li>
- Otevře se nastavení SmartScreen filtru. Upravte jej dle obrázku:
<li style="list-style-type: none">![smartscreen](https://securityhandbook.cz/img/cs/smartscreen.png)</li>
- Klikněte na <span class="green">OK</span>.

<br>

### Bezpečné nastavení sítě:
> Konfigurace síťového adaptéru + DNS

- Stiskněte kláv. zkratku ![win](https://securityhandbook.cz/img/icons/wkey.png) <span class="ks">+ R</span>, do textového pole zadejte:
<li style="list-style-type: none"><pre><code>ncpa.cpl</code></pre>
a stiskněte **Enter**.</li>
- Otevře se seznam síťových adaptérů. Klikněte na první adaptér (obvykle ethernet) pravým tlačítkem a zvolte možnost <span class="green">Vlastnosti</span>.
<li style="list-style-type: none">![wntnet](https://securityhandbook.cz/img/cs/wntnet.png)</li>
- V seznamu odškrtněte všechny nepotřebné položky. Běžným uživatelům stačí ponechat pouze <span class="green">Sdílení souborů a tiskáren v sítích Microsoft</span>, <span class="green">Protokol IP verze 4 (TCP/IPv4)</span> a <span class="green">Protokol IP verze 6 (TCP/IPv6)</span>.
- Pokud nesdílíte žádnou tiskárnu v síti a nepoužíváte IPv6 (pokud nevíte, zdali používáte IPv6, můžete to zjistil pomocí následujícího rychlého [online testu](https://www.test-ipv6.cz/)\), můžete pro vyšší bezpečnost ponechat zaškrtnutý pouze <span class="green">Protokol IP verze 4 (TCP/IPv4)</span>.
<li style="list-style-type: none">![wntnet1](https://securityhandbook.cz/img/cs/wntnet1.png)</li>
- Klikněte na **Protokol IP verze 4 (TCP/IPv4)** a zvolte možnost <span class="green">Vlastnosti</span>.
<li style="list-style-type: none">![wntnet2](https://securityhandbook.cz/img/cs/wntnet2.png)</li>

<div class="alert success"><p><em class="icon-ok-circled"></em>**Úspěch**<br>
Potenciálně nebezpečné protokoly jsou nyní vypnuty. Dále nastavíme bezpečné DNS servery.</p></div>

- Pokud vám zkratka DNS nic neříká, podívejte se na následující [jednoduchou stránku](http://www.jakfungujedns.cz/).
- Klikněte na <span class="green">Použít následující adresy serverů DNS</span> a do kolonek vepište následující DNS servery:
<li style="list-style-type: none"><pre><code>193.17.47.1
185.43.135.1</code></pre></li>
<li style="list-style-type: none">![wntnet3](https://securityhandbook.cz/img/cs/wntnet3.png)</li>
- Klikněte na tlačítko <span class="green">Upřesnit&#8230;</span>
- V horním panelu se přesuňte do záložky **WINS** a zvolte možnost <span class="green">Zakázat rozhraní NetBIOS nad protokolem TCP/IP</span>.
<li style="list-style-type: none">![wntnet4](https://securityhandbook.cz/img/cs/wntnet4.png)</li>
- Klikněte na <span class="green">OK</span>.
- Klikněte na <span class="green">OK</span> a okno zavřete.
- Pro *IPv6* použijte obdobný postup s následujícími servery:
<li style="list-style-type: none"><pre><code>2001:148f:ffff::1
2001:148f:fffe::1</code></pre></li>

<div class="alert exclaim"><p><em class="icon-attention"></em>**Varování**<br>
Pro dosáhnutí kýženého efektu je nutné kompletní postup aplikovat pro všechny síťové adaptéry v seznamu – obvykle Wi-Fi modul.</p></div>

<br>

### Další bezpečnostní nastavení:
- Vypněte Usnadnění přístupu na přihlašovací obrazovce – součást skriptu *WinSecOpt*.
- Vypněte AutoPlay:
    - Otevřete si <span class="green">Nastavení.</span> Rozklikněte kategorii **Zařízení** a následně zvolte podkategorii <span class="green">Automatické přehrávání</span>.
    - Automatické přehrávání vypněte.
    <li style="list-style-type: none">![autoplay](https://securityhandbook.cz/img/cs/autoplay.png)</li>
- Vypněte Remote Assistance:
    - Stiskněte kláv. zkratku ![win](https://securityhandbook.cz/img/icons/wkey.png) <span class="ks">+ R</span>, do textového pole zadejte:
    <li style="list-style-type: none"><pre><code>sysdm.cpl</code></pre>
a stiskněte **Enter**.</li>
    - Zobrazí se Vlastnosti systému.
    - Přesuňte se do záložky **Vzdálený přístup** a <span style="color: #BF0000">odstraňte</span> zatržítko u položky <span class="green">Povolit připojení vzdálené pomoci k tomuto počítači</span>.
    <li style="list-style-type: none">![sysdm](https://securityhandbook.cz/img/cs/sysdm.png)</li>
    - Klikněte na <span class="green">OK</span>.

<br><br><hr><br>

## Ochrana proti malware
Jako nejúčinnější metoda ochrany proti malware se osvědčila bezpečnostní konfigurace skládající se z více vrstev (*&bdquo;layered config&ldquo;*) – pokud selže jedna vrstva, nastupuje druhá. Bohužel stále není neobvyklé spoléhání se pouze na jednu tradiční vrstvu – antivirus – což je z hlediska bezpečnosti tristní.

Samotný OS poskytuje jistou úroveň ochrany proti malware, která se liší v závislosti na verzi a edici OS. V základním nastavení nejsou všechny bezpečnostní funkce zapnuty a/nebo korektně nastaveny.

<br>

### Aktualizace OS a SW:
Je důležité mít aktuální verzi veškerého SW, jelikož nové verze často opravují mnoho bezpečnostních chyb. Neaktuální děravý SW je implicitně nebezpečný.

Windows by se měly ve výchozím nastavení aktualizovat samy (v edici *Home* automatické aktualizace dokonce nelze vypnout). Důležité aplikace (např. prohlížeče, Adobe Reader) se zpravidla aktualizují automaticky.

Pro kontrolu aktualizací ostatního SW aktuálně neexistuje ideální aplikace.

> Kontrola nastavení aktualizací OS (starší verze Windows)

- Stiskněte kláv. zkratku ![win](https://securityhandbook.cz/img/icons/wkey.png) <span class="ks">+ R</span>, do textového pole zadejte:
<li style="list-style-type: none"><pre><code>wuapp</code></pre>
a stiskněte **Enter**.</li>
- V levém panelu klikněte na tlačítko <span class="green">Změnit nastavení</span>.
- Zkontrolujte, že **důležité aktualizace** mají zvolenou možnost <span class="green">Instalovat aktualizace automaticky (doporučeno)</span>, případně napravte.
- Zkontrolujte, že je <span style="color: #BF0000">odstraněné</span> zatržítko u možnosti <span class="green">Získávat doporučené aktualizace stejným způsobem jako důležité aktualizace</span>, případně napravte.
- Klikněte na <span class="green">OK</span> a okno zavřete.

<br>

### Windows Defender:
Windows Defender je integrovaný komplexní bezpečnostní systém, jenž spolehlivě pokrývá vrstvy zabezpečení **antivirus / antimalware**, **firewall** i **anti-exploit**.

Antivirus nebo antimalware (AV/M) je uživateli často chápán jako vrstva zabezpečení, která sama o sobě stačí k zabezpečení OS. Tato teze již dlouhou dobu není pravdivá. Tradiční antimalware ochrana nicméně má v bezpečnostní konfiguraci své místo, a je integrována v rámci systému *Windows Defender*.

<div class="alert exclaim"><p><em class="icon-attention"></em>**Varování**<br>
Instalace antivirových řešení třetích stran je důrazně nedoporučena.</p></div>

<div class="alert info"><p><em class="icon-info-circled"></em>**Info**<br>
Windows Defender může zobrazovat varování, pokud používáte lokální uživatelský účet bez propojení s účtem Microsoftu. Varování se snadno zbavíte otevřením *Centra zabezpečení v programu Windows Defender* a následně tlačítkem *Zavřít*.</p></div>

> Rozebrání problematiky antivirů

Tradiční mechanismus antiviru je založen na detekci známého malware, jehož otisk má v databázi. Pokud otisk pro malware neexistuje, nebude vyhodnocen jako škodlivý.

Novější technologií je *heuristika*: škodlivost kódu je vyhodnocena podle aktivity po jeho spuštění (vzorek je testován v izolovaném prostředí), na základě předvolených pravidel a indikací, které jsou u vzorku pozorovány. Provede-li malware nekalou činnost, která není heuristickými pravidly označena jako škodlivá, malware bude vyhodnocen jako neškodný.

Obejít výše zmíněné postupy není příliš náročné. Nejnovějším trendem je využití velkých dat a *AI* pro detekci malware. Tyto pokročilé technologie jsou zpravidla implementovány pouze v enterprise placených produktech nepřístupných běžným uživatelům (např. [SentinelOne](https://www.sentinelone.com/)) a ani ty nejsou nepřůstřelné.

Detekce **Windows Defender** je na velmi dobré úrovni. Jedná se o výchozí AV/M řešení na instalacích aktuálních verzí OS – počet uživatelů zvyšuje šanci zachytit nový malware. Implementuje vyspělý cloudový systém, díky kterému nabízí užitečné pokročilé funkce (např. *block on first sight*).

<br>

#### Ochrana proti tradičnímu malware:

> Konfigurace Ochrany před viry a hrozbami

- Otevřete si <span class="green">Centrum zabezpečení v programu Windows Defender</span>.
- Rozklikněte kategorii **Ochrana před viry a hrozbami**.
- Tlačítkem <span class="green">Spravovat nastavení</span> otevřete nastavení ochrany před viry a hrozbami.
- Zkontrolujte konfiguraci ochrany a případně opravte:
<li style="list-style-type: none">![wdmal](https://securityhandbook.cz/img/cs/wdmal.png)</li>

> Konfigurace Ochrany na základě reputace

- Přesuňte se do kategorie **Řízení aplikací a prohlížečů**.
- Otevřete <span class="green">Nastavení Ochrany na základě reputace</span>.
- Zkontrolujte konfiguraci SmartScreen filtru a případně opravte:
<li style="list-style-type: none">![wdmal1](https://securityhandbook.cz/img/cs/wdmal1.png)</li>

<br>

Ve verzi OS **Windows 8.1 Update 3** obsahuje *Windows Defender* podstatně méně funkcí, stále se ovšem jedná o rozumnou volbu pro tradiční antimalware ochranu.

> Konfigurace Ochrany před viry a hrozbami (starší verze Windows)

- Otevřete si <span class="green">Windows Defender</span>.
- Přesuňte se do záložky **Nastavení** a zvolte podkategorii <span class="green">Ochrana v reálném čase</span>.
- Zkontrolujte zatržítko u volby <span class="green">Zapnout ochranu v reálném čase</span>.
- Přesuňte se do podkategorie **Upřesnit**. Zkontrolujte konfiguraci ochrany a případně opravte:
<li style="list-style-type: none">![wdleg](https://securityhandbook.cz/img/cs/wdleg.png)</li>
- Přesuňte se do podkategorie **Komunita MAPS**. Zkontrolujte konfiguraci ochrany a případně opravte:
<li style="list-style-type: none">![wdleg1](https://securityhandbook.cz/img/cs/wdleg1.png)</li>
- Přesuňte se do podkategorie **Správce** a zkontrolujte zatržítko u volby <span class="green">Zapnout tuto aplikaci</span>.
- Případné změny uložte a aplikaci zavřete.

<br>

#### Ochrana proti ransomware:
**Řízený přístup ke složkám** je velice cenná a důležitá integrovaná bezpečnostní funkce, která spravuje přístup aplikací k obsahu uživatelských složek. Na základě pravidel zhodnotí, zdali je pokus o přístup ze strany aplikace legitimní, a pokud vyhodnotí pokus o přístup jako podezřelý/nestandardní, odepře jej.

Zmíněná funkce prozatím není ve výchozím nastavení aktivována, jelikož čas od času chybně vyhodnotí pokus o přístup legitimní aplikace k souborům a odepře jej. Takovým aplikacím se následně musí v nastavení povolit přístup několika kliknutími.

> Konfigurace Řízeného přístupu ke složkám

- Otevřete si <span class="green">Centrum zabezpečení v programu Windows Defender</span>.
- Přesuňte se do kategorie **Ochrana před viry a hrozbami**.
- Na konci stránky zvolte <span class="green">Spravovat ochranu před ransomwarem</span>.
- Zapněte <span class="green">Řízený přístup ke složkám</span>.
<li style="list-style-type: none">![wdrans](https://securityhandbook.cz/img/cs/wdrans.png)</li>
- Ve výchozím nastavení jsou chráněny složky **Dokumenty**, **Obrázky**, **Videa** a **Hudba**.
- Pro přidání chráněné složky (např. Plochy) klikněte na <span class="green">Chráněné složky</span>, zvolte <span class="green">Přidat chráněnou složku</span>, nalezněte cestu k dané složce a potvrďte.

> Manuální povolení aplikace v Řízeném přístupu ke složkám

- Ve **správě ochrany před ransomwarem** zvolte <span class="green">Povolit aplikace v Řízeném přístupu ke složkám</span>.
- Klikněte na <span class="green">Přidat povolenou aplikaci</span>. Můžete buď požadovanou aplikaci nalézt na seznamu aplikací, jimž byl nedávno odepřen přístup, nebo aplikaci nalézt v souborovém systému.
- Nalezněte požadovanou aplikaci a přidejte ji (případně ostatní její spustitelné programy) na seznam.

<br>

#### Ochrana proti exploitaci:
Každý kód obsahuje minimálně jednu chybu. Některé z těchto chyb kvůli své povaze přináší bezpečnostní riziko. Takových chyb následně využívají tzv. *exploity* za účelem kompromitace systému a provedení typicky nekalé činnosti. Windows implementují nejmodernějších mitigace, exploitace důležitých samotného OS je proto časově náročná a velmi nákladná. Některé důležité aplikace (např. prohlížeč *Google Chrome*) jsou z hlediska mitigací proti exploitům také na velmi vysoké úrovni. Poté jsou zde ovšem aplikace, které dostatečné mitigace neimplementují, a jsou bohužel pro uživatele nezbytné.

Systém *Windows Defender* integruje extrémně robustní a silnou ochranu proti exploitaci kritických částí OS na bázi virtualizace, která ovšem ve výchozím nastavení není povolena z důvodu nepatrné ztráty systémových prostředků. **Je důrazně doporučeno funkcionalitu aktivovat.**

> Konfigurace izolace jádra

- Otevřete si <span class="green">Centrum zabezpečení v programu Windows Defender</span>.
- Přesuňte se do kategorie **Zabezpečení zařízení**.
- Otevřete <span class="green">Podrobnosti o izolaci jádra</span>.
- Aktivujte fuknci <span class="green">Integrita paměti</span>:
<li style="list-style-type: none">![wd2](https://securityhandbook.cz/img/cs/wd2.png)</li>
- Potvrďte restart OS.

Dále integruje *anti-exploit* řešení, které umí na spuštěnou aplikaci dodatečně nabalit různé mitigace a tím jejich exploitaci výrazně ztížit. Tuto funkcionalitu standardně ve výchozím nastavení aplikuje na některé důležité systémové procesy.

> Konfigurace mitigací pro jednotlivé aplikace (příklad: VoodooShield)

<div class="alert info"><p><em class="icon-info-circled"></em>**Info**<br>
Aplikace *VoodooShield* je rozebírána v sekci [Anti-executable](#wnt2.3) níže.</p></div>

<div class="alert exclaim"><p><em class="icon-attention"></em>**Varování**<br>
Níže uvedená konfigurace je určena pro aplikaci **VoodooShield** a nemusí být kompatibilní s jinými aplikacemi.</p></div>

- Otevřete si <span class="green">Centrum zabezpečení v programu Windows Defender</span>.
- Přesuňte se do kategorie **Řízení aplikací a prohlížečů**
- Otevřete <span class="green">Nastavení Ochrany Exploit Protection</span>.
- V horním panelu se přesuňte do záložky **Nastavení programu**.
- Klikněte na <span class="green">Přidat program, který chcete přizpůsobit</span> a poté <span class="green">Zvolit přesnou cestu k souboru</span>.
- Nalezněte a potvrďte požadovanou aplikaci, kterou chcete mitigovat (*VoodooShield.exe*).
<li style="list-style-type: none">![wdexpl](https://securityhandbook.cz/img/cs/wdexpl.png)</li>
- Upravte konfiguraci dle obrázku:
<li style="list-style-type: none">![wdexplvs](https://securityhandbook.cz/img/cs/wdexplvs.png)</li>
- Klikněte na <span class="green">Použít</span>.
- Postup zopakujte pro **VoodooShieldService.exe** ve stejném umístění s následující konfigurací:
<li style="list-style-type: none">![wdexplvss](https://securityhandbook.cz/img/cs/wdexplvss.png)</li>

> Konfigurace mitigací pro Microsoft Office

<div class="alert exclaim"><p><em class="icon-attention"></em>**Varování**<br>
Níže uvedená konfigurace je určena pro aplikace **MS Office** a nemusí být kompatibilní s jinými aplikacemi.</p></div>

- Klikněte na <span class="green">Přidat program, který chcete přizpůsobit</span> a poté <span class="green">Přidat podle názvu aplikace</span>.
- Do textového pole zadejte:
<li style="list-style-type: none"><pre><code>WINWORD.EXE</code></pre></li>
- Upravte konfiguraci dle obrázku:
<li style="list-style-type: none">![wdexplmso](https://securityhandbook.cz/img/cs/wdexplmso.png)</li>
- Klikněte na tlačítko <span class="green">Použít</span>.
- Obdobný způsob aplikujte pro aplikaci MS Excel:
<li style="list-style-type: none"><pre><code>EXCEL.EXE</code></pre></li>
- Obdobný způsob aplikujte pro aplikaci MS PowerPoint:
<li style="list-style-type: none"><pre><code>POWERPNT.EXE</code></pre></li>

<br>

Alternativním řešením, které v *anti-exploit* sekci stojí za zmínku, je placený software [HitmanPro.Alert](https://www.hitmanpro.com/en-us/alert.aspx) od společnosti Sophos. Kritický může být pro uživatele verze **Windows 8.1 Update 3**, kde nejsou pokročilé funkce ochrany integrovány v OS. Aplikace není dostupná v češtině.

> Instalace a konfigurace HitmanPro.Alert (starší verze Windows)

- Stáhněte si [HMP.A](https://www.hitmanpro.com/en/alert.aspx).
- Aplikaci nainstalujte, ponechte doporučené nastavení a možnost skenu po instalaci.
- Vyčkejte na dokončení skenu a vyřešte případné nálezy.
- Klikněte na ozubené kolo v pravém horním rohu a zvolte možnost <span class="green">Advanced interface</span>.
- Rozklikněte kategorii <span class="green">Risk reduction</span>.
- Zapněte funkci **BadUSB** a změňte nastavení funkce **Vaccination** na <span class="green">Active vaccination</span>.
<li style="list-style-type: none">![hmpa](https://securityhandbook.cz/img/en/hmpa.png)</li>
- Při otevření prohlížeče nebo jiné chráněné aplikace se při ponechání myši na pár sekund na kraji jejího okna zobrazí ohraničení, které signalizuje, že HMP.A chrání danou aplikaci a také ukazuje, které funkce HMP.A jsou pro danou aplikaci zapnuté. Mimo jiné se při prvním startu aplikace za uživatelské sezení objeví notifikace o aktivní ochraně.
<li style="list-style-type: none">![hmpa1](https://securityhandbook.cz/img/en/hmpa1.png)</li>
<li style="list-style-type: none">![hmpa2](https://securityhandbook.cz/img/en/hmpa2.png)</li>
- Při zachycení útoku HMP.A školivou aplikaci ukončí a zobrazí následující hlášku:
<li style="list-style-type: none">![hmpa3](https://securityhandbook.cz/img/en/hmpa3.png)</li>

<br>

#### Firewall:
Firewall je velmi důležitá vrstva zabezpečení, která chrání OS síťovými útoky. Systém *Windows Defender* integruje **Windows Defender Firewall** (WDF), který je pro standardní použití plně dostačující. *Poznámka na okraj: základem síťového zabezpečení v domácnosti je rozumný router.*

<div class="alert exclaim"><p><em class="icon-attention"></em>**Varování**<br>
Instalace firewall řešení třetích stran je důrazně nedoporučena.</p></div>

Firewall je v základu korektně nastaven na blokování příchozí komunikace, která není explicitně povolena. Pro citelné zvýšení bezpečnosti je možné nastavit FW na blokování veškeré odchozí komunikace, která není explicitně povolena. V novějších verzích OS je taková konfigurace ovšem nesnadný počin a rámcový návod je proto dostupný pouze v [sekci pro pokročilé](https://securityhandbook.cz/cs/wnt/adv.php#wnt1).

<br>

### Anti-executable:
Anti-executable je specifická vrstva ochrany. Jedná se o řešení, které na základě definovaných pravidel spravuje, jaký kód je v OS spuštěn. Tímto principem ideálně zachytí pokus o spuštění malware a zabrání mu. Většina řešení funguje na principu *whitelistu* – má nastaveno, které spustitelné soubory povolit, a při spuštění neznámého souboru zobrazí uživateli dialog pro povolení/zakázání, případně v závislosti na nastavení souboru přímo exekuci odepře. Nastavení whitelistu není triviální úkol, existují ovšem i řešení, která umí whitelist vytvořit s minimem uživatelské interakce.

Nejpřívětivějším řešením je software [VoodooShield](https://voodooshield.com/), jenž kromě placené verze nabízí i bezplatnou pro nekomerční využití, která poskytuje srovnatelnou ochranu, akorát nenabízí možnost rozšířené konfigurace. Jedinou zásadní nevýhodou je absence českého rozhraní.

> Instalace a konfigurace VoodooShield

- Stáhněte si [VoodooShield](https://voodooshield.com/#download).
- Aplikaci nainstalujte. Zadejte email pro bezplatnou registraci, zvolte <span class="green">Application Whitelisting Mode</span>.
- Vyčkejte na dokončení konfigurace. Uvítací okno následně zavřete.
- Klikněte pravým tlačítkem na ikonu aplikace v hlavním panelu a vyberte možnost <span class="green">Hide Desktop Shield</span>, čímž skryjete widget aplikace z pracovního prostoru.
- Klikněte pravým tlačítkem na ikonu aplikace v hlavním panelu a zvolte mód <span class="green">TRAINING</span>.
<li style="list-style-type: none">![vs](https://securityhandbook.cz/img/en/vs.png)</li>
- VoodooShield se nyní učí aplikace, které používáte, aby je následně mohl povolit bez uživatelské interakce. Ideální je v tréninkovém módu zařízení používat jeden den, aby VoodooShield vše stihl zapsat.
- Po ukončení tréninku VoodooShield klikněte pravým tlačítkem na ikonu aplikace v hlavním panelu a zvolte mód <span class="green">ALWAYS ON</span>.
<li style="list-style-type: none">![vs1](https://securityhandbook.cz/img/en/vs1.png)</li>

<div class="alert success"><p><em class="icon-ok-circled"></em>**Úspěch**<br>
Nyní máte plně funkční anti-executable ochranu aplikace VoodooShield. Když budete chtít instalovat libovolnou aplikaci, dočasně přepněte mód ochrany na <strong>DISABLE / INSTALL</strong>.</p></div>

> Ukázky a poznatky z provozu VoodooShield

- Jakmile VS zablokuje neznámou, ale možná bezpečnou aplikaci, zobrazí následující bublinu:
<li style="list-style-type: none">![vs2](https://securityhandbook.cz/img/en/vs2.png)</li>
- Pokud chcete aplikaci povolit, na bublinu klikněte a v následujícím okně zvolte možnost <span class="green">Install</span>.
<li style="list-style-type: none">![vs3](https://securityhandbook.cz/img/en/vs3.png)</li>
- Když VS zablokuje aplikaci, kterou detekuje alespoň 1 antivirový produkt nebo VoodooAI jako malware, zobrazí následující bublinu:
<li style="list-style-type: none">![vs4](https://securityhandbook.cz/img/en/vs4.png)</li>
- Zde je povolení o pár kliků delší, jedná-li se o legitimní aplikaci. Klikněte na bublinu, v následujícím okně zvolte možnost <span class="green">Allow False Positive</span> a odsouhlaste veškerá vyskakovací okna.
<li style="list-style-type: none">![vs5](https://securityhandbook.cz/img/en/vs5.png)</li>
- Po povolení aplikace a provedení vámi požadované akce se vždy přesvědčte, že VS běží v módu <span class="green">Always On</span>.

<br>

### Virtualizace:
Virtualizace může být velmi bezpečný způsob ochrany před malware v závislosti na způsobu implementace, jelikož odděluje požadovanou část OS od jeho zbytku. Standardních způsobů implementace virtualizace je několik:

- virtuální stroj (VM; virtual machine)
- semivirtuální stroj (např. docker)
- sandbox

#### Virtuální stroj:
Nejpokročilejší způsob virtualizace je emulace na nejnižší úrovni, kdy je virtualizován celý OS. Za korektního použití a nastavení (např. snapshoty) může jít o vysoce robustní bezpečnostní vrstvu. Po patřičné konfiguraci můžete virtuální stroj používat např. k relativně bezpečnému brouzdání internetem. Virtualizován může být libovolný OS jako Windows nebo linuxová distribuce. Pro virtualizaci OS Windows pro něj ovšem budete potřebovat dodatečnou licenci, nebo členství v programu Insider.

- [Hyper-V](https://docs.microsoft.com/cs-cz/virtualization/hyper-v-on-windows/about/)
- [VMware Workstation Player](https://www.vmware.com/go/downloadworkstationplayer)
- [VirtualBox](https://www.virtualbox.org/)

Majitelé edic OS Windows **Pro** a **Enterprise** mohou využít vestavěné profesionální řešení [Hyper-V](https://docs.microsoft.com/cs-cz/virtualization/hyper-v-on-windows/about/). Majitelé nižších edic OS mají na výběr z několika bezplatných a mnoha placených řešení třětích stran.

Z bezplatných řešení je jedinou volbou integrující důležité bezpečnostní funkce (mj. snapshoty) software <span class="red">VirtualBox</span>, populární bezplatné open-source řešení. Není ideální k profesionálnímu nasazení, spíše na hraní. Možnou robustnější alternativu tvoří <span class="red">VMware Workstation Player</span>, který je zdarma pro nekomerční využití, nepodporuje ovšem tvorbu snapshotů a neobsahuje české rozhraní.

> Vytvoření VM pomocí VirtualBox

- Stáhněte si .iso obraz OS, který chcete virtualizovat.
- Stáhněte si [VirtualBox](https://www.virtualbox.org/wiki/Downloads).
- Aplikaci nainstalujte.
- Po otevření aplikace v horním menu klikněte na tlačítko <span class="green">Nový</span>.
- V dolním panelu zvolte <span class="green">Expertní režim</span>.
- Zvolte název VM a požadovaný OS. Následně určete velikost paměti OS a tlačítkem <span class="green">Vytvořit</span> otevřete dialog k vytvoření virtuálního pevného disku.
- Zvolte jeho velikost (alespoň *22 GB*) a vytvořte jej.
- Upravte nastavení VM dle potřeby a následně virtuální stroj spusťte. Vyberte bootovací disk požadovaného OS a klikněte na tlačítko <span class="green">Spustit</span>.
- Nainstalujte a nakonfigurujte OS. Po úspěšné konfiguraci pro požadované účely virtuální stroj vypněte.
- V pravém horním menu rozklikněte nabídku **Machine Tools** a zvolte <span class="green">Snímky</span>.
<li style="list-style-type: none">![vbox](https://securityhandbook.cz/img/cs/vbox.png)</li>
- Tlačítkem <span class="green">Take</span> vytvořte nový snapshot virtuálního stroje.
- Snapshot pojmenujte a klikněte na <span class="green">OK</span>.
<li style="list-style-type: none">![vbox1](https://securityhandbook.cz/img/cs/vbox1.png)</li>
- Při následujícím vypnutí virtuálního stroje nastavte automatické obnovení vytvořeného snapshotu.
- Čas od času (např. 1x měsíčně) virtuální OS aktualizujte a vytvořte nový snapshot.

> Vytvoření VM pomocí VMware Workstation Player

- Stáhněte si .iso obraz OS, který chcete virtualizovat.
- Stáhněte si [VMware Workstation Player](https://www.vmware.com/go/downloadworkstationplayer).
- Aplikaci nainstalujte a otevřete. Potvrďte nekomerční účel využití.
- Klikněte na <span class="green">Create a New Virtual Machine</span>.
- Zvolte umístění instalace z **Installer disc image file (iso)** a nalezněte požadovaný ISO soubor. VMWare Player automaticky detekuje OS.
-  Projděte postupně konfigurací VM. Pojmenujte virtuální stroj, přidělte mu alespoň *25 GB* místa na disku, zvolte variantu **Store virtual disk as a single file**. Na konci zvolte možnost <span class="green">Customize hardware&#8230;</span>.
- V zařízení **Memory** přidělte virtuálnímu stroji alespoň *3072 MB* paměti. V zařízení **Processors** přidělte virtuálnímu stroji minimálně polovinu jader vašeho CPU, ideálně alespoň *4*.
- Klikněte na <span class="green">Close</span> a následně <span class="green">Finish</span>.

<br>

#### Sandbox:
Sandbox je populární způsob implementace virtualizace. Existují dva druhy sandboxu:

- sandbox nativně integrovaný v aplikaci (např. *Microsoft Edge*)
- externí sandbox – např. [Sandboxie](https://www.sandboxie.com/)

Sandbox nativně integrovaný v aplikaci je nejúčinnější možností implementace sandboxu, jelikož je nastaven přesně na míru dané aplikaci. Externí sandbox nemusí být nutně účinný jako sandbox integrovaný v aplikaci, jelikož není dělaný přesně na míru určité aplikaci, a při porovnání může ponechat větší prostor pro exploitaci. Stále ovšem může být velmi účinný a přirozeně je mnohem lepší, nežli žádný sandbox.

Bezplatné řešení [Sandboxie](https://www.sandboxie.com/) poskytující externí sandbox pro aplikace, je spíše na hraní. *Tato část sekce již nemá příliš praktické využití.*

> Instalace a konfigurace Sandboxie

- Stáhněte si [Sandboxie](https://www.sandboxie.com/DownloadSandboxie).
- Aplikaci nainstalujte a projděte úvodním tutoriálem.
- Otevřete **Ovládání Sandboxie**.
- Klikněte pravým tlačítkem na **Sandbox DefaultBox** a zvolte možnost <span class="green">Nastavení Sandboxu</span>.
<li style="list-style-type: none">![sbie](https://securityhandbook.cz/img/cs/sbie.png)</li>
- V pravém panelu rozbalte možnost **Vymazat** a klikněte na <span class="green">Smazat pracovní soubory</span>.
- Zatrhněte možnost <span class="green">Automaticky smazat obsah Sandboxu</span> a klikněte na <span class="green">OK</span>.
<li style="list-style-type: none">![sbie1](https://securityhandbook.cz/img/cs/sbie1.png)</li>

<br>

### Ostatní aplikace:
Užitečné aplikace související s bezpečností, které nelze zařadit pod určitou vrstvu zabezpečení.

#### Doporučené ostatní aplikace:
- [Unchecky](https://unchecky.com/)
- [NVT Anti-AutoExec](https://www.novirusthanks.org/products/anti-autoexec/)
- [HashTab](http://implbits.com/products/hashtab/)

> Instalace a konfigurace Unchecky

- Stáhněte si [Unchecky](https://unchecky.com/files/unchecky_setup.exe).
- Aplikaci nainstalujte.
- Otevřete rozhraní aplikace a přesuňte se do sekce **Nastavení**.
- Vypněte zobrazování ikony v oznamovací oblasti a klikněte na <span class="green">Použít</span>.
<li style="list-style-type: none">![un](https://securityhandbook.cz/img/cs/un.png)</li>

> Instalace a konfigurace NVT Anti-AutoExec

- Stáhněte si [NVT Anti-AutoExec](https://downloads.novirusthanks.org/files/anti-autoexec_setup.exe).
- Aplikaci nainstalujte.

> Instalace a konfigurace HashTab

- Stáhněte si [HashTab](http://implbits.com/products/hashtab/).
- Aplikaci nainstalujte.
- Nalezněte libovolný soubor na disku a otevřete jeho **Vlastnosti**.
- V horním panelu se přesuňte do záložky **File Hashes** a klikněte na tlačítko <span class="green">Settings</span>.
<li style="list-style-type: none">![ht](https://securityhandbook.cz/img/en/ht.png)</li>
- Upravte konfiguraci dle obrázku a klikněte na <span class="green">OK</span>.
<li style="list-style-type: none">![ht1](https://securityhandbook.cz/img/en/ht1.png)</li>

<br><br><hr><br>

## Zabezpečení internetového prohlížeče
- bezpečnější nastavení (vypnutí nebezpečných funkcí, ideálně vč. JavaScriptu)
- blokování reklamy

> Porovnání prohlížečů z ohledu bezpečnosti

Všechny prohlížeče jsou po korektním nastavení relativně bezpečné, kritickým důležitým faktorem je také samotný uživatel. V následující sekci naleznete postup pro bezpečnou konfiguraci **Microsoft Edge**, **Google Chrome** i **Mozilla Firefox** jakožto dominantních prohlížečů. Také zde naleznete prohlížeče **Brave** (open-source prohlížeč vycházející z Chromium, v *základu integruje blokování reklam a trackerů*) a **Chromium** (open-source prohlížeč, ze kterého vychází Google Chrome).

Z uvedených prohlížečů jsou z hlediska bezpečnosti nejlepší volbou <span class="green">Microsoft Edge</span> a <span class="green">Chromium</span>, případně jeho proprietární varianta [Google Chrome](https://www.google.com/chrome/browser/index.html) či prohlížeč [Brave](https://brave.com/).

<span class="green">Microsoft Edge / Google Chrome / Chromium</span> využívají špičkovou implementaci vestavěného sandboxu OS (LP-AC) a integrují všechny moderní mitigace včetně **CFG**. Prohlížeč *Brave* je na tom obdobně. <span class="red">Mozilla Firefox</span> z hlediska zabezpečení v porovnání s konkurencí stále zaostává, nicméně na Windows již situace není tak kritická jak dříve.

<br>

<!--- ./browsers.md -->

<br><br><hr><br>

## Doporučené bezpečnostní konfigurace
Zde naleznete několik příkladů bezpečnostních konfigurací, čistě pro inspiraci.

#### Bezplatná konfigurace pro běžného uživatele, který neumí anglicky:
> Konfigurace

- OS – Windows **10 May 2020 Update**
- bezpečné nastavení OS – **kompletní**
- AV/M – **Windows Defender**
- FW – **Windows Defender Firewall**
- anti-exploit – **Windows Defender**
- anti-ransomware – **Windows Defender**
- anti-executable – **N/A**
- virtualizace – **integrovaná**
- internetový prohlížeč – **MS Edge**, **Google Chrome** / **Brave**
- užitečné aplikace – **Unchecky**, **NVT Anti-AutoExec**
- konfigurace pro pokročilé – dle znalostí

Je nutné dodržovat základy bezpečnosti a bezpečného pohybu na internetu. **MS Edge** používat pro bankovní účely a podobné citlivé věci, **Google Chrome** či **Brave** pro běžné brouzdání.

<br>

#### Konfigurace pro středně pokročilého, který umí anglicky:
> Konfigurace

- OS – Windows **10 May 2020 Update** / **8.1 Update 3**
- bezpečné nastavení OS – **kompletní**
- AV/M:
    - W10 / W8.1 bezplatný – **Windows Defender**
    - W8.1 placený – **Sophos Home** / **F-Secure SAFE** / **Emsisoft Anti-Malware Home**
- FW – **Windows Defender Firewall** / **Windows Firewall**
- anti-exploit:
    - W10 bezplatný – **Windows Defender**
    - W8.1 placený – **HitmanPro.Alert**
- anti-executable – **VoodooShield**, **NVT Anti-AutoExec**
- virtualizace – **integrovaná**, **virtuální stroj**
- internetový prohlížeč – **MS Edge**, **Chromium** / **Brave**
- užitečné aplikace – **HashTab**
- konfigurace pro pokročilé – dle znalostí

<br><br><hr>

<h3 class="nocol">To je vše. Stay safe! ![smile](https://securityhandbook.cz/img/sm/smile.svg)</h3>
