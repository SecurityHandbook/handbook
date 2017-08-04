# FAQ &ndash; OS Android
Android je dominantní OS na mobilním trhu (>88% podíl) vyvíjený společností **Google, Inc.** Díky svému majoritnímu zastoupení se těší velké pozornosti hackerů.

Android má robustní bezpečnostní model, který předpokládá, že aplikace třetích stran běžící v OS nejsou důvěryhodné. Hlavním bezpečnostním problémem je rozmanitost zařízení, z nichž většina modelů nedostává pravidelné bezpečnostní aktualizace a běží na zastaralých verzích OS.

#### FAQ se dělí na několik sekcí:
- bezpečnostní model OS (teorie)
- obecné bezpečnostní rady
- bezpečná zařízení
- bezpečné nastavení OS
- doporučené aplikace
- bezpečné ROM

<br>

## Bezpečnostní model OS:
Android má robustní vícevrstevný bezpečnostní model. Používá linuxové jádro, implementuje <abbr title="Mandatory Access Control">MAC</abbr> a mitigace proti *memory corruption* exploitům &ndash; Android je jediná linuxová distribuce, která neumožňuje spuštění *non-<abbr title="Position Independent Executable">PIE</abbr>* kódu. Každé aplikaci je přiřazen unikátní uživatelský ID, aplikace je uzavřena v sandboxovaném prostředí, nemůže operovat s žádnou jinou aplikací a je jí umožněno operovat pouze se soubory/komponenty OS, ke kterým dostane oprávnění od vlastníka zařízení.

