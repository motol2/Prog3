# Hodnocení odevzdaných sad testových otázek

**Jak číst sloupec „prošlo“:** kolik otázek se dostalo do finální sady. Vyřazovaly
se pouze duplicity (stejná otázka od dvou autorů — ponechána lepší verze) a položky,
které netestovaly téma nebo byly věcně sporné. Není to známka, ale ukazatel toho,
kolik práce bylo rovnou použitelné.

---

## Souhrn

| Student | Téma | Otázek | Prošlo |
|---|---|---|---|
| Tomáš Jandák | Metody strojového učení | 8 | 8 |
| Marek Miláček | AI a GDPR | 5 | 5 |
| Vincent Procházka | Metody strojového učení | 5 | 5 |
| Marek Řehák | Autorské právo a AI | 5 | 5 |
| Petr Škarvan | Agentní programování | 5 | 5 |
| Antonín Povolný | Autonomní vozidla | 5 | 4 |
| Šimon Kubala / Lukáš Jiránek | Autonomní vozidla | 10 (sdílené) | 8 |
| Anastasiia Balanets | AI a GDPR | 10 | 7 |
| Vitalii Fenynets | Autorské právo a AI | 10 | 7 |
| Šimon Kreperát | AI ve škole | 10 | 7 |
| Ondřej Borovička | Agentní programování | 10 | 6 |
| Tomáš Filip / Vojtěch Garčic | AI a GDPR | 10 | 6 |
| Maksym Kravets | Autorské právo a AI | 10 | 5 |
| Pavel Kubát | Metody strojového učení | 10 | 5 |
| Dominik Pavelka | Autorské právo a AI | 5 | 3 |
| Mark Nahornyi / Jáchym Viták | AI ve škole | 10 (sdílené) | 3 |

**Nejvýraznější zjištění:** všechny pětiotázkové sady měly průchodnost 100 % nebo
80 %. U desetiotázkových sad prošlo typicky 50–70 %. Pět promyšlených otázek mělo
větší hodnotu než deset vygenerovaných.

---

# 1. Autorské právo a AI

## Vitalii Fenynets — 10 otázek, prošlo 7

**Co se povedlo.** Otázka „Může být text vytvořený pomocí AI automaticky považován
za dílo chráněné autorským právem?“ se správnou odpovědí *Záleží na konkrétních
okolnostech a míře lidské tvůrčí činnosti* přesně vystihuje, že odpověď není ano/ne.
Stejně dobře je postavená otázka na veřejně dostupné fotografie — *Ne vždy, veřejná
dostupnost neznamená automaticky volné použití*.

**Kde je prostor.** Distraktory. U otázky „Co je tzv. prompt?“ nabízíš varianty
*Počítačový virus / Druh autorské licence / Digitální podpis autora* — žádnou z nich
student nezvolí, takže otázka nic nezměří. Věrohodné varianty by byly „Textová
odpověď, kterou AI vygeneruje“ (záměna vstupu za výstup) nebo „Nastavení, kterým se
volí verze modelu“. Otázky č. 3 a č. 10 se navíc ptají na totéž jinými slovy.

## Maksym Kravets — 10 otázek, prošlo 5

**Co se povedlo.** Nejvyšší právní úroveň ve třídě. TDM výjimka s možností výhrady,
opt-out jako strojově čitelná výhrada práv, srovnání amerického fair use s evropským
uzavřeným výčtem výjimek, povinnost transparentnosti u GPAI modelů podle AI Actu.
To jsou témata, která se běžně probírají až na právnické fakultě.

**Kde je prostor.** Dvě věci. Za prvé: otázka o ochranných známkách tvrdí, že
AI generovaná označení nelze registrovat, protože chybí lidský prvek. To je nepřesné —
známkové právo neřeší, kdo označení vytvořil; přihlašovatelem je vždy osoba a znaky
strojového původu registrovat lze. 

## Marek Řehák, Tomáš Sunkovský — 5 otázek, prošlo 5

**Co se povedlo.** Nejlepší didaktický cit ze všech odevzdání. Otázka „Může být umělá
inteligence odsouzena a jít do vězení?“ vede studenta přímo k pojmu právní subjektivity,
aniž by ho musela jmenovat. Otázka „Dostávají autoři automaticky peníze, když se AI učí
z jejich děl?“ otevře celou debatu o licencování trénovacích dat jedinou větou. Všech
pět otázek prošlo beze změny zadání.

**Kde je prostor.** Hlavně rozsah — při stoprocentní průchodnosti byla škoda zůstat
u pěti otázek. A u distraktoru „Malíř musí firmě s AI zaplatit za reklamu svého jména“
zkus příště něco méně absurdního, například „Jde o povolené užití, protože podpis je
jen malá část obrázku“ — to je omyl, na který se dá skutečně naletět.

