# FAQ &ndash; OS Windows
Windows se jakožto nejrozšířenější desktopový OS těší velké pozornosti hackerů, jeho dostatečné zabezpečení je proto velmi důležité.

V FAQ pro pokročilé se budeme věnovat hlavně vestavěným funkcím OS &ndash; cílem je dosáhnout špičkového zabezpečení za použití co nejméně řádků kódu, jejichž počet s 3-P aplikacemi rapidně roste.

Tato sekce FAQ počítá s tím, že jste pročetli FAQ Windows pro méně pokročilé uživatele a máte znalosti ve zmíněné sekci rozebírané.

#### FAQ se dělí na několik sekcí:
- vrstvy zabezpečení
- integritní politika
- ACL
- AppContainer

<br>

## Vrstvy zabezpečení:
### Antivirus:
<span class="green">Windows Defender</span> integrovaný ve **Windows 8.1 Update 3** a **Windows 10** dosáhl úrovně, kdy dostatečně pokrývá tradiční vstrvu zabezpečení. Již tedy není nutné instalovat antivirus třetí strany, jehož kvalita kódu je řádově menší a v OS mnohdy provádí v porovnání s integrovaným řešením naprosté šílenosti. Defender mj. běží jako jediné antivirové řešení s **CFG**.

<br>

### Firewall:
Windows obsahují vestavěný <span class="green">Windows Firewall</span> (WF), který je na velmi dobré úrovni.

Použití FW třetí strany je zbytečné rozšiřování attack surface. Základem síťového zabezpečení v domácnosti je rozumný router s použitelným FW (např. Mikrotik, kde si FW ovšem samozřejmě musíte nastavit).

Co se týče blokování odchozí komunikace, Windows Firewall tuto funkci podporuje a umožňuje vcelku jednoduše nastavit.

