# FAQ &ndash; OS Android
Android je dominantní OS na mobilním trhu (>88% podíl) vyvíjený společností **Google, Inc.** Díky svému majoritnímu zastoupení se těší velké pozornosti hackerů.

Android má robustní bezpečnostní model, který předpokládá, že aplikace třetích stran běžící v OS, nejsou důvěryhodné. Hlavním bezpečnostním problémem je rozmanitost zařízení, z nichž většina modelů nedostává pravidelné bezpečnostní aktualizace a/nebo běží na zastaralých verzích OS.

> Trocha teorie o bezpečnostním modelu OS Android

## Bezpečnostní model OS:
Android má robustní vícevrstevný bezpečnostní model. Používá linuxové jádro, implementuje <abbr title="Mandatory Access Control">MAC</abbr> a mitigace proti *memory corruption* exploitům &ndash; Android je jediná linuxová distribuce, která neumožňuje spuštění *non-<abbr title="Position Independent Executable">PIE</abbr>* kódu. Každé aplikaci je přiřazen unikátní uživatelský ID, aplikace je uzavřena v sandboxovaném prostředí, nemůže operovat s žádnou jinou aplikací a je jí umožněno operovat pouze se soubory/komponenty OS, ke kterým dostane oprávnění od vlastníka zařízení.