## Dominik Pavelka, Mykoa Mandziuk — 5 otázek, prošlo 3

**Co se povedlo.** Otázka na memorizaci trénovacích dat (AI doslovně reprodukuje části
toho, na čem se učila) propojuje autorské právo s ochranou osobních údajů — to je
pokročilý vhled, který nikdo jiný nenabídl. Otázka na AI generovaný zdrojový kód je
zase jediná, která téma vztahuje k programování.

**Kde je prostor.** Formátování odevzdaného HTML (varianty A–D uvnitř seznamů `<ul>` s Wordovými
styly) komplikuje strojové zpracování; prostý text je spolehlivější.

---

# 2. AI a GDPR

## Tomáš Filip, Vojtěch Garčic — 10 otázek, prošlo 6

**Co se povedlo.** Systematické pokrytí celé šíře nařízení — definice, právní titul,
anonymizace, práva subjektu, sankce, role správce. Otázka „Co musí firma udělat při
zpracování osobních údajů?“ s odpovědí *Mít pro zpracování právní důvod* míří přesně
na jádro GDPR, které se často vynechává.

**Kde je prostor.** Distraktory jsou návodné: *Zveřejnit všechny údaje na internetu*,
*Údaje nikdy nesmí smazat*, *Poslat údaje všem zaměstnancům*. U otázky o právním důvodu
by skutečně těžké varianty byly „Musí získat souhlas od každého subjektu údajů“ — to je
velmi rozšířený omyl, souhlas je jen jeden ze šesti právních titulů — nebo „Musí
zpracování předem ohlásit dozorovému úřadu“. Tvoje sada se navíc z poloviny kryje se
sadou Anastasiie Balanets z jiné skupiny; nesmluvená shoda naznačuje, že jste oba vzali
první výstup AI bez úprav.

## Anastasiia Balanets, Adam Brož — 10 otázek, prošlo 7

**Co se povedlo.** Nejpečlivější formulace mezi základními sadami. Píšeš „informace,
podle kterých lze **přímo nebo nepřímo** určit fyzickou osobu“ a „úprava údajů tak, aby
osobu nebylo možné **rozumně** identifikovat“. Obě upřesnění jsou právně podstatná a
právě díky nim tvoje verze vyhrála nad konkurenční všude, kde se sady překrývaly.

**Kde je prostor.** Délka odpovědí. Správná odpověď je u tebe téměř vždy nejdelší a
nejpropracovanější — to je samo o sobě nápověda a studenti se ji naučí poznat během
několika otázek. Zkus držet všechny čtyři varianty přibližně stejně dlouhé.

## Marek Miláček, Matyáš Sauer — 5 otázek, prošlo 5

**Co se povedlo.** Nejvyšší odborná úroveň v celé třídě. Otázka, proč je právo na výmaz
technicky problematické u natrénovaného modelu — *osobní údaje jsou hluboce integrovány
do matematických vah* — propojuje právo s technikou tak, jak to nikdo jiný netrefil.
Správně i článek 22 o automatizovaném rozhodování, povinnost provést DPIA a rozdíl mezi
pseudonymizovanými a anonymizovanými daty. Distraktory věrohodné, nikoli absurdní.
Tvých pět otázek tvoří celou těžkou kategorii tématu.

**Kde je prostor.** Věcně nemám co vytknout. Jen rozsah — doplnit obtížnost s vysvětlením bys zvládl
za pár minut.

---

# 3. Autonomní vozidla

## Šimon Kubala a Lukáš Jiránek — 10 sdílených otázek, prošlo 8

**Co se povedlo.** Nejširší pokrytí tématu — senzory, mapové podklady, vliv počasí,
detekce chodců, role strojového učení, testování. Otázka „Co znamená, když systém
detekuje chodce?“ s odpovědí *Systém rozpoznal objekt jako chodce na základě dostupných
dat* správně odlišuje detekci od predikce záměru. To je jemný, ale zásadní rozdíl,
na kterém stojí pochopení, proč autonomní vozidla chybují.

**Kde je prostor.** Odevzdali jste identický soubor i identický odkaz na jednu sdílenou
konverzaci. U párové práce je to legitimní, ale znamená to, že výsledek nikdo
nezkontroloval nezávisle. Druhý pár očí by odhalil, že distraktory typu „Aby mělo při
jízdě co nejvyšší spotřebu energie“ otázku prozrazují. Zkuste příště rozdělení rolí:
jeden generuje, druhý hledá slabá místa.

## Antonín Povolný, Evelyn Andriienko — 5 otázek, prošlo 4

