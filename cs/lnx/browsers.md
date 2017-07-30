<h3 id="lin4.1" class="chm">![chm](https://mople71.cz/img/cs/chm16.ico) Chromium:</h3>

> Bezpečnější nastavení

- Do adresního řádku prohlížeče zadejte:
<li style="list-style-type: none"><pre><code>chrome://plugins</code></pre>
a stiskněte **Enter**.</li>
- Zobrazí se seznam rozšíření. V seznamu nalezněte **Adobe Flash Player** a deaktivujte jej.
<li style="list-style-type: none">![ch1](https://faq.mople71.cz/img/cs/ch1.png)</li>
- Do adresního řádku prohlížeče zadejte:
<li style="list-style-type: none"><pre><code>chrome://settings</code></pre>
a stiskněte **Enter**.</li>
- Zobrazí se nastavení. Sjeďte na konec stránky a klikněte na tlačítko <span class="green">Zobrazit rozšířená nastavení...</span>
- V sekci **Ochrana soukromí** klikněte na tlačítko <span class="green">Nastavení obsahu...</span>
- V sekci **Soubory cookie** zatrhněte možnost <span class="green">Blokovat soubory cookie třetích stran a data webových stránek</span>.
<li style="list-style-type: none">![ch2](https://faq.mople71.cz/img/cs/ch2.png)</li>
- V pravém dolním rohu klikněte na <span class="green">Hotovo</span>.
- Prohlížeč restartujte.

> Blokování reklamy

- Nainstalujte si následující bezpečnostní doplněk: <a href="https://chrome.google.com/webstore/detail/ublock-origin/cjpalhdlnbpafiamejdnhcphjbkeiagm?hl=cs" target="_blank">uBlock Origin</a>.

#### Nastavení uBlock:

- Klikněte na ikonu uBlock v panelu ikon a následně klikněte na nápis <span class="green">uBlock Origin</span>.
<li style="list-style-type: none">![chublock](https://faq.mople71.cz/img/cs/chublock.png)</li>
- Zobrazí se nastavení uBlock Origin. V sekci **Soukromí** zatrhněte možnost <span class="green">Předejít úniku lokálních IP adres přes WebRTC</span>.
- Následně se přesuňte do záložky <span class="green">Filtry třetích stran</span>.
<li style="list-style-type: none">![ublock1](https://faq.mople71.cz/img/cs/ublock1.png)</li>
- Zde vyberte filtry pro blokování webového obsahu. Doporučuji kromě výchozích zvolit následující:</li>
<li style="list-style-type: none">![ublock2](https://faq.mople71.cz/img/cs/ublock2.png)</li>
<li style="list-style-type: none">![ublock3](https://faq.mople71.cz/img/cs/ublock3.png)</li>
<li style="list-style-type: none">![ublock4](https://faq.mople71.cz/img/cs/ublock4.png)</li>
<li style="list-style-type: none">![ublock5](https://faq.mople71.cz/img/cs/ublock5.png)</li>
- Následně v pravém horním rohu klikněte na tlačítko: ![ublock6](https://faq.mople71.cz/img/cs/ublock6.png)
- Přesuňte se na začátek stránky, zkontrolujte zatržítko u položky <span class="green">Automaticky aktualizovat seznamy filtrů</span> a klikněte na tlačítko <span class="green">Aktualizovat nyní</span>. Během aktualizace panel nezavírejte.
<li style="list-style-type: none">![ublock7](https://faq.mople71.cz/img/cs/ublock7.png)</li>

> Oddělení prohlížeče od OS a dat

Chromium používá špičkovou implementaci sandboxu.

<br>

<h3 id="win3.4" class="ff">![ff](https://mople71.cz/img/cs/ff.png) Mozilla Firefox</h3>

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
- Výše uvedeným způsobem vyhledejte a změňte výchozí nastavení následujících hodnot:
<li style="list-style-type: none"><pre><code>accessibility.blockautorefresh  ---  vypíná automatické přesměrování
browser.pocket.enabled  ---  vypíná službu Pocket
pdfjs.disabled  ---  vypne otevírání PDF v prohlížeči
security.mixed_content.block_display_content  ---  nezabezpečený obsah
security.ssl3.ecdhe_ecdsa_rc4_128_sha  ---  slabé šifrování
security.ssl3.ecdhe_rsa_rc4_128_sha  ---  slabé šifrování
security.ssl3.rsa_des_ede3_sha  ---  slabé šifrování
security.ssl3.rsa_rc4_128_md5  ---  slabé šifrování
security.ssl3.rsa_rc4_128_sha  ---  slabé šifrování

Volitelné hodnoty:
--------------------
dom.storage.enabled  ---  vypíná DOM úložiště (bezpečnější, ovšem může být
                                              vyžadováno některými službami)
media.peerconnection.enabled  ---  WebRTC</code></pre></li>
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