![Android Security Model](https://faq.mople71.cz/img/android.png)

> Trocha teorie o bezpečnostním modelu OS Android

#### Jádro:
Android je postaven na linuxovém jádru. Linuxové jádro Androidu z bezpečnostního hlediska nabízí slušný model oprávnění založený na uživatelích a uživatelských skupinách, izolaci procesů atd. V poslední době se vývojáři linuxového jádra začali více soustředit na zabezpečení samotného jádra, z čehož benefituje i Android.

#### MAC:
Android **Kitkat** a výše používá silně modifikovanou implementaci linuxového MAC *SELinux* &ndash; tzv. **SEAndroid**. SEAndroid výrazně snižuje prostor pro exploitaci. Také hraje roli v modelu oprávnění OS Android. Díky implementaci MAC nyní pouze velmi malá část kódu běží s plným root oprávněním.

#### Aplikace:
Android vyžaduje digitální podpis aplikací &ndash; nepodepsané aplikace nemohou být nainstalovány. Také implementuje několik bezpečnostních kontrolních bodů pro aplikace, díky kterým aplikaci vyhodnotí jako škodlivou a její instalaci odepře (tato funkce je závislá na službách Google). Ve výchozím nastavením lze také instalovat aplikace pouze z předinstalovaného obchodu aplikací &ndash; obvykle **Google Play**.

Veškeré aplikace jsou uzavřeny v sandboxu (*IsolatedProcess*), tudíž každá aplikace je izolovaná od ostatních aplikací a OS. Android také podporuje použití **seccomp** sandboxu, který nabízí pokročilejší možnosti izolace a vyšší míru bezpečnosti. Je využíván například aplikací Google Chrome.

Android **Marshmallow** a výše nabízí rozšířený model oprávnění &ndash; uživatel si může zvolit, k jakým komponentům/souborům bude mít daná aplikace přístup. Vestavěný správce oprávnění zatím není perfektní, jelikož neumožňuje nastavení všech důležitých oprávnění, ale funguje spolehlivě, což se nedá říci o správcích oprávnění třetích stran (např. XPrivacy).

Funkce závislé na službách Google (např. *VerifyApps*, *Google Play Protect*), zde nebudou rozebírány. Pro další informace o architektuře nahlédněte do návodu <a href="https://guide.mople71.cz/iot/andr_vyber.php" target="_blank">Výběr telefonu &ndash; OS Android</a>.

<br><br><hr><br>

## Obecné bezpečnostní rady:
- používejte aktuální záplatovanou verzi Androidu, minimálně **Marshmallow**
- nerootujte své zařízení &ndash; rootem rozbíjíte bezpečnostní model OS popsaný výše
- neodemykejte bootloader svého zařízení a neflashujte potenciálně nebezpečné recovery oddíly (např. TWRP)
- používejte stock Android s minimálním množstvím předinstalovaných aplikací od výrobce
- neflashujte nebezpečné ROM se špatnou root implementací (např. CM / Lineage OS)
- instalujte aplikace pouze z důvěryhodných zdrojů &ndash; Google Play, Amazon, F-Droid
- neinstalujte aplikace vyžadující nesmyslná oprávnění (např. Flashlight+++ vyžadující přístup k SMS a kontaktům)
- zvažte využívání open source aplikací (FOSS &ndash; free and open-source software
- nepřipojujte se k nedostatečné zabezpečeným sítím (např. v kavárně), zvažte použití VPN
- všechny rizikové činnosti provádějte pod uživatelem hosta
- šifrujte své zařízení, nezapomínejte na fyzické zabezpečení

### Bezpečnostní rady pro pokročilé:
- nerootujte a už vůbec root oprávnění neposkytujte aplikacím, rozbíjíte tím velmi solidní bezpečnostní model OS a výrazně tím zvyšujete prostor pro exploitaci &ndash; škodlivá aplikace, která úspěšně provede exploitaci jiné aplikace běžící s root oprávněním, získává plná root oprávnění, která ve stock Androidu má pouze drobná část kódu
- používejte aktualizované ROM bez bloatware od výrobce
- neflashujte do ROM nic typu Open GApps &ndash; je to řádově méně bezpečné než správná integrace služeb Google výrobcem
- kompilujte ROM (+ jádro) a aplikaci sami, ošklivá oprávnění aplikací poté můžete zakázat přímo v AndroidManifest.xml

<br><br><hr><br>

## Bezpečná zařízení:
Jak již bylo zmíněno, rozmanitost zařízení s OS Android je možná z jistého úhlu výhoda, ovšem z pohledu bezpečnosti velký problém.

V dnešní době není problém pořídit si telefon s OS Android za velmi malou finanční částku. Co již ovšem nikdo neřeší, je podpora a aktualizace. Většina levných zařízení se nikdy nedočkají žádné bezpečnostní aktualizace, natož pak aktualizace na nejnovější verzi OS. Tato zařízení mohou obsahovat stovky známých bezpečnostních děr, které se lehce dají zneužít, pokud zařízení není záplatováno výrobcem. Situace ovšem nemusí být o nic lepší u dražších modelů.

Níže naleznete několik bodů, které by mělo zařízení splňovat, aby se dalo nazvat bezpečným. Také zde naleznete seznam modelů, které zmíněné požadavky splňují.

### Bezpečnostní požadavky na zařízení s OS Android:
- 64-bit architektura (x86/ARM)
- jádro > 3.18 (ideálně 4.4)
- full verified boot (ideálně i pro custom ROM)
- časté (ideálně měsíční) bezpečnostní aktualizace pro firmware a proprietární komponenty
- garance bezpečnostních aktualizací po dobu morální životnosti modelu (min. 1 rok od koupi)

<br>

### Zařízení s OS Android splňující bezpečnostní požadavky:

Seznam zařízení naleznete v návodu <a href="https://guide.mople71.cz/iot/andr_vyber.php#vyber2" target="_blank">Výběr telefonu &ndash; OS Android</a>.

<br><br><hr><br>

## Bezpečné nastavení OS:
Android je bezpečně nastaven již v základu, není ovšem od věci podívat se do nastavení a zkontrolovat jej.

> Kontrola korektního nastavení OS Android

- Otevřete si aplikaci <span class="green">Nastavení</span>.
- Nalezněte podkategorii **Zabezpečení** a otevřete ji.
- Nemáte-li, nastavte si <span class="green">zámek obrazovky</span>. Ověřte konfiguraci zabezpečení, případně opravte.
<li style="list-style-type: none">![andset](https://faq.mople71.cz/img/cs/andset.png)</li>
- Aplikaci zavřete.

> Kontrola aktuálního OS

- Otevřete si aplikaci <span class="green">Nastavení</span>.
- Nalezněte podkategorii **Informace o telefonu** a otevřete ji.
- Zkontrolujte, zdali máte aktuální **verzi systému Android** &ndash; **7.1.2** a **8.0**.
- Zkontrolujte, zdali máte nejnovější **úroveň opravy zabezpečení Android**.
<li style="list-style-type: none">![andinf](https://faq.mople71.cz/img/cs/andinf.png)</li>
- Máte-li starší *verzi systému Android* než **7.1.1**, telefon není implicitně bezpečný &ndash; můžete se dívat po náhradě. Máte-li starší *úroveň opravy zabezpečení Android* nežli **5. července 2017** (a k nápravě nedojde do konce září), telefon je nebezpečný &ndash; můžete se dívat po náhradě.
- Více informací o této problematice naleznete v návodu <a href="https://guide.mople71.cz/iot/andr_vyber.php" target="_blank">Výběr telefonu &ndash; OS Android</a>.
- Aplikaci zavřete.

<br>

### Využití účtu hosta:
Pod uživatelem hosta můžete relativně bezpečně např. prohlížet rizikové internetové stránky. Instalaci pochybných aplikací nedoporučuji ani pod uživatelem hosta, jelikož aplikace může OS exploitovat mnohem snadněji než internetová stránka. Pokud by aplikace úspěšně získala root pravomoce (např. pomocí *CVE-2015-1805* aka KingRoot), nepomůže vám ani reset zařízení do továrního nastavení.

> Přepnutí se na účet hosta

- Stáhněte dolů notifikační lištu dvěma prsty, případně ji rozšiřte kliknutím na šipku v pravém horním rohu.
- V pravé horní liště klikněte na obrázek svého uživatelského účtu.
- Zobrazí se seznam uživatelských účtů. Klikněte na tlačítko <span class="green">Přidat hosta</span>.
<li style="list-style-type: none">![andg](https://faq.mople71.cz/img/cs/andg.png)</li>
- Budete automaticky přepnuti na uživatele hosta.
- Jakmile z účtu hosta budete chtít odejít, stáhněte notifikační lištu a klikněte na tlačítko <span class="green">Odstranit hosta</span>.
<li style="list-style-type: none">![andg2](https://faq.mople71.cz/img/cs/andg2.png)</li>
- Odstranění potvrďte.

<br><br><hr><br>

## Doporučené aplikace:
V následující sekci naleznete doporučené bezpečnostní aplikace a aplikace s bezpečností úzce související. Aplikace jsou děleny na FOSS (free and open source) a poprietární. Důvod je prostý: někteří lidé nevěří proprietárním aplikacím a používání bezpečnostní aplikace s uzavřeným kódem, považují za nepřijatelné.

### Obchod s aplikacemi:
Obchod s aplikacemi velmi úzce souvisí s bezpečností, jelikož z něj stahujete a instalujete veškeré aplikace do OS. Z tohoto důvodu musí být důvěryhodný a bezpečný.

#### FOSS:
- F-Droid: <a href="https://f-droid.org/" target="_blank">https://f-droid.org/</a>

#### Proprietární:
- Google Play: <a href="https://play.google.com/" target="_blank">https://play.google.com/</a>
- Amazon: <a href="https://www.amazon.com/appstore" target="_blank">https://www.amazon.com/appstore</a>

*Amazon* má zdlouhavý proces kontroly aplikací (jsou kontrolovány manuálně), proto má témeř vždy zastaralé verze aplikací, zvláště těch, které jsou často aktualizovány.

<br>

### Firewall:
Firewall je velmi důležitá bezpečnostní vrstva OS, která poskytuje ochranu před síťovými útoky. Na veřejných WiFi připojeních je prakticky nutností.

Nejlepší volbou je integrovaný FW, bohužel jej prakticky žádná ROM nenabízí. Znásilnění VPN API (NetGuard, NoRoot Data Firewall) není nejlepší a nejspolehlivější implementace FW, ale alespoň nevyžaduje destrukci bezpečnostního modelu OS. Bohužel, vypadá to, že pouze velmi málo lidí má zájem implementovat tyto věci správně &ndash; přímo do OS.

#### FOSS:
- integrovaný (CopperheadOS)
- NetGuard (VPN): <a href="https://github.com/M66B/NetGuard" target="_blank">https://github.com/M66B/NetGuard</a>

#### Proprietární:
- NoRoot Data Firewall (VPN): <a href="https://play.google.com/store/apps/details?id=com.jianjia.firewall" target="_blank">https://play.google.com/store/apps/details?id=com.jianjia.firewall</a>

<br>

### Blokování reklamy:
Blokování reklamy je z hlediska bezpečnosti esenciální kvůli četnému výskytu škodlivých reklam na internetu. Doporučuji oblíbené stránky podporovat jinou bezpečnější &ndash; finanční &ndash; formou.

#### FOSS lokální VPN:
- DNS66: <a href="https://github.com/julian-klode/dns66" target="_blank">https://github.com/julian-klode/dns66</a>

#### Proprietární lokální VPN:
- Adguard: <a href="https://adguard.com/en/adguard-android/overview.html" target="_blank">https://adguard.com/en/adguard-android/overview.html</a>

#### VPN:
- Freedome: <a href="https://play.google.com/store/apps/details?id=com.fsecure.freedome.vpn.security.privacy.android" target="_blank">https://play.google.com/store/apps/details?id=com.fsecure.freedome.vpn.security.privacy.android</a>

#### Internetový prohlížeč:
- Google Chrome / Chromium
- Brave: <a href="https://play.google.com/store/apps/details?id=com.brave.browser" target="_blank">https://play.google.com/store/apps/details?id=com.brave.browser</a>
- atd.

#### DNS:</h3>
- Adguard DNS: <a href="https://adguard.com/en/adguard-dns/overview.html" target="_blank">https://adguard.com/en/adguard-dns/overview.html</a>
- NoAd: <a href="https://noad.zone" target="_blank">https://noad.zone</a>

DNS je jednoduchý způsob blokace reklam, vyžaduje to ovšem důvěru v poskytovatele DNS. Použití prohlížeče blokující reklamy je nejlepším řešením. *Chrome(ium)* od verze 62 umožní nativně blokovat agresivní reklamy nesplňující podmínky. VPN je také dobrý způsob, ovšem implementace OpenVPN na Androidu není 100% ideální.

<br>

### Správce oprávnění:
Správce oprávnění umožňuje nastavit, k jakým informacím a komponentům má konkrétní aplikace přístup. Jedná se více o záležitost soukromí než bezpečnosti.

#### FOSS:
- integrovaný (Marshmallow a výše)

> Využití vestavěného správce oprávnění

- Otevřete si aplikaci <span class="green">Nastavení</span>.
- Nalezněte podkategorii **Aplikace** a otevřete ji.
- V pravém horním rohu klikněte na <span class="green">ozubené kolo</span>.
<li style="list-style-type: none">![andapp](https://faq.mople71.cz/img/cs/andapp.png)</li>
- Klikněte na <span class="green">Oprávnění aplikací</span>.
- Otevřete postupně všechny kategorie a zakažte všem aplikacím nepotřebný přístup.
<li style="list-style-type: none">![andapp1](https://faq.mople71.cz/img/cs/andapp1.png)</li>
<li style="list-style-type: none">![andapp2](https://faq.mople71.cz/img/cs/andapp2.png)</li>
- Po dokončení nastavení oprávnění se z kategorie **Oprávnění aplikací** přesuňte o úroveň výše a otevřete si <span class="green">Speciální přístup</span>.
- Zde můžete nastavit např. které aplikace mají přístup k prémiovým SMS nebo mohou na pozadí neomezeně používat mobilní data.
<li style="list-style-type: none">![andapp3](https://faq.mople71.cz/img/cs/andapp3.png)</li>
- Aplikaci zavřete.

<br>

<span class="red">XPrivacy</span>. Když pominu, že všechno využívající Xposed je hack a není korektně implementováno do OS, XPrivacy je nefunkční a nedoporučená varianta.

> Technické informace o XPrivacy

XPrivacy primárně nahrazuje Java API novým kódem a často pouze kódem strany klienta &ndash; většina dat může být stále získána. Například skrývá sériové číslo v Java system property API (<a href="https://github.com/M66B/XPrivacy/blob/master/src/biz/bokhorst/xprivacy/XSystemProperties.java" target="_blank">link</a>). Sériové číslo je ovšem stále přístupné nativnímu kódu, případně Java kódu používajícímu jiné rozhraní pro přístup. Tímto způsobem evidentně (ne)funguje větší část XPrivacy.

Mít bezpečnostní aplikaci, kterou lze obejít i bez exploitace, moc nemá smysl. ![wink](https://mople71.cz/img/sm/wink.gif)

<br>

### Internetový prohlížeč:
Chrome(ium) je prohlížeč s nejkvalitnějšími mitigacemi proti exploitům na Linuxu &ndash; tedy i na Androidu. Prohlížeče založené na Mozilla Firefox jsou několik let za Chromium v oblasti mitigací proti exploitům, na Androidu je situace ovšem méně kritická než na desktopových OS.

![Bezpečnostní model Chromium](https://faq.mople71.cz/img/en/chmandr.png)

#### FOSS:
- Chromium: <a href="https://www.chromium.org/developers/how-tos/android-build-instructions" target="_blank">https://www.chromium.org/developers/how-tos/android-build-instructions</a>  <a href="https://play.google.com/store/apps/details?id=com.anddevw.getchromium" target="_blank">https://play.google.com/store/apps/details?id=com.anddevw.getchromium</a>
- Brave: <a href="https://play.google.com/store/apps/details?id=com.brave.browser" target="_blank">https://play.google.com/store/apps/details?id=com.brave.browser</a>

#### Proprietární:
- Google Chrome: <a href="https://play.google.com/store/apps/details?id=com.android.chrome" target="_blank">https://play.google.com/store/apps/details?id=com.android.chrome</a>

> Omezení JavaScriptu v Google Chrome / Chromium

- Otevřete si aplikaci <span class="green">Google Chrome</span> / <span class="green">Chromium</span>.
- Kliknutím na tři tečky v horním pravém rohu otevřete boční panel a klikněte na tlačítko <span class="green">Nastavení</span>.
- Klikněte na **Nastavení webu** a Otevřete podkategorii <span class="green">JavaScript</span>.
- Zablokujte spouštění JS.
<li style="list-style-type: none">![chmandrjs](https://faq.mople71.cz/img/cs/chmandrjs.png)</li>
- Klikněte na tlačítko <span class="green">Přidat výjimku pro konkrétní web</span>.
- Zadejte adresu důvěryhodnéhu webu, na kterém se může spouštět JS. Syntax je oproti desktopové verzi značně omezený.
<li style="list-style-type: none">![chmandrjs1](https://faq.mople71.cz/img/cs/chmandrjs1.png)</li>
- Klikněte na <span class="green">Přidat</span>.

<br><br><hr><br>

## Bezpečné ROM:
Seznam je řazen od nejbezpečnější po nejméně bezpečnou.

- CopperheadOS: <a href="https://copperhead.co/android/" target="_blank">https://copperhead.co/android/</a>
- UnaOS*: <a href="https://unaos.com/os.html" target="_blank">https://unaos.com/os.html</a>
- Silent OS*: <a href="https://www.silentcircle.com/products-and-solutions/devices/silent-os/" target="_blank">https://www.silentcircle.com/products-and-solutions/devices/silent-os/</a>
- Blackberry Android*: <a href="http://ca.blackberry.com/software/smartphones/android.html" target="_blank">http://ca.blackberry.com/software/smartphones/android.html</a>
- čistý Android &ndash; Nexus / Pixel
- Android předinstalovaný výrobcem bez zbytečného nízko-úrovňového bloatware
- Android předinstalovaný výrobcem s bloatware od výrobce
- custom ROM bez root implementace
- ...

\* tyto ROM byly v době psaní FAQ postavené na **Marshmallow**, který je v ohledu bezpečnosti o úroveň níže než **Nougat**, po aktualizaci všech ROM na Nougat bude seznam 100% platný

<br><br><hr>

<h3 class="nocol">To je vše. Stay safe! ![smile](https://mople71.cz/img/sm/smile.gif)</h3>
