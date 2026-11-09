# micro:bit – praktikum z elektrotechniky

## Úvod: jak s praktikem pracovat

Praktikum obsahuje 11 krátkých pokusů, každý na zhruba 10 až 20 minut, a vystačí si s micro:bitem V2, USB kabelem a běžnými součástkami. Každý pokus ukazuje jednu součástku z dokumentu „micro:bit – laboratoř velikosti kreditky“ v praxi a končí kontrolními otázkami.

**Co budete potřebovat.** Počítač s prohlížečem Chrome nebo Edge a web makecode.microbit.org. Programy jsou v Pythonu pro MakeCode: vytvořte nový projekt, nahoře přepněte z *Blocks* na *Python* a vložte kód. Pozor, je to pythonový dialekt MakeCode, ne MicroPython z python.microbit.org, proto se liší názvy funkcí. Program nahrajete tlačítkem *Download*; pokud je deska spárovaná přes WebUSB (*Connect device*), nahraje se přímo. Hodnoty z desky se vypisují příkazem `serial.write_value("název", hodnota)` a graf se zobrazí pod simulátorem po kliknutí na *Show data Device*. Pokud graf v editoru nefunguje, přidejte v *Extensions* rozšíření *datalogger* a použijte soubor MY_DATA.HTM s tlačítkem *Visual Preview*.

**Bezpečnost.** Všechno běží na napětí do 3,3 V. Na piny nikdy nepřipojujte signál o 5 V, nezkratujte 3V a GND a neodebírejte z jednoho pinu víc než jednotky miliampér. Magnety držte daleko od telefonů a platebních karet a pozor na skřípnutí prstů mezi silnými magnety.

**Struktura pokusů.** Každý pokus má stejné části: cíl, pomůcky, program, postup, co očekávat a kontrolní otázky. Stručné odpovědi pro učitele jsou na konci. Naměřené hodnoty berte jako orientační: každá deska je trochu jiná, proto hlavně porovnávejte změny, ne absolutní čísla.

