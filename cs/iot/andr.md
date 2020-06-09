# OS Android
Android se jakožto nejrozšířenější mobilní OS těší velké pozornosti hackerů, jeho dostatečné zabezpečení je proto nezbytné. Android má robustní bezpečnostní model, který předpokládá, že aplikace třetích stran běžící v OS nejsou důvěryhodné. Hlavním bezpečnostním problémem je rozmanitost zařízení, z nichž většina modelů nedostává pravidelné bezpečnostní záplaty a/nebo běží na zastaralých verzích OS.

Podporovanou verzí Android je <span class="green">Q (10)</span> jakožto aktuální verze OS. Starší verze OS by neměly být používány. Přesto je většina obsažených informací platná i pro starší verze OS, pouze se může lišit přesný postup aplikace různých kroků.

#### Sekce kapitoly:
- [Bezpečná zařízení](#andr1)
- [Základní bezpečnostní nastavení](#andr2)
- [Doporučené aplikace](#andr3)
- [Bezpečné ROM](#andr4)

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

<div class="alert info"><p><em class="icon-info-circled"></em>**Info**<br>
Existují dvě úrovně měsíčních bezpečnostních aktualizací – **prvního** dne v měsíci a **pátého** dne v měsíci. Obě úrovně jsou aplikovatelné pro většinu modelů na trhu. Pokud výrobce celkem pravidelně zařízení aktualizuje, ale implementuje pouze první úroveň (např. *1. listopadu 2019*), může to značit problém.</p></div>

<br>

### Přijatelné modely dle bezpečnostních kritérií:
- **libovolný model** řady **<span class="go">Pixel</span>**
- **libovolný model** projektu [Android One](https://www.android.com/one/)
- **libovolný model** výrobce **<span class="no">Nokia</span>**
- vlajkové lodě většiny známých výrobců jako **SONY**, **<span class="sam">Samsung</span>**, **<span class="lg">LG</span>**, **<span class="hu">Huawei</span>** apod.
- vyšší modely výrobců **<span class="sam">Samsung</span>** a **SONY**

<div class="alert info"><p><em class="icon-info-circled"></em>**Tip**<br>
Pro inspiraci se také můžete podívat na [seznam doporučených modelů pro firemní sféru](https://androidenterprisepartners.withgoogle.com/devices/) od Google.</p></div>

<div class="alert info"><p><em class="icon-info-circled"></em>**Info**<br>
Výše rozebíraná kritéria jsou především z hlediska SW, které je v praxi nejkritičtější. Z hlediska HW splňují bezpečnostní standardy porovnatelné s iPhone **pouze modely řady Pixel 3. generace a výše**.</p></div>

<br><br><hr><br>

## Základní bezpečnostní nastavení:
Android je většinou bezpečně nastaven již v základu, není ovšem od věci konfiguraci zkontrolovat.

> Kontrola nastavení zabezpečení

- Otevřete si <span class="green">Nastavení</span>.
- Přesuňte se do podkategorie **Zabezpečení**.
- Zkontrolujte bezpečnou konfiguraci **Zámku obrazovky** – <span class="green">Heslo</span>, nebo alespoň <span class="green">PIN</span>
<li style="list-style-type: none">![andinf](https://securityhandbook.cz/img/cs/andinf.png)</li>
- V *rozšířených nastavení* zkontrolujte **Aplikace pro správu zařízení**. Jedinou důvěryhodnou povolenou aplikací by měla být <span class="green">Najdi moje zařízení</span>, je-li uživatelem vyžadována.
- Výjimku tvoří MDM aplikace nezbytné pro umožnění přístupu k firemním datům ve vašem zaměstnání (např. <span class="green">Device Policy</span> pro gSuite).
<li style="list-style-type: none">![andinf1](https://securityhandbook.cz/img/cs/andinf1.png)</li>
- Zkontrolujte **Šifrování** vašeho zařízení a absenci jakýchkoli **Agentů důvěry**.
- Aplikaci zavřete.

> Kontrola aktuálního OS

- Otevřete si <span class="green">Nastavení</span>.
- Přesuňte se do podkategorie **Zabezpečení**.
- Klikněte na <span class="green">Aktualizace zabezpečení</span>.
- Zkontrolujte, zdali máte aktuální **verzi systému Android** – <span class="green">10</span> či výše.
- Zkontrolujte, zdali máte nejnovější **aktualizaci zabezpečení Androidu**.
<li style="list-style-type: none">![andinf2](https://securityhandbook.cz/img/cs/andinf2.png)</li>
- Máte-li starší *verzi systému Android* než **9.0** a výrobce nepotvrdil aktualizaci, zařízení je implicitně nebezpečné – můžete se dívat po náhradě. Máte-li starší *aktualizaci zabezpečení Androidu* než **3 měsíce**, zařízení není bezpečné – můžete se dívat po náhradě.
- Aplikaci zavřete.

<br>

### Správce oprávnění:
Správce oprávnění umožňuje nastavit, k jakým informacím a komponentům má konkrétní aplikace přístup.

> Nastavení oprávnění aplikací

- Otevřete si <span class="green">Nastavení</span>.
- Přesuňte se do podkategorie **Aplikace a oznámení**.
- V *rozšířených nastavení* otevřete <span class="green">Správce oprávnění</span>.
- Rozklikněte postupně všechny kategorie a zakažte všem aplikacím nepotřebný přístup.
<li style="list-style-type: none">![andapp](https://securityhandbook.cz/img/cs/andapp.png)</li>
<li style="list-style-type: none">![andapp1](https://securityhandbook.cz/img/cs/andapp1.png)</li>
- Následně se ze *Správce oprávnění* přesuňte o úroveň výše a rozklikněte <span class="green">Přístup ke spec. aplikacím</span>.
- Zde můžete nastavit např. které aplikace mají přístup k prémiovým SMS, mohou měnit nastavení systému nebo instalovat neznámé aplikace. Zakažte všechen nepotřebný přístup.
<li style="list-style-type: none">![andapp2](https://securityhandbook.cz/img/cs/andapp2.png)</li>
- Aplikaci zavřete.

<br><br><hr><br>

## Doporučené aplikace:
V následující sekci naleznete doporučené bezpečnostní aplikace a aplikace s bezpečností úzce související. Aplikace jsou děleny na FOSS (free and open source) a proprietární.

### Obchod s aplikacemi:
Obchod s aplikacemi velmi úzce souvisí s bezpečností, jelikož z něj stahujete a instalujete veškeré aplikace do OS. <span class="red">Je důrazně doporučeno používat pouze předinstalovaný obchod s aplikacemi.</span>

#### FOSS:
- F-Droid: https://f-droid.org/
- *Aurora Store – open-source frontend pro obchod Google Play*

#### Proprietární:
- <span class="green">Google Play</span>: https://play.google.com/
- Huawei AppGallery: https://huaweimobileservices.com/appgallery/

Obchody typu *Amazon* či *Samsung* nemusí vždy mít nejnovější verze aplikací, zvláště těch, které jsou často aktualizovány. Zejména Amazon má extrémně zdlouhavý proces kontroly aplikací (prováděno ručně).

<br>

### Firewall:
Firewall je velmi důležitá bezpečnostní vrstva OS, která poskytuje ochranu před síťovými útoky. Na veřejných WiFi připojeních je nutností. Android integruje základní firewall.

Aplikační firewall OS neintegruje, funkcionalitu je možné dodat externí aplikací, která pro implementaci zneužije *VPN API*, což není nejčistší a nejspolehlivější implementace FW, nicméně se jedná o nejschůdnější variantu, která nevyžaduje destrukci bezpečnostního modelu OS.

#### FOSS:
- <span class="green">NetGuard</span>: https://www.netguard.me/

<br>

### Blokování reklamy:
Blokování reklamy je bohužel z hlediska bezpečnosti nezbytné kvůli výskytu škodlivých reklam na internetu. Rozumnější je oblíbené stránky podporovat jinou a bezpečnější – např. finanční – formou.

VPN je dobrý způsob blokace reklam, standardním typem připojení je ovšem přes *OpenVPN* a Android bohužel tento druh připojení neintegruje, uživatel je tedy zpravidla odkázán na aplikaci svého poskytovatele. Použití prohlížeče blokující reklamy (viz sekce níže) je na OS Android nejlepším řešením. **Google Chrome** nativně blokuje agresivní reklamy. Prohlížeč **Brave** v základu integruje blokování reklam a trackerů.

#### FOSS lokální VPN:
- Blokada: http://blokada.org/
- DNS66: https://github.com/julian-klode/dns66

#### Proprietární lokální VPN:
- Adguard: https://adguard.com/en/adguard-android/overview.html

#### VPN:
- <span class="green">F-Secure Freedome</span>: https://www.f-secure.com/en/home/products/freedome

#### Internetový prohlížeč:
- Brave: https://play.google.com/store/apps/details?id=com.brave.browser&hl=cs
- Google Chrome
- &#8230;

<br>

### Internetový prohlížeč:
Chrome/Chromium je prohlížeč s nejkvalitnějšími mitigacemi proti exploitům. Prohlížeče založené na *Mozilla Firefox* stále v této oblasti za Chromium zaostávají, na OS Android dvojnásob.

#### FOSS:
- <span class="green">Brave</span>: https://play.google.com/store/apps/details?id=com.brave.browser&hl=cs
- Chromium: https://www.chromium.org/developers/how-tos/android-build-instructions

<!--- ../browsers.md -->

#### Proprietární:
- Google Chrome: https://play.google.com/store/apps/details?id=com.android.chrome&hl=cs

<!--- ../browsers.md -->

<br><br><hr><br>

## Bezpečné ROM:
Aby ROM mohla být považována za bezpečnou, musí udržovat striktní bezpečnostní standardy. Musí implementovat pravidelné bezpečnostní aktualizace a podporovat verified boot, nesmí jakýmkoli způsobem degradovat integrované bezpečnostní funkce, nesmí zpřístupňovat pravomoci root uživatele atd.

Nejbezpečnější ROM je originální ROM spravovaná společností Google – <span class="green">Pixel</span>, nebo součást projektu <span class="green">[Android One](https://www.android.com/one/)</span>.

Originální ROM implementované ostatními výrobci s *integrovanými službami Google* zpravidla základní bezpečnostní kritéria splňují. **Zařízením bez integrovaných služeb Google je důrazně doporučeno se vyhnout.**

<span class="red">Custom ROM bezpečnostní kritéria nesplňují.</span> Například bohužel velmi oblíbený *LineageOS* nesplňuje ani jedno z několika výše vyjmenovaných kritérií. Výjimku potvrzující pravidlo tvoří projekt [GrapheneOS](https://grapheneos.org/), který ovšem cílí na specifickou skupinu uživatelů, neobsahuje služby Google a podporuje pouze bezpečný HW (modely řady Pixel).

<div class="alert exclaim"><p><em class="icon-attention"></em>**Varování**<br>
Instalace libovolné neoriginální ROM je důrazně nedoporučena.</p></div>

<br><hr>

<h3 class="nocol">To je vše. Stay safe! ![smile](https://securityhandbook.cz/img/sm/smile.svg)</h3>
