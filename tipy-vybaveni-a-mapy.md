# 6. Praktické tipy, mapy a vylepšení výbavy (nepovinné)

Tato kapitola je **nepovinná a rozšiřující**. Shrnuje osvědčené zkušenosti z praxe mentora a absolventů minulých běhů kurzu. Najdete zde doporučení na užitečné doplňky k hardwaru, návody a odkazy ke stažení map pro sledování čáry i postup výroby vlastní odolné dráhy.

Tento dokument je živý – můžete jej v průběhu kurzu obohacovat o další vlastní nápady a vychytávky!

---

## 1. Užitečné doplňky k hardwaru

### 🧲 Magnetický microUSB kabel
Při vývoji a ladění kódu budete kabel k desce **Pico:ed** připojovat a odpojovat desítkykrát za večer. 
- **Riziko u běžného kabelu:** Časté zasunování a vyndávání konektoru namáhá microUSB port na desce. Pokud navíc robot nečekaně vyjede ze stolu nebo dráhy a kabel zůstane připojený, hrozí vytržení konektoru z plošného spoje.
- **Výhoda magnetického kabelu:** V portu desky Pico:ed zůstává trvale zasunutá miniaturní magnetická koncovka. Samotný kabel stačí přiblížit a magnet se sám bezpečně spojí. Pokud robot cukne nebo ujede, kabel se v magnetickém spoji bezpečně a bez poškození rozpojí.
- **Ověřený tip z praxe:**
  - [AlzaPower MagCore 2in1 USB-C / micro USB 3A (1,5 m)](https://www.alza.cz/alzapower-magcore-2in1-usb-c-micro-usb-3a-1-5m-cerny-d6486450.htm)
  - [AlzaPower MagCore 2in1 USB-C / micro USB 3A (2 m)](https://www.alza.cz/alzapower-magcore-2in1-usb-c-micro-usb-3a-2m-cerny-d6486452.htm)

<!-- Obrázek magnetického kabelu v desce:
![Magnetický kabel v desce Pico:ed](images/magneticky-kabel.jpg)
-->

> [!NOTE]
> Magnetický kabel není povinný – veškerou práci zvládnete i s běžným microUSB kabelem. Jde o praktické doporučení pro ochranu desky a pohodlnější práci.

---

### 🔋 Baterie a napájení při dlouhém ladění
Robot JoyCar používá 4 ks speciálních **USB nabíjecích Li-ion akumulátorů**, které v sobě mají zabudovaný měnič udržující stabilní napětí **1,5 V** po celou dobu provozu (celkem 6 V pro robot).
- **Vlastnost těchto baterií:** Na rozdíl od běžných alkalických baterií jejich napětí s vybíjením neklesá, takže motory mají stále stejnou rychlost a senzory čtou stabilně. Jakmile se však akumulátor vybije, vestavěná elektronika jej **skokově vypne**.
- **Tipy z praxe:**
  - **Druhá sada baterií:** Mít po ruce náhradní sadu 4 ks baterií znamená, že zatímco se jedna sada nabíjí přes USB, vy můžete plynule pokračovat v práci.
  - **Externí zdroj 6 V:** Pro dlouhé statické ladění algoritmů na stole (např. kalibrace senzorů čáry, testování displeje nebo stavových automatů) lze robot napájet ze stabilizovaného zdroje 6 V DC s dostatečně dlouhým a ohebným přívodním kabelem.

---

## 2. Testovací mapa a dráha pro robota

Autonomní robot JoyCar se orientuje pomocí odrazových infračervených (IR) senzorů na spodní straně podvozku. Pro spolehlivou jízdu po čáře potřebuje **výrazný kontrast mezi světlým podkladem a černou čarou** (ideální šířka čáry je **přibližně 15 mm**, což přesně odpovídá standardní elektrikářské izolační pásce).

Existuje několik způsobů, jak si testovací dráhu připravit:

### Možnost A: Černá elektrikářská izolační páska (nejrychlejší řešení)
- Stačí zakoupit běžnou černou elektrikářskou pásku šířky **15 mm** (lze koupit v každém hobbymarketu nebo elektru za pár desítek korun).
- Nalepte ji na světlou podlahu, lamino desku nebo velký karton.
- *Pozor na ostré pravé úhly v zatáčkách – robot má svou setrvačnost a poloměr otáčení, proto je lepší začínat plynulými oblouky.*

---

### Možnost B: Modulární dlaždice RobotSquare (tisk na A4)
Velmi oblíbený systém modulárních papírových dlaždic, které si můžete vytisknout na běžné domácí tiskárně na papíry formátu A4 a poskládat z nich libovolnou trasu:
- 📖 [RobotSquare – Popis principu sledování čáry a dlaždic](https://robotsquare.com/2012/11/28/line-following/)
- 📄 [RobotSquare – PDF šablona dlaždic k přímému tisku (A4)](http://robotsquare.com/wp-content/uploads/2012/11/linefollowtiles.pdf)

---

### Možnost C: Oficiální předlohy map pro kurz (A1 / A3)
Pro finální projekt a křižovatky máme k dispozici připravené PDF šablony pro velkoformátový tisk:
- 📂 **[Odkaz na stažení souborů map z OneDrive](https://1drv.ms/f/c/c957b235b7cc93a4/IgC6aauu_nNZQrMK8IJcA2njASdURRjqxCBx6xwbaK_lPdo?e=lDsPzl)**
  - `maps.pdf` – obsahuje dva ovály pro jízdu po čáře a rozvržení křižovatek pro náš projekt (formát A1).
  - `maps - split to A3.pdf` – stejná mapa rozdělená na formát A3 pro tisk v běžných copycentrech.
  - `maps2.pdf` – dvě alternativní rozložení křižovatek pro pokročilejší testování.
  - `maps2 - split to A3.pdf` – verze maps2 rozdělená na listy A3.

---

### 💡 Návod: Jak vyrobit pevnou a srolovatelnou mapu na lino (zkušenost mentora)

Pokud máte doma málo místa a potřebujete dráhu po práci snadno uklidit, skvěle se osvědčil podklad z linolea:

1. **Příprava dlaždic:** Vytiskněte a pečlivě vystříhejte jednotlivé dlaždice na papíry formátu A4.
2. **Výběr rozměrů:** Vyberte místo v místnosti, kde budete dráhu rozkládat, a určete maximální rozměry.
3. **Základ z linolea:** Pořiďte kus běžného linolea nebo PVC podlahové krytiny odpovídajícího rozměru (často se dají velmi levně sehnat odřezky ve stavebninách či podlahářstvích).
   - *Výhoda linolea:* Je těžké a leží zcela rovně, nezvlní se jako papír, netrhá se a lze jej kdykoliv srolovat a postavit do kouta.
4. **Návrh tratě:** Rozložte dlaždice "nasucho" tak, aby dráha obsahovala jak rovinky a oblouky pro jízdu po čáře, tak křižovatky pro plnění úloh projektu.
5. **Lepení:** Jednotlivé díly pečlivě srovnejte podle čar (aby na sebe čáry plynule navazovaly bez schodů) a přilepte k linoleu lepidlem na papír nebo tenkou oboustrannou lepicí páskou.

> [!TIP]
> Výsledkem je rovný podklad s vysokým kontrastem bílé a černé, po kterém robot hladce přejíždí bez zadrhávání podvozku či senzorů.

<!-- Obrázky mapy na linoleu:
![Rozložená mapa na linoleu](images/mapa-linoleum-hotova.jpg)
![Srolovaná mapa pro snadný transport](images/mapa-linoleum-srolovana.jpg)
![Detail spasování čar](images/mapa-lepeni-detail.jpg)
-->

---

## 3. 💡 HW úpravy a tuning JoyCaru vyzkoušené v kurzu

> [!NOTE]
> Následující úpravy jsou **čistě tuning a dobrovolné rozšíření**. Nejsou nutné pro úspěšné absolvování kurzu ani pro odevzdávání běžných úkolů.
> Berte je jako inspiraci od mentora kurzu (**Jan Chaloupek**), co všechno lze se stávajícím hardwarem dokázat a jaké možnosti stavebnice JoyCar nabízí, pokud chcete experimentovat a posunout robotiku o úroveň výš.

V této části najdete přehled vyzkoušených úprav:
1. **Šest senzorů čáry a odhalení tajemství I2C expandéru**
2. **Fotopostup výroby adaptérové „kostky“ pro přídavné senzory**
3. **Plexisklový držák baterie s rychloupínáním bez nářadí**
4. **Uchycení dvojitého serva – návrh 3D součástky**
5. **Znakový LCD displej přes I²C (zobrazování odometrie a křižovatek)**
6. **Rozšíření hlavního konektoru JoyCaru pro 3pinové periferie**
7. **Robustní motory s kovovou osou a integrovaným enkodérem**
8. **Záchrana robota: Kompletní náhrada motorového H-můstku (PCA9685 + L298N)**

---

### 3.1 Šest senzorů čáry a odhalení tajemství I2C expandéru

#### 🔍 Nezdokumentovaná změna výrobce – Kde jsou zapojené enkodéry rychlosti?
Podle oficiální dokumentace výrobce JoyCar by měly být všechny hlavní senzory připojeny k 8bitovému I2C expandéru **PCF8574** (adresa `0x38`):
- 2 senzory rychlosti (optické enkodéry otáčení kol)
- 2 senzory překážek (infračervené snímače přiblížení)
- 3 senzory sledování čáry  
*(Dohromady 7 senzorů obsazujících 7 bitů z 8).*

**Realita na naší verzi robota:**  
Výrobce provedl **nezdokumentovanou změnu zapojení základní desky**, která v minulém běhu kurzu způsobila velké trápení, protože senzory rychlosti nešlo z I2C expandéru vyčíst. Až noční měření šikovného hardwaráře kurzu odhalilo skutečnost:
- **Senzory rychlosti (enkodéry) NEJSOU připojeny k I2C expandéru!**
- Jsou zapojeny **přímo na piny P14 a P15** procesorové desky micro:bit / Pico:ed.

**Co to znamená pro nás?**  
Na I2C expandéru je reálně připojeno **pouze 5 senzorů** (3 čárové + 2 překážkové). **Celé 3 bity jsou zcela volné!**  
Tyto 3 nepoužité piny expandéru jsou vyvedeny na dlouhý rozšiřující konektor na horní straně základní desky JoyCaru a jsou popsané jako:
- **`EOUT0`** (bit 0 na I2C expandéru)
- **`EOUT1`** (bit 1 na I2C expandéru)
- **`EOUT7`** (bit 7 na I2C expandéru)

---

#### 🚦 Proč 3 senzory čáry nestačí na spolehlivou detekci křižovatek?
- Pro samotnou jízdu po čáře stačí 2 diskrétní senzory.
- Pro detekci křižovatky by se na první pohled zdálo, že 3 senzory stačí (stačí přece, aby se aktivovaly 2 senzory najednou).
- **Proč to v praxi selhává:**  
  Při sledování čáry robot neustále jemně zatáčí zprava doleva a zpět (kmitá kolem čáry). Pokud robot dorazí k odbočce právě v momentě, kdy je krajním senzorem nad čárou, **odbočku zcela mine bez toho, aby ji kterýkoliv senzor zachytil**.  
  Pro spolehlivou a robustní detekci křižovatek je potřeba **alespoň 5 senzorů** (přidat na každý bok ještě jeden předsazený senzor).

---

#### 🛠️ Způsob A: Odpojení senzorů překážek (rychlé řešení pro 5 senzorů čáry)
1. Odpojte konektory obou předních senzorů překážek.
2. Místo nich připojte 2 dodatečné senzory čáry umístěné na bocích podvozku.
3. Funguje to spolehlivě, ale robot přijde o možnost detekovat překážky před sebou těmito senzory.
4. Vyžaduje to vyvrtání dalších otvorů do spodní desky podvozku pro šroubky senzorů.

<!-- Obrázky Způsobu A:
![Odpojené konektory senzorů překážek](images/senzory-prekazek-odpojene.jpg)
![Přídavné senzory přišroubované zespodu do navrtané desky](images/senzory-zespodu-navrtane.jpg)
-->

> [!TIP]
> **Video ukázka:** Podívejte se, jak lze stavy senzorů živě přenášet a vizualizovat na maticovém LED displeji Pico:edu:  
> 🎥 **[Video na OneDrive – Vizualizace senzorů na displeji](https://1drv.ms/v/s!AqSTzLc1slfJlJR_47mjA5mhaky1GQ?e=4n5zWL)**

---

#### ⚡ Způsob B: Využití volných pinů EOUT – až 6 senzorů čáry i 2 senzory překážek!
Díky volným pinům I2C expandéru nemusíte senzory překážek odpojovat. Můžete připojit **až 3 další senzory čáry** a provozovat všech 8 bitů expandéru současně:
- Piny **`EOUT0`**, **`EOUT1`** a **`EOUT7`** na konektoru JoyCaru obsluhují signální vodiče (bity 0, 1 a 7).
- K senzoru je však potřeba přivést také **zem (GND / černý vodič)** a **napájení (VCC / červený vodič)**.

---

#### 📐 Rozmístění 6 senzorů čáry zespodu podvozku

Výsledné rozmístění 6 senzorů na spodní desce robota nabízí vynikající vlastnosti:

```
[ Krajní levý ]      [ Vnitřní 1 ][ Vnitřní 2 ][ Vnitřní 3 ][ Vnitřní 4 ]      [ Krajní pravý ]
 (detekce křiž.)                  (jemné sledování 15mm čáry)                   (detekce křiž.)
```

1. **Vnitřní 4 senzory:**
   - Jsou natěsnané těsně vedle sebe.
   - Jsou tak blízko, že standardní černá čára šířky **15 mm** dokáže aktivovat i 2 sousední senzory najednou, pokud čára prochází mezi nimi.
   - Získáváte tak teoreticky **až 10 jemných stavů polohy čáry vůči podvozku**, což umožňuje odstupňovat více intenzit zatáčení pro dokonale plynulou jízdu bez trhavých pohybů.
2. **Krajní 2 senzory:**
   - Jsou oddělené větší mezerou směrem k okrajům robota.
   - Pro detekci křižovatky stačí současná aktivace dvou senzorů.
   - Běžné kmitání robota při jízdě po čáře na rovince tyto krajní senzory vůbec nezasáhne, takže křižovatku nikdy neminete ani omylem nezachytíte falešný odbočovací signál.

<!-- Obrázky rozmístění 6 senzorů:
![Rozmístění 6 senzorů na spodní straně podvozku](images/6-senzoru-rozmisteni.jpg)
![Detail 15mm čáry pod 4 vnitřními senzory](images/6-senzoru-detail-cary.jpg)
-->

---

### 3.2 Postup výroby adaptérové „kostky“ pro přídavné senzory krok za krokem

Vyrobil jsem si kompaktní „kostku“ z běžné dvouřadé kolíkové lišty, která řeší rozvod signálů, napájení a země pro 3 přídavné senzory čáry:

#### 🛠️ Krok za krokem:
1. **Výchozí součástka:** Běžná dvouřadá kolíková lišta s roztečí 2,54 mm.
2. **Zkrácení lišty:** Lištu zkraťte na velikost **2×9 pinů** (fungovalo by to i s úspornější velikostí 2×7 pinů).
3. **Pájení vodivých cest:** Na piny lišty připájejte 2 samostatné spoje z odizolovaného drátu (jednu sběrnici pro zem GND, druhou pro napájení VCC).
4. **Kontrola vedení spojů:** Zkontrolujte správnost propojení zespodu i shora podle schématu.
5. **Izolace:** Spodní stranu s přečnívajícími piny odštípněte, obruste dohladka a důkladně zaizolujte černou elektrikářskou páskou, aby nedošlo k nechtěnému zkratu o součástky na desce JoyCaru.
6. **Pohled shora:** Zkontrolujte čistotu konektorových pinů.
7. **Barevný štítek:** Na vršek lišty nasaďte vytištěný papírový štítek s barevným značením pinů pro přehlednost při zapojování kabelů.
8. **Nasazení jumperů:** Do kostky zasuňte 3 propojovací jumpery, které ji přichytí k základnímu konektoru JoyCaru a současně přivedou zem (GND).
9. **Umístění na robotovi:** Kostka přesně dosedne na rozšiřující konektor JoyCaru v blízkosti pinů EOUT0, EOUT1 a EOUT7.
10. **Zapojení senzorů:** Do kostky zapojte 3pinové kabely přídavných senzorů (na fotografii jsou zapojeny 2 dodatečné senzory, ale k dispozici je plné místo i pro 3. senzor).

> [!CAUTION]
> **Kritické varování pro napájení (3,3 V vs. 5 V):**  
> Na konektoru JoyCaru se na ideálním místě nachází pin **5V** (který by lákal k přímému propojení dalším jumperem).  
> **To nikdy nedělejte!** Procesor Pico:ed i I2C expandér PCF8574 pracují s napětím **3,3 V**. Pokud byste senzory napájeli z 5 V, na signálních pinech by se objevilo 5 V a mohlo by dojít ke zničení expandéru i desky Pico:ed!  
> Proto je napájení 3,3 V vyřešeno **krátkým červeným propojovacím vodičem**, který přivádí bezpečné napětí 3,3 V z příslušného pinu na konektoru JoyCaru.

<!-- Fotodokumentace výroby kostky:
![1. Výchozí kolíková lišta](images/kostka-1-vychozi-lista.jpg)
![2. Zkrácená lišta na 2x9 pinů](images/kostka-2-zkracena-lista.jpg)
![3. Pájené spoje z odizolovaného drátu](images/kostka-3-pajene-spoje.jpg)
![4. Vedení spojů zespoda](images/kostka-4-vedeni-spoju-zespodu.jpg)
![5. Vedení spojů shora](images/kostka-5-vedeni-spoju-shora.jpg)
![6. Zaizolování spodku páskou](images/kostka-6-zaizolovana-paskou.jpg)
![7. Pohled shora na vyrobenou kostku](images/kostka-7-pohled-shora.jpg)
![8. Potištěný papír s barevným značením](images/kostka-8-barevny-papir.jpg)
![9. Výsledná kostka s jumpery](images/kostka-9-s-jumpery.jpg)
![10. Kostka položená na JoyCaru](images/kostka-10-na-joycaru-volne.jpg)
![11. Kostka zapojená s přídavnými senzory](images/kostka-11-zapojena-senzory.jpg)
-->

#### 🔄 Další (prodloužená) verze kostky – připojení 3,3 V přímo jumpery
V další vývojové variantě vznikla **prodloužená verze adaptérové kostky**:
- **Přímé propojení 3,3 V jumpery:** Díky prodloužení lišty lze napájení 3,3 V propojit přímo pomocí jumperů, takže odpadá nutnost vést samostatný červený vodič na dálku přes celou desku.
- **Příprava pro analogové senzory čáry:** Tato prodloužená kostka poskytuje více volných pozic s napájením a zemí, což je ideální pro připojení kabelů od dalších (např. analogových) senzorů čáry.
- *Zaznamenáno v diskuzním kanálu kurzu: „Senzory připojené k Joy-Car (až 6 senzorů čáry)“.*

<!-- Obrázky prodloužené kostky:
![Prodloužená verze kostky s přímým 3,3V jumperem](images/kostka-prodlouzena-1.jpg)
![Pohled na osazení na konektoru JoyCaru](images/kostka-prodlouzena-2.jpg)
![Příprava pro další kabely senzorů](images/kostka-prodlouzena-3.jpg)
-->

---

### 3.3 Plexisklový rychloupínací držák baterie

Při dynamických jízdách a prudkém zatáčení robota hrozí, že se baterie uvolní, posune nebo dokonce vypadne a přeruší napájení.

- **Vlastnosti plexisklového držáku:**
  - Pevně fixuje bateriový modul (battery pack) na podvozku.
  - **Výměna zcela bez nářadí:** Držák má v horní části vytvořenou praktickou drážku. Stačí vložit nehet do drážky, zatáhnout lehce k sobě a celý battery pack pohodlně vytáhnout směrem dozadu.
  - Zvyšuje mechanickou odolnost a usnadňuje bleskovou výměnu vybitých baterií během testování.

<!-- Obrázky plexisklového držáku:
![Plexisklový držák baterie na JoyCaru](images/drzak-baterie-1.jpg)
![Detail drážky a vysouvání battery packu](images/drzak-baterie-2.jpg)
-->

---

### 3.4 Uchycení dvojitého serva – návrh 3D součástky

Základní stavebnice JoyCar obsahuje držák pro jedno servo (např. pro natáčení ultrazvukového snímače), ale základní deska nabízí výstupy pro **dvě modelářská serva**.

- V 1. běhu kurzu jsme v rámci dobrovolného domácího úkolu řešili **návrh 3D tištěného dílu pro uchycení druhého serva**.
- Cílem bylo najít smysluplné využití obou serv najednou – například dvouosý mechanismus pro natáčení a naklápění snímače (Pan/Tilt), zvedací rameno, čisticí radlici nebo chapač překážek.

<!-- Obrázky 3D dílu pro servo:
![3D model uchycení druhého serva](images/uchyceni-serva-3d-1.jpg)
![Montáž druhého serva na robotovi](images/uchyceni-serva-3d-2.jpg)
![Detail dvouosého mechanismu](images/uchyceni-serva-3d-3.jpg)
-->

---

### 3.5 Znakový LCD displej přes sběrnici I²C

Čelní 5×5 LED matice desky Pico:ed je skvělá pro jednoduché ikony a rolování krátkých textů, ale pro detailní telemetrii za jízdy je výhodné připojit plnohodnotný znakový LCD displej (např. 16×2 nebo 20×4 znaků).

- **Výhody připojení přes I²C:**
  - Využívá pouze **2 vodiče pro data (SDA a SCL)** na rozšiřujícím konektoru.
  - Není nutné složitě zapojovat paralelní datovou sběrnici (D0–D7).
- **Využití v praxi:**
  - Živé zobrazování pozice a stavu navigace (odometrie):
    ```text
    x: 4
    y: 3
    theta: 90°
    ```
  - Okamžitý odečet stavu všech 6 senzorů čáry, aktuální rychlosti motorů či stavu řídicího automatu na křižovatkách.

<!-- Obrázky LCD displeje:
![Znakový LCD displej připojený přes I2C](images/lcd-displej-i2c-1.jpg)
![Pohled na umístění displeje na JoyCaru](images/lcd-displej-i2c-2.jpg)
![Displej zobrazující živá data odometrie](images/lcd-displej-odometrie.jpg)
-->

---

### 3.6 Rozšíření hlavního konektoru JoyCaru a evoluce periferií

Když na robota přidáte přídavné senzory čáry i LCD displej, původní kolíková lišta JoyCaru přestane stačit pro pohodlné napájení.

- **Účel vlastního rozšíření konektoru:**
  - Poskytuje stabilní sběrnici napájení a země pro více periferních modulů.
  - Umožňuje **přímé zacvaknutí standardních 3pinových servokonektorů** (GND, VCC, Signál) bez nutnosti bastlit kablíky.
  - Zjednodušuje kabeláž a radikálně zvyšuje spolehlivost za jízdy.
- **Konstrukce a připojení:**
  - Rozšíření je přichyceno k hlavnímu konektoru JoyCaru pomocí jumperů, které přivádějí **3,3 V** a **GND**.
  - **Bezpečnostní pravidlo 3,3 V:** Stejně jako u kostky senzorů byl záměrně obejit pin s 5 V. Pico:ed pracuje s 3,3V logikou a vyšší napětí na signálových vodičích by mohlo procesor poškodit.
- **Postupný vývoj:**
  - V raných verzích bylo 3,3V napájení přivedeno na dálku samostatným červeným kablíkem.
  - Pozdější celistvá verze rozšíření již integrovala jumpery pro kompaktní a robustní montáž.

<!-- Obrázky rozšíření konektoru:
![Starší verze s červeným napájecím kablíkem](images/rozsireni-konektoru-v1.jpg)
![Pokročilá verze rozšíření hlavního konektoru](images/rozsireni-konektoru-v2.jpg)
![Detail zapojení jumperů pro 3,3V a GND](images/rozsireni-konektoru-detail.jpg)
-->

---

### 3.7 Robustní motory s kovovou osou a integrovaným enkodérem

Při experimentování s vyšší zátěží a přesnějším odměřováním ujeté dráhy vyvstala otázka vylepšení pohonu robota:

#### Srovnání: Původní motor vs. Nový robustní motor s enkodérem
| Vlastnost | Původní motor v JoyCaru | Nový vylepšený motor |
|---|---|---|
| **Odkaz výrobce** | [DFRobot FIT0100](https://www.dfrobot.com/product-100.html) | [DFRobot FIT01458](https://www.dfrobot.com/product-1458.html) |
| **Dostupnost v ČR/EU** | Běžně v sadách | [Botland – Úhlový motor SJ02 120:1](https://botland.cz/stejnosmerne-motory-s-prevodovkou-a-kodery/6288-uhlovy-motor-s-prevodovkou-sj02-120-1-6v-160rpm-enkoder-6959420910199.html) |
| **Materiál hřídele** | Plastová osa | **Pevná kovová osa** (vysoká odolnost) |
| **Integrovaný enkodér** | Ne (pouze externí optická clonka v JoyCaru) | **Dvoukanálový magnetický enkodér** (směr i otáčky) |
| **Proud naprázdno (při 6 V)** | cca 120 mA | cca **250 mA** |
| **Proud v zátěži** | do 250 mA | **přes 500 mA** |
| **Cena** | cca 2,89 € | cca 6,31 € |

> [!WARNING]
> **Pozor na proudové zatížení hlavní desky JoyCaru!**  
> Kvůli podstatně vyššímu odběru proudu (při zátěži přes 500 mA na motor) **tento motor nepřipojujte přímo na hlavní desku JoyCaru** – hrozí přehřátí a poškození vestavěného motorového budiče.  
> Motor byl úspěšně testován na dedikované výkonnější desce **[Elecfreaks motor:bit](https://shop.elecfreaks.com/products/elecfreaks-micro-bit-motor-bit)** (v ČR na [HW Kitchen](https://www.hwkitchen.cz/motorbit-pro-microbit-rozsirujici-modul-pro-motory/)), která je na vyšší proudové špičky stavěná.

#### Mechanická montáž do podvozku JoyCaru:
Motory mají shodné vnější rozměry i rozteč montážních bodů, takže by se zdálo, že půjdou vyměnit kus za kus. Kvůli přidané elektronice enkodéru na zadní části se však motor nevejde do spodního výlisku podvozku. Pro montáž bylo nutné **do plastového podvozku vyříznout/vyvrtat dodatečný otvor**, aby se tělo motoru s enkodérem bez pnutí usadilo.

<!-- Obrázky motorů:
![Srovnání původního motoru a motoru s kovovou osou](images/motory-srovnani.jpg)
![1. Úprava podvozku JoyCaru pro nový motor](images/motor-uprava-podvozku-1.jpg)
![2. Vyříznutý otvor v plastu podvozku](images/motor-uprava-podvozku-2.jpg)
![3. Usazení motoru s enkodérem do podvozku](images/motor-uprava-podvozku-3.jpg)
![4. Detail kovové hřídele a uchycení](images/motor-uprava-podvozku-4.jpg)
![5. Testování s deskou motor:bit](images/motor-uprava-podvozku-5.jpg)
-->

---

### 3.8 🔧 Záchrana robota: Kompletní náhrada motorového H-můstku (PCA9685 + L298N)

Co dělat, když na JoyCaru selže integrovaný H-můstek řízení motorů?  
Oficiální reklamace a výměna základní desky přes R_D sice funguje, ale v průběhu kurzu může trvat i několik týdnů, během kterých by student zůstal bez funkčního robota.

JoyCar lze však **plnohodnotně oživit svépomocí** pomocí dvou levných, běžně dostupných modulů připojených přes I²C sběrnici:

#### 1. 🔵 PCA9685 – 16kanálový 12bitový I²C PWM generátor (řízení rychlosti)
Slouží k vytváření přesného PWM signálu pro oba motory.
- **Výhoda:** 12bitové rozlišení (hodnoty 0–4095) poskytuje výrazně jemnější regulaci otáček než původní 8bitový čip PCA9633 (0–255).
- **I²C adresa:** Výchozí adresa modulu je `0x40`. Propájením adresních plošek A0 a A5 na modulu ji lze změnit na `0x61` (přímo vedle adresy PCA9633 na JoyCaru), není to však nutné, pokud `0x40` nekoliduje s jinou periferií.
- **Zapojení do JoyCaru:**
  - `GND` $\rightarrow$ `GND` JoyCar
  - `VCC` $\rightarrow$ `3V3` JoyCar
  - `SCL` $\rightarrow$ `SCL` JoyCar
  - `SDA` $\rightarrow$ `SDA` JoyCar
- **Dostupnost:** [LaskaKit PCA9685](https://www.laskakit.cz/16-kanalovy-12-bit-pwm-servo-mini-shield-i2c-pca9685/) nebo [Drátek PCA9685](https://dratek.cz/arduino-platforma/1686-iic-i2c-modulovy-driver-servo-motoru-pro-arduino-pca9685-16-kanalu-12-bit-pwm.html).
- 🎥 **Video:** [Ukázka PWM signálu generovaného přes PCA9685 na OneDrive](https://1drv.ms/v/c/c957b235b7cc93a4/EQxVImcPpqRNuBUnf40Q3zcBbeebQbfqqGO9fuUTcbp7Pg?e=kMonTN)

#### 2. 🔴 L298N – Duální výkonový H-můstek (řízení směru a spínání motorů)
Slouží k výkonovému spínání polarity a proudu z baterie do stejnosměrných motorů.
- **Zapojení:**
  - `ENA`, `ENB` $\rightarrow$ ponechat osazené jumpery (stále aktivní)
  - `+12V` (napájecí svorka) $\rightarrow$ `V_BAT` JoyCaru (přímé napětí cca 6 V z baterií)
  - `GND` $\rightarrow$ `GND` JoyCar
  - `5V jumper` $\rightarrow$ **zapnout** (aktivuje interní 5V stabilizátor modulu pro jeho vlastní logiku)
  - `IN1`, `IN2`, `IN3`, `IN4` $\rightarrow$ připojit na výstupy `PWM0`, `PWM1`, `PWM2`, `PWM3` z modulu PCA9685
- **Logika řízení v kódu:**
  - `IN1` a `IN2` řídí levý motor (jeden kanál = 0, druhý kanál = požadovaná rychlost 0–4095; pro couvání obráceně).
  - `IN3` a `IN4` řídí pravý motor.
- **Dostupnost:** [Drátek L298N](https://dratek.cz/arduino-platforma/877-arduino-h-mustek-pro-krokovy-motor-l298n-dual-h-most-dc.html) nebo [LaskaKit L298N](https://www.laskakit.cz/h-mustek-pro-krokovy-motor-l298n--dualni-motorovy-modul/).
- 🎥 **Video:** [Ukázka řízení motorů JoyCaru přes PCA9685 + L298N na OneDrive](https://1drv.ms/v/c/c957b235b7cc93a4/EX965LoTJE9ImRro_H19WR8BmOk0GXOaT2mM66E-Y2-qxA?e=fAZtym)

> [!TIP]
> **Knihovny a software:**  
> Pro řízení máme připravené CircuitPython knihovny i příklady:
> - Původní `PCA9633`: 1 byte (hodnoty 0–255)
> - Náhradní `PCA9685`: 2 byty (hodnoty 0–4095)  
> Pokud se vám stane, že integrovaný budič odejde, mentor vám potřebné knihovny a schéma zapojení rád poskytne.

<!-- Obrázky náhrady H-můstku:
![Zapojení modulů PCA9685 a L298N na robotovi](images/hmustek-pca9685-l298n.jpg)
-->

---

## 4. Užitečné studijní odkazy

### 🛠️ Práce s Git a GitHubem pro začátečníky:
- 🎥 **Video:** [Jak na Git a Git-Hub ve Visual Studio Code (YouTube video pro úplné začátečníky)](https://www.youtube.com/watch?v=0v5K4GvK4Gs)
- 📖 **Tahák příkazů:** [14 Git příkazů, které musí znát každý vývojář (Skillmea blog)](https://skillmea.cz/blog/14-git-prikazu-ktere-musi-znat-kazdy-vyvojar)

---

## 5. Prostor pro další vylepšení a nápady

Tuto sekci budeme v průběhu kurzu průběžně doplňovat. Pokud přijdete na zajímavý tip, 3D model (např. ochranné nárazníky, držáky čidel), úpravu nebo zlepšovák, pošlete nám jej a zařadíme ho sem pro ostatní!

---

### Kam pokračovat dál?

- **Základní řízení motorů a ochrana můstku:**  
  👉 **[5. Ovládání motorů robota JoyCar](ovladani-motoru.md)**
- **Zpět na rozcestník všech návodů:**  
  👉 **[Hlavní přehled kurzu](README.md)**
