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
### Firewall:
Windows obsahují vestavěný <span class="green">Windows Defender Firewall</span> (WDF), který je na velmi dobré úrovni.

Použití FW třetí strany je zbytečné rozšiřování attack surface. Základem síťového zabezpečení v domácnosti je rozumný router s použitelným FW (např. Mikrotik, kde si FW ovšem samozřejmě musíte nastavit).

Co se týče blokování odchozí komunikace, *Windows Defender Firewall* tuto funkci podporuje a umožňuje vcelku jednoduše nastavit.

![idea](https://mople71.cz/img/sm/idea.gif) Návod měl původně být v sekci pro méně pokročilé, ovšem z důvodu nepříjemného bugu (nebo funkce) Windows 10, automatické aktualizace OS nelze ve whitelistu rozumně definovat.

> Konfigurace WDF pro blokování odchozí komunikace

- Otevřete si **hledání Windows**, do vyhledávacího pole zadejte:
<li style="list-style-type: none"><pre><code>wf.msc</code></pre></li>
- Na nalezenou položku klikněte pravým tlačítkem a zvolte možnost: ![admin](https://mople71.cz/img/admin.png) **Spustit jako správce**.
<li style="list-style-type: none">![wdf](https://faq.mople71.cz/img/cs/wdf.png)</li>
- Otevře se pokročilé nastavení Windows Firewall. V prostředním sloupci zvolte možnost <span class="green">Vlastnosti brány Firewall v programu Windows Defender</span>.
- V horním panelu si otevřete záložku **Privátní profil**. U položky **Odchozí připojení** zvolte možnost <span class="green">Blokovat</span>.
<li style="list-style-type: none">![wdf1](https://faq.mople71.cz/img/cs/wdf1.png)</li>
- Postup zopakujte pro záložku **Veřejný profil**.
- Klikněte na <span class="green">OK</span>.
<li style="list-style-type: none">![wdf2](https://faq.mople71.cz/img/cs/wdf2.png)</li>

![arrow](https://mople71.cz/img/sm/arrow.gif) <span class="green">Nyní WDF blokuje veškerou odchozí kouminakci, která není na whitelistu. Dále je třeba nastavit whitelist.</span>

> Povolení odchozí komunikace pro všechny moderní aplikace

- V levém sloupci otevřete <span class="green">Odchozí pravidla</span>.
- V pravém sloupci zvolte možnost <span class="green">Nové pravidlo...</span>
- Jako typ pravidla zvolte **Program** a klikněte na tlačítko <span class="green">Další</span>.
- Zvolte možnost **Všechny programy** a klikněte na tlačítko <span class="green">Další</span>.
- Zvolte možnost **Povolit připojení** a klikněte na tlačítko <span class="green">Další</span>.
- Zkontrolujte zatržítka u všech položek a klikněte na tlačítko <span class="green">Další</span>.
- Zadejte název pravidla &ndash; v tomto případě např. **All MoUI Apps**
- Klikněte na <span class="green">Dokončit</span>.
- Nové pravidlo otevřete. Přesuňte se do záložky **Programy a služby** a v sekci **Balíčky aplikací** klikněte na <span class="green">Nastavení...</span>
<li style="list-style-type: none">![wdf3](https://faq.mople71.cz/img/cs/wdf3.png)</li>
- Zvolte možnost <span class="green">Použít pouze pro balíčky aplikací</span> a potvrďte. Následně uložte změny v pravidle.
<li style="list-style-type: none">![wdf4](https://faq.mople71.cz/img/cs/wdf4.png)</li>

> Povolení odchozí komunikace pro všechny služby Windows

- V pravém sloupci zvolte možnost <span class="green">Nové pravidlo...</span>
- Jako typ pravidla zvolte **Program** a klikněte na tlačítko <span class="green">Další</span>.
- Zvolte možnost **Všechny programy** a klikněte na tlačítko <span class="green">Další</span>.
- Zvolte možnost **Povolit připojení** a klikněte na tlačítko <span class="green">Další</span>.
- Zkontrolujte zatržítka u všech položek a klikněte na tlačítko <span class="green">Další</span>.
- Zadejte název pravidla &ndash; v tomto případě např. **All Services**
- Klikněte na <span class="green">Dokončit</span>.
- Nové pravidlo otevřete. Přesuňte se do záložky **Programy a služby** a v sekci **Služby** klikněte na <span class="green">Nastavení...</span>
- Zvolte možnost <span class="green">Použít pouze pro balíčky aplikací</span> a potvrďte. Následně uložte změny v pravidle.
<li style="list-style-type: none">![wdf5](https://faq.mople71.cz/img/cs/wdf5.png)</li>

> Povolení odchozí komunikace pro důležité aplikace

- V pravém sloupci zvolte možnost <span class="green">Nové pravidlo...</span>
- Jako typ pravidla zvolte **Program** a klikněte na tlačítko <span class="green">Další</span>.
- Zvolte možnost **Cesta k tomuto programu** a do textového pole vložte cestu k následujícímu souboru:
<li style="list-style-type: none"><pre><code>%SystemRoot%\System32\smartscreen.exe</code></pre></li>
<li style="list-style-type: none">![wdf6](https://faq.mople71.cz/img/cs/wdf6.png)</li>
- Klikněte na tlačítko <span class="green">Další</span>.
- Zvolte možnost **Povolit připojení** a klikněte na tlačítko <span class="green">Další</span>.
- Zkontrolujte zatržítka u všech položek a klikněte na tlačítko <span class="green">Další</span>.
- Zadejte název pravidla &ndash; v tomto případě např. **SmartScreen**
- Klikněte na <span class="green">Dokončit</span>.
- Stejný postup aplikujte pro následující aplikace:
<li style="list-style-type: none"><pre><code>%SystemRoot%\ImmersiveControlPanel\SystemSettings.exe
%programfiles%\Windows Defender\MsMpEng.exe
%programfiles%\Windows Defender\MpUXSrv.exe
%programfiles%\Windows Defender\MpCmdRun.exe
%programfiles%\Windows Defender\wdnsfltr.exe</code></pre></li>

> Windows Update na Windows 10

Od verze **Windows 10 Creators Update** není možné rozumně povolit Windows Update &ndash; nestačí povolit pouze nezbytné služby, je nutné povolit celý *svchost.exe*.

Je zde několik možností:

- <span class="s">Permanentně povolit SVCHost.exe pro porty 80 a 443</span>. (<span class="red">nedoporučeno</span>)
- Povolit SVCHost.exe pouze po dobu instalace aktualizací.
- Instalovat aktualizace 1x měsíčně ručně a WU neřešit.
- ...

![arrow](https://mople71.cz/img/sm/arrow.gif) Problémem ovšem je, že přes WU se aktualizují definice <span class="green">Windows Defender</span>, které je důležité mít aktuální.

Jako nejrozumější varianta se tedy jeví následující:

Vytvořit pravidlo pro povolení celého *SVCHost.exe* ve WDF, pojmenovat jej **SVCHost** a pravidlo zakázat (pravým tlačítkem). Následně pro aktualizaci definicí WD napsat jednoduchý skript a naplánovat v *Plánovači úloh* jeho spuštění 1x za 6 hodin.
<pre><code>@echo off
netsh advfirewall firewall set rule name="SVCHost" new enable=yes
"%programfiles%\Windows Defender\MpCmdRun.exe" -SignatureUpdate
netsh advfirewall firewall set rule name="SVCHost" new enable=no
pause</code></pre>

Windows Update následně můžete řešit libovolným způsobem.

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

## ACL:
<span class="green">Access Control List</span> je součást bezpečnostního modelu OS, s jejíž pomocí můžeme zakázat např. spuštění aplikací v určité složce.

> Nutná teorie k ACL

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

## Integritní politika:
Pomocí integritní politiky &ndash; součásti bezpečnostního modelu OS &ndash; je možné omezit přístup aplikacím s nízkou úrovní integrity do osobních složek.

> Nutná teorie k úrovním integrity a integritní politice

- Windows obsahuje mechanismus jménem **Kontrola přístupu**, který by se dal označit za základ bezpečnostního modelu Windows.
- Vždy, když libovolná aplikace žádá o přístup k nějakému objektu apod., musí projít Kontrolou přístupu. Bezpečnostní systém Windows získá tzv. **token** aplikace, což je zjednodušeně řečeno souhrn důkazů, proč má, potažmo nemá aplikace právo na vykonání dané akce.
- Na druhé straně (u požadovaného objektu) leží tzv. **deskriptor zabezpečení**, který říká, kdo k objektu má/nemá přístup a pravomoci k jeho manipulaci.
- Tokeny a deskriptory zabezpečení obsahují mnoho věcí, pro nás jsou ale důležité dvě položky: <span class='green'>úroveň integrity</span> a <span class='green'>integritní politika</span>.

**Úroveň integrity** je číslo udávající důvěryhodnost aplikace/objektu. Existují následující úrovně integrity:

- AppContainer
- nedůvěryhodná
- <span style='color: #BF0000'>nízká</span>
- <span style='color: #FF8000'>střední</span>
- <span style='color: #008000'>vysoká</span>
- Systémová

Pokud je úroveň integrity tokenu menší než úroveň integrity deskriptoru, dochází k aplikaci právě <span class='green'>integritní politiky</span>. Zde začíná pro nás zábava a pro hackera noční můra.

**Integritní politika** určuje pravomoce procesů s nižší úrovní integrity k operaci s objekty s vyšší úrovní integrity. To znamená, že může např. malware s nízkou úrovní integrity zamezit práva zápisu do složky střední/vysoké integrity. Pro nás jsou nejzajímavější následující pravidla integritní politiky:

- NO_READ_UP &ndash; omezuje práva ke čtení
- NO_WRITE_UP &ndash; omezuje práva k zápisu
- NO_EXECUTE_UP &ndash; omezuje práva ke spouštění

Pravidla určovaná integritní politikou jsou absolutní &ndash; aplikaci je natvrdo zamezen přístup a jediné, co s tím může dělat, je úroveň integrity navýšit. Což může pouze skrz UAC dialog, rozhodnutí je následně samozřejmě na uživateli. Malware ovšem obvykle chce zůstat utajen, dokud nedokončí svoji práci &ndash; UAC dialog by ho tak nějak prozradil.

Většina lépe naprogramovaného malware pozná, že běží s nízkou integritou a hrdě spáchá *seppuku*. Exploitace UAC (samo-povýšení) je v jistých případech teoreticky možná a proveditelná se střední úrovní integrity &ndash; proces s nízkou úrovní integrity nemůže nic, maximálně se pokusit o exploitaci kernelu.

<br>

Níže naleznete návod na konfiguraci integritní politiky pro osobní složky &ndash; *střední integrita*, **NO_WRITE_UP**, **NO_EXECUTE_UP**. Možností je ovšem více. Můžete například osobním složkám (kromě *Stažených soborů*) nastavit místo střední integrity **vysokou** integritu a tím zamezit většině uživatelských aplikací manipulaci s daty. V takovém případě soubory, které budete chtít v uživatelské aplikaci upravit, budete muset dočasně překopírovat jinam a následně zpět.

Kromě složek můžete přenastavit nižší úroveň integrity i aplikacím. Mělo by se jednat o aplikace, které nepotřebují zapisovat do osobních složek &ndash; PDF prohlížeč, VLC etc. Nejedná se ovšem o komfortní a jednoduchou konfiguraci. Pro nastavení přístupu aplikací k disku je doporučeno použít <span class="green">FIDES</span>.

<br>

> Instalace CHML

Windows má vestavěný nástroj jménem <span class="green">icacls</span>, který umožňuje měnit úrovně integrity, neumožňuje ovšem pokročilé nastavení integritní politiky. Z tohoto důvodu je nutné použít drobný nástroj třetí strany.

- Stáhněte si [chml](https://mople71.cz/mirror/chml.exe) (by *[Mark Minasi](https://www.minasi.com/)*) a uložte jej <span class="blue">na Plochu</span>.
- Zkontrolujte *checksums* aplikace:
<li style="list-style-type: none"><pre><code>SHA-256: 59aa55d2eac6b295d42ef2aadc607b759f034f4557a66dec0214a4cc032ecc17
SHA-512: a22317552f90e896fb6f0e4a30f7834baf97a771211a37aca12f52d55ff8b85212d4ded5138ab66a70eaaa1193002b98158938bc17185ea94ccc9f7f4b8120f4</code></pre></li>
- Aplikaci zkopírujte do umístění: <span class="blue">C:\Windows\System32</span>
- Smažte *chml* z původní lokace.
- Stiskněte kláv. zkratku <img src="https://mople71.cz/img/wkey.png" alt="win"> <span class="ks">+ X</span> a z nabídky vyberte <span class="green">Windows PowerShell (správce)</span>.
<li style="list-style-type: none">![wx](https://mople71.cz/img/cs/wx.png)</li>
- Do příkazové řádky zadejte následující příkaz pro validaci úspěšné instalace aplikace:
<li style="list-style-type: none"><pre><code>chml /?</code></pre></li>
- Pokud chml zareagoval svým výstupem, je správně nainstalován.

> Nastavení integritní politiky osobních složek

- Nyní můžeme nastavit integritní politiku osobních složek, jejichž obsah chceme chránit před malware. Cestu ke složkám tedy upravte pro váš OS.:
<li style="list-style-type: none"><pre><code>chml C:\Users\[uživatel]\Documents -i:m -nw -nx
chml C:\Users\[uživatel]\Pictures -i:m -nw -nx
chml C:\Users\[uživatel]\Music -i:m -nw -nx
chml C:\Users\[uživatel]\Videos -i:m -nw -nx

/* -i:l (nízká úroveň integrity)
-i:m (střední úroveň integrity)
-i:h (vysoká úroveň integrity)
-nw (NO_WRITE_UP)
-nx (NO_EXECUTE_UP)
-nr (NO_READ_UP) */</code></pre></li>
- Stejným způsobem můžete nastavit integritu pro libovolnou privátní složku na disku. Úroveň integrity a integritní politika se *dědí*, není tedy potřeba nastavovat integritu pro složky nacházející se v již nakonfigurovaných složkách.

![arrow](https://mople71.cz/img/sm/arrow.gif) <span class='green'>Nyní máte nastavenou integritní politiku pro vaše privátní složky.</span>

<br><br><hr><br>

## AppContainer:
AppContainer je implementace sandboxu integrovaná v OS od Windows 8. Je vyvinut pro ModernUI aplikace a např. MS Edge na něm má postavený svůj bezpečnostní model (používá několik AppContainerů zároveň). Existují také možnosti, jak upravit Win32 aplikaci, aby běžela v AppContainer, viz. [zde](https://www.howtogeek.com/250041/how-to-convert-a-windows-desktop-app-to-a-universal-windows-app/) nebo [zde](https://news.saferbytes.it/analisi/2013/07/securing-microsoft-windows-8-appcontainers/).

AppContainer odděluje aplikace od sebe a částí OS. Podobnou snahu můžeme pozorovat i u Linuxu (Flatpak). Více o izolaci si můžete přečíst [zde](https://msdn.microsoft.com/en-us/library/windows/desktop/mt595898(v=vs.85).aspx).

<br><br><hr>

<h3 class="nocol">To je vše. Stay safe! ![smile](https://mople71.cz/img/sm/smile.gif)</h3>
