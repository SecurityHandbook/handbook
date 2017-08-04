<h3 id="lin4.1" class="chm">![chm](https://mople71.cz/img/chm16.ico) Chromium:</h3>

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

Chromium používá špičkovou implementaci sandboxu.

<br>

<h3 id="win3.4" class="ff">![ff](https://mople71.cz/img/ff.png) Mozilla Firefox</h3>

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