**Co se povedlo.** Jediný, kdo do tématu zavedl skutečné odborné pojmy — redundance a
fúze senzorů, simulace milionů kilometrů před reálným testem, výpočet trajektorie a
volba manévru s nejnižším rizikem v reálném čase. Tvoje otázky tvoří celou těžkou
kategorii; bez nich by test skončil u toho, k čemu slouží kamery.

**Kde je prostor.** Otázka „Co se stane, když senzor něco nerozpozná správně?“ má
v odpovědi znovu redundanci a kombinaci čidel — opakuje tím pointu své předchozí otázky.
Proto jsem ji nahradil jednodušší verzí od druhé dvojice. Každá otázka by měla testovat
jednu věc.

---

# 4. AI ve škole

## Šimon Kreperát, Michal Hron — 10 otázek, prošlo 7

**Co se povedlo.** Jako jediný jsi pokryl i pohled učitele (příprava výuky) a
individualizaci výuky — to jsou nejzajímavější části tématu, ostatní zůstali u pohledu
žáka. Otázka na transparentní používání AI, tedy uvést, že a jak byla při práci použita,
míří na skutečné jádro akademické poctivosti.

**Kde je prostor.** Distraktory jsou u všech deseti otázek postavené jako absurdní
extrém: *K nahrazení veškerého učení*, *Vkládat do AI všechny údaje o spolužácích*,
*Uvést AI jako jediného autora školní práce*. Nikdo je nezvolí, takže se neměří znalost.
U transparentnosti by skutečně těžké varianty byly „Stačí výstup přeformulovat vlastními
slovy, pak se uvádět nemusí“ nebo „Uvést AI v seznamu literatury jako autora zdroje“ —
obojí zní poctivě a obojí je špatně. Tak jsem otázku nakonec přepsal.

## Mark Nahornyi a Jáchym Viták — 10 sdílených otázek, prošlo 3

**Co se povedlo.** Otázka „Které zadání pro AI je nejvhodnější?“ je nápad, který nikdo
jiný v celé třídě neměl — testuje praktickou dovednost místo definice. Jáchym navíc
převedl test do Kahootu, jediný projev iniciativy nad rámec zadání.

**Kde je prostor.** Právě ta nejlepší otázka má nejslabší distraktory: *„Něco mi
napiš.“ / „Udělej všechno.“ / „Odpověz.“* Kdyby všechny čtyři varianty byly reálně
použitelné prompty lišící se jen kvalitou, byla by to nejlepší otázka celého testu —
v tomto smyslu jsem ji přepsal. Otázky „Co znamená zkratka AI?“ a „Může AI vytvořit
nepravdivou odpověď? (Ano / Ne)“ netestují nic a do sady se nedostaly.

---

# 5. Agentní programování

## Ondřej Borovička, Michael Bartůněk — 10 otázek, prošlo 6

**Co se povedlo.** Nejúplnější pojmová mapa tématu ze všech odevzdání — agent, smyčka
agenta, paměť, nástroje, plánování, autonomie, bezpečnost i rozdíl proti běžnému
skriptu. Otázka na tento rozdíl (*skript provádí předem daný postup, agent volí kroky
podle situace*) vystihuje podstatu jednou větou lépe než většina učebnic.

**Kde je prostor.** Distraktory srážejí jinak výbornou sadu: *Zvyšuje fyzickou velikost
monitoru*, *Schopnost počítače pracovat bez elektřiny*, *Nahrazuje internetové
připojení*. U otázky na autonomii by skutečným chytákem měla být varianta „Schopnost
fungovat zcela bez omezení a přidělených oprávnění“ — záměna autonomie za neomezená
práva je omyl, který dělají i lidé z oboru.

## Petr Škarvan, Tomáš Štěpán — 5 otázek, prošlo 5

**Co se povedlo.** Jediný v celé třídě, kdo dodržel cílový formát včetně vysvětlení
správné odpovědi. Tvoje otázky šly do databáze prakticky beze změny. Definice tool
callingu (*model si vyžádá spuštění externí funkce a dál pracuje s jejím výstupem*) je
přesná včetně toho podstatného, že model funkci sám nevykonává.

**Kde je prostor.** Distraktor „Specializovaný počítačový virus určený ke sběru dat“
u definice AI agenta vypadává z jinak věrohodné řady — nahradil jsem ho variantou
„jazykový model s větším kontextovým oknem a rychlejšími odpověďmi“, což je skutečná
mylná představa. Jinak jen rozsah.

---

# 6. Metody strojového učení

## Tomáš Jandák — 8 otázek, prošlo 8