| Pokus | Součástka | Co se zkoumá | Pomůcky navíc |
| --- | --- | --- | --- |
| 1.1 | [LED matice](#pokus-11-led-jako-světelný-senzor) | světelný senzor z LED | baterka, barevná fólie |
| 1.2 | [LED matice](#pokus-12-multiplexování-je-vidět) | multiplexování | tmavá místnost, mobil |
| 2.1 | [Logo a kroužky](#pokus-21-kapacita-proti-odporu-kůže) | dva druhy dotykového snímání | alobal, krokosvorky |
| 3.1 | [Akcelerometr](#pokus-31-tíha-a-náklon) | tíha a náklon | žádné |
| 3.2 | [Akcelerometr](#pokus-32-volný-pád) | volný pád | měkká podložka |
| 4.1 | [Magnetometr](#pokus-41-pole-magnetu-v-závislosti-na-vzdálenosti) | pole magnetu a vzdálenost | slabý magnet, pravítko |
| 5.1 | [Teploměr](#pokus-51-zahřívání-čipu-a-rozdíl-proti-teplotě-vzduchu) | zahřívání čipu | referenční teploměr |
| 6.1 | [Mikrofon](#pokus-61-hlasitost-a-vzdálenost-od-zdroje) | hlasitost a vzdálenost | metr |
| 6.2 | [Mikrofon](#pokus-62-spínač-na-zatleskání) | spínač na zatleskání | žádné |

[Klíč: Stručné odpovědi](#klíč-stručné-odpovědi)

Pokusy s krystalem, časovači a vestavěným reproduktorem (tón 440 Hz hardwarově a programově) jsou k dispozici jako samostatné programy mimo toto praktikum.

## 1. LED matice: světelný senzor a multiplexování

LED matice dělá dvě věci, které jinde potřebují dvě součástky: svítí a měří světlo. První pokus ukáže měření světla, druhý to, jak oko přehlédne rychlé přepínání řádků.

### Pokus 1.1: LED jako světelný senzor

**Cíl:** ověřit, že úroveň světla z LED roste s osvětlením, a zjistit, jak na ni působí barva světla.

**Pomůcky:** micro:bit, baterka (stačí mobil), kousky barevné fólie nebo průhledných plastových obalů (červená, modrá, zelená), papír na zápis.

**Program:**

```python
def on_forever():
    uroven = input.light_level()   # 0 až 255
    serial.write_value("uroven", uroven)
    basic.pause(100)

basic.forever(on_forever)
```

**Postup:**

1. Nahrajte program a zobrazte graf hodnot (*Show data Device*).
2. Zakryjte displej dlaní a zapište hodnotu.
3. Posviťte baterkou na displej z 10 cm, pak z 20 cm a ze 40 cm. Zapište každou hodnotu.
4. Posviťte z 10 cm přes červenou, zelenou a modrou fólii. Zapište hodnoty.
5. Sestavte tabulku vzdálenost – hodnota a barva – hodnota.

**Co očekávat:**

- Při zakrytí hodnota klesne, při osvětlení vzroste.
- Se vzdáleností baterky hodnota klesá.
- Barvy fólie se zřejmě projeví různě. Červená LED by měla lépe reagovat na světlo kratších vlnových délek, než je její vlastní barva, ale ověřte to svým měřením, výsledek závisí na zdroji světla a fólii.

**Kontrolní otázky:**

1. Proč může stejná LED svítit i měřit světlo?
2. Proč se hodnota při zdvojnásobení vzdálenosti baterky nezmění přesně o polovinu?
3. Jak byste senzor využili k automatické změně jasu displeje nebo k zapnutí nočního světla?

### Pokus 1.2: Multiplexování je vidět

**Cíl:** na vlastní oči vidět, že LED matice nesvítí pořád, ale rychle přepíná řádky, a odhadnout kmitočet.

**Pomůcky:** micro:bit, tmavá místnost, mobil s funkcí zpomaleného videa nebo s ručním nastavením expozice, metr.

**Program:**

```python
JASY = [28, 85, 142, 198, 255]   # jas sloupců při stisku A (0 až 255)

def zobraz_svit():
    for x in range(5):
        for y in range(5):
            led.plot_brightness(x, y, 255)

def zobraz_prechod():
    for x in range(5):
        for y in range(5):
            led.plot_brightness(x, y, JASY[x])

def on_forever():
    if input.button_is_pressed(Button.A):
        zobraz_prechod()
    else:
        zobraz_svit()
    basic.pause(50)

basic.forever(on_forever)
```

Obrázky v MakeCode znají jen „svítí / nesvítí“, proto se jas nastavuje po jednotlivých LED příkazem `led.plot_brightness`.

**Postup:**

1. V zatemněné místnosti držte micro:bit v natažené ruce a rychle s ním pohybujte do stran. Pozorujte pohybující se LED.
2. Natočte pohyb mobilem (zpomalené video, pokud ho telefon umí, nebo fotka s expozicí kolem 1/30 s). Změřte pravítkem na snímku nebo obrazovce vzdálenost mezi sousedními čárkami stopy.
3. Podržte A a sledujte, jak se obraz změní. LED v matici mají teď různý jas.
4. Odhadněte kmitočet obnovování: f = v / d, kde v je rychlost pohybu a d vzdálenost čárek.

**Co očekávat:**

- Stopa LED při pohybu není souvislá čára, ale řada oddělených čárek.
- Při držení A se jas LED ve sloupcích liší od nejslabšího po nejsilnější.
- Obnovování obrazu vychází řádově desítky hertzů.

**Kontrolní otázky:**

1. Proč stačí na 25 LED jen 10 pinů procesoru?
2. Pohybujete deskou rychlostí 1 m/s a čárky jsou od sebe 1,5 cm. Jaký je kmitočet obnovování?
3. Jak micro:bit nastavuje jas jednotlivé LED, když nemůže měnit napětí?
4. Proč LED při multiplexování svítí jen zlomek času a přesto se nezdá, že by svítila slaběji?

## 2. Dotykové logo a kroužky: dva způsoby snímání dotyku

Logo a kroužky na pinech poznají dotek rozdílně: logo kapacitou těla, kroužky odporem kůže. Pokus to ukáže na tom, že kroužek potřebuje druhý dotek, ale logo ne.

### Pokus 2.1: Kapacita proti odporu kůže

**Cíl:** zjistit, kdy logo a kdy kroužek P0 reagují, a vysvětlit rozdíl.

**Pomůcky:** micro:bit, krokosvorka s vodičem, kousek alobalu, papír, kapka vody; volitelně multimetr.

**Program:**

```python
def on_forever():
    if input.logo_is_pressed():
        basic.show_string("L")
    elif input.pin_is_pressed(TouchPin.P0):
        basic.show_string("0")
    else:
        basic.clear_screen()
    basic.pause(50)

basic.forever(on_forever)
```

**Postup:**

1. Dotkněte se loga jedním prstem a sledujte displej.
2. Dotkněte se jedním prstem kroužku P0 (druhou ruku nechte ve vzduchu). Pak se druhou rukou dotkněte kroužku GND a znovu P0.
3. Zopakujte dotek P0 se suchým prstem a s prstem lehce navlhčeným vodou.
4. Připojte krokosvorkou kousek alobalu k P0, dotkněte se alobalu a druhou rukou GND.
5. Položte na logo list papíru a zkuste, jestli micro:bit stále reaguje. Totéž zkuste s kroužkem P0.
6. Volitelně: multimetrem v rozsahu ohmů změřte odpor mezi dvěma prsty, nejdřív suchými, pak navlhčenými.

**Co očekávat:**

- Logo reaguje na jeden dotek, pro kroužek je potřeba spojit tělem P0 a GND.
- S navlhčeným prstem se kroužek rozpozná spolehlivěji než se suchým.
- Alobal se chová jako prodloužení kroužku.
- Logo by mělo reagovat i přes tenký papír (měří kapacitu), kroužek přes papír reagovat nebude (potřebuje vodivý kontakt).
- Odpor mezi prsty je řádu stovek kiloohmů až megaohmů a po navlhčení klesne.

**Kontrolní otázky:**

1. Proč kroužek potřebuje dotek GND, ale logo ne?
2. Proč vlhký prst vede lépe než suchý?
3. Jak procesor pozná, že se prstem dotýkáte loga?
4. Proč dotykové displeje telefonů pracují i přes sklo a kroužky na pinech přes papír ne?


## 3. Akcelerometr: tíha, náklon a volný pád

Akcelerometr měří zrychlení v miligech: v klidu měří tíhu (1 g) a ve volném pádu téměř nulu. První pokus z toho určí náklon, druhý zachytí pád.

### Pokus 3.1: Tíha a náklon

**Cíl:** ukázat, že v klidu měří akcelerometr tíhu Země, a z hodnot spočítat náklon desky.

**Pomůcky:** micro:bit, rovný stůl, papír na zápis.

**Program:**

```python
def on_forever():
    x = input.acceleration(Dimension.X)
    y = input.acceleration(Dimension.Y)
    z = input.acceleration(Dimension.Z)
    celkem = Math.round(Math.sqrt(x * x + y * y + z * z))
    serial.write_value("x", x)
    serial.write_value("y", y)
    serial.write_value("z", z)
    serial.write_value("celkem", celkem)
    basic.pause(50)

basic.forever(on_forever)
```

**Postup:**

1. Nahrajte program a zobrazte graf hodnot (*Show data Device*).
2. Položte desku na stůl displejem nahoru a zapište hodnoty x, y, z a celkem.
3. Zopakujte pro dalších pět poloh: displejem dolů, na levý a pravý bok, na horní hranu a na spodní hranu s konektorem.
4. Z hodnot v jedné šikmé poloze spočítejte náklon podle vzorce:

   **θ = arctan( x / √(y² + z²) )**

5. Deskou několikrát zatřeste a sledujte hodnotu celkem.

| Poloha | x (mg) | y (mg) | z (mg) | celkem (mg) |
| --- | --- | --- | --- | --- |
| Displej nahoru |  |  |  |  |
| Displej dolů |  |  |  |  |
| Levý bok |  |  |  |  |
| Pravý bok |  |  |  |  |
| Horní hrana |  |  |  |  |
| Spodní hrana |  |  |  |  |

**Co očekávat:**

- V každé poloze je jedna osa přibližně ±1000 mg a ostatní dvě blízko nuly (znaménko závisí na orientaci os).
- Hodnota celkem je ve všech klidových polohách přibližně 1000 mg.
- Při zatřesení hodnota celkem vzroste na násobky klidové hodnoty.

**Kontrolní otázky:**

1. Proč je celkové zrychlení v klidu vždy přibližně 1 g, ať je deska jakkoli nakloněná?
2. Jaký náklon dostanete, když je x = 500 mg, y = 0 a z = 866 mg?
3. Proč akcelerometr nepozná otáčení desky kolem svislé osy, když leží na stole?
4. Jak micro:bit pozná gesto „zatřesení“?

### Pokus 3.2: Volný pád

**Cíl:** zaznamenat pokles zrychlení při pádu a porovnat dobu pádu s výpočtem.

**Pomůcky:** micro:bit s držákem na dvě baterie AAA (nebo dlouhý měkký kabel), polštář nebo matrace, pravítko nebo metr.

**Příprava:** v editoru klikněte na *Extensions* a přidejte rozšíření *datalogger*.

**Program:**

```python
def on_button_a():
    datalogger.delete_log(datalogger.DeleteType.FAST)   # smaže starý záznam
    datalogger.set_column_titles("celkem")
    datalogger.include_timestamp(FlashLogTimeStampFormat.SECONDS)
    music.play_tone(880, 200)                           # pípnutí = začátek
    for i in range(80):                                 # 80 vzorků po asi 20 ms
        x = input.acceleration(Dimension.X)
        y = input.acceleration(Dimension.Y)
        z = input.acceleration(Dimension.Z)
        celkem = Math.round(Math.sqrt(x * x + y * y + z * z))
        datalogger.log(datalogger.create_cv("celkem", celkem))
        basic.pause(20)
    music.play_tone(440, 400)                           # nižší pípnutí = konec
input.on_button_pressed(Button.A, on_button_a)
```

**Postup:**

1. Nahrajte program (tlačítkem *Download*), odpojte USB kabel a napájejte desku z baterií, aby jí kabel při pádu nebránil. Záznam se maže jen stiskem A, ne restartem, takže zůstane v paměti i po opětovném připojení k počítači.
2. Nad polštářem držte desku 30 cm nad podložkou. Stiskněte A a hned po pípnutí desku pusťte.
3. Po skončení připojte desku k počítači, na disku MICROBIT otevřete MY_DATA.HTM a v *Visual Preview* najděte pokles hodnoty celkem.
4. Odečtěte dobu, po kterou je hodnota blízko nule, a porovnejte s výpočtem.
5. Zopakujte z výšky 20 cm a 40 cm.

**Co očekávat:**

- Před pádem je hodnota celkem kolem 1000 mg, během pádu klesne k nule, při dopadu na polštář krátce vzroste.
- Delší pád (větší výška) znamená delší úsek s hodnotou kolem nuly.

**Kontrolní otázky:**

1. Proč akcelerometr v pádu ukáže téměř nulu, přestože na desku stále působí gravitace?
2. Spočítejte dobu pádu z výšky 30 cm podle vzorce t = √(2h/g).
3. Proč jsou astronauti na oběžné dráze v beztíži, i když tam gravitace nezmizela?
4. K čemu se detekce pádu využívá v notebooku nebo telefonu?

## 4. Magnetometr: pole magnetu a vzdálenost

Magnetometr měří sílu magnetického pole v mikroteslách a pole magnetu slábne s třetí mocninou vzdálenosti. Pokus to ověří z naměřených dat.

### Pokus 4.1: Pole magnetu v závislosti na vzdálenosti

**Cíl:** změřit zemské pole a ověřit, že pole malého magnetu klesá přibližně s 1/r³.

**Pomůcky:** micro:bit, slabý magnet (například z lednice), pravítko, tabulka, daleko od kovových předmětů a počítačových reproduktorů.

**Program:**

```python
input.calibrate_compass()   # naklánějte desku, dokud se displej nezaplní

def on_forever():
    pole = input.magnetic_force(Dimension.STRENGTH)   # v mikroteslách
    serial.write_value("pole", Math.round(pole * 10) / 10)
    basic.pause(100)

basic.forever(on_forever)
```

**Postup:**

1. Nahrajte program a proveďte kalibraci (naklánějte desku, až se zaplní celý displej).
2. Daleko od magnetu zapište naměřené pole B0, tedy zemské pole.
3. Magnet přibližujte po jedné straně desky ve vzdálenostech 20, 15, 10, 7, 5 a 3 cm. Každou hodnotu zapište.
4. Vypočtěte rozdíl B − B0 a hodnotu 1/r³.
5. Vyneste do grafu B − B0 (osa y) proti 1/r³ (osa x).

| r (cm) | B (µT) | B − B0 (µT) | 1/r³ (1/cm³) |
| --- | --- | --- | --- |
| 20 |  |  |  |
| 15 |  |  |  |
| 10 |  |  |  |
| 7 |  |  |  |
| 5 |  |  |  |
| 3 |  |  |  |

**Co očekávat:**

- Zemské pole vychází řádově desítky mikrotesel (ve střední Evropě kolem 48 µT, uvnitř budov to bývá odlišné kvůli ocelové konstrukci).
- Při přibližování magnetu hodnota prudce roste, při zmenšení vzdálenosti na polovinu přibližně osmkrát.
- Body v grafu leží zhruba na přímce.
- Odečítat velikosti pole je jen hrubá aproximace, protože pole magnetu míří jinam než zemské. Přesnější je odečítat vektory x, y a z zvlášť.

**Kontrolní otázky:**

1. Proč se kompas před použitím kalibruje?
2. O kolik se zvětší pole magnetu, když vzdálenost zmenšíte ze 10 cm na 5 cm?
3. Proč se nemá magnet přikládat těsně k desce?
4. Jak byste z micro:bitu a magnetu vyrobili poplachový senzor otevřených dveří?

## 5. Teploměr: teplota čipu

Teploměr v micro:bitu měří teplotu křemíku uvnitř procesoru, ne vzduchu, a proto ji pokus srovná s referenčním teploměrem.

### Pokus 5.1: Zahřívání čipu a rozdíl proti teplotě vzduchu

**Cíl:** ukázat, že údaj teploměru sleduje teplotu čipu, a změřit rozdíl proti teplotě vzduchu.

**Pomůcky:** micro:bit, referenční pokojový teploměr, stopky nebo hodinky, tabulka na zápis.

**Program:**

```python
def on_forever():
    serial.write_value("teplota", input.temperature())   # celé stupně Celsia
    basic.pause(1000)

basic.forever(on_forever)
```

**Postup:**

1. Nechte desku alespoň 10 minut bez napájení v místnosti, aby se vyrovnala s teplotou okolí. Zapište teplotu referenčním teploměrem.
2. Připojte desku k počítači, nahrajte program a zobrazte graf hodnot (*Show data Device*).
3. Každou minutu po dobu 10 minut zapisujte údaj z micro:bitu.
4. Na konci přiložte prst na zadní stranu desky k hlavnímu čipu na 30 sekund a sledujte změnu.
5. Pak na desku zafoukejte nebo ji ofoukněte ventilátorem a sledujte pokles.

| Minuta | micro:bit (°C) | Referenční teploměr (°C) |
| --- | --- | --- |
| 0 |  |  |
| 2 |  |  |
| 4 |  |  |
| 6 |  |  |
| 8 |  |  |
| 10 |  |  |

**Co očekávat:**

- Údaj se v prvních minutách po zapojení zvýší o několik stupňů a pak se ustálí, protože se čip zahřeje vlastní spotřebou.
- Údaj je vyšší než teplota vzduchu, rozdíl je offset.
- Teplo prstu hodnotu zvýší, proud vzduchu ji sníží.
- Údaj je v celých stupních, takže se mění skokově.

**Kontrolní otázky:**

1. Proč se údaj micro:bitu liší od teploty vzduchu?
2. Na jakém principu pracuje teploměr uvnitř čipu?
3. Jak by se dal offset kompenzovat v programu?
4. Jak se změní údaj, když program zapne rádio nebo rozsvítí celý displej, a proč?

## 6. Mikrofon: hlasitost a spínač na zatleskání

Mikrofon neměří výšku tónu, ale hlasitost, a z hlasitosti se dá udělat jednoduchý spínač. První pokus zkoumá hlasitost podle vzdálenosti, druhý práh spínání.

### Pokus 6.1: Hlasitost a vzdálenost od zdroje

**Cíl:** ověřit, že údaj mikrofonu klesá se vzdáleností od zdroje zvuku.

**Pomůcky:** micro:bit, zdroj stálého tónu (telefon se zapnutým tónovým generátorem na stálou hlasitost), metr, tabulka. Pokus dělejte v tichu.

**Program:**

```python
def on_forever():
    hlasitost = input.sound_level()   # 0 až 255
    serial.write_value("hlasitost", hlasitost)
    basic.pause(50)

basic.forever(on_forever)
```

**Postup:**

1. Najděte mikrofon: malý otvor na přední straně desky se svítící tečkou vedle něj.
2. Bez zdroje zvuku zapište hodnotu ticha (několik hodnot, průměr).
3. Zapněte tón a umístěte telefon ve vzdálenosti 10, 20, 40 a 80 cm od mikrofonu. Při každé vzdálenosti zapište průměr z pěti hodnot.
4. Nezapomeňte telefon i desku nechat při všech měřeních ve stejné poloze a orientaci.

| Vzdálenost (cm) | Hlasitost (0 až 255) |
| --- | --- |
| ticho |  |
| 10 |  |
| 20 |  |
| 40 |  |
| 80 |  |

**Co očekávat:**

- V tichu hodnota není nulová, protože mikrofon snímá i šum prostředí.
- S rostoucí vzdáleností hodnota klesá, ale ne přesně přímo úměrně.
- Údaj není v decibelech, je to bezrozměrná hodnota od 0 do 255.

**Kontrolní otázky:**

1. Jak funguje MEMS mikrofon a co se v něm mění při dopadu zvuku?
2. Proč v tichu mikrofon neukazuje nulu?
3. Akustický tlak klesá s rostoucí vzdáleností zhruba jako 1/r. O kolik decibelů se sníží při zdvojnásobení vzdálenosti?
4. Proč údaj `input.sound_level()` neumožňuje určit výšku tónu?

### Pokus 6.2: Spínač na zatleskání

**Cíl:** nastavit práh hlasitosti, při kterém tlesknutí přepne srdíčko na displeji.

**Pomůcky:** micro:bit.

**Program:**

```python
PAUZA = 500       # ochrana proti dvojitému sepnutí (ms)
svit = False
posledni = 0

input.set_sound_threshold(SoundThreshold.LOUD, 150)   # práh (0 až 255)

def on_sound_loud():
    global svit, posledni
    if control.millis() - posledni < PAUZA:
        return
    posledni = control.millis()
    svit = not svit
    if svit:
        basic.show_icon(IconNames.HEART)
    else:
        basic.clear_screen()
input.on_sound(DetectedSound.LOUD, on_sound_loud)
```

**Postup:**

1. Nahrajte program a zatleskejte. Srdce se rozsvítí, druhým zatleskáním zhasne.
2. Vyzkoušejte reakci na šepot, běžnou řeč, hlasité volání a tlesknutí z 1 m.
3. Změňte práh na 100 a pak na 200 a opakujte zkoušku. Zapište, co spínání spustí.
4. Nastavte `PAUZA = 0` a znovu zatleskejte. Sledujte, co se stane.

**Co očekávat:**

- Při nižším prahu program reaguje i na hlasitou řeč, při vyšším jen na hlasité tlesknutí.
- Bez ochranné pauzy se může spínač přepnout víckrát po jednom tlesknutí, protože zvuk trvá a odráží se.

**Kontrolní otázky:**

1. K čemu je ochranná pauza 500 ms a s kterým jevem u tlačítek ji můžete srovnat?
2. Jak práh ovlivňuje citlivost a falešná spuštění?
3. Jak byste program upravili, aby spínač reagoval jen na dvě tlesknutí po sobě?

---
### Pokus: Tón A4 bez zátěže a se zátěží

**Cíl:** ověřit, že tón vytvářený programově (ručním přepínáním pinu) závisí na tom, co procesor dělá, a porovnat ho s tónem bez zátěže.

**Pomůcky:** micro:bit V2, piezo reproduktor nebo sluchátko, dva vodiče s krokosvorkami. Reproduktor připojte mezi P0 a GND. Sluchátka jsou mono, takže při zapojení krokosvorkami stačí připojit jen jeden měnič.

**Program:** [otevřít sdílený program v MakeCode](https://makecode.microbit.org/S52076-77326-64942-01113)

```python
# Experiment: Vliv zatížení procesoru na generování tónu
# Test A: tón bez zátěže
# Test B: tón se zátěží
# Připoj piezo reproduktor/sluchátka mezi P0 a GND.

POLOPERIODA = 1136   # mikrosekundy pro tón 440 Hz
DOBA = 3000          # délka pokusu v ms

def zatez():
    # Zbytečně zaměstnáme procesor výpočty
    s = 0
    for i in range(100):
        s = s + i * i

def ton(se_zatezi):
    start = control.millis()

    while control.millis() - start < DOBA:
        pins.digital_write_pin(DigitalPin.P0, 1)
        control.wait_micros(POLOPERIODA)
        pins.digital_write_pin(DigitalPin.P0, 0)
        control.wait_micros(POLOPERIODA)

        if se_zatezi:
            zatez()

    pins.digital_write_pin(DigitalPin.P0, 0)

# ZAČÁTEK EXPERIMENTU

basic.show_string("A")
basic.pause(500)

# 1. Tón bez zátěže
ton(False)
basic.pause(1000)
basic.show_string("B")
basic.pause(500)

# 2. Tón se zátěží
ton(True)
basic.pause(500)
basic.show_icon(IconNames.HAPPY)
```

**Postup:**

1. Připojte reproduktor mezi P0 a GND.
2. Nahrajte program do micro:bitu (tlačítko *Download*).
3. Poslouchejte tón při písmenu A (bez zátěže, 3 s) a pak při písmenu B (se zátěží, 3 s).
4. Porovnejte výšku obou tónů. Můžete použít ladičku v mobilu a tón A4 (440 Hz) porovnat s referenčním.
5. Změňte počet průchodů cyklu ve funkci `zatez()` (například 100 na 20 a na 300) a opakujte. Zapište, jak se výška tónu mění.

**Co očekávat:**

- Tón A zní jako čisté A4, tedy kolem 440 Hz. Mírná odchylka je běžná, protože přepínání pinu a čtení času také něco trvají.
- Tón B zní nižší, protože k každé periodě se přičte doba výpočtu ve funkci `zatez()`, takže perioda se prodlouží a kmitočet klesne.
- Čím větší zátěž (víc průchodů cyklu), tím nižší tón.

**Kontrolní otázky:**

1. Proč má tón A zhruba kmitočet 440 Hz, když je poloperioda 1136 µs? Spočítejte f = 1 / (2 · 1136 µs).
2. Proč se tón B liší od tónu A a proč je nižší, a ne vyšší?
3. Proč by se hardwarově generovaný tón (PWM nebo časovač) při stejné zátěži nezměnil?
4. Jak byste v programu zjistili, o kolik se perioda prodloužila?

---

## Klíč: stručné odpovědi

Odpovědi jsou pořadím otázek u jednotlivých pokusů; kde jde o výpočet, je uveden výsledek.

**Pokus 1.1**

1. LED je přechod PN. Foton v něm vytvoří pár elektron–díra a vzniklý fotoproud vybíjí kapacitu přechodu; z doby vybíjení procesor určí osvětlení.
2. Osvětlení klesá s druhou mocninou vzdálenosti a k senzoru se přidává i okolní světlo, takže závislost není lineární.
3. Změřenou úroveň světla lze využít k automatické změně jasu displeje nebo k zapnutí nočního světla pod zvolenou hranicí.

**Pokus 1.2**

1. LED jsou v mřížce 5 řádků × 5 sloupců, takže stačí 5 + 5 = 10 pinů.
2. f = v / d = 1 m/s / 0,015 m ≈ 67 Hz.
3. Jas se nastavuje dobou, po kterou LED v periodě svítí (střída), ne napětím.
4. Oko je setrvačné a vnímá průměrný jas za krátký čas, ne jednotlivé záblesky.

**Pokus 2.1**

1. Kroužek potřebuje uzavřený obvod P0–tělo–GND (měří se vodivost). Logo měří změnu kapacity vůči okolí a druhý kontakt nepotřebuje.
2. Vlhkost sníží odpor kůže a zlepší kontakt.
3. Prst přidá k elektrodě kapacitu, elektroda se nabíjí pomaleji a procesor to pozná podle delší doby nabíjení.
4. Elektrické pole prochází izolantem (sklem, papírem), ale odporové snímání potřebuje vodivý kontakt.


**Pokus 3.1**

1. Gravitace působí vždy stejně, náklon jen rozděluje její vektor mezi osy, takže jeho velikost zůstává.
2. θ = arctan(500 / 866) = 30°.
3. Při otáčení kolem svislé osy se směr tíže nemění, proto je potřeba magnetometr nebo gyroskop.
4. Celkové zrychlení krátce překročí zvolený práh.

**Pokus 3.2**

1. Akcelerometr měří sílu, kterou je držena pohyblivá hmota. Ve volném pádu padá spolu s pouzdrem, takže se nevychyluje.
2. t = √(2 · 0,3 / 9,81) ≈ 0,25 s.
3. Astronauti spolu se stanicí volně padají kolem Země, gravitace tam stále působí (kolem 90 % pozemské).
4. Například k zaparkování hlaviček pevného disku nebo k rozpoznání pádu telefonu.

**Pokus 4.1**

1. K zemskému poli se přidávají stálá pole od magnetů, oceli a proudů na desce. Kalibrace najde jejich posun a odečte ho.
2. Osmkrát (2³).
3. Senzor má omezený rozsah a u silného pole se nasytí. Navíc model dipólu platí jen pro vzdálenost mnohem větší než rozměr magnetu.
4. Magnet na křídle dveří a micro:bit u rámu. Při otevření pole klesne pod práh a program spustí alarm.

**Pokus 5.1**

1. Měří teplotu čipu, který se zahřívá vlastní spotřebou, ne teplotu vzduchu.
2. Napětí na přechodu PN závisí na teplotě (asi −2 mV/K); čip ho změří a přepočítá.
3. Odečtením offsetu zjištěného při ustáleném stavu, například `input.temperature() - OFFSET`.
4. Zvýší se spotřeba a tím i teplo, takže údaj stoupne.

**Pokus 6.1**

1. Membrána nad pevnou elektrodou tvoří kondenzátor. Zvuk mění vzdálenost elektrod, a tím kapacitu, a obvod ji převede na napětí.
2. Mikrofon i převodník mají vlastní šum a v prostředí je vždy šum pozadí.
3. Poloviční tlak odpovídá poklesu o 6 dB.
4. Funkce vrací jen úroveň signálu (amplitudu), ne kmitočet.

**Pokus 6.2**

1. Zvuk trvá a odráží se, takže práh překročí víckrát; podobně se tlačítko při stisku „zakmitává“ (debouncing).
2. Nízký práh je citlivý, ale spouští se i od řeči; vysoký práh je odolnější, ale může tlesknutí zmeškat.
3. Při prvním tlesknutí si uložte čas (`control.millis()`) a druhé tlesknutí do jedné sekundy teprve přepněte.
