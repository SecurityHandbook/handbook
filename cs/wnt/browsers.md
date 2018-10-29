<h3 class="ch">![ch](https://mople71.cz/img/icons/ch16.png) Google Chrome</h3>

> Bezpečnější nastavení

- Do adresního řádku prohlížeče zadejte:
<li style="list-style-type: none"><pre><code>chrome://settings</code></pre>
a stiskněte **Enter**.</li>
- Zobrazí se nastavení. Sjeďte na konec stránky a klikněte na tlačítko ![ch](https://faq.mople71.cz/img/cs/ch.png)
- V sekci **Ochrana soukromí** klikněte na tlačítko <span class="green">Nastavení obsahu...</span>
<li style="list-style-type: none">![ch1](https://faq.mople71.cz/img/cs/ch1.png)</li>
- V sekci **Soubory cookie** zatrhněte možnost <span class="green">Blokovat soubory cookie třetích stran a data webových stránek</span>.
<li style="list-style-type: none">![ch2](https://faq.mople71.cz/img/cs/ch2.png)</li>
- V sekci **Flash** zablokujte spouštění obsahu Flash na webech.
<li style="list-style-type: none">![ch3](https://faq.mople71.cz/img/cs/ch3.png)</li>
- V sekci **Synchronizace na pozadí** zablokujte nedávno zavřeným webům dokončit odeslání a příjem dat.
<li style="list-style-type: none">![ch4](https://faq.mople71.cz/img/cs/ch4.png)</li>
- V sekci **Přístup pluginu mimo izolovaný prostor** zablokujte webům přístup do počítače pomocí pluginu.
<li style="list-style-type: none">![ch5](https://faq.mople71.cz/img/cs/ch5.png)</li>
- V sekci **Schránka** zablokujte webům přístup k datům ve schránce.
<li style="list-style-type: none">![ch6](https://faq.mople71.cz/img/cs/ch6.png)</li>
- Prohlížeč restartujte.

> Omezení JavaScript

- Do adresního řádku prohlížeče zadejte:
<li style="list-style-type: none"><pre><code>chrome://settings</code></pre>
a stiskněte **Enter**.</li>
- Zobrazí se nastavení. Sjeďte na konec stránky a klikněte na tlačítko ![ch](https://faq.mople71.cz/img/cs/ch.png)
- V sekci **Ochrana soukromí** klikněte na tlačítko <span class="green">Nastavení obsahu</span>
<li style="list-style-type: none">![ch1](https://faq.mople71.cz/img/cs/ch1.png)</li>
- V sekci **JavaScript** zablokujte spouštění JS.
<li style="list-style-type: none">![ch7](https://faq.mople71.cz/img/cs/ch7.png)</li>
- Klikněte na tlačítko <span class="green">Přidat</span> v sekci **Povolit**.
- Zadejte adresu důvěryhodného webu, na kterém se může spouštět JS. Syntax je jednoduchý.
<li style="list-style-type: none">![ch8](https://faq.mople71.cz/img/cs/ch8.png)</li>
- Klikněte na <span class="green">Přidat</span>.
- Prohlížeč restartujte.

> Blokování reklamy

- Nainstalujte si následující bezpečnostní doplněk: [uBlock Origin](https://chrome.google.com/webstore/detail/ublock-origin/cjpalhdlnbpafiamejdnhcphjbkeiagm?hl=cs)

#### Nastavení uBlock:

- Klikněte na ikonu uBlock v panelu ikon a následně klikněte na nápis <span class="green">uBlock Origin</span>.
<li style="list-style-type: none">![chublock](https://faq.mople71.cz/img/en/chublock.png)</li>
- Zobrazí se nastavení uBlock Origin. V sekci **Soukromí** zatrhněte možnost <span class="green">Předejít úniku lokálních IP adres přes WebRTC</span>.
- Následně se přesuňte do záložky <span class="green">Filtry třetích stran</span>.
<li style="list-style-type: none">![ublock](https://faq.mople71.cz/img/cs/ublock.png)</li>
- Zde vyberte filtry pro blokování webového obsahu. Doporučuji kromě výchozích zvolit následující:</li>
<li style="list-style-type: none">![ublock1](https://faq.mople71.cz/img/cs/ublock1.png)</li>
- Následně v pravém horním rohu klikněte na tlačítko: ![ublock2](https://faq.mople71.cz/img/cs/ublock2.png)
- Přesuňte se na začátek stránky, zkontrolujte zatržítko u položky <span class="green">Automaticky aktualizovat seznamy filtrů</span> a klikněte na tlačítko <span class="green">Aktualizovat nyní</span>. Během aktualizace panel nezavírejte.
<li style="list-style-type: none">![ublock3](https://faq.mople71.cz/img/cs/ublock3.png)</li>


> Oddělení prohlížeče od OS a dat

Google Chrome používá velmi dobrou implementaci sandboxu.

<br>

<h3 class="chm">![chm](https://mople71.cz/img/icons/chm16.ico) Chromium:</h3>

Nechcete-li používat *Google Chrome*, doporučuji použít open-source Chromium, na kterém je *Google Chrome* založen. Chromium na Windows se bohužel neumí automaticky aktualizovat. Můžete ovšem použít komunitní open-source nástroj.

> Instalace a nastavení chrlauncher

- Stáhněte si nejnovější verzi [Chrlauncher](https://github.com/henrypp/chrlauncher/releases).
- Archiv extrahujte. V závislosti na bitové verzi vašeho OS určete, kterou složku z archivu budete potřebovat (64-bit OS &ndash; složka **64**), a následně ji přesuňte na důstojné místo (ideálně *%localappdata%*, ale stačí *Dokumenty*). Také je vhodné ji přejmenovat.
- Ve složce nalezněte a otevřete konfigurační soubor <span class="green">chrlauncher.ini</span>.
- Nalezněte řádek začínající na **ChromiumArchitecture** a za rovnítko vepište požadovanou architekturu (na novějších zařízeních <span class="green">64</span>):
<li style="list-style-type: none">![chrl](https://faq.mople71.cz/img/en/chrl.png)</li>
- Sjeďte níže na řádek začínající na **ChromiumType** a za rovnítko vepište druh prohlížeče, který chcete použít. <span class="green">Stable-codecs-nosync</span> je verze s kodeky a bez služeb Google, je tedy doporučena. Naopak *ungoogled-chromium* je neoficiální nebezpečný fork a jeho užití je důrazně <span style="color: #bf0000">nedoporučeno</span>.
- Zkontrolujte nastavení **ChromiumCheckPeriod**, případně opravte.
<li style="list-style-type: none">![chrl1](https://faq.mople71.cz/img/en/chrl1.png)</li>
- Dále zkontrolujte a případně opravte nastavení následujících argumentů:
<li style="list-style-type: none"><pre><code>ChromiumAutoDownload=true
ChromiumBringToFront=true
ChromiumWaitForDownloadEnd=true</code></pre></li>
- Změny uložte a konfigurační soubor zavřete.
- Spusťte aplikaci <span class="green">chrlauncher</span>.
- Chcete-li nastavit chrlauncher jako výchozí prohlížeč, klikněte pravým tlačítkem na skript <span class="green">SetDefaultBrowser</span> ve složce a zvolte možnost: ![admin](https://mople71.cz/img/icons/admin.png) **Spustit jako správce**.
- Na Windows 10 budete muset následně výchozí prohlížeč ještě zvolit v **Nastavení**.
<li style="list-style-type: none">![chrl2](https://faq.mople71.cz/img/cs/chrl2.png)</li>

> Bezpečnější nastavení a blokování reklam

Použijte postup pro **Google Chrome** výše, je identický.

<br>

<h3 class="ed">![edge](https://mople71.cz/img/icons/edge16.png) Microsoft Edge</h3>

> Bezpečnější nastavení

- V pravém panelu otevřete <span class="green">Nastavení</span>.
- Sjeďte na konec stránky a klikněte na <span class="green">Zobrazit upřesňující nastavení</span>.
- Zkontrolujte konfiguraci a případně upravte:
<li style="list-style-type: none">![edge](https://faq.mople71.cz/img/cs/edge.png)</li>
- Prohlížeč restartujte.

> Blokování reklamy

- Nainstalujte si následující bezpečnostní doplněk: [uBlock Origin](https://www.microsoft.com/cs-cz/store/p/ublock-origin/9nblggh444l4)

#### Nastavení uBlock:
- Klikněte na ikonu uBlock v panelu ikon a následně otevřete **Nastavení**.
<li style="list-style-type: none">![edublock](https://faq.mople71.cz/img/en/edublock.png)</li>
- Zobrazí se nastavení uBlock Origin. V sekci **Soukromí** zatrhněte možnost <span class="green">Předejít úniku lokálních IP adres přes WebRTC</span>.
- Následně se přesuňte do záložky <span class="green">Filtry třetích stran</span>.
<li style="list-style-type: none">![ublock](https://faq.mople71.cz/img/cs/ublock.png)</li>
- Zde vyberte filtry pro blokování webového obsahu. Doporučuji kromě výchozích zvolit následující:</li>
<li style="list-style-type: none">![ublock1](https://faq.mople71.cz/img/cs/ublock1.png)</li>
- Následně v pravém horním rohu klikněte na tlačítko: ![ublock2](https://faq.mople71.cz/img/cs/ublock2.png)
- Přesuňte se na začátek stránky, zkontrolujte zatržítko u položky <span class="green">Automaticky aktualizovat seznamy filtrů</span> a klikněte na tlačítko <span class="green">Aktualizovat nyní</span>. Během aktualizace panel nezavírejte.
<li style="list-style-type: none">![ublock3](https://faq.mople71.cz/img/cs/ublock3.png)</li>


> Oddělení prohlížeče od OS a dat

Microsoft Edge používá špičkovou implementaci sandboxu.

<br>

<h3 class="ff">![ff](https://mople71.cz/img/icons/ff.png) Mozilla Firefox</h3>

> Bezpečnější nastavení

- Do adresního řádku prohlížeče zadejte:
<li style="list-style-type: none"><pre><code>about:preferences</code></pre>
a stiskněte **Enter**.</li>
- V levém panelu se přesuňte do záložky <span class="green">Soukromí a zabezpečení</span>.
- V sekci **Nastavení soukromí** zapněte blokování <span class="green">Všech nalezených sledovacích prvků</span> a <span class="green">Cookies třetích stran</span>.
- U nastavení blokování zvolte možnost <span class="green">Vždy</span>, u nastavení cookies třetích stran zvolte <span class="green">Cookies sledovacích prvků</span>. Následně klikněte na tlačítko <span class="green">Změnit seznam blokací</span>.
<li style="list-style-type: none">![ff2](https://faq.mople71.cz/img/cs/ff.png)</li>
- V seznamu vyberte možnost **Přísná ochrana s Disconnect.me** a klikněte na <span class="green">Uložit změny</span>.
- Sjeďte níže do sekce **Oprávnění**.
- Zatrhněte položku <span class="green">Zabránit službám pro přístupnost v přístupu k vašemu prohlížeči</span> a povtrďte restart aplikace.
<li style="list-style-type: none">![ff2](https://faq.mople71.cz/img/cs/ff1.png)</li>

- Do adresního řádku prohlížeče zadejte:
<li style="list-style-type: none"><pre><code>about:config</code></pre>
a stiskněte **Enter**.</li>
- Varování potvrďte tlačítkem <span class="green">Beru to na vědomí!</span>.
- Do vyhledávacího pole ve vrchní části stránky zadejte:
<li style="list-style-type: none"><pre><code>ocsp</code></pre></li>
- Vyhledávání zobrazí veškeré hodnoty s **OCSP** v názvu. Dvakrát poklepejte levým myšítkem na následující hodnotu:
<li style="list-style-type: none"><pre><code>security.OCSP.require</code></pre></li>
- Tím změníte konfiguraci hodnoty (zapnete/vypnete požadovanou funkci).
<li style="list-style-type: none">![ff0](https://faq.mople71.cz/img/cs/ff2.png)
![ff1](https://faq.mople71.cz/img/cs/ff3.png)</li>
- Výše uvedeným způsobem vyhledejte a změňte nastavení následujících hodnot (pokud se neshoduje):
<li style="list-style-type: none"><pre><code>accessibility.blockautorefresh  ---  automatické přesměrování; true
security.mixed_content.block_display_content  ---  nezabezpečený obsah; true
security.mixed_content.block_object_subrequest --- true
media.peerconnection.ice.no_host --- true
javascript.options.asmjs  ---  false
shumway.disabled  ---  true
network.negotiate-auth.allow-insecure-ntlm-v1  ---  false
security.insecure_password.ui.enabled  ---  true
network.allow-experiments --- false</code></pre></li>
- Do vyhledávacího pole ve vrchní části stránky zadejte:
<li style="list-style-type: none"><pre><code>flash</code></pre></li>
- Vyhledávání zobrazí veškeré hodnoty s **flash** v názvu. Dvakrát poklepejte levým myšítkem na následující hodnotu:
<li style="list-style-type: none"><pre><code>plugin.state.flash</code></pre></li>
- Tím otevřete okno pro změnu hodnoty položky. Nastavte hodnotu na <span class="red">0</span> a klikněte na <span class="green">OK</span>.
- Postup zopakujte pro následující položku:
<li style="list-style-type: none"><pre><code>plugin.state.java</code></pre></li>

> Blokování reklamy

- Nainstalujte si následující bezpečnostní doplněk: [uBlock Origin](https://addons.mozilla.org/cs/firefox/addon/ublock-origin/)

#### Nastavení uBlock:
- Klikněte na ikonu uBlock v panelu ikon a následně klikněte na nápis <span class="green">uBlock Origin</span>.
<li style="list-style-type: none">![ffublock](https://faq.mople71.cz/img/en/ffublock.png)</li>
- Zobrazí se nastavení uBlock Origin. V sekci **Soukromí** zatrhněte možnost <span class="green">Předejít úniku lokálních IP adres přes WebRTC</span>.
- Následně se přesuňte do záložky <span class="green">Filtry třetích stran</span>.
<li style="list-style-type: none">![ublock](https://faq.mople71.cz/img/cs/ublock.png)</li>
- Zde vyberte filtry pro blokování webového obsahu. Doporučuji kromě výchozích zvolit následující:</li>
<li style="list-style-type: none">![ublock1](https://faq.mople71.cz/img/cs/ublock1.png)</li>
- Následně v pravém horním rohu klikněte na tlačítko: ![ublock2](https://faq.mople71.cz/img/cs/ublock2.png)
- Přesuňte se na začátek stránky, zkontrolujte zatržítko u položky <span class="green">Automaticky aktualizovat seznamy filtrů</span> a klikněte na tlačítko <span class="green">Aktualizovat nyní</span>. Během aktualizace panel nezavírejte.
<li style="list-style-type: none">![ublock3](https://faq.mople71.cz/img/cs/ublock3.png)</li>

> Oddělení prohlížeče od OS a dat

Sandbox Firefoxu je v aktivním vývoji a již nyní je v celkem použitelném stavu.

<br>

<h3 class="ie">![ie](https://mople71.cz/img/icons/ie16.png) Internet Explorer</h3>

> Bezpečnější nastavení

- Stiskněte kláv. zkratku ![win](https://mople71.cz/img/icons/wkey.png) <span class="ks">+ R</span>, do textového pole zadejte:
<li style="list-style-type: none"><pre><code>inetcpl.cpl</code></pre>
a stiskněte **Enter**.</li>
- Zobrazí se Vlastnosti internetu. V horní liště se přesuňte do záložky <span class="green">Zabezpečení</span>.
- Zobrazí se nastavení úrovně zabezpečení internetových zón.
<li style="list-style-type: none">![ie0](https://faq.mople71.cz/img/cs/ie.png)</li>
- V zóně **Internet** se ujistěte, že má nastavenou výchozí úroveň zabezpečení. Pokud nemá, klikněte na tlačítko <span class="green">Výchozí úroveň</span>, čímž nastavení opravíte.
- Přesuňte se do zóny **Místní intranet** a upravte její úroveň zabezpečení dle obrázku:
<li style="list-style-type: none">![ie1](https://faq.mople71.cz/img/cs/ie1.png)</li>
- Stejným způsobem upravte úroveň zabezpečení zóny **Důvěryhodné weby**.
- V horní liště se přesuňte do záložky <span class="green">Osobní údaje</span>, případně napravte.
- Nastavení upravte na 3. nebo 2. nejvyšší možnost (<span class="green">Vyšší</span> nebo <span class="green">Vysoká</span>).
<li style="list-style-type: none">![ie2](https://faq.mople71.cz/img/cs/ie2.png)</li>
- V horní liště se přesuňte do záložky <span class="green">Upřesnit</span>.
- V sekci **Procházení** <span style="color: #BF0000">odstraňte</span> zatržítko u položky <span class="green">Povolit rozšíření prohlížečů jiných výrobců</span>.
- V sekci **Zabezpečení** <span style="color: #BF0000">odstraňte</span> zatržítko u následujících položek:
  - Používat protokol SSL 3.0
  - Povolit úložiště DOM (volitelné, může znefunkčnit některé stránky)
- A naopak <span style="color: #BF0000">přidejte</span> zatržítko k následujícím položkám:
  - Blokovat nezabezpečené bitové kopie s ostatním smíšeným obsahem
  - Povolit filtr SmartScreen
  - Povolit rozšířený chráněný režim
  - Povolit striktní ověřování P3P
- V dolním panelu aplikace klikněte na tlačítko <span class="green">OK</span> a nastavení zavřete.

- Otevřete prohlížeč.
- Klikněte na ozubené kolo v pravém horním rohu.
- Rozbalte záložku <span class="green">Zabezpečení</span>.
- Klikněte na tlačítko <span class="green">Filtrování ActiveX</span>.
<li style="list-style-type: none">![ie3](https://faq.mople71.cz/img/cs/ie3.png)</li>

> Blokování reklamy

- Otevřete v IE [následující stránku](http://dayngo.com/static/filter.html).
- Zobrazí se seznam filtrů pro Tracking Protection (vestavěný blokátor nejen reklam).
- Ze seznamu doporučuji přidat filtry <span class="green">EasyList</span>, <span class="green">EasyList Czech and Slovak</span> a <span class="green">EasyPrivacy</span>.

#### Přidání filtru pro Tracking Protection:
- Klikněte na takto vypadající odkaz: ![ie4](https://faq.mople71.cz/img/en/ie4.png)
- V zobrazeném vyskakovacím okně klikněte na tlačítko <span class="green">Přidat seznam</span>.

Další český filtr naleznete např. [zde](http://adblock.dajbych.net/).

> Oddělení prohlížeče od OS a dat

Prohlížeč je částečně oddělen od OS díky technologii **Protected Mode**.
