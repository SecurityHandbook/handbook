<h3 class="chm">![chm](https://mople71.cz/img/icons/chm16.ico) Chromium:</h3>

> Instalace

- Otevřete si <span class="green">Terminál</span>. Zadejte do něj následující příkazy:
<li style="list-style-type: none"><pre><code>sudo dnf install -y chromium
exit</code></pre></li>

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

Chromium používá špičkovou implementaci sandboxu.

<br>

<h3 class="brv">![brv](https://mople71.cz/img/icons/brv.png) Brave</h3>

> Instalace

<div class="alert info"><p><em class="icon-info-circled"></em>**Info**<br>
Níže uvedený postup je platný pro distribuci **<span class="fe">Fedora</span>**. Používáte-li jinou distribuci, návod k instalaci naleznete [zde](https://brave-browser.readthedocs.io/en/latest/installing-brave.html#release-channel-installation).</p></div>

- Otevřete si <span class="green">Terminál</span>. Zadejte do něj následující příkazy:
<li style="list-style-type: none"><pre><code>sudo -i
dnf config-manager --add-repo https://brave-browser-rpm-release.s3.brave.com/x86_64/
rpm --import https://brave-browser-rpm-release.s3.brave.com/brave-core.asc
dnf install -y brave-browser brave-keyring
exit
exit</code></pre></li>

> Bezpečnější nastavení

- Do adresního řádku prohlížeče zadejte:
<li style="list-style-type: none"><pre><code>chrome://settings</code></pre>
a stiskněte **Enter**.</li>
- Zobrazí se nastavení. V sekci **Brave shields defaults** zkontrolujte konfiguraci a případně opravte:
 <li style="list-style-type: none">![brv](https://faq.mople71.cz/img/en/brv.png)</li>
- Sjeďte na konec stránky a klikněte na tlačítko ![ch](https://faq.mople71.cz/img/cs/ch.png)
- V sekci **Ochrana soukromí** klikněte na tlačítko <span class="green">Nastavení obsahu...</span>
<li style="list-style-type: none">![ch1](https://faq.mople71.cz/img/cs/ch1.png)</li>
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
- Zobrazí se nastavení. V sekci **Brave shields defaults** upravte konfiguraci dle obrázku:
 <li style="list-style-type: none">![brv1](https://faq.mople71.cz/img/en/brv1.png)</li>
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

Brave používá velmi dobrou implementaci sandboxu.

<br>

<h3 class="epiph">![epiph](https://mople71.cz/img/icons/epiph.png) GNOME Web:</h3>

> Instalace

- Otevřete si <span class="green">Terminál</span>. Zadejte do něj následující příkazy:
<li style="list-style-type: none"><pre><code>sudo dnf install -y epiphany
exit</code></pre></li>

>  Bezpečnější nastavení

- Rozklikněte nabídku v kontextovém menu a otevřete <span class="green">Předvolby</span>.
<li style="list-style-type: none">![epiph](https://faq.mople71.cz/img/cs/epiph.png)</li>
- V sekci **Obsah WWW** zatrhněte možnost <span class="green">Blokovat vyskakovací okna</span> a <span style="color: #BF0000">odstraňte</span> zatržítko u možnosti <span class="green">Povolit zásuvné moduly</span>.
<li style="list-style-type: none">![epiph1](https://faq.mople71.cz/img/cs/epiph1.png)</li>
- Přesuňte se do záložky **Uchovaná data** a v sekci **Cookies** zvolte možnost <span class="green">Jen ze serverů, které navštěvujete</span>.
<li style="list-style-type: none">![epiph2](https://faq.mople71.cz/img/cs/epiph2.png)</li>

> Blokování reklamy

Prohlížeč má vestavěný blokátor reklam se základními filtry.

> Oddělení prohlížeče od OS a dat

Epiphany podporuje flatpak sandbox. Lepší, nežli žádný.

<br>

<h3 class="ff">![ff](https://mople71.cz/img/icons/ff.png) Mozilla Firefox</h3>

> Instalace

- Otevřete si <span class="green">Terminál</span>. Zadejte do něj následující příkazy:
<li style="list-style-type: none"><pre><code>sudo dnf install -y firefox
exit</code></pre></li>

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

Sandbox Firefoxu je v aktivním vývoji a již nyní je v celkem použitelném stavu. Využití Flatpak sandboxu proto není nutné ani rozumné.