**Co se povedlo.** Jediný, kdo šel do hloubky konkrétních algoritmů — Giniho index a
entropie jako míry nečistoty uzlu, prořezávání stromu proti přeučení, vliv volby K = 1,
nutnost normalizace u algoritmu počítajícího vzdálenosti. Distraktory jsou věcně správné
a nenávodné: rozlišit Giniho index od eukleidovské vzdálenosti si student musí skutečně
promyslet. Všech osm otázek prošlo.

**Kde je prostor.** Odevzdal jsi jiné téma, než jsi měl zadané — byl jsi přidělen
k autorskému právu. Práce je výborná a zařadil jsem ji pod strojové učení, ale téma
autorského práva ve skupině A zůstalo nepokryté, protože tvůj kolega neodevzdal nic.
Drobnost: v jedné odpovědi zůstalo „i pro neexperimentální uživatele“ — má být
„neodborné“; překlep po AI, kterého si při čtení nikdo nevšiml.

## Vincent Procházka, Hynek Mayrhofer — 5 otázek, prošlo 5

**Co se povedlo.** Otázka, která vedle sebe postaví rozpoznání psa a kočky, odhad ceny
bytu, shlukování zákazníků a hledání trasy a ptá se, co z toho je klasifikace — to je
elegantní konstrukce, která jednou položkou otestuje rozdíl mezi klasifikací, regresí,
učením bez učitele a optimalizací. Definice přeučení i perceptronu jsou věcně přesné a
distraktor „model se trénoval příliš krátce“ správně nabízí opačný jev (podučení).

**Kde je prostor.** Přiložil jsi odkaz na svůj soukromý Gemini chat ve tvaru
`gemini.google.com/app/…` místo sdílecího odkazu — nikomu jinému se neotevře. Použij
tlačítko Sdílet, ostatní ve třídě odevzdali `share.gemini.google/…`.

## Pavel Kubát, Karyna Kryvka — 10 otázek, prošlo 5

**Co se povedlo.** Otázka na rozdělení dat na trénovací a testovací část míří na správnou
věc — metodiku vyhodnocení, kterou všichni ostatní vynechali. Dobrý nápad je i otázka
na význam přesnosti (accuracy).

**Kde je prostor.** Většina otázek je o informatice obecně, ne o metodách strojového
učení: „Co znamená zkratka?“, „Který jazyk je populární?“, „Jak se nazývají informace
zadávané do modelu?“ (odpověď *Data*), „Které zařízení se používá k trénování?“. Téma
volalo po rozdílu učení s učitelem a bez učitele, po přeučení, po metrikách. Distraktory
navíc otázky znehodnocují úplně — *Sítko na kávu*, *Počítač okamžitě vyhoří*,
*Model automaticky vymyslí chybějící data sám*. U otázky na accuracy by skutečným
chytákem bylo „Jaký podíl skutečně pozitivních případů model zachytil“, protože to je
jiná metrika (úplnost, recall), a student musí obě odlišit. Tvoje kolegyně neodevzdala
nic, takže jsi téma nesl sám — o to větší škoda.

---

# Společná doporučení pro příští zadání

**1. Distraktor je nejtěžší část otázky, ne výplň.**
Nejčastější chyba celé třídy: správná odpověď je jediná, která dává smysl. Taková
otázka netestuje znalost tématu, ale schopnost poznat vtip. Pravidlo pro příště: každá
nesprávná varianta musí být něco, čemu někdo skutečně věří. Dobrý zdroj distraktorů jsou
vlastní dřívější omyly a věci, které zněly logicky, než jste je pochopili správně.

**2. Ověřujte výstup AI, i když píšete otázky o tom, že se má ověřovat.**
Jediná věcná chyba v celé sadě (tvrzení o ochranných známkách) vznikla tak, že model
vyprodukoval sebevědomě znějící nepravdu a nikdo ji neověřil. Přesně tomu se věnuje
jedna z vašich vlastních otázek. Stojí za to si to uvědomit.

**3. Pět promyšlených otázek je víc než deset vygenerovaných.**
Všechny pětiotázkové sady měly průchodnost 80–100 %, desetiotázkové 50–70 %. Kdo
nepřipisoval do počtu, odevzdal lepší práci.

**4. U párové práce si rozdělte role.**
Dvě dvojice odevzdaly identický soubor z jedné sdílené konverzace. Efektivnější model:
jeden vytvoří návrh, druhý hledá slabá místa — a to se prohodí. Dvě dvojice ze stejného
tématu si navíc měly rozdělit podtémata, aby se otázky nekryly.

**5. Dodržte formát zadání.**
Obtížnost a vysvětlení správné odpovědi dodal jediný student z osmnácti. Přitom právě
psaní vysvětlení odhalí, kdy autor sám neví, proč je správná odpověď správná.

---


