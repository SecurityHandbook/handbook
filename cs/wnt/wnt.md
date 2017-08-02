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

![us](https://faq.mople71.cz/img/cs/us.png)
- Otevře se dialog pro přidání nového uživatele. V levém dolním rohu klikněte na <span class="green">Nemám přihlašovací údaje této osoby</span>.
- V levém dolním rohu zvlote možnost <span class="green">Přidat uživatele bez účtu Microsoft</span>.
- Zadejte název účtu Správce (např. **Admin**) a zvolte pro něj silné zapamatovatelné heslo.
- V seznamu jiných uživatelů se zobrazí účet **Admin**. Klikněte na něj a následně zvolte <span class="green">Změnit typ účtu</span>.

![us1](https://faq.mople71.cz/img/cs/us1.png)
- Zobrazí se dialog pro změnu typu účtu. Ze seznamu zvolte možnost <span class="green">Správce</span> a klikněte na <span class="green">OK</span>.

![us2](https://faq.mople71.cz/img/cs/us2.png)
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

Pro kontrolu aktualizací ostatního SW můžete použít aplikaci <a href="http://www.flexerasoftware.com/enterprise/products/software-vulnerability-management/personal-software-inspector/" target="_blank">Personal Software Inspector</a>, která běží na pozadí a upozorní vás v případě neaktuálního SW. *Nedoporučuji používat pododné aplikace, který neaktuální SW aktualizují za vás, jelikož tyto aplikace mohou způsobit problémy.*

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

![batch](https://mople71.cz/img/bat.png) **SaferSRV**:
- Stáhněte si <a href="https://mople71.cz/safersrv.zip" download='SaferSRV'>SaferSRV</a>.
- Uložte a obsah archivu vyextrahujte <span class="blue">na Plochu</span>.
- Na skript jménem <span class="green">safersrv</span> klikněte pravým tlačítkem a zvolte možnost: ![admin](https://mople71.cz/img/admin.png) **Spustit jako správce**.
- Nechte skript pracovat, na konci procesu vám řekne o souhlas k restartu OS.

<br>

#### Bezpečné nastavení sítě:
> Konfigurace síťového adaptéru + DNS

- Stiskněte kláv. zkratku ![win](https://mople71.cz/img/wkey.png) <span class="ks">+ R</span>, do textového pole zadejte:
<li style="list-style-type: none"><pre><code>ncpa.cpl</code></pre>
a stiskněte **Enter**.</li>
- Otevře se seznam síťových adaptérů. Klikněte na první adaptér (obvykle ethernet) pravým tlačítkem a zvolte možnost <span class="green">Vlastnosti</span>.
<li style="list-style-type: none">![vlastnosti](https://faq.mople71.cz/img/cs/net.png)</li>
- V seznamu odškrtněte všechny nepotřebné položky. Běžným uživatelům stačí ponechat pouze <span class="green">Sdílení souborů a tiskáren v sítích Microsoft</span>, <span class="green">Protokol IP verze 4 (TCP/IPv4)</span> a <span class="green">Protokol IP verze 6 (TCP/IPv6)</span>.
- Pokud nesdílíte žádnou tiskárnu v síti a nepoužíváte IPv6 (pokud nevíte, zdali používáte IPv6, můžete to zjistil pomocí následujícího rychlého <a href="http://www.test-ipv6.cz/" target="_blank">online testu</a>), můžete pro vyšší bezpečnost ponechat zaškrtnutý pouze <span class="green">Protokol IP verze 4 (TCP/IPv4)</span>.
<li style="list-style-type: none">![vlastnosti2](https://faq.mople71.cz/img/cs/net1.png)</li>
- Klikněte na **Protokol IP verze 4 (TCP/IPv4)** a zvolte možnost <span class="green">Vlastnosti</span>.
<li style="list-style-type: none">![vlastnosti3](https://faq.mople71.cz/img/cs/net2.png)</li>

![arrow](https://mople71.cz/img/sm/arrow.gif) <span class="green">Nyní nastavíme bezpečné DNS servery.</span>
- Pokud nevíte, co DNS je, přečtěte si tento <a href="https://www.nic.cz/page/312/o-domenach-a-dns/" target="_blank">krátký článek</a>.
- Doporučuji použít DNSSEC. Ale můžete si vybrat z mnoha DNS serverů, zde je pár příkladů:
<li style="list-style-type: none"><pre><code>CZ.NIC DNSSEC:        217.31.204.130, 193.29.206.206
Adguard DNS:          176.103.130.130, 176.103.130.131
OpenDNS:              208.67.222.222, 208.67.220.220</code></pre></li>
- Po zvolení DNS serverů se přepněte zpět do okna Vlastností IPv4 protokolu.
- Klikněte na <span class="green">Použít následující adresy serverů DNS</span> a do kolonek vepište vámi zvolené DNS.
<li style="list-style-type: none">![vlastnosti4](https://faq.mople71.cz/img/cs/net3.png)</li>
- Klikněte na <span class="green">OK</span> a okno zavřete.

![arrow](https://mople71.cz/img/sm/arrow.gif) <span class="green">Stejný postup aplikujte pro všechny síťové adaptéry v seznamu (obvykle WLAN).</span>

<br>

### Ostatní bezpečnostní nastavení

- Vypněte Usnadnění přístupu na přihlašovací obrazovce (pokud nepotřebujete, tak kompletně).
- Vypněte AutoPlay (<a href="http://windows.microsoft.com/cs-cz/windows/change-autoplay-settings#1TC=windows-7" target="_blank">návod</a>).
- Vypněte Remote Assistance
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

> Nastavení Windows Defender

- Otevřete si <span class="green">Centrum zabezpečení v programu Windows Defender</span>.
- Rozklikněte kategorii **Ochrana před viry a hrozbami** a zvolte <span class="green">Nastavení ochrany před viry a hrozbami</span>.
- Zkontrolujte, zdali máte zapnuté volby **Ochrana v reálném čase**, **Cloudová ochrana** a **Automatické odesílání vzorků**, případně napravte.
- Přepněte se do kategorie <span class="green">Řízení aplikací a prohlížečů</span>.
- Upravte nastavení, aby odpovídalo obrázku níže.
<li style="list-style-type: none">![wd](https://faq.mople71.cz/img/cs/wd.png)</li>

<br>

Pro nižší verze Windows lze instalaci antiviru třetí strany pochopit, jelikož OS nemá integrované antimalware řešení.

> Doporučené antiviry pro Windows 8 a níže

#### Bezplatná řešení:
- <a href="https://www.sophos.com/en-us/lp/sophos-home.aspx" target="_blank">Sophos Home</a> &ndash; anglické rozhraní, špičková administrace
- <a href="https://www.microsoft.com/cs-cz/download/details.aspx?id=5201" target="_blank">Microsoft Security Essentials</a> &ndash; české rozhraní, substituce Defenderu pro Windows 7 a Windows Vista
- <a href="https://www.bitdefender.com/solutions/free.html" target="_blank">Bitdefender Free</a> &ndash; anglické rozhraní

#### Placená řešení:
- <a href="https://www.emsisoft.com/en/software/antimalware/" target="_blank">Emsisoft Anti-Malware</a> &ndash; anglické rozhraní
- <a href="https://www.f-secure.com/en/web/home_global/safe?icid=1526" target="_blank">F-Secure</a> &ndash; české rozhraní
- <a href="https://www.webroot.com/us/en/home" target="_blank">Webroot</a> &ndash; anglické rozhraní
- <a href="http://www.bitdefender.com/" target="_blank">Bitdefender</a> &ndash; anglické rozhraní, existuje i <a href="http://www.bitdef.cz/" target="_blank">česká verze</a>

<br>

### Firewall:

Firewall je velmi důležitá vrstva zabezpečení, která chrání OS před útoky ze sítě. Windows obsahují vestavěný <span class="green">Windows Firewall</span> (WF), který je na velmi dobré úrovni a plně dostačující (spousta AV/M produktů přestala vyvíjet vlastní FW a maximálně nabízet alternativní rozhraní pro Windows Firewall). *Poznámka na okraj: základem síťového zabezpečení v domácnosti je rozumný router.*

Základní nevýhoda WF pro běžné uživatele je absence jakéhokoli intuitivního rozhraní. Velmi jednoduché rozhraní naleznete v <span class="green">Centru zabezpečení v programu Windows Defender</span>.

<span class="red">Comodo Firewall</span>. Velmi oblíbená alternativa. Ano, je intuitivnější a obsahuje HIPS. Na druhou stranu, osobně důrazně nedoporučuji jakýkoli produkt od firmy **Comodo**.

**Windows Firewall** je v základu nastaven na blokování příchozí komunikace, která není explicitně povolena. Chcete-li posunout bezpečnost na výrazně vyšší úroveň, je dobrý nápad nastavit FW na blokování veškeré odchozí komunikace, která není explicitně povolena. V nejnovější verzi Windows je ovšem takové nastavení problematické, a návod proto naleznete pouze v FAQ pro pokročilé.

<br>

### Anti-exploit:
Každý kód obsahuje minimálně jednu chybu. Toho zneužívají exploity šířící se internetem. Anti-exploit aplikace přicházejí s mitigacemi, které mají za cíl znemožnit využití jednoduchých způsobů exploitace a proces exploitace výrazně ztížit.

Windows využívají velké množství mitigací a exploitace samotného OS a aplikací OS je tedy velmi nákladná. Některé aplikace (např. Chrome) jsou také na velmi vysoké úrovni a jejich exploitace je nákladná. Jsou zde ovšem aplikace, které žádné anti-exploit techniky nepoužívají a někdy je používání těchto aplikací nezbytné. V takovém případě existují anti-exploit řešení, která umí exploitaci zmíněných aplikací výrazně ztížit.

#### Přehled anti-exploit řešení:
- <a href="http://www.surfright.nl/en/alert" target="_blank">HitmanPro.Alert</a> (HMP.A)
- <a href="https://technet.microsoft.com/en-us/security/jj653751" target="_blank">Microsoft Enhanced Mitigation Experience Toolkit</a> (EMET)

<span class="red">EMET</span> je anti-exploit řešení od MS a v nejnovější verzi Windows je **již nepotřebný**, jelikož veškeré jeho funkce (a mnohem více) jsou nyní integrovány přímo do OS. Návod na podrobnější nastavení těchto funkcí naleznete v FAQ pro pokročilé.

> Instalace a konfigurace EMET (starší verze Windows)

- Stáhněte si nejnovější verzi <a href="https://technet.microsoft.com/en-us/security/jj653751" target="_blank">EMET</a>.
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

<span class="red">HitmanPro.Alert</span> je placená aplikace, která nabízí komplexní zabezpečení včetně mitigací proti exploitům. Je to velmi solidní SW a investice do něj není nesmyslná.

> Instalace a konfigurace HMP.A

- Stáhněte si <a href="http://www.surfright.nl/en/alert" target="_blank">HMP.A</a>.
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

![idea](https://mople71.cz/img/sm/idea.gif) Více se dozívte v <a href="http://dl.surfright.nl/HitmanPro%20Alert%20Getting%20Started.pdf">manuálu</a>.

<br>

### Anti-executable:
Anti-executable je jedna z nejúčinnějších vrstev ochrany. Jak napovídá název, anti-executable řešení zabraňuje spuštění malware.

Většinou funguje na bázi *whitelistu* &ndash; má nastaveno, které spustitelné soubory povolit, a při spuštění neznámého souboru zobrazí uživateli dialog pro povolení/zakázání, případně souboru rovnou zabraní spustit se. Nastavení whitelistu není úkol pro běžné uživatele, existují ovšem i řešení, která umí whitelist vytvořit prakticky bez uživatelské interakce.

#### Přehled anti-executable řešení:
- <a href="https://voodooshield.com/" target="_blank">VoodooShield</a> (VS)
- <a href="https://www.foolishit.com/cryptoprevent-malware-prevention/" target="_blank">CryptoPrevent</a>
- <a href="http://www.appguardus.com/index.php/appguard/personal/overview1" target="_blank">AppGuard</a> (AG)
- <a href="http://www.novirusthanks.org/products/exe-radar-pro/" target="_blank">NVT ExeRadarPro</a> (NVT ERP)
- <a href="http://www.novirusthanks.org/products/anti-autoexec/" target="_blank">NVT Anti-AutoExec</a>
- <a href="https://technet.microsoft.com/cs-cz/library/dd759117.aspx" target="_blank">AppLocker</a>
- <a href="https://technet.microsoft.com/cs-cz/library/hh831534.aspx" target="_blank">Software Restrtiction Policies</a> (SRP)

<span class="red">VoodooShield</span> je nejpřívětivější anti-executable a nejlepší volba pro obyčejné uživatele. Kromě placené verze poskytuje i bezplatnou pro nekomerční využití, která poskytuje srovnatelnou ochranu, akorát nenabízí možnost rozšířené konfigurace, což běžnému uživateli nevadí. V základu je nakonfigurován bezpečně. Bohužel zatím nenabízí české rozhraní.

> Instalace a konfigurace VoodooShield

- Stáhněte si <a href="https://voodooshield.com/" target="_blank">VoodooShield</a>.
- Aplikaci nainstalujte.
- Jakmile budete dotázáni na volbu módu, zvolte <span class="green">Application Whitelisting Mode</span>.
- Po instalaci klikněte pravým tlačítkem na ikonu aplikace v hlavním panelu a vyberte možnost <span class="green">Hide</span>, čímž skryjete štít z pracovního prostoru.
- Klikněte pravým tlačítkem na ikonu aplikace v hlavním panelu a zvolte mód <span class="green">Training</span>.
<li style="list-style-type: none">![vs](https://faq.mople71.cz/img/en/vs.png)</li>
- Nyní se VoodooShield učí aplikace, které používáte, a povoluje je. V tréninkovém módu postupně spusťte všechny aplikace, které používáte. Ideální je v tréninkovém módu PC používat jeden den, aby VoodooShield vše stihl zapsat.
- Po ukončení tréniku VoodooShield klikněte pravým tlačítkem na ikonu aplikace v hlavním panelu a zvolte mód <span class="green">Always On</span>.
<li style="list-style-type: none">![vs1](https://faq.mople71.cz/img/en/vs1.png)</li>

![arrow](https://mople71.cz/img/sm/arrow.gif) <span class="green">To je vše, nyní máte plně funkční anti-executable ochranu aplikace VoodooShield. Když budete chtít instalovat libovolnou aplikaci, zvolte **Disable/Install Mode**.</span>

![idea](https://mople71.cz/img/sm/idea.gif) Pokud vaše bezpečnostní konfigurace obsahuje aplikaci <span class="red">EMET</span>, můžete v něm nastavit ochranu aplikace VoodooShield. Tím ztížíte exploitaci VoodooShield.
![vs6](https://faq.mople71.cz/img/en/vs6.png)

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

<span class="red">CryptoPrevent</span> je anti-executable řešení, které automaticky dle svých pravidel pomocí SRP zakáže spouštění rizikových souborů v rizikových lokacích. Jedná se o dobré preventivní opatření.

<span class="red">NVT Anti-AutoExec</span> je drobná aplikace, která automaticky zabraňuje šíření USB malware. Stačí nainstalovat a ochrana je aktivní.

<span class="red">AppGuard</span> je profesionální anti-executable určený převážně pro firemní sféru, je ovšem dostupný i v domácí verzi. Jeho nastavení je vcelku komplikované a přizpůsobené pro odborníky.

<span class="red">AppLocker</span> je anti-executable integrovaný ve Windows v edicích Ultimate, Education a Enterprise. Umožňuje ovládání spustitelných souborů, skriptů, DLL knihoven, MSI instalátorů a ModernUI (metro) aplikací. Poskytuje velmi slušnou ochranu.

<span class="red">Software Restriction Policy</span> je velmi funkčně omezený anti-executable dostupný ve všech edicích Windows. Umožňuje ovládání spustitelných souborů a skriptů. Jeho pravidla jsou ovšem vázána na proces *explorer.exe*, který je vlastněn uživatelem, není tedy v porovnání s AppLocker určen pro profesionální použití.

<br>

### Virtualizace:
Virtualizace může být velmi bezpečný způsob ochrany před malware (záleží na způsobu aplikace), jelikož odděluje požadovanou část OS od fyzického OS.

#### Možnosti virtualizace:
- virtuální poočítač &ndash; <a href="https://www.virtualbox.org/" target="_blank">VirtualBox</a>, <a href="https://my.vmware.com/en/web/vmware/free#desktop_end_user_computing/vmware_workstation_player/12_0" target="_blank">VMware Player</a>,...
- lehká virtualizace OS &ndash; <a href="http://www.shadowdefender.com/" target="_blank">Shadow Defender</a>
- sandbox &ndash; <a href="http://www.sandboxie.com/" target="_blank">Sandboxie</a>

Nejbezpečnější způsob virtualizace je virtuální počítač při korektním nastavení a aplikaci snapshotů. Lehká virtualizace OS spočívá ve vrácení změn v OS při restartu, může být velmi užitečná proti např. ransomware. U sandboxu velmi záleží na implementaci, bezplatné řešení Sandboxie poskytující externí sandbox pro aplikace, je spíše na hraní.

> Instalace a konfigurace Sandboxie

- Stáhněte si <a href="http://www.sandboxie.com/index.php?DownloadSandboxie" target="_blank">Sandboxie</a>.
- Aplikaci nainstalujte a projděte úvodním tutoriálem.
- Otevřete **Ovládání Sandboxie**.
- Klikněte pravým tlačítkem na **Sandbox DefaultBox** a zvolte možnost <span class="green">Nastavení Sandboxu</span>.
<li style="list-style-type: none"><img src="https://faq.mople71.cz/img/cs/sbie2.png" alt="sandboxie"></li>
- V pravém panelu rozbalte možnost **Vymazat** a klikněte na <span class="green">Smazat pracovní soubory</span>.
- Zatrhněte možnost <span class="green">Automaticky smazat obsah Sandboxu</span> a klikněte na <span class="green">OK</span>.
<li style="list-style-type: none"><img src="https://faq.mople71.cz/img/cs/sbie1.png" alt="sandboxie_2"></li>

<br>

### Ostatní aplikace:
Užitečné aplikace, které nespadají ani pod jednu kategorii vrstev zabezpečení.

#### Doporučené ostatní aplikace:
- <a href="https://unchecky.com/" target="_blank">Unchecky</a>
- <a href="http://implbits.com/products/hashtab/" target="_blank">HashTab</a>

<br><br><hr><br>

## Zabezpečení internetového prohlížeče:
- bezpečnější nastavení (vypnutí nebezpečných funkcí, ideálně vč. javascriptu)
- blokování reklamy
- anti-exploit mitigace
- oddělení prohlížeče od dat a fyzického OS (sandbox &lt; VM &lt; live OS)

Jelikož se mne uživatelé velmi často ptají na můj názor na prohlížeče a mnou doporučovaný prohlížeč, rozhodl jsem se tyto informace implementovat do FAQ. Naleznete zde i vysvětlení, které už je ovšem trochu pokročilejší.

> Doporučené prohlížeče z ohledu bezpečnosti

Všechny prohlížeče jsou po korektním nastavení relativně bezpečné, nejvíce také záleží na vás. Proto zde rozeberu pouze teoretické zabezpečení prohlížečů z hlediska mitigací exploitů apod. Níže v sekci naleznete návody na zabezpečení **Mozilla Firefox**, **Internet Explorer**, **Google Chrome** a **Microsoft Edge** kvůli jejich dominantnímu postavení.</p>

Ze zmíněných prohlížečů bych doporučil <span class="green">Microsoft Edge</span> a <a href="https://chromium.woolyss.com/" target="_blank"><span class="green underline">Chromium</span></a>, případně jeho proprietární variantu <a href="https://www.google.com/chrome/browser/index.html" target="_blank">Google Chrome</a>. S prohlížečem **Internet Explorer** taky nemám zásadní problém, pokud se korektně nastaví.

<span class="red">Mozilla Firefox</span>. Tento prohlížeč z hlediska zabezpečení nemohu doporučit, v porovnání s ostatními zmíněnými prohlížeči výrazně zaostává. Má starý kód výrazně nižší kvality nežli Edge či Chromium. Také postrádá základní mitigace proti exploitům. Externí sandbox typu Sandboxie (pro Linux např. firejail) nedosahuje zdaleka takové kvality jako vestavěný sandbox.

<span class="green">Chrome(ium)</span> používá vestavěný sandbox velmi dobré kvality. Také nabízí možnost využití vestavěného sandboxu ve Windows (AppContainer). Nové verze jsou kompilovány s **CFG**, což je významné plus.

<span class="green">Microsoft Edge</span> je nový a moderní prohlížeč využívající špičkovou implementaci sandboxu. Mimo jiné používá **CFG**, což je významné plus.

<br>

<!--- ./browsers.md -->

<br><br><hr><br>

## Doporučené bezpečnostní konfigurace:
Zde naleznete několik příkladů bezpečnostních konfigurací. Není tedy je slovo od slova kopírovat, stačí se inspirovat. Na druhou stranu níže zmíněné příklady konfigurací jsou plně funkční a relativně účinné. Pokud byste chtěli příklad aplikovat, počítá se s prostudováním celé sekce OS Windows v FAQ &ndash; hlavně návodů na jednotlivé programy &ndash; a aplikací zmíněných doporučení.

#### Bezplatná konfigurace pro BFU, který neumí anglicky (např. prarodiče):
> Konfigurace

- OS &ndash; Windows 10 Creators Update
- bezpečné nastavení OS &ndash; **kompletní**
- AV/M &ndash; **Windows Defender**
- FW &ndash; **Windows Firewall**
- anti-exploit &ndash; **nic**
- anti-executable &ndash; **CryptoPrevent**, **NVT Anti-AutoExec**
- virtualizace &ndash; **nic**
- internetový prohlížeč &ndash; **MS Edge** / **Google Chrome**
- zabezpečení prohlížeče &ndash; **kompletní**
- užitečné aplikace &ndash; **Unchecky**
- konfigurace pro pokročilé &ndash; dle znalostí

Je nutné proškolit BFU, jak se má chovat na PC a na internetu. Bezpečně nastavit OS (hlavně účet s omezeným oprávněním). V případě instalace 3-P internetového prohlížeče používat MS Edge pro bankovní účely a podobné citlivé věci. Samozřejmě, pokud zvládáte pokročilou konfiguraci popisovanou v FAQ pro pokročilé, úroveň zabezpečení můžete velmi výrazně zvýšit.

![arrow](https://mople71.cz/img/sm/arrow.gif) Tato konfigurace by při správném použití měla spolehlivě zabránit malware infekci.

<br>

#### Bezplatná konfigurace pro mírně pokročilého, který umí anglicky:
> Konfigurace

- OS &ndash; Windows 10/8.1/7
- bezpečné nastavení OS &ndash; **kompletní**
- AV/M &ndash; **Windows Defender** / **Microsoft Security Essentials**
- FW &ndash; **Windows Firewall**
- anti-exploit &ndash; **nic** / **EMET**
- anti-executable &ndash; **VoodooShield**, **NVT Anti-AutoExec**
- virtualizace &ndash; **Sandboxie**
- internetový prohlížeč &ndash; **MS Edge** / **Google Chrome** / **Internet Explorer**
- zabezpečení prohlížeče &ndash; **kompletní**
- užitečné aplikace &ndash; **Unchecky**, **HashTab**
- konfigurace pro pokročilé &ndash; dle znalostí

![arrow](https://mople71.cz/img/sm/arrow.gif) Tato konfigurace by při správném použití měla spolehlivě zabránit malware infekci.

<br><br><hr>

<h3 class="nocol">To je vše. Stay safe! ![smile](https://mople71.cz/img/sm/smile.gif)</h3>
