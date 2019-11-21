# FAQ – OS Android
Android je dominantní OS na mobilním trhu (>88% podíl) vyvíjený společností **Google, Inc.** Díky svému majoritnímu zastoupení se těší velké pozornosti hackerů.

Android má robustní bezpečnostní model, který předpokládá, že aplikace třetích stran běžící v OS nejsou důvěryhodné. Hlavním bezpečnostním problémem je rozmanitost zařízení, z nichž většina modelů nedostává pravidelné bezpečnostní záplaty a/nebo běží na zastaralých verzích OS.

> Trocha teorie o bezpečnostním modelu OS Android

Android má robustní vícevrstevný bezpečnostní model. Používá linuxové jádro, implementuje <abbr title="Mandatory Access Control">MAC</abbr> a mitigace proti *memory corruption* exploitům – Android je jediná linuxová distribuce, která neumožňuje spuštění *non-<abbr title="Position Independent Executable">PIE</abbr>* kódu. Každé aplikaci je přiřazen unikátní uživatelský ID, aplikace je uzavřena v sandboxovaném prostředí, nemůže operovat s žádnou jinou aplikací a je jí umožněno operovat pouze se soubory/komponenty OS, ke kterými dostane oprávnění od vlastníka zařízení.

![Android Security Model](https://faq.mople71.cz/img/en/and.png)
<p class="imgsrcf">*The Android security model (upraveno).* Zdroj: [Android Security 2015 Annual Report](http://source.android.com/security/reports/Google_Android_Security_2015_Report_Final.pdf)</p>

#### Jádro:
Android je postaven na jádru Linux. Linuxové jádro možná není nejlepší volbou z hlediska bezpečnosti, Androidu ovšem nabízí slušný model oprávnění založený na uživatelích a uživatelských skupinách, izolaci procesů apod.

#### MAC:
Android **Kitkat** a výše používá silně modifikovanou implementaci linuxového MAC **SELinux** – tzv. *SEAndroid*. SEAndroid výrazně snižuje prostor pro exploitaci. Také hraje roli v modelu oprávnění OS Android. Díky implementaci MAC nyní pouze velmi malá část kódu běží s plným root oprávněním. Výrazná zlepšení z pohledu MAC byla představena ve verzích **Lollipop** a **Oreo**.

#### Aplikace:
Android vyžaduje digitální podpis aplikací – nepodepsané aplikace nemohou být nainstalovány. Ve výchozím nastavením lze instalovat aplikace pouze z předinstalovaného obchodu aplikací – obvykle **Google Play**. Veškeré aplikace jsou uzavřeny v sandboxu (*IsolatedProcess*), každá aplikace je tedy izolovaná od ostatních aplikací a OS. Android implementuje **seccomp** sandbox, který nabízí pokročilejší možnosti izolace a přináší vyšší míru bezpečnosti. Interně je využíván například aplikací *Google Chrome*.

Android **Marshmallow** a výše nabízí aplikační model oprávnění – uživatel si může zvolit, k jakým komponentům/souborům bude mít daná aplikace přístup. S verzí **Q** byl systém oprávnění zrobustněn. <span class="red">Využití správců oprávnění třetích stran (např. *XPrivacy*) je důrazně nedoporučeno.</span>

Funkce závislé na službách Google (např. *VerifyApps*, *Google Play Protect*), zde nebudou rozebírány.

#### FAQ se dělí na několik sekcí:
- [Bezpečná zařízení](#andr1)
- [Základní bezpečnostní nastavení](#andr2)
- [Doporučené aplikace](#andr3)

<br>

## Bezpečná zařízení:
Jak již bylo zmíněno, diverzita zařízení s OS Android je z pohledu bezpečnosti velký problém. Ne všichni výrobci nabízejí pravidelné bezpečnostní záplaty a aktualizace OS pro své modely, důvody mohou být různé. Na trhu tedy můžeme nalézt zbrusu nová zařízení se starou verzí OS Android, která již od výroby obsahují známé bezpečnostní díry a výrazně zvyšují pravděpodobnost exploitace. Tato praxe se bohužel nevztahuje pouze na levné modely, nýbrž i na dražší telefony. Uživatel by se měl při výběru svého zařízení zajímat o jeho bezpečnostní parametry. Níže naleznete několik parametrů, které by mělo zařízení splňovat, aby se o něm dalo uvažovat.

### Bezpečnostní kritéria pro zařízení s OS Android:
- verze dodávaného OS minimálně **Q** (*10*)
- časté (měsíční, minimálně čtvrtletní) bezpečnostní aktualizace pro firmware a proprietární komponenty
- garance bezpečnostních aktualizací po dobu morální životnosti modelu
- full verified boot
- 64-bit architektura (x86/ARM)
- jádro >= 4.4
- podpora *Treble*

<div class="alert info"><p><em class="icon-info-circled"></em>**Info**<br>
Existují dvě úrovně měsíčních bezpečnostních aktualizací – **prvního** dne v měsíci a **páteho** dne v měsíci. Obě úrovně jsou aplikovatelné pro většinu modelů na trhu. Pokud výrobce celkem pravidelně zařízení aktualizuje, ale implementuje pouze první úroveň (např. *1. listopadu 2019*), může to značit problém.</p></div>

> Proč záleží na verzi OS

Každá verze OS Android přináší mnohá bezpečnostní a jiná vylepšení. **Marshmallow** přinesl správu oprávnění pro aplikace, kdy si uživatel může zvolit, jaká aplikace má k čemu přístup. **Nougat** přinesl přepsaný *MediaServer*, který likviduje řadu typů exploitů jako např. *Stagefright*. **Oreo** posunul sandboxing na vyšší úroveň díky *Project Treble* a celoplošenému využítí *seccomp* pro veškeré aplikace. Dále například zrobustnil *WebView* a model oprávnění aplikací. Lze s klidným svědomím říci, že <span class="red">žádná verze OS Android starší nežli *Pie* není bezpečná a neměla by být používána.</span>

> Proč záleží na bezpečnostních aktualizacích

Uveďme drobný příklad. Nainstalujete si škodlivou aplikaci na starší verzi <span class="green">8.1</span> – máte kontrolu nad oprávněními aplikace a všechna nepotřebná oprávnění tedy můžete zakázat. Nemáte ovšem nejnovější bezpečnostní záplaty. Aplikace tedy může využít známou bezpečnostní díru a exploitovat OS – uživatel se o tom nikdy nedozví. Toto je bežná praxe malware pro OS Android, jelikož se jedná o nejjednodušší a nejméně nákladný způsob infikace – cca. **90% zařízení nemá kritické bezpečnostní záplaty**.

<br>

### Přijatelné modely dle bezpečnostních kritérií:
- **libovolný model** řady **<span class="go">Pixel</span>**
- **libovolný model** projektu [Android One](https://www.android.com/one/)
- **libovolný model** výrobce **<span class="no">Nokia</span>**
- vlajkové lodě většiny známých výrobců jako **SONY**, **<span class="sam">Samsung</span>**, **<span class="lg">LG</span>**, **<span class="hu">Huawei</span>** apod.
- vyšší modely výrobců **<span class="sam">Samsung</span>** a **SONY**

<div class="alert info"><p><em class="icon-info-circled"></em>**Tip**<br>
Pro inspiraci se také můžete podívat na [seznam doporučených modelů pro firemní sféru](https://androidenterprisepartners.withgoogle.com/devices/) od Google.</p></div>

<br><br><hr><br>

## Základní bezpečnostní nastavení:
Android je (většinou) bezpečně nastaven již v základu, není ovšem od věci konfiguraci zkontrolovat.

> Kontrola nastavení zabezpečení

- Otevřete si <span class="green">Nastavení</span>.
- Nalezněte podkategorii **Zabezpečení a poloha** a otevřete ji.
- Zkontrolujte bezpečnou konfiguraci **Zámku obrazovky** – <span class="green">PIN</span> nebo <span class="green">Heslo</span>
- Zkontrolujte **Administrátorské aplikace v zařízení**. Neměly by zde být žádné aplikace kromě aplikací Google, pokud je používáte.
- Zkontrolujte **Šifrování** vašeho zařízení.
- Aplikaci zavřete.

> Kontrola aktuálního OS

- Otevřete si <span class="green">Nastavení</span>.
- Nalezněte podkategorii **Systém** a otevřete ji.
- Klikněte na <span class="green">Informace o telefonu</span>.
- Zkontrolujte, zdali máte aktuální **verzi systému Android** – **10.0** či výše.
- Zkontrolujte, zdali máte nejnovější **úroveň opravy zabezpečení Android**.
<li style="list-style-type: none">![andinf](https://faq.mople71.cz/img/cs/andinf.png)</li>
- Máte-li starší *verzi systému Android* než **9.O** a výrobce nepotvrdil aktualizaci, zařízení je implicitně nebezpečné – můžete se dívat po náhradě. Máte-li starší *úroveň opravy zabezpečení Android* než **3 měsíce**, zařízení není bezpečné – můžete se dívat po náhradě.
- Aplikaci zavřete.

<br>

### Správce oprávnění:
Správce oprávnění umožňuje nastavit, k jakým informacím a komponentům má konkrétní aplikace přístup.

> Nastavení oprávnění aplikací

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

### Využití účtu hosta:
Pod účtem hosta můžete relativně v bezpečí např. prohlížet rizikové internetové stránky. Instalace pochybných aplikací není doporučena ani pod uživatelem hosta, jelikož aplikace může OS exploitovat mnohem snadněji nežli internetová stránka. Pokud by aplikace úspěšně získala administrátorské pravomoce, nemusí pomoci ani reset zařízení do továrního nastavení.

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
- *Aurora Store – open-source frontend pro obchod Google Play*

#### Proprietární:
- Google Play: https://play.google.com/

Obchody typu *Amazon* či *Samsung* nemusí vždy mít nejnovější verze aplikací, zvláště těch, které jsou často aktualizovány. Zejména Amazon má extrémně zdlouhavý proces kontroly aplikací (prováděno ručně).

<br>

### Firewall:
Firewall je velmi důležitá bezpečnostní vrstva OS, která poskytuje ochranu před síťovými útoky. Na veřejných WiFi připojeních je nutností.

Nejlepší volbou je integrovaný FW, bohužel jej prakticky žádná ROM nenabízí. Zneužití *VPN API* (NetGuard, NoRoot Data Firewall) není nejlepší a nejspolehlivější implementace FW, ale alespoň nevyžaduje destrukci bezpečnostního modelu OS. Bohužel, vypadá to, že pouze velmi málo lidí má zájem implementovat tyto věci správně – přímo do OS.

#### FOSS:
- integrovaný
- NetGuard (VPN): https://github.com/M66B/NetGuard

#### Proprietární:
- NoRoot Data Firewall (VPN): https://play.google.com/store/apps/details?id=com.jianjia.firewall&hl=cs

<br>

### Blokování reklamy:
Blokování reklamy je z hlediska bezpečnosti nezbytné z důvodu výskytu škodlivých reklam na internetu. Rozumnější je oblíbené stránky podporovat jinou a bezpečnější – finanční – formou.

#### FOSS lokální VPN:
- Blokada: http://blokada.org/
- DNS66: https://github.com/julian-klode/dns66

#### Proprietární lokální VPN:
- Adguard: https://adguard.com/en/adguard-android/overview.html

#### VPN:
- Freedome: https://play.google.com/store/apps/details?id=com.fsecure.freedome.vpn.security.privacy.android&hl=cs

#### Internetový prohlížeč:
- Brave: https://play.google.com/store/apps/details?id=com.brave.browser&hl=cs
- Google Chrome
- &#8230;

VPN je dobrý způsob blokace reklam, ovšem implementace *OpenVPN* na Androidu není perfektní. Lokální VPN tímto problémem netrpí. Použití prohlížeče blokující reklamy je na OS Android nejlepším řešením. **Chrome** již umožňuje nativně blokovat agresivní reklamy nesplňující podmínky. Prohlížeč **Brave** v základu integruje blokování reklam a trackerů.

<br>

### Internetový prohlížeč:
Chrome/Chromium je prohlížeč s nejkvalitnějšími mitigacemi proti exploitům. Prohlížeče založené na Mozilla Firefox stále v této oblasti za Chromium zaostávají, na OS Android obzvlášť.

#### FOSS:
- Chromium: https://www.chromium.org/developers/how-tos/android-build-instructions
- Brave: https://play.google.com/store/apps/details?id=com.brave.browser&hl=cs

#### Proprietární:
- Google Chrome: https://play.google.com/store/apps/details?id=com.android.chrome&hl=cs

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
Nyní máte ve výchozím nastavení vypnutý JS pro všechny weby. Jakmile budete chtít spuštění JS pro určitý web povolit, stačí poklepat na ikonu prohlížeče v horním panelu a skripty povolit.<br><br>
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
