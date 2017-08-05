<h3 id="win3.1" class="ch">![ch](https://mople71.cz/img/ch16.png) Google Chrome</h3>

> Bezpečnější nastavení

- Do adresního řádku prohlížeče zadejte:
<li style="list-style-type: none"><pre><code>chrome://settings</code></pre>
a stiskněte **Enter**.</li>
- Zobrazí se nastavení. Sjeďte na konec stránky a klikněte na tlačítko ![ch1](https://faq.mople71.cz/img/cs/ch1.png)
- V sekci **Ochrana soukromí** klikněte na tlačítko <span class="green">Nastavení obsahu...</span>
<li style="list-style-type: none">![ch2](https://faq.mople71.cz/img/cs/ch2.png)</li>
- V sekci **Soubory cookie** zatrhněte možnost <span class="green">Blokovat soubory cookie třetích stran a data webových stránek</span>.
<li style="list-style-type: none">![ch3](https://faq.mople71.cz/img/cs/ch3.png)</li>
- V pravém dolním rohu klikněte na <span class="green">Hotovo</span>.
- Prohlížeč restartujte.

> Omezení JavaScript

- Do adresního řádku prohlížeče zadejte:
<li style="list-style-type: none"><pre><code>chrome://settings</code></pre>
a stiskněte **Enter**.</li>
- Zobrazí se nastavení. Sjeďte na konec stránky a klikněte na tlačítko ![ch1](https://faq.mople71.cz/img/cs/ch1.png)
- V sekci **Ochrana soukromí** klikněte na tlačítko <span class="green">Nastavení obsahu</span>
<li style="list-style-type: none">![ch2](https://faq.mople71.cz/img/cs/ch2.png)</li>
- V sekci **JavaScript** zablokujte spouštění JS.
<li style="list-style-type: none">![ch4](https://faq.mople71.cz/img/cs/ch4.png)</li>
- Klikněte na tlačítko <span class="green">Přidat</span> v sekci **Povolit**.
- Zadejte adresu důvěryhodnéhu webu, na kterém se může spouštět JS. Syntax je jednoduchý.
<li style="list-style-type: none">![ch5](https://faq.mople71.cz/img/cs/ch5.png)</li>
- Klikněte na <span class="green">Přidat</span>.

> Blokování reklamy

- Nainstalujte si následující bezpečnostní doplněk: <a href="https://chrome.google.com/webstore/detail/ublock-origin/cjpalhdlnbpafiamejdnhcphjbkeiagm?hl=cs" target="_blank">uBlock Origin</a>.

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

<h3 id="lin4.1" class="chm">![chm](https://mople71.cz/img/chm16.ico) Chromium:</h3>

Nechcete-li používat *Google Chrome*, doporučuji použít open-source Chromium, na kterém je *Google Chrome* založen. Chromium na Windows se bohužel neumí automaticky aktualizovat. Můžete ovšem použít komunitní open-source nástroj.

> Instalace a nastavení chrlauncher

- Stáhněte si nejnovější verzi <a href="https://github.com/henrypp/chrlauncher/releases" target="_blank">Chrlauncher</a>.
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
- Chrlauncher následně můžete připnout na panel a nastavit jako výchozí prohlížeč v **Nastavení**.
<li style="list-style-type: none">![chrl2](https://faq.mople71.cz/img/cs/chrl2.png)</li>

> Bezpečnější nastavení a blokování reklam

Použijte postup pro **Google Chrome** výše, je identický.

<br>

<h3 id="win3.2" class="ed">![edge](https://mople71.cz/img/edge16.png) Microsoft Edge</h3>

> Bezpečnější nastavení

- V pravém panelu otevřete <span class="green">Nastavení</span>.
- Sjeďte na konec stránky a klikněte na <span class="green">Zobrazit upřesňující nastavení</span>.
- Zkontrolujte konfiguraci a případně upravte:
<li style="list-style-type: none">![edge](https://faq.mople71.cz/img/cs/edge.png)</li>
- Prohlížeč restartujte.

> Blokování reklamy

- Nainstalujte si následující bezpečnostní doplněk: <a href="https://www.microsoft.com/cs-cz/store/p/ublock-origin/9nblggh444l4" target="_blank">uBlock Origin</a>.

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

Microsoft Edge nyní používá velmi robustní implementaci sandboxu.

<br>

<h3 id="win3.3" class="ie">![ie](https://mople71.cz/img/ie16.png) Internet Explorer</h3>

> Bezpečnější nastavení

- Stiskněte kláv. zkratku ![win](https://mople71.cz/img/wkey.png) <span class="ks">+ R</span>, do textového pole zadejte:
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

- Otevřete v IE <a href="http://dayngo.com/static/filter.html" target="_blank">následující stránku</a>.
- Zobrazí se seznam filtrů pro Tracking Protection (vestavěný blokátor nejen reklam).
- Ze seznamu doporučuji přidat filtry <span class="green">EasyList</span>, <span class="green">EasyList Czech and Slovak</span> a <span class="green">EasyPrivacy</span>.

#### Přidání filtru pro Tracking Protection:
- Klikněte na takto vypadající odkaz: ![tp](https://mople71.cz/img/tp1.png)
- V zobrazeném vyskakovacím okně klikněte na tlačítko <span class="green">Přidat seznam</span>.

Další český filtr naleznete např. <a href="http://adblock.dajbych.net/">zde</a>.


> Oddělení prohlížeče od OS a dat

Prohlížeč je částečně oddělen od OS díky technologii **Protected Mode**. Jedná se o relativně spolehlivou metodu.

<br>

<h3 id="win3.4" class="ff">![ff](https://mople71.cz/img/ff.png) Mozilla Firefox</h3>

> Bezpečnější nastavení

- Do adresního řádku prohlížeče zadejte:
<li style="list-style-type: none"><pre><code>about:config</code></pre>
a stiskněte **Enter**.</li>
- Tlačítkem <span class="green">Beru to na vědomí!</span>, potvrďte varování.
- Zobrazí se podrobné nastavení prohlížeče. Zde lze provést pár bezpečnostních opatření.
- Do vyhledávacího pole ve vrchní části stránky zadejte:
<li style="list-style-type: none"><pre><code>ocsp</code></pre></li>
- Vyhledávání zobrazí veškeré hodnoty s **OCSP** v názvu. Dvakrát poklepejte myší na následující hodnotu:
<li style="list-style-type: none"><pre><code>security.OCSP.GET.enabled</code></pre></li>
- Tím změníte její výchozí nastavení (zapnete/vypnete požadovanou funkci).
<li style="list-style-type: none">![ff0](https://faq.mople71.cz/img/cs/ff.png)</li>
<li style="list-style-type: none"![ff1](https://faq.mople71.cz/img/cs/ff1.png)</li>
- Výše uvedeným způsobem vyhledejte a změňte nastavení následujících hodnot (pokud se neshoduje):
<li style="list-style-type: none"><pre><code>accessibility.blockautorefresh  ---  automatické přesměrování; true
browser.pocket.enabled  ---  vypíná službu Pocket; false
extensions.pocket.enabled ---  false
pdfjs.disabled  ---  vypne otevírání PDF v prohlížeči; true
security.mixed_content.block_display_content  ---  nezabezpečený obsah; true
security.ssl3.rsa_null_sha  ---  false
security.ssl3.rsa_null_md5  ---  false
security.ssl3.ecdhe_rsa_null_sha  ---  false
security.ssl3.ecdhe_ecdsa_null_sha  ---  false
security.ssl3.ecdh_rsa_null_sha  ---  false
security.ssl3.ecdh_ecdsa_null_sha  ---  false
security.ssl3.rsa_seed_sha  ---  false
security.ssl3.rsa_rc4_40_md5  ---  false
security.ssl3.rsa_rc2_40_md5  ---  false
security.ssl3.rsa_1024_rc4_56_sha  ---  false
security.ssl3.rsa_camellia_128_sha  ---  false
security.ssl3.ecdhe_rsa_aes_128_sha  ---  false
security.ssl3.ecdhe_ecdsa_aes_128_sha  ---  false
security.ssl3.ecdh_rsa_aes_128_sha  ---  false
security.ssl3.ecdh_ecdsa_aes_128_sha  ---  false
security.ssl3.dhe_rsa_camellia_128_sha  ---  false
security.ssl3.dhe_rsa_aes_128_sha  ---  false
security.ssl3.ecdh_ecdsa_rc4_128_sha  ---  false
security.ssl3.ecdh_rsa_rc4_128_sha  ---  false
security.ssl3.ecdhe_ecdsa_rc4_128_sha  ---  false
security.ssl3.ecdhe_rsa_rc4_128_sha  ---  false
security.ssl3.rsa_rc4_128_md5  ---  false
security.ssl3.rsa_rc4_128_sha  ---  false
security.tls.unrestricted_rc4_fallback  ---  false
security.ssl3.dhe_dss_des_ede3_sha  ---  false
security.ssl3.dhe_rsa_des_ede3_sha  ---  false
security.ssl3.ecdh_ecdsa_des_ede3_sha  ---  false
security.ssl3.ecdh_rsa_des_ede3_sha  ---  false
security.ssl3.ecdhe_ecdsa_des_ede3_sha  ---  false
security.ssl3.ecdhe_rsa_des_ede3_sha  ---  false
security.ssl3.rsa_des_ede3_sha  ---  false
security.ssl3.rsa_fips_des_ede3_sha  ---  false
security.ssl3.ecdh_rsa_aes_256_sha  ---  false
security.ssl3.ecdh_ecdsa_aes_256_sha  ---  false
security.ssl3.rsa_camellia_256_sha  ---  false
security.ssl3.dhe_rsa_camellia_256_sha  ---  false
security.ssl3.dhe_rsa_aes_256_sha  ---  false
security.ssl3.dhe_dss_aes_128_sha  ---  false
security.ssl3.dhe_dss_aes_256_sha  ---  false
security.ssl3.dhe_dss_camellia_128_sha  ---  false
security.ssl3.dhe_dss_camellia_256_sha  ---  false
media.peerconnection.ice.no_host --- true
network.jar.open-unsafe-types  ---  false
security.xpconnect.plugin.unrestricted  ---  false
javascript.options.asmjs  ---  false
shumway.disabled  ---  true
plugins.click_to_play  ---  true
network.negotiate-auth.allow-insecure-ntlm-v1  ---  false
security.insecure_password.ui.enabled  ---  true
plugins.update.notifyUser  ---  true


Volitelné hodnoty:
========================
(mohou znefunkčnit některé stránky, označené hvězdičkou obzvlášť)

*dom.storage.enabled  ---  DOM úložiště; false
*media.peerconnection.enabled  ---  WebRTC; false
dom.serviceWorkers.enabled  ---  false
dom.workers.enabled  ---  false
geo.enabled  ---  false
dom.mozTCPSocket.enabled  ---  false
dom.telephony.enabled  ---  false
beacon.enabled  ---  false
media.webspeech.recognition.enable  ---  false
media.webspeech.synth.enabled  ---  false
device.sensors.enabled  ---  false
browser.send_pings  ---  false
dom.vr.enabled  ---  false
dom.vibrator.enabled  ---  false
webgl.disabled  ---  true
camera.control.face_detection.enabled  ---  false
keyword.enabled  ---  false
gfx.font_rendering.opentype_svg.enabled  ---  false
svg.disabled  ---  false
devtools.webide.enabled  ---  false
devtools.debugger.remote-enabled  ---  false
network.allow-experiments  ---  false
browser.uitour.enabled  ---  false
dom.flyweb.enabled  ---  false
privacy.trackingprotection.enabled  ---  true
privacy.trackingprotection.pbmode.enabled  ---  true
privacy.resistFingerprinting  ---  true
browser.safebrowsing.downloads.remote.enabled  ---  false
security.pki.sha1_enforcement_level  ---  1
security.ssl.treat_unsafe_negotiation_as_broken  ---  true</code></pre></li>
- Do vyhledávacího pole ve vrchní části stránky zadejte:
<li style="list-style-type: none"><pre><code>flash</code></pre></li>
- Vyhledávání zobrazí veškeré hodnoty s **OCSP** v názvu. Dvakrát poklepejte myší na následující hodnotu:
<li style="list-style-type: none"><pre><code>plugin.state.flash</code></pre></li>
- Tím otevřete okno pro změnu hodnoty položky. Nastavte hodnotu na <span class="red">0</span> a klikněte na <span class="green">OK</span>.
- Postup zopakujte pro následující položku:
<li style="list-style-type: none"><pre><code>plugin.state.java</code></pre></li>

- Do adresního řádku prohlížeče zadejte:
<li style="list-style-type: none"><pre><code>about:preferences</code></pre>
a stiskněte **Enter**.</li>
- V levém panelu se přesuňte do záložky <span class="green">Aplikace</span>.
- Ve sloupci **Akce** rozklikněte pole v řádku **Soubor PDF**.
- Zvolte vámi preferovanou metodu &ndash; buď se vždy zeptat nebo automaticky PDF soubory stahovat nebo použít na otevření výchozí PDF prohlížeč. Osobně preferuji použít výchozí PDF prohlížeč.
<li style="list-style-type: none">![ff2](https://faq.mople71.cz/img/cs/ff2.png)</li>


> Blokování reklamy

- Nainstalujte si následující bezpečnostní doplněk: <a href="https://addons.mozilla.org/cs/firefox/addon/ublock-origin/" target="_blank">uBlock Origin</a>.</li>

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

Možno využít libovolný externí způsob, prohlížeč zatím nemá žádný integrovaný.
