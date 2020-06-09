# OS Windows pro pokročilé
Windows se jakožto nejrozšířenější desktopový OS těší velké pozornosti hackerů, jeho dostatečné zabezpečení je proto nezbytné.

Tato část příručky počítá s tím, že jste pročetli kapitolu [OS Windows pro méně pokročilé](https://securityhandbook.cz/cs/wnt/index.php#wnt) a máte minimálně znalosti v kapitole rozebírané.

#### Sekce kapitoly:
- [Bezpečnostní aplikace](#wnt1)
- [ACL](#wnt2)

<br>

## Bezpečnostní aplikace:
### Firewall:
Windows v základu integrují <span class="green">Windows Defender Firewall</span> (WDF) pro blokování příchozí komunikace. Co se blokování odchozí komunikace týče, *Windows Defender Firewall* tuto funkci podporuje, ovšem její nastavení se v nových verzích OS limitně blíží k úrovni nemožného.

> Konfigurace WDF pro blokování odchozí komunikace

- Otevřete si **hledání Windows**, do vyhledávacího pole zadejte:
<li style="list-style-type: none"><pre><code>wf.msc</code></pre></li>
- Na nalezenou položku klikněte pravým tlačítkem a zvolte možnost: ![admin](https://securityhandbook.cz/img/icons/admin.png) **Spustit jako správce**.
<li style="list-style-type: none">![wdf](https://securityhandbook.cz/img/cs/wdf.png)</li>
- Otevře se pokročilé nastavení Windows Firewall. V prostředním sloupci zvolte možnost <span class="green">Vlastnosti brány Firewall v programu Windows Defender</span>.
- V horním panelu si otevřete záložku **Privátní profil**. U položky **Odchozí připojení** zvolte možnost <span class="green">Blokovat</span>.
<li style="list-style-type: none">![wdf1](https://securityhandbook.cz/img/cs/wdf1.png)</li>
- Postup zopakujte pro záložku **Veřejný profil**.
- Klikněte na <span class="green">OK</span>.
<li style="list-style-type: none">![wdf2](https://securityhandbook.cz/img/cs/wdf2.png)</li>

<div class="alert success"><p><em class="icon-ok-circled"></em>**Úspěch**<br>
Nyní WDF blokuje veškerou odchozí komunikaci, která není specificky povolena. Dále je třeba nastavit whitelist.</p></div>

> Whitelist odchozí komunikace

<pre><code># sitove sluzby OS
%SystemRoot%\System32\svchost.exe

# nastaveni
%SystemRoot%\ImmersiveControlPanel\SystemSettings.exe

# Defender
%ProgramFiles%\Windows Defender\MsMpEng.exe
%ProgramFiles%\Windows Defender\MpCmdRun.exe
%ProgramFiles%\Windows Defender\NisSrv.exe
%ProgramData%\Microsoft\Windows Defender\Platform\*\MsMpEng.exe
%ProgramData%\Microsoft\Windows Defender\Platform\*\MpCmdRun.exe
%ProgramData%\Microsoft\Windows Defender\Platform\*\MpDlpCmd.exe
%ProgramData%\Microsoft\Windows Defender\Platform\*\NisSrv.exe

# OpenSSH
%SystemRoot%\System32\OpenSSH\ssh-agent.exe
</code></pre>

<br>

### MemProtect:
[Excubits MemProtect](https://excubits.com/content/en/products_memprotect.html) je drobný ovladač určující které procesy mají přístup k jakým procesům v RAM. Jedná se o špičkové řešení mitigace proti exploitům, jehož konfigurace je triviální.

Existuje bezplatná demo verze, která je po nějakou dobu plně funkční, s omezením velikosti konfigurační souboru na 2 kB, což není dostatek pro pokročilé nastavení, investice do plné verze je tedy žádoucí.

> Instalace MemProtect

- Stáhněte si demo verzi ze stránek výrobce, soubor spusťte a aplikaci vybalte.
- Otevřete složku **64-bit**.
- Klikněte pravým tlačítkem na INF soubor a zvolte **Install**.
- RTFM, který je ve složce *Tools*.

> Ukázka syntaxe konfiguračního souboru

Příklad: Zablokování přístupu všem nesystémovým procesům k procesům VoodooShield – jednoduché ztížení exploitace.

<pre><code>[LETHAL]
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
</code></pre>

<br>

### FIDES:
[Excubits FIDES](https://excubits.com/content/en/products_pumpernickelfides.html) je drobný ovladač určující které procesy mají k jakým souborům/složkám přístup. Jedná se o špičkové řešení mitigace proti exploitům, jehož konfigurace je triviální.

Existuje bezplatná demo verze, která je po nějakou dobu plně funkční, s omezením velikosti konfigurační souboru na 2 kB, což není dostatek pro pokročilé nastavení, investice do plné verze je tedy žádoucí.

> Instalace FIDES

- Stáhněte si demo verzi ze stránek výrobce, soubor spusťte a aplikaci vybalte.
- Otevřete složku **64-bit**.
- Klikněte pravým tlačítkem na INF soubor a zvolte **Install**.
- RTFM, který je ve složce *Tools*.

<br>

### Bouncer:
[Excubits Bouncer](https://excubits.com/content/en/products_bouncer.html) je drobný ovladač umožňující pokročilý whitelist spustitelných souborů. Jedná se o špičkové řešení mitigace proti exploitům, jehož konfigurace je triviální.

Existuje bezplatná demo verze, která je po nějakou dobu plně funkční, s omezením velikosti konfigurační souboru na 5 kB, což není dostatek pro pokročilé nastavení, investice do plné verze je tedy žádoucí.

Postup je podobný jako u výše zmíněných produktů stejné společnosti.

<br><br><hr><br>

## ACL:
<span class="green">Access Control List</span> je součást bezpečnostního modelu OS, jež v důsledku pro koncového uživatele umožňuje např. spuštění aplikací v určité složce.

> Nutná teorie k ACL

<span class="green">ACL</span> je seznam záznamů (jednotlivý záznam je nazýván **ACE**) určujících, který subjekt má jaké pravomoce pro manipulaci se zabezpečeným objektem (konkrétně se budeme bavit pouze o DACL). Při přihlášení je uživateli přiřazen přístupový **token**, který následně přebírají všechny aplikace spuštěné daným uživatelem. Pokud proces chce operovat se zabezpečeným objektem, kontrola přístupu se podívá na jeho token a na deskriptor zabezpečení u objektu.

Token obsahuje mnoho věcí, pro nás je ale aktuálně důležitá jedna položka: <span class="green">SID</span>.

**SID** je unikátní hodnota určená k identifikaci vlastníka – uživatelského účtu nebo uživatelské skupiny. Např.: *S-1-5-32-544*.

Kontrola přístupu z tokenu aplikace získá jeho SID a následně v ACL seznamu vyhledá veškeré záznamy (ACE), ve kterých je daný SID. Následně všechny nalezené ACE sekvenčně prozkoumá, dokud nenalezne ACE, který přístup k objektu explicitně zakáže/povolí. ACE zakazující přístup jsou zkoumány přednostně.

--

ACL lze využít následovně: můžeme zakázat spouštění spustitelných souborů v uživatelských složkách a složce pro dočasné soubory. Běžný uživatel by neměl potřebovat spouštět ve svých složkách spustitelné soubory – a pokud ano, vždy lze nastavit výjimka.

> Konfigurace exekuce v uživatelské složce

- Stiskněte kláv. zkratku <img src="https://securityhandbook.cz/img/icons/wkey.png" alt="win"> <span class="ks">+ X</span> a z nabídky vyberte <span class="green">Windows PowerShell (správce)</span>.
<li style="list-style-type: none">![wx](https://guide.mople71.cz/img/cs/wx.png)</li>
- Do příkazové řádky zadejte následující příkazy (cestu ke složce uživatele patřičně upravte):
<li style="list-style-type: none"><pre><code>icacls "(cesta k uživatelské složce)" /c /deny "Everyone:(OI)(CI)(X)"
# např.: icacls "C:\Users\Uzivatel" /c /deny "Everyone:(OI)(CI)(X)"
icacls "(cesta k uživatelské složce)\AppData\Local\Microsoft\WindowsApps" /inheritance:d
icacls "(cesta k uživatelské složce)\AppData\Local\Microsoft\WindowsApps" /remove:d Everyone /t</code></pre></li>

Stejný postup proveďte pro globální složku dočasných souborů.

<br>

### Integritní politika:
Pomocí integritní politiky je možné např. omezit přístup aplikacím s nízkou úrovní integrity do osobních složek. Pro komplexní konfiguraci přístupu aplikací k disku je doporučeno použít <span class="green">FIDES</span>. Ochranu proti ransomware poskytuje <span class="green">Windows Defender</span>. *Tato sekce již nemá příliš praktické využití.*

> Instalace CHML

Integrovaný nástroj **icacls** neumožňuje nastavení integritní politiky, je proto nutné použít drobný nástroj třetí strany.

- Stáhněte si [chml](https://securityhandbook.cz/mirror/chml.exe) (by *[Mark Minasi](https://www.minasi.com/)*) a uložte jej <span class="blue">na Plochu</span>.
- Zkontrolujte checksum aplikace:
<li style="list-style-type: none"><pre><code>SHA-256: 59aa55d2eac6b295d42ef2aadc607b759f034f4557a66dec0214a4cc032ecc17</code></pre></li>
- Aplikaci zkopírujte do umístění: <span class="blue">%SystemRoot%\System32</span>
- Stiskněte kláv. zkratku <img src="https://securityhandbook.cz/img/icons/wkey.png" alt="win"> <span class="ks">+ X</span> a z nabídky vyberte <span class="green">Windows PowerShell (správce)</span>.
<li style="list-style-type: none">![wx](https://guide.mople71.cz/img/cs/wx.png)</li>
- Do příkazové řádky zadejte následující příkaz pro validaci úspěšné instalace aplikace:
<li style="list-style-type: none"><pre><code>chml</code></pre></li>

> Nastavení integritní politiky osobních složek

- Do příkazové řádky zadejte následující příkazy:
<li style="list-style-type: none"><pre><code>chml "(cesta k uživatelské složce)\Documents" -i:m -nw -nx
chml "(cesta k uživatelské složce)\Pictures" -i:m -nw -nx
chml "(cesta k uživatelské složce)\Music" -i:m -nw -nx
chml "(cesta k uživatelské složce)\Videos" -i:m -nw -nx

# -i:l (nízká úroveň integrity)
# -i:m (střední úroveň integrity)
# -i:h (vysoká úroveň integrity)
# -nw (NO_WRITE_UP)
# -nx (NO_EXECUTE_UP)
# -nr (NO_READ_UP)</code></pre></li>
- Analogicky lze nastavit integritní politiku pro libovolnou složku/soubor. Úroveň integrity a integritní politika jsou ve výchozím nastavení dědičné atributy.

<br><br><hr>

<h3 class="nocol">To je vše. Stay safe! ![smile](https://securityhandbook.cz/img/sm/smile.svg)</h3>