![Android Security Model](https://faq.mople71.cz/img/en/and.png)
<p class="imgsrcf">*The Android security model (upraveno).* Zdroj: [Android Security 2015 Annual Report](http://source.android.com/security/reports/Google_Android_Security_2015_Report_Final.pdf)</p>

#### Jádro:
Android je postaven na linuxovém jádru. Linuxové jádro není nejbezpečnější jádro na trhu, Androidu ovšem z bezpečnostního hlediska nabízí slušný model oprávnění založený na uživatelích a uživatelských skupinách, izolaci procesů atd. V poslední době se vývojáři linuxového jádra začali více soustředit na zabezpečení samotného jádra, z čehož benefituje i OS Android.

#### MAC:
Android **Kitkat** a výše používá silně modifikovanou implementaci linuxového MAC **SELinux** &ndash; tzv. *SEAndroid*. SEAndroid výrazně snižuje prostor pro exploitaci. Také hraje roli v modelu oprávnění OS Android. Díky implementaci MAC nyní pouze velmi malá část kódu běží s plným root oprávněním. Výrazná zlepšení z pohledu MAC byla představena ve verzích **Lollipop** a **Oreo**.

#### Aplikace:
Android vyžaduje digitální podpis aplikací &ndash; nepodepsané aplikace nemohou být nainstalovány. Také implementuje několik bezpečnostních kontrolních bodů pro aplikace, díky kterým aplikaci může vyhodnotit jako škodlivou a její instalaci odepře (tato funkce je závislá na službách Google). Ve výchozím nastavením lze také instalovat aplikace pouze z předinstalovaného obchodu aplikací &ndash; obvykle **Google Play**.

Veškeré aplikace jsou uzavřeny v sandboxu (*IsolatedProcess*), tudíž každá aplikace je izolovaná od ostatních aplikací a OS. Android implementuje **seccomp** sandbox, který nabízí pokročilejší možnosti izolace a vyšší míru bezpečnosti. Interně je využíván například aplikací *Google Chrome*.

Android **Marshmallow** a výše nabízí rozšířený model oprávnění &ndash; uživatel si může zvolit, k jakým komponentům/souborům bude mít daná aplikace přístup. Vestavěný správce oprávnění zatím není perfektní, jelikož neumožňuje nastavení všech důležitých oprávnění, ale funguje spolehlivě, což se nedá říci o správcích oprávnění třetích stran (např. *XPrivacy*).

Funkce závislé na službách Google (např. *VerifyApps*, *Google Play Protect*), zde nebudou rozebírány.

#### FAQ se dělí na několik sekcí:
- Obecné bezpečnostní zásady
- Bezpečná zařízení
- Bezpečné nastavení OS
- Doporučené aplikace

<br>

## Obecné bezpečnostní zásady:
- používejte aktuální záplatovanou verzi OS, minimálně **Oreo**
- nerootujte své zařízení &ndash; rootem rozbíjíte bezpečnostní model OS
- neodemykejte bootloader svého zařízení &ndash; vystavujete se riziku krádeže dat
- neflashujte nebezpečné ROM se špatnou root implementací (např. *LineageOS*)
- instalujte aplikace pouze z důvěryhodných zdrojů &ndash; Google Play, F-Droid,&#8230;
- neinstalujte aplikace vyžadující nesmyslná oprávnění (např. Flashlight+ vyžadující přístup k SMS a kontaktům)
- zvažte využívání open source aplikací
- všechny rizikové činnosti provádějte pod účtem hosta
- zamykejte své zařízení

### Bezpečnostní tipy pro pokročilé:
- používejte aktualizované ROM bez bloatware od výrobce
- neflashujte nic typu *Open GApps* &ndash; je to řádově méně bezpečné než korektní integrace služeb Google výrobcem
- ošklivá oprávnění aplikací následně můžete zakázat přímo v *AndroidManifest.xml*

<br><br><hr><br>

## Bezpečná zařízení:
Jak již bylo zmíněno, rozmanitost zařízení s OS Android je z pohledu bezpečnosti velký problém.

V dnešní době není problém pořídit si telefon s OS Android za směšnou finanční částku. Pořizovací cena ovšem není všechno, a neměla by být hlavním faktorem při výběru. Většina levných zařízení se nikdy nedočká žádné bezpečnostní aktualizace, natož pak aktualizace na novější verzi OS. Tato zařízení mohou obsahovat stovky známých bezpečnostních děr, které lze lehce zneužít, pokud zařízení není záplatováno výrobcem. Situace u dražších modelů ale nemusí být o nic lepší. Níže naleznete několik bodů, které by mělo zařízení splňovat, aby se s ním z hlediska bezpečnosti dalo pracovat.

### Bezpečnostní požadavky na zařízení s OS Android:
- 64-bit architektura (x86/ARM)
- jádro >= 3.18 (ideálně 4.4)
- full verified boot (ideálně i pro custom ROM)
- podpora *Treble*
- časté (měsíční, minimálně čtvrtletní) bezpečnostní aktualizace pro firmware a proprietární komponenty
- garance bezpečnostních aktualizací po dobu morální životnosti modelu (jak dlouho chcete zařízení používat)

<br>

### Zařízení s OS Android splňující bezpečnostní požadavky:
Informace potřebné k výběru takového zařízení naleznete v odděleném návodě [Výběr telefonu &ndash; OS Android](https://guide.mople71.cz/cs/iot/andr_vyber.php).

<br><br><hr><br>

## Bezpečné nastavení OS:
Android je (většinou) bezpečně nastaven již v základu, není ovšem od věci podívat se do nastavení a zkontrolovat jej.

> Kontrola nastavení zabezpečení

- Otevřete si <span class="green">Nastavení</span>.
- Nalezněte podkategorii **Zabezpečení a poloha** a otevřete ji.
- Zkontrolujte bezpečnou konfiguraci **Zámku obrazovky** &ndash; <span class="green">PIN</span> nebo <span class="green">Heslo</span>
- Zkontrolujte **Administrátorské aplikace v zařízení**. Neměly by zde být žádné aplikace kromě aplikací Google, pokud je používáte.
- Zkontrolujte **Šifrování** vašeho zařízení.
- Aplikaci zavřete.

> Kontrola aktuálního OS

- Otevřete si <span class="green">Nastavení</span>.
- Nalezněte podkategorii **Systém** a otevřete ji.
- Klikněte na <span class="green">Informace o telefonu</span>.
- Zkontrolujte, zdali máte aktuální **verzi systému Android** &ndash; **8.1**.
- Zkontrolujte, zdali máte nejnovější **úroveň opravy zabezpečení Android**.
<li style="list-style-type: none">![andinf](https://faq.mople71.cz/img/cs/andinf.png)</li>
- Máte-li starší *verzi systému Android* než **8.0** a výrobce nepotvrdil aktualizaci, zařízení je implicitně nebezpečné &ndash; můžete se dívat po náhradě. Máte-li starší *úroveň opravy zabezpečení Android* než **3 měsíce**, zařízení není bezpečné &ndash; můžete se dívat po náhradě.
- Aplikaci zavřete.

<br>

### Využití účtu hosta:
Pod účtem hosta můžete relativně bezpečně např. prohlížet rizikové internetové stránky. Instalace pochybných aplikací není doporučena ani pod uživatelem hosta, jelikož aplikace může OS exploitovat mnohem snadněji než internetová stránka. Pokud by aplikace úspěšně získala root pravomoce (např. pomocí *CVE-2015-1805* aka KingRoot), nepomůže vám ani reset zařízení do továrního nastavení.

> Přepnutí se na účet hosta

- Stáhněte dolů notifikační lištu dvěma prsty, případně ji rozšiřte kliknutím na šipku v pravém dolním rohu.
- V pravém dolním sloupci klikněte na obrázek svého uživatelského účtu.
- Zobrazí se seznam uživatelských účtů. Klikněte na tlačítko <span class="green">Přidat hosta</span>.
<li style="list-style-type: none">![andg](https://faq.mople71.cz/img/cs/andg.png)</li>
- Budete automaticky přepnuti na uživatele hosta.
- Jakmile z účtu hosta budete chtít odejít, stáhněte notifikační lištu a klikněte na tlačítko <span class="green">Odstranit hosta</span>.
<li style="list-style-type: none">![andg1](https://faq.mople71.cz/img/cs/andg1.png)</li>
- Odstranění potvrďte.

<br><br><hr><br>

## Doporučené aplikace:
V následující sekci naleznete doporučené bezpečnostní aplikace a aplikace s bezpečností úzce související. Aplikace jsou děleny na FOSS (free and open source) a proprietární.

### Obchod s aplikacemi:
Obchod s aplikacemi velmi úzce souvisí s bezpečností, jelikož z něj stahujete a instalujete veškeré aplikace do OS.

#### FOSS:
- F-Droid: https://f-droid.org/

#### Proprietární:
- Google Play: https://play.google.com/
- Amazon: https://www.amazon.com/appstore

*Amazon* má zdlouhavý proces kontroly aplikací (jsou kontrolovány manuálně), proto má téměř vždy zastaralé verze aplikací, zvláště těch, které jsou často aktualizovány.

<br>

### Firewall:
Firewall je velmi důležitá bezpečnostní vrstva OS, která poskytuje ochranu před síťovými útoky. Na veřejných WiFi připojeních je prakticky nutností.

Nejlepší volbou je integrovaný FW, bohužel jej prakticky žádná ROM nenabízí. Zneužití *VPN API* (NetGuard, NoRoot Data Firewall) není nejlepší a nejspolehlivější implementace FW, ale alespoň nevyžaduje destrukci bezpečnostního modelu OS. Bohužel, vypadá to, že pouze velmi málo lidí má zájem implementovat tyto věci správně &ndash; přímo do OS.

#### FOSS:
- integrovaný
- NetGuard (VPN): https://github.com/M66B/NetGuard

#### Proprietární:
- NoRoot Data Firewall (VPN): https://play.google.com/store/apps/details?id=com.jianjia.firewall

<br>

### Blokování reklamy:
Blokování reklamy je z hlediska bezpečnosti nezbytné z důvodu výskytu škodlivých reklam na internetu. Rozumnější je oblíbené stránky podporovat jinou a bezpečnější &ndash; finanční &ndash; formou.

#### FOSS lokální VPN:
- Blokada: http://blokada.org/
- DNS66: https://github.com/julian-klode/dns66

#### Proprietární lokální VPN:
- Adguard: https://adguard.com/en/adguard-android/overview.html

#### VPN:
- Freedome: https://play.google.com/store/apps/details?id=com.fsecure.freedome.vpn.security.privacy.android

#### Internetový prohlížeč:
- Brave: https://play.google.com/store/apps/details?id=com.brave.browser
- Google Chrome / Chromium
- &#8230;

VPN je dobrý způsob blokace reklam, ovšem implementace *OpenVPN* na Androidu není perfektní. Lokální VPN tímto problémem netrpí. Použití prohlížeče blokující reklamy je nejlepším řešením. **Chrome** již umožňuje nativně blokovat agresivní reklamy nesplňující podmínky.

<br>

### Správce oprávnění:
Správce oprávnění umožňuje nastavit, k jakým informacím a komponentům má konkrétní aplikace přístup. Jedná se více o záležitost soukromí než bezpečnosti.

#### FOSS:
- integrovaný (Marshmallow a výše)

> Využití vestavěného správce oprávnění

- Otevřete si <span class="green">Nastavení</span>.
- Nalezněte podkategorii **Aplikace a oznámení** a otevřete ji.
- Klikněte na <span class="green">Oprávnění aplikací</span>.
- Otevřete postupně všechny kategorie a zakažte všem aplikacím nepotřebný přístup.
<li style="list-style-type: none">![andapp](https://faq.mople71.cz/img/cs/andapp.png)</li>
<li style="list-style-type: none">![andapp1](https://faq.mople71.cz/img/cs/andapp1.png)</li>
- Po dokončení nastavení oprávnění se z kategorie **Oprávnění aplikací** přesuňte o úroveň výše, rozklikněte **Rozšířená nastavení**.
- Otevřete <span class="green">Přístup ke spec. aplikacím</span>.
- Zde můžete nastavit např. které aplikace mají přístup k prémiovým SMS nebo mohou měnit nastavení systému.
<li style="list-style-type: none">![andapp2](https://faq.mople71.cz/img/cs/andapp2.png)</li>
- Aplikaci zavřete.

<br>

### Internetový prohlížeč:
Chrome/Chromium je prohlížeč s nejkvalitnějšími mitigacemi proti exploitům na Linuxu &ndash; tedy i na Androidu. Prohlížeče založené na Mozilla Firefox stále v této oblasti za Chromium zaostávají.

#### FOSS:
- Chromium: https://www.chromium.org/developers/how-tos/android-build-instructions
- Brave: https://play.google.com/store/apps/details?id=com.brave.browser

#### Proprietární:
- Google Chrome: https://play.google.com/store/apps/details?id=com.android.chrome

> Bezpečné nastavení Brave

- Otevřete prohlížeč <span class="green">Brave</span>.
- Přes menu v pravém rohu otevřete <span class="green">Nastavení</span>.
- Rozklikněte nabídku **Ochrana soukromí**. Zatrhněte položky <span class="green">Režim ochrany proti sledování</span>, <span class="green">Blokování reklam</span>, <span class="green">Blokování regionálních reklam</span> a <span class="green">Ochrana proti otisku prohlížeče</span>.
<li style="list-style-type: none">![brvand](https://faq.mople71.cz/img/cs/brvand.png)</li>
- Vraťte se o úroveň výše a rozklikněte nabídku <span class="green">Nastavení webu</span>.
- V sekci **JavaScript** zablokujte spouštění JS.
<li style="list-style-type: none">![brvand1](https://faq.mople71.cz/img/cs/brvand1.png)</li>
- V sekci **Schránka** zablokujte webům přístup k datům ve schránce.
<li style="list-style-type: none">![brvand2](https://faq.mople71.cz/img/cs/brvand2.png)</li>

<div class="alert info"><p><em class="icon-info-circled"></em>**Info**<br>
Nyní máte ve výchozím nastavení vypnutý JS pro všechny weby. Jakmile budete chtít spuštění JS pro určitý web povolit, stačí kliknout na ikonu prohlížeče v horním panelu a skripty povolit.<br>
![brvand3](https://faq.mople71.cz/img/cs/brvand3.png)</p></div>

> Omezení JavaScriptu v Google Chrome / Chromium

- Otevřete si <span class="green">Google Chrome</span> / <span class="green">Chromium</span>.
- Kliknutím na tři tečky v horním pravém rohu otevřete boční panel a klikněte na tlačítko <span class="green">Nastavení</span>.
- Klikněte na **Nastavení webu** a otevřete podkategorii <span class="green">JavaScript</span>.
- Zablokujte spouštění JS.
<li style="list-style-type: none">![chmandrjs](https://faq.mople71.cz/img/cs/chmandrjs.png)</li>
- Klikněte na tlačítko <span class="green">Přidat výjimku pro konkrétní web</span>.
- Zadejte adresu důvěryhodného webu, na kterém se může spouštět JS. Syntax je oproti desktopové verzi značně omezený.
<li style="list-style-type: none">![chmandrjs1](https://faq.mople71.cz/img/cs/chmandrjs1.png)</li>
- Klikněte na <span class="green">Přidat</span>.

<br><br><hr>

<h3 class="nocol">To je vše. Stay safe! ![smile](https://mople71.cz/img/sm/smile.svg)</h3>
