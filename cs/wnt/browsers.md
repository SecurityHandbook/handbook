<h3 id="win3.1" class="ch">![ch](https://mople71.cz/cs/ch16.png) Google Chrome</h3>

> Bezpečnější nastavení

- Do adresního řádku prohlížeče zadejte:
<li style="list-style-type: none"><pre><code>chrome://plugins</code></pre>
a stiskněte **Enter**.</li>
- Zobrazí se seznam rozšíření. V seznamu nalezněte **Adobe Flash Player** a deaktivujte jej.
<li style="list-style-type: none">![ch1](https://mople71.cz/faq/ch1.png)</li>
- Do adresního řádku prohlížeče zadejte:
<li style="list-style-type: none"><pre><code>chrome://settings</code></pre>
a stiskněte **Enter**.</li>
- Zobrazí se nastavení. Sjeďte na konec stránky a klikněte na tlačítko <span class="green">Zobrazit rozšířená nastavení...</span>
- V sekci **Ochrana soukromí** klikněte na tlačítko <span class="green">Nastavení obsahu...</span>
- V sekci **Soubory cookie** zatrhněte možnost <span class="green">Blokovat soubory cookie třetích stran a data webových stránek</span>.
<li style="list-style-type: none">![ch2](https://mople71.cz/faq/ch2.png)</li>
- V pravém dolním rohu klikněte na <span class="green">Hotovo</span>.
- Prohlížeč restartujte.

#### Pro Windows 8 a výše:
- Do adresního řádku prohlížeče zadejte:
<li style="list-style-type: none"><pre><code>chrome://flags/#enable-ppapi-win32k-lockdown</code></pre>
a stiskněte **Enter**.</li>
- Zobrazí se pokročilá nastavení. Rozklikněte nabídku u položky **Aktivovat uzamknutí pluginů PPAPI pole zásady Win32k** a zvolte možnost <span class="green">Všechny pluginy</span>.
- Rozklikněte nabídku u položky **Aktivovat uzamknutí do kontejneru AppContainer** a zvolte možnost <span class="green">Aktivní</span>.
<li style="list-style-type: none">![ch3](https://mople71.cz/faq/ch3.png)</li>
- Prohlížeč restartujte.


> Blokování reklamy

- Nainstalujte si následující bezpečnostní doplněk: <a href="https://chrome.google.com/webstore/detail/ublock-origin/cjpalhdlnbpafiamejdnhcphjbkeiagm?hl=cs" target="_blank">uBlock Origin</a>.

#### Nastavení uBlock:

- Klikněte na ikonu uBlock v panelu ikon a následně klikněte na nápis <span class="green">uBlock Origin</span>.
<li style="list-style-type: none">![chublock](https://mople71.cz/faq/chublock.png)</li>
- Zobrazí se nastavení uBlock Origin. V sekci **Soukromí** zatrhněte možnost <span class="green">Předejít úniku lokálních IP adres přes WebRTC</span>.
- Následně se přesuňte do záložky <span class="green">Filtry třetích stran</span>.
<li style="list-style-type: none">![ublock1](https://mople71.cz/faq/ublock1.png)</li>
- Zde vyberte filtry pro blokování webového obsahu. Doporučuji kromě výchozích zvolit následující:</li>
<li style="list-style-type: none">![ublock2](https://mople71.cz/faq/ublock2.png)</li>
<li style="list-style-type: none">![ublock3](https://mople71.cz/faq/ublock3.png)</li>
<li style="list-style-type: none">![ublock4](https://mople71.cz/faq/ublock4.png)</li>
<li style="list-style-type: none">![ublock5](https://mople71.cz/faq/ublock5.png)</li>
- Následně v pravém horním rohu klikněte na tlačítko: ![ublock6](https://mople71.cz/faq/ublock6.png)
- Přesuňte se na začátek stránky, zkontrolujte zatržítko u položky <span class="green">Automaticky aktualizovat seznamy filtrů</span> a klikněte na tlačítko <span class="green">Aktualizovat nyní</span>. Během aktualizace panel nezavírejte.
<li style="list-style-type: none">![ublock7](https://mople71.cz/faq/ublock7.png)</li>


> Oddělení prohlížeče od OS a dat

Google Chrome používá velmi dobrou implementaci sandboxu.

<br>

<h3 id="win3.2" class="ed">![edge](https://mople71.cz/win/edge16.png) Microsoft Edge</h3>

> Blokování reklamy (AdBlock)

- Otevřete prohlížeč, v pravém horním rohu klikněte na ikonu tří teček a klikněte na tlačítko <span class="green">Rozšíření</span>.
- Klikněte na tlačítko <span class="green">Získat rozšíření ze Storu</span>.
<li style="list-style-type: none">![edge2](https://mople71.cz/faq/edge2.png)</li>
- Otevře se obchod s aplikacemi na stránce s dostupnými doplňky. V seznamu doplňků nalezněte doplněk <span class="green">Adblock Plus</span> a nainstalujte jej.
- Restartujte prohlížeč.
- V pravém horním rohu se zobrazí vyskakovací okno o novém rozšíření. Zvolte možnost <span class="green">Zapnout</span>.
<li style="list-style-type: none">![edge3](https://mople71.cz/faq/edge3.png)</li>
- Zobrazí se stránka o úspěšné instalaci Adblock Plus. Sjeďte úplně dolů a zapněte <span class="green">Blokování malware</span>, případně i zbylé možnosti.
- V pravém horním prohlížeče rohu klikněte na ikonu tří teček a klikněte na tlačítko <span class="green">Adblock Plus</span>.
- Zobrazí se panel Adblock Plus. Klikněte na tlačítko <span class="green">Možnosti</span>.
- V možnostech klikněte na tlačítko <span class="green">Přidat cizí filtry</span>.
- Rozklikněte seznam filtrů a vyberte **EasyList Czech and Slovak+EasyList**.
<li style="list-style-type: none">![edge4](https://mople71.cz/faq/edge4.png)</li>
- Klikněte na tlačítko <span class="green">Přidat</span>.


> Blokování reklamy pro pokročilejší (uBlock)

- Otevřete v prohlížeči <a href="https://github.com/nikrolls/uBlock-Edge/releases" target="_blank">následující stránku</a>.
- Stáhněte si nejnovější verzi <span class="green">uBlock Origin</span>. Doporučena je stabilní a **rc** verze. Užití beta verze zvažte.
- Ze staženého archivu vybalte složku <span class="blue">uBlock0.edge</span> a přesuňte ji do své složky <span class="green">Dokumenty</span>. Pro používání uBlock Origin ji nesmíte odstranit.
- Do adresního řádku prohlížeče zadejte:
<li style="list-style-type: none"><pre><code>about:flags</code></pre>
a stiskněte **Enter**.</li>
- Aktivujte <span class="green">funkce pro vývojáře rozšíření</span>.
<li style="list-style-type: none">![edge5](https://mople71.cz/faq/edge5.png)</li>
- Restartujte prohlížeč.
- V pravém horním rohu klikněte na ikonu tří teček a klikněte na tlačítko <span class="green">Rozšíření</span>.
- Zvolte možnost <span class="green">Načíst rozšíření</span> a vyberte složku **uBlock0.edge**.

#### Nastavení uBlock:
- Klikněte na ikonu <span class="green">uBlock Origin</span> v panelu ikon a následně klikněte na nápis <span class="green">uBlock Origin</span>.
<li style="list-style-type: none">![edublock](https://mople71.cz/faq/edublock.png)</li>
- Zobrazí se nastavení uBlock Origin. V sekci **Soukromí** zatrhněte možnost <span class="green">Předejít úniku lokálních IP adres přes WebRTC</span>.
- Následně se přesuňte do záložky <span class="green">Filtry třetích stran</span>.
<li style="list-style-type: none">![ublock1](https://mople71.cz/faq/ublock1.png)</li>
- Zde vyberte filtry pro blokování webového obsahu. Doporučuji kromě výchozích zvolit následující:</li>
<li style="list-style-type: none">![ublock2](https://mople71.cz/faq/ublock2.png)</li>
<li style="list-style-type: none">![ublock3](https://mople71.cz/faq/ublock3.png)</li>
<li style="list-style-type: none">![ublock4](https://mople71.cz/faq/ublock4.png)</li>
<li style="list-style-type: none">![ublock5](https://mople71.cz/faq/ublock5.png)</li>
- Následně v pravém horním rohu klikněte na tlačítko: ![ublock6](https://mople71.cz/faq/ublock6.png)
- Přesuňte se na začátek stránky, zkontrolujte zatržítko u položky <span class="green">Automaticky aktualizovat seznamy filtrů</span> a klikněte na tlačítko <span class="green">Aktualizovat nyní</span>. Během aktualizace panel nezavírejte.
<li style="list-style-type: none">![ublock7](https://mople71.cz/faq/ublock7.png)</li>


> Oddělení prohlížeče od OS a dat

Microsoft Edge nyní používá velmi robustní implementaci sandboxu.

<br>

<h3 id="win3.3" class="ie">![ie](https://mople71.cz/win/ie16.png) Internet Explorer</h3>

> Bezpečnější nastavení

- Stiskněte kláv. zkratku ![win](https://mople71.cz/cs/wkey.png) <span class="ks">+ R</span>, do textového pole zadejte:
<li style="list-style-type: none"><pre><code>inetcpl.cpl</code></pre>
a stiskněte **Enter**.</li>
- Zobrazí se Vlastnosti internetu. V horní liště se přesuňte do záložky <span class="green">Zabezpečení</span>.
- Zobrazí se nastavení úrovně zabezpečení internetových zón.
<li style="list-style-type: none">![ie0](https://mople71.cz/faq/ie.png)</li>
- V zóně **Internet** se ujistěte, že má nastavenou výchozí úroveň zabezpečení. Pokud nemá, klikněte na tlačítko <span class="green">Výchozí úroveň</span>, čímž nastavení opravíte.
- Přesuňte se do zóny **Místní intranet** a upravte její úroveň zabezpečení dle obrázku:
<li style="list-style-type: none">![ie1](https://mople71.cz/faq/ie1.png)</li>
- Stejným způsobem upravte úroveň zabezpečení zóny **Důvěryhodné weby**.
- V horní liště se přesuňte do záložky <span class="green">Osobní údaje</span>, případně napravte.
- Nastavení upravte na 3. nebo 2. nejvyšší možnost (<span class="green">Vyšší</span> nebo <span class="green">Vysoká</span>).
<li style="list-style-type: none">![ie2](https://mople71.cz/faq/ie2.png)</li>
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
<li style="list-style-type: none">![ie3](https://mople71.cz/faq/ie3.png)</li>


> Blokování reklamy

- Otevřete v IE <a href="http://dayngo.com/static/filter.html" target="_blank">následující stránku</a>.
- Zobrazí se seznam filtrů pro Tracking Protection (vestavěný blokátor nejen reklam).
- Ze seznamu doporučuji přidat filtry <span class="green">EasyList</span>, <span class="green">EasyList Czech and Slovak</span> a <span class="green">EasyPrivacy</span>.

#### Přidání filtru pro Tracking Protection:
- Klikněte na takto vypadající odkaz: ![tp](https://mople71.cz/win/tp1.png)
- V zobrazeném vyskakovacím okně klikněte na tlačítko <span class="green">Přidat seznam</span>.

Další český filtr naleznete např. <a href="http://adblock.dajbych.net/">zde</a>.


> Oddělení prohlížeče od OS a dat

Prohlížeč je částečně oddělen od OS díky technologii **Protected Mode**. Jedná se o relativně spolehlivou metodu.

<br>

<h3 id="win3.4" class="ff">![ff](https://mople71.cz/cs/ff.png) Mozilla Firefox</h3>

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
<li style="list-style-type: none">![ff0](https://mople71.cz/faq/ff.png)</li>
<li style="list-style-type: none"![ff1](https://mople71.cz/faq/ff1.png)</li>
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
<li style="list-style-type: none">![ff2](https://mople71.cz/faq/ff2.png)</li>


> Blokování reklamy

- Nainstalujte si následující bezpečnostní doplněk: <a href="https://addons.mozilla.org/cs/firefox/addon/ublock-origin/" target="_blank">uBlock Origin</a>.</li>

#### Nastavení uBlock:
- Klikněte na ikonu uBlock v panelu ikon a následně klikněte na nápis <span class="green">uBlock Origin</span>.
<li style="list-style-type: none">![ublock](https://mople71.cz/faq/ublock.png)</li>
- Zobrazí se nastavení uBlock Origin. V sekci **Soukromí** zatrhněte možnost <span class="green">Předejít úniku lokálních IP adres přes WebRTC</span>.
- Následně se přesuňte do záložky <span class="green">Filtry třetích stran</span>.
<li style="list-style-type: none">![ublock1](https://mople71.cz/faq/ublock1.png)</li>
- Zde vyberte filtry pro blokování webového obsahu. Doporučuji kromě výchozích zvolit následující:</li>
<li style="list-style-type: none">![ublock2](https://mople71.cz/faq/ublock2.png)</li>
<li style="list-style-type: none">![ublock3](https://mople71.cz/faq/ublock3.png)</li>
<li style="list-style-type: none">![ublock4](https://mople71.cz/faq/ublock4.png)</li>
<li style="list-style-type: none">![ublock5](https://mople71.cz/faq/ublock5.png)</li>
- Následně v pravém horním rohu klikněte na tlačítko: ![ublock6](https://mople71.cz/faq/ublock6.png)
- Přesuňte se na začátek stránky, zkontrolujte zatržítko u položky <span class="green">Automaticky aktualizovat seznamy filtrů</span> a klikněte na tlačítko <span class="green">Aktualizovat nyní</span>. Během aktualizace panel nezavírejte.
<li style="list-style-type: none">![ublock7](https://mople71.cz/faq/ublock7.png)</li>


> Oddělení prohlížeče od OS a dat

Možno využít libovolný externí způsob, prohlížeč zatím nemá žádný integrovaný.