![idea](https://mople71.cz/img/sm/idea.gif) Návod měl původně být v sekci pro méně pokročilé, ovšem z důvodu nepříjemného bugu (nebo funkce) Windows 10 Creators Update, automatické aktualizace OS nelze ve whitelistu rozumně definovat.

> Nastavení WF na blokování odchozí komunikace

- Otevřete si **hledání Windows**, do vyhledávacího pole zadejte:
<li style="list-style-type: none"><pre><code>wf.msc</code></pre></li>
- Na nalezenou položku klikněte pravým tlačítkem a zvolte možnost: ![admin](https://mople71.cz/img/admin.png) **Spustit jako správce**.
<li style="list-style-type: none">![wf](https://faq.mople71.cz/img/cs/wf.png)</li>
- Otevře se pokročilé nastavení Windows Firewall. V prostředním sloupci zvolte možnost <span class="green">Vlastnosti brány firewall</span>.
- V horním panelu si otevřete záložku **Privátní profil**. U položky **Odchozí připojení** zvolte možnost <span class="green">Blokovat</span>.
<li style="list-style-type: none">![wf1](https://faq.mople71.cz/img/cs/wf1.png)</li>
- Postup zopakujte pro záložku **Veřejný profil**.
- Klikněte na <span class="green">OK</span>.
<li style="list-style-type: none">![wf2](https://faq.mople71.cz/img/cs/wf2.png)</li>

![arrow](https://mople71.cz/img/sm/arrow.gif) <span class="green">Nyní WF blokuje veškerou odchozí kouminakci, která není na whitelistu. Dále je třeba nastavit whitelist.</span>

> Povolení odchozí komunikace pro důležité aplikace

- V levém sloupci otevřete <span class="green">Odchozí pravidla</span>.
- V pravém sloupci zvolte možnost <span class="green">Nové pravidlo...</span>
- Jako typ pravidla zvolte **Program** a klikněte na tlačítko <span class="green">Další</span>.
- Zvolte možnost **Cesta k tomuto programu** a klikněte na tlačítko <span class="green">Procházet...</span>
- Nalezněte a zvolte následující aplikaci: <span class="blue">C:\Windows\System32\smartscreen.exe</span>
<li style="list-style-type: none">![wf3](https://faq.mople71.cz/img/cs/wf3.png)</li>
- Klikněte na tlačítko <span class="green">Další</span>.
- Zvolte možnost **Povolit připojení** a klikněte na tlačítko <span class="green">Další</span>.
- Zkontrolujte zatržítka u všech možností a klikněte na tlačítko <span class="green">Další</span>.
- Zadejte název pravidla &ndash; v tomto případě např. **SmartScreen.exe**
- Klikněte na <span class="green">Dokončit</span>.

![idea](https://mople71.cz/img/sm/idea.gif) Stejným způsobem povolte veškeré další aplikace, které potřebují přístup k internetu (např. internetové prohlížeče, "%programfiles%\Windows Defender\MpCmdRun.exe", VoodooShield,...)

> Windows Update na Windows 10 (Creators Update)

Ve W10 CU není možné rozumně povolit Windows Update &ndash; nestačí povolit pouze nezbytné služby, je nutné povolit celý *svchost.exe*.

Je zde několik možností:

- Permanentně povolit SVCHost.exe pro porty 80 a 443 **(nedoporučeno)**.
- Povolit SVCHost.exe pouze po dobu instalace aktualizací.
- Instalovat aktualizace 1x měsíčně ručně a WU neřešit.
- ...

![arrow](https://mople71.cz/img/sm/arrow.gif) Problémem ovšem je, že přes WU se aktualizují definice Windows Defender, které je důležité mít aktuální.

Zde existuje také několik možností:

- Permanentně povolit WU.
- Vytvořit pravidlo pro povolení SVCHost.exe ve WF a pravidlo zakázat. Následně pro aktualizaci definicí WD napsat jednoduchý skript a naplánovat jeho spuštění 1x za 12 hodin. Např.:
<li style="list-style-type: none"><pre><code>@echo off
netsh advfirewall firewall set rule name="SVCHost.exe" new enable=yes
"%programfiles%\Windows Defender\MpCmdRun.exe" -SignatureUpdate
netsh advfirewall firewall set rule name="SVCHost.exe" new enable=no
pause</code></pre></li>
- ...

<br>

### Anti-executable:
<span class="red">AppLocker</span> je anti-executable integrovaný ve Windows v edicích Ultimate, Education a Enterprise. Umožňuje ovládání spustitelných souborů, skriptů, DLL knihoven, MSI instalátorů a ModernUI aplikací. Poskytuje vcelku slušnou ochranu, na druhou stranu existují známé způsoby jeho obejití.

<span class="red">NVT Anti-AutoExec</span> je drobná aplikace, která automaticky zabraňuje šíření USB malware. Stačí nainstalovat a ochrana je aktivní.

<span class="red">AppGuard</span> je profesionální anti-executable určený převážně pro firemní sféru, je ovšem dostupný i v domácí verzi. Jeho nastavení je vcelku komplikované a přizpůsobené pro odborníky. Návod na něj aktuálně není v plánu.

<br>

### FIDES:
[FIDES](https://excubits.com/content/en/products_pumpernickelfides.html) je drobný ovladač na úrovni kernelu, který si můžete představit jako nějakou obdobu MAC na Linuxu &ndash; program určuje, které procesy mají ke kterým souborům přístup. Jedná se o špičkové řešení, jehož konfigurace je vcelku jednoduchá, syntax konfiguračního souboru je triviální.

Existuje demo verze, která je po nějakou dobu (obvykle rok) plně funkční, akorát podporuje konfigurační soubor pouze do velikosti 2 kB, což není dostatek pro pokročilé nastavení. Doporučuji tedy investovat do plné verze a podpořit vývojáře, 12 € jako jednorázová platba mi přijde jako dobrá cena.

> Instalace FIDES

- Stáhněte si demo verzi ze stránek výrobce, soubor spusťte a aplikaci vybalte.
- V závislosti na bitové verzi OS otevřete složku **32-bit** / **64-bit**.
- Klikněte pravým tlačítkem na INF soubor a zvolte **Install**.
- Vraťte se do rootu aplikace a otevřete **Pumpernickel.ini**.
- Otevře se konfigurační soubor, kde definujete pravidla. V základu tam naleznete pravidlo, že Notepad nemá právo k modifikaci žádného souboru kromě TXT na Plochách uživatelů. RTFM, je v rootu aplikace.
- Po dokončení úprav konfiguračního souboru jej přesuňte do lokace **C:\Windows**.
- Následně ovladač aktivujte pomocí *net start pumpernickel*.

<br>

### MemProtect:
[MemProtect](https://excubits.com/content/en/products_memprotect.html) je drobný ovladač na úrovni kernelu, který určuje, které procesy mají přístup k ostatním procesům v RAM. Jedná se o špičkové řešení nejen proti řadám rodin exploitům, jehož konfigurace je vcelku jednoduchá, syntax konfiguračního souboru je triviální.

Existuje demo verze, která je po nějakou dobu (obvykle rok) plně funkční, akorát podporuje konfigurační soubor pouze do velikosti 2 kB, což není dostatek pro pokročilé nastavení. Doporučuji tedy investovat do plné verze a podpořit vývojáře, 12 € jako jednorázová platba mi přijde jako dobrá cena.

> Instalace MemProtect

- Stáhněte si demo verzi ze stránek výrobce, soubor spusťte a aplikaci vybalte.
- V závislosti na bitové verzi OS otevřete složku **32-bit** / **64-bit**.
- Klikněte pravým tlačítkem na INF soubor a zvolte **Install**.
- Vraťte se do rootu aplikace a otevřete **MemProtect.ini**.
- Otevře se konfigurační soubor, kde definujete pravidla. V základu tam naleznete pravidlo, že Notepad nemá právo k modifikaci žádného souboru kromě TXT na Plochách uživatelů. RTFM, je v rootu aplikace.
- Po dokončení úprav konfiguračního souboru jej přesuňte do lokace **C:\Windows**.
- Následně ovladač aktivujte pomocí *net start MemProtect*.

> Příklady MemProtect

- Zablokování přístupu všem nesystémovým procesům k procesům VoodooShield &ndash; jednoduché ztížení exploitace:
<li style="list-style-type: none"><pre><code>[LETHAL]
[LOGGING]
[DEFAULTALLOW]
[WHITELIST]
!C:\Program Files\VoodooShield\*>C:\Program Files\VoodooShield\*
!C:\Windows\explorer.exe>C:\Program Files\VoodooShield\*
!C:\Windows\System32\*>C:\Program Files\VoodooShield\*
!C:\Windows\SystemApps\*>C:\Program Files\VoodooShield\*
!C:\Program Files\Windows Defender\*>C:\Program Files\VoodooShield\*
[BLACKLIST]
*>C:\Program Files\VoodooShield\*
[EOF]
</code></pre></li>
- ...

<br><br><hr><br>

## Integritní politika:
Pomocí úrovní integrity a integritní politiky &ndash; součástí bezpečnostního modelu OS &ndash; je možné snížit pravomoce rizikovým aplikacím. Například můžeme zabránit aplikaci Mozilla Firefox v zápisu do osobních složek (Dokumenty, Obrázky apod.). Pouze za použití vestavěných funkcí OS. To se může velmi hodit, když se exploit nějakým zázrakem dostane přes zabezpečení prohlížeče, anti-exploit mitigace, anti-executable a další vrstvy. Nebo také, když omylem škodlivý kód spustíte. Jelikož bude mít omezená práva, nenapáchá výraznou škodu (pokud je dobře naprogramovaný, tak pozná, že nemá dostatečná práva a o nic se ani nepokusí).

> Trocha teorie o bezpečnostním modelu OS Windows

- Windows obsahuje mechanismus jménem **Kontrola přístupu**, který by se dal označit za základ bezpečnostního modelu Windows.
- Vždy, když libovolná aplikace žádá o přístup k nějakému objektu apod., musí projít Kontrolou přístupu. Bezpečnostní systém Windows získá tzv. **token** aplikace, což je zjednodušeně řečeno souhrn důkazů, proč má, potažmo nemá aplikace právo na vykonání dané akce.
- Na druhé straně (u požadovaného objektu) leží tzv. **deskriptor zabezpečení**, který říká, kdo k objektu má/nemá přístup a pravomoci k jeho manipulaci.
- Tokeny a deskriptory zabezpečení obsahují mnoho věcí, pro nás jsou ale důležité dvě položky: <span class='green'>úroveň integrity</span> a <span class='green'>integritní politika</span>.

**Úroveň integrity** je číslo udávající důvěryhodnost aplikace/objektu. Existují následující úrovně integrity:

- AppContainer &ndash; ve W8 a výše
- nedůvěryhodná
- <span style='color: #BF0000'>nízká</span>
- <span style='color: #FF8000'>střední</span>
- <span style='color: #008000'>vysoká</span>
- System

Pokud je úroveň integrity tokenu menší než úroveň integrity deskriptoru, dochází k aplikaci právě <span class='green'>integritní politiky</span>. Zde začíná pro nás zábava a pro útočníka noční můra.

**Integritní politika** určuje pravomoce aplikací s nižší úrovní integrity k operaci s objekty s vyšší úrovní integrity. To znamená, že může např. malware s nízkou úrovní integrity zamezit práva zápisu do složky střední/vysoké integrity. Pro nás jsou nejzajímavější následující pravidla integritní politiky:

- NO_READ_UP &ndash; omezuje práva ke čtení
- NO_WRITE_UP &ndash; omezuje práva k zápisu
- NO_EXECUTE_UP &ndash; omezuje práva ke spouštění

Pravidla určovaná integritní politikou jsou naprosto neoblomná &ndash; aplikaci je natvrdo zamezen přístup a jediné, co s tím může dělat, je úroveň integrity si navýšit. Což samozřejmě jen tak nemůže, může se o to pokusit a vyhodit UAC dialog, ale ten uživatel samozřejmě nechce odsouhlasit. Navíc malware obvykle chce zůstat utajen, dokud nedokončí svoji práci => UAC dialog by ho tak nějak prozradil...

#### ![idea](https://mople71.cz/img/sm/idea.gif) Vzorový příklad 1:
- Aplikaci **Mozilla Firefox** a osobní složky ponecháme na výchozí (=<span class='tip'>střední</span>) úrovni integrity.
- Přes aplikaci si stáhneme do **Stažených souborů** nějaký pěkný ransomware.</li>
- Ransomware získává (dědí) <span class='tip'>střední</span> úroveň integrity => má právo na neomezenou operaci s objekty střední úrovně integrity.
- Ransomware spustíme.
- Ransomware vesele šifruje veškerý obsah složek střední a nízké integrity &ndash; osobní složky (Dokumenty, Obrázky apod.).

- Ransomware chce zašifrovat i systémové složky.
- Systémové složky mají <span style="color: #008000">vysokou</span> úroveň integrity s nastavenou integritní politikou <span class="dblue">NO_WRITE_UP</span>, která říká, že subjekty s nižší úrovní integrity nemají právo zápisu.
- Ransomware smutně naráží do neviditelné zdi a nemůže dál.

<span class="red">Uživatelská data</span> <span style="color: #BF0000">jsou zašifrována</span>, <span style="color: #008000">OS je v bezpečí</span>.

#### ![idea](https://mople71.cz/img/sm/idea.gif) Vzorový příklad 2:
- Aplikaci **Mozilla Firefox** a osobní složky nastavíme na nízkou úroveň integrity.
- Přes aplikaci si stáhneme do **Stažených souborů** nějaký pěkný ransomware.
- Ransomware získává (dědí) <span style="color: #BF0000">nízkou</span> úroveň integrity => má právo na neomezenou operaci s objekty nízkou úrovně integrity.
- Ransomware spustíme.
- Ransomware vesele šifruje veškerý obsah složek nízké integrity &ndash; Stažené soubory, dočasné složky apod.

- Ransomware chce zašifrovat i osobní data a systémové složky.
- Osobní data mají <span class='tip'>střední</span> úroveň integrity s nastavenou integritní politikou <span class="dblue">NO_WRITE_UP</span>, která říká, že subjekty s nižší úrovní integrity nemají právo zápisu.
- Systémové složky mají <span style="color: #008000">vysokou</span> úroveň integrity s nastavenou integritní politikou <span class="dblue">NO_WRITE_UP</span>, která říká, že subjekty s nižší úrovní integrity nemají právo zápisu.
- Ransomware smutně naráží do neviditelné zdi a nemůže dál.

<span class="green">Uživatelská data</span> <span style="color: #008000">i OS jsou v bezpečí</span>.

Většina lépe naprogramovaných malware/ransomware pozná, že běží s nízkou integritou a hrdě spáchají seppuku. Obvykle ověřuje přístupová práva do registrových klíčů, které jsou pro subjekty s <span style="color: #BF0000">nízkou</span> integritou a nižší značně omezené. Exploitace UAC (samo-povýšení) je v jistých případech teoreticky možná a proveditelná se střední úrovní integrity, proces s nízkou úrovní integrity se může jít klouzat...

![arrow](https://mople71.cz/img/sm/arrow.gif) Integritní politika dokáže při správném nastavení a modelu spolehlivě uchovat vaše soubory v bezpečí. Samozřejmě je teoreticky možné exploitovat chybu ve Windows a s její pomocí sám sobě navýšit úroveň integrity, ale praktická šance, že by takový exploit byl v běžném ransomware, je <span class="red">nulová</span>.

Rozdíly v pravomocech procesů <span class='tip'>střední</span> a <span style="color: #BF0000">nízké</span> integrity jsou velké, spouštění prohlížeče jako proces s <span style="color: #BF0000">nízkou</span> integritou tedy má mnoho dalších bezpečnostních benefitů.

<br>

Pokud jste si přečetli teorii, snad již chápete, že nastavení např. internetového prohlížeče (Mozilla Firefox) jako procesu s <span style="color: #BF0000">nízkou</span> integritou a zároveň nastavení integritní politiky pro vybrané složky je velkým bezpečnostním přínosem, jelikož když vše ostatní selže, bezpečnostní model OS se prolamuje velmi nesnadno.

Má to ovšem jednu zásadní komfortní nevýhodu. Vždy, když spustíte aplikaci s nízkou úrovní integrity, zobrazí se bezpečnostní varování, zdali aplikaci chcete opravdu spustit. To platí i pro prohlížeč. (neplatí pro <span class="green">Windows 10</span>) Výměnou za tuto drobnější otravnost ovšem dosáhnete řádově vyššího zabezpečení, jelikož na rozdíl od ostatních bezpečnostních vrstev, integritní politiku malware nemůže exploitovat a obejít. U veškerého SW třetí strany je toto riziko vyšší.

### Návody:

> Nastavení integritní politiky osobních složek

Windows má vestavěný nástroj jménem <span class="green">icacls</span>, který umožňuje měnit úrovně integrity, neumožňuje ovšem pokročilé nastavení integritní politiky. Z tohoto důvodu musíme použít nástroj třetí strany, který je dle mého názoru v mnoha ohledech lepší než vestavěný.

- Stáhněte si [chml](https://mople71.cz/mirror/chml.exe) (by *[Mark Minasi](http://minasi.com/)*) a uložte jej <span class="blue">na Plochu</span>.
- Zkontrolujte checksums aplikace (návod případně naleznete v sekci **Užitečné aplikace** FAQ Windows pro méně pokročilé):
<li style="list-style-type: none"><pre><code>SHA-256: 59aa55d2eac6b295d42ef2aadc607b759f034f4557a66dec0214a4cc032ecc17
SHA-512: a22317552f90e896fb6f0e4a30f7834baf97a771211a37aca12f52d55ff8b85212d4ded5138ab66a70eaaa1193002b98158938bc17185ea94ccc9f7f4b8120f4</code></pre></li>
- Aplikaci přesuňte do umístění: <span class="blue">C:\Windows\System32</span>
    - Klikněte na aplikaci a stiskněte <span class="green">Ctrl + C</span>
    - Stiskněte kláv. zkratku  ![win](https://mople71.cz/img/wkey.png) <span class="ks">+ R</span>, do textového pole zadejte:
    <li style="list-style-type: none"><pre><code>C:\Windows\System32</code></pre>
a stiskněte **Enter**.</li>
    - Otevře se složka System32. Stiskněte <span class="green">Ctrl + V</span> a a potvrďte přesun do složky.
    - Smažte *chml* z původní lokace.

- Stiskněte kláv. zkratku <img src="https://mople71.cz/img/wkey.png" alt="win"> <span class="ks">+ X</span> a z nabídky vyberte <span class="green">Windows PowerShell (správce)</span>.
<li style="list-style-type: none">![wx](https://mople71.cz/img/cs/wx.png)</li>

- Do příkazové řádky zadejte následující příkaz pro validaci úspěšné instalace aplikace:
<li style="list-style-type: none"><pre><code>chml /?</code></pre></li>
- Pokud chml zareagoval svým výstupem, je správně nainstalován.
- Nyní můžeme nastavit integritní politiku osobních složek, jejichž obsah chceme chránit před malware. Přesná lokace složek závisí na každém OS, cestu ke složkám tedy prosím zkontrolujte a upravte pro váš OS. Např.:
<li style="list-style-type: none"><pre><code>chml C:\Users\(uživ. jméno)\Documents -i:m -nw -nx
chml C:\Users\(uživ. jméno)\Pictures -i:m -nw -nx
chml C:\Users\(uživ. jméno)\Music -i:m -nw -nx
chml C:\Users\(uživ. jméno)\Videos -i:m -nw -nx

/* -i:l (nízká úroveň integrity)
-i:m (střední úroveň integrity)
-i:h (vysoká úroveň integrity)
-nw (NO_WRITE_UP)
-nx (NO_EXECUTE_UP)
-nr (NO_READ_UP) */</code></pre></li>
- Stejným způsobem můžete nastavit integritu pro libovolnou privátní složku na disku. Není potřeba nastavovat integritu pro složky nacházející se ve složkách, jejichž úroveň integrity a integritní politika byla již změněna (např. po změně integrity složky Dokumenty není třeba měnit integritu složky Škola nacházející se v Dokumentech). Integritní úroveň a politika se "dědí".

![arrow](https://mople71.cz/img/sm/arrow.gif) <span class='green'>Nyní máte nastavenou integritní politiku pro vaše privátní složky.</span>

> Tipy

- Můžete nastavit nižší integritu i dalším aplikacím, které nepotřebují zapisovat do osobních složek (např. PDF prohlížeč, VLC etc.).
- Také můžete osobním složkám nastavit vysokou integritu a soubory, které budete chtít upravit, dočasně překopírovat jinam a následně zpět.
- ...

<br><br><hr><br>

## ACL:
<span class="green">Access Control List</span> je další součást bezpečnostního modelu OS, s jejíž pomocí můžeme zakázat např. spuštění aplikací v určité složce.

> Další trocha teorie (méně než minule)

<span class="green">ACL</span> je seznam záznamů (jednotlivý záznam je nazýván **ACE**) určujících, který subjekt má jaké pravomoce pro manipulaci se zabezpečeným objektem (konkrétně se budeme bavit pouze o DACL). Při přihlášení je uživateli přiřazen přístupový **token**, který následně přebírají všechny aplikace spuštěné daným uživatelem. Pokud proces chce operovat se zabezpečeným objektem, kontrola přístupu se podívá na jeho token a na deskriptor zabezpečení u objektu.

Token obsahuje mnoho věcí, pro nás je ale aktuálně důležitá jedna položka: <span class="green">SID</span>.

**SID** je unikátní hodnota určená k identifikaci vlastníka &ndash; uživatelského účtu nebo uživatelské skupiny. Např.: *S-1-5-32-544*.

Kontrola přístupu z tokenu aplikace získá jeho SID a následně v ACL seznamu vyhledá veškeré záznamy (ACE), ve kterých je daný SID. Následně všechny naleznené ACE sekvenčně prozkoumá, dokud nenalezne ACE, který přístup k objektu explicitně zakáže/povolí. ACE zakazující přístup jsou zkoumány přednostně.

<br>

Pokud jste si přečetli teorii, snad máte alespoň matnou představu o tom, jak ACL a kontrola přístupu funguje. Nyní se podívejme na praktické využití.

![idea](https://mople71.cz/img/sm/idea.gif) Předpoklad pro mnou uvedený příklad využití je separátní administrátorský účet, který beru jako samozřejmost.

ACL můžeme využít následovně: můžeme zakázat spouštění spustitelných souborů v uživatelských složkách. Běžný uživatel nepotřebuje spouštět ve svých složkách spustitelné soubory &ndash; a pokud ano, nic mu nebrání v přesunutí souboru mimo jeho osobní složky. Výhody jsou doufám jasné &ndash; pokud se malware dostane na disk, nespustí se.

### Návody:

> Odebrání pravomoce exekuce souborů v uživatelských složkách

- Stiskněte kláv. zkratku <img src="https://mople71.cz/img/wkey.png" alt="win"> <span class="ks">+ X</span> a z nabídky vyberte <span class="green">Windows PowerShell (správce)</span>.</li>
<li style="list-style-type: none">![wx](https://mople71.cz/img/cs/wx.png)</li>
- Do příkazové řádky zadejte následující příkazy (cestu ke složce uživatele patřičně upravte):</li>
<li style="list-style-type: none"><pre><code>icacls "C:\Users\(uživ. jméno)" /c /inheritance:d
icacls "C:\Users\(uživ. jméno)" /c /deny Everyone:(OI)(CI)(X)</code></pre></li>

> Opětovné přidání pravomoce exekuce souborů v uživatelské složce

- Stiskněte kláv. zkratku <img src="https://mople71.cz/img/wkey.png" alt="win"> <span class="ks">+ X</span> a z nabídky vyberte <span class="green">Windows PowerShell (správce)</span>.</li>
<li style="list-style-type: none">![wx](https://mople71.cz/img/cs/wx.png)</li>
- Do příkazové řádky zadejte následující příkaz (cestu ke složce patřičně upravte):</li>
<li style="list-style-type: none"><pre><code>icacls "C:\Users\User\AppData\Local\Temp" /remove Everyone /t</code></pre></li>

![idea](https://mople71.cz/img/sm/idea.gif) V příkladu byla použita složka **Temp**, jejíž pravomoc exekuce obsahujících souborů může být vyžadována některými aplikacemi (včetně systémových &ndash; MS Edge). Každopádně z bezpečnostního hlediska není úplně ideální exekuci ve složce povolit.

<br><br><hr><br>

## AppContainer:
AppContainer je implementace sandboxu integrovaná v OS od Windows 8. Je vyvinut pro ModernUI aplikace a např. MS Edge na něm má postavený svůj bezpečnostní model (používá několik AppContainerů zároveň). Existují také možnosti, jak upravit Win32 aplikaci, aby běžela v AppContainer, viz. [zde](https://www.howtogeek.com/250041/how-to-convert-a-windows-desktop-app-to-a-universal-windows-app/) nebo [zde](https://news.saferbytes.it/analisi/2013/07/securing-microsoft-windows-8-appcontainers/).

AppContainer odděluje aplikace od sebe a částí OS. Podobnou snahu můžeme pozorovat i u Linuxu (Flatpak). Více o izolaci si můžete přečíst [zde](https://msdn.microsoft.com/en-us/library/windows/desktop/mt595898(v=vs.85).aspx).

<br><br><hr>

<h3 class="nocol">To je vše. Stay safe! ![smile](https://mople71.cz/img/sm/smile.gif)</h3>
