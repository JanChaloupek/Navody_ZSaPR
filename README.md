# Návody pro studenty – Základy stavby a programování robotů

Vítejte v kurzu **Základy stavby a programování robotů**!  
Tento repozitář obsahuje ucelené návody krok za krokem pro přípravu vývojového prostředí, práci s hardwarem a odevzdávání úkolů kurzu.

---

## 🤖 Používaný hardware v kurzu

Během kurzu budete pracovat se **stavebnicí JoyCar** a **dvěma procesorovými deskami**.

### 🚗 Co je to JoyCar a k čemu slouží?

**JoyCar** je modulární vzdělávací robotická stavebnice na kolovém podvozku navržená pro praktickou výuku robotiky, mechatroniky a autonomních systémů. Představuje ideální most mezi softwarovým programováním a reálným fyzickým světem:

- **Mechanická konstrukce:** Dvoukolový podvozek s nezávislým pohonem levého a pravého kola pomocí stejnosměrných motorů s převodovkou a předním opěrným kuličkovým kolečkem (tzv. diferenciální řízení podvozku).
- **Bohatá senzorická výbava:**
  - **Sledování čáry (Line Tracking):** 3 infračervené optické senzory na spodní straně podvozku pro detekci černé vodící linie na světlém podkladu.
  - **Detekce překážek:** 2 přední infračervené senzory přiblížení a **ultrazvukový dálkoměr** (na pohyblivém držáku) pro přesné měření vzdálenosti v centimetrech.
  - **Měření rychlosti a ujeté dráhy (Odometrie):** Rychlostní senzory s perforovanými kotouči (enkodéry) na hřídelích obou motorů.
  - **Snímání okolí:** Dva fotorezistory (světelné senzory) pro měření intenzity osvětlení vlevo a vpravo.
- **Akční členy a signalizace:**
  - Výkonové řízení obou stejnosměrných motorů přes integrovaný I²C budič (obvod PCA9633).
  - Adresovatelné RGB LED diody (NeoPixel / WS2812B) vpředu i vzadu pro blinkry, brzdová světla a světlomety.
  - Piezoelektrický bzučák pro akustickou signalizaci a přehrávání tónů.
- **Rozšiřitelnost:** Hlavní sběrnice I²C s expandérem PCF8574, který nabízí volné piny pro připojení dalších periferií (jak si ukážeme v kapitole o rozšíření na 6 senzorů čáry, LCD displej či externí H-můstek).

#### 🎯 K čemu JoyCar v kurzu slouží:
1. **Autonomní navigace a jízda po čáře:** Vývoj algoritmů od základního binárního přepínání přes plynulou regulaci (P/PD regulátor) až po spolehlivou detekci složitých křižovatek a odboček.
2. **Bezkolizní pohyb a vyhýbání se překážkám:** Reakce na statické i pohybující se překážky v reálném čase.
3. **Odometrie a kinematika robota:** Přesné odměřování ujeté vzdálenosti, otáčení o zadané úhly a výpočet pozice v prostoru.
4. **Reálný neblokující multitasking:** Naučíte se psát kód, který zvládá současně řídit motory, číst desítky senzorů za sekundu, blikat LED pásky a hrát melodie bez použití zhoubného `time.sleep()`.

---

### 🧠 Dvě procesorové desky

1. **Pico:ed v2 (s procesorem Raspberry Pi RP2040)** *(Hlavní platforma kurzu)*
   - Deska s výkonným dvoujádrovým procesorem RP2040 (ARM Cortex-M0+ na 133 MHz), na které běží **CircuitPython** (verze 9 nebo vyšší).
   - K počítači se připojuje jako USB disk s názvem **`CIRCUITPY`**, což umožňuje okamžité nahrávání a editaci kódu.
   - Obsahuje vestavěný maticový LED displej 7×17, dvě tlačítka, stavovou neopixel LED a piezobzučák.
   - V této desce probíhá drtivá většina praktických úkolů kurzu s robotem JoyCar. Vývoj probíhá ve **Visual Studio Code**.

2. **BBC micro:bit v2** *(Úvodní srovnávací platforma)*
   - Populární výuková deska s procesorem Nordic nRF52833, na které běží **MicroPython**.
   - Slouží na začátku kurzu pro demonstraci rozdílů v architektuře mezi MicroPythonem a CircuitPythonem.
   - Pro začátek s micro:bitem používáme jednoduchý **Mu Editor**, pokročilí mohou využít připravené prostředí přímo ve **VS Code**.

---

## 📦 Vybavení pro kurz

### 🎁 Co dostanete (vzdělávací sada od R_D):
- ✅ **Vzdělávací robot JoyCar** (kompletní podvozek, senzory čáry, ultrazvukový senzor překážek, světelné senzory, bzučák a LED).
- ✅ **Procesorová deska Pico:ed v2** (s mikrokontrolérem Raspberry Pi RP2040).
- ✅ **4 ks USB nabíjecích baterií** (speciální akumulátory s vestavěným měničem, které drží stabilní napětí 1,5 V po celou dobu až do vypnutí).

### 🛠️ Co si musíte zajistit sami:
- ☐ **Počítač** s volným USB portem (Windows, macOS nebo Linux).
- ☐ **Micro USB kabel** pro připojení desky Pico:ed k počítači.
- ☐ **Testovací mapu/dráhu pro jízdu po čáře**:
  - *Nejlevnější řešení:* černá elektroinstalační páska šířky 15 mm na světlou podlahu nebo karton.
  - *Lepší řešení:* vytisknout čtvercové dlaždice na A4 a poskládat z nich dráhu.
  - *Předlohy pro velkoformátový tisk:* hotové PDF podklady pro formáty A1 nebo A3.

> [!TIP]
> Tipy na praktické doplňky (magnetický USB kabel proti poškození konektoru, záložní napájení, podrobný návod jak vyrobit srolovatelnou dráhu na linoleu a odkazy na PDF mapy) najdete v rozšiřující kapitole **[5. Praktické tipy, mapy a vylepšení výbavy](5-tipy-vybaveni-a-mapy.md)**.

---

## 📚 Rozcestník návodů

Postupujte podle jednotlivých kapitol v uvedeném pořadí:

| Kapitola | Název návodu | Popis |
|---|---|---|
| **Krok 1** | [1. Instalace a nastavení Visual Studio Code](1-instalace-vscode.md) | Stažení VS Code, instalace správných rozšíření (pozor na správnou verzi CircuitPythonu!) a příprava pracovní složky. |
| **Krok 2** | [2. Práce s Pico:ed a CircuitPythonem](2-nastaveni-picoed.md) | Kontrola a upgrade firmware, automatické nahrávání kódu při uložení (`copy.ps1`), sériová konzole (REPL), řešení potíží a práce ve Workspace. |
| **Doplněk** | [3. Úvodní práce s Micro:bitem a MicroPythonem](3-microbit-mu-editor.md) | Úvodní srovnání s MicroPythonem: jednoduchý Mu Editor nebo pokročilé prostředí přímo ve VS Code s rozšířením MicroPython Panel a knihovnou `picoed_v2_lib`. |
| **Krok 3** | [4. Práce s Git a GitHubem (Odevzdávání úkolů)](4-prace-s-gitem.md) | Vytvoření forku, klonování, správa větví a **vytváření čistých Pull Requestů bez míchání starých úkolů**. |
| **Hardware** | [6. Ovládání motorů robota JoyCar](6-ovladani-motoru-joycar.md) | **Kriticky důležitá kapitola:** princip budiče PCA9633, bezpečný kód pro motory, prevence spálení můstku a náhradní řešení přes PCA9685. |
| **Tipy (nepovinné)** | [5. Praktické tipy, mapy a vylepšení](5-tipy-vybaveni-a-mapy.md) | Magnetický USB kabel, tipy pro napájení, srolovatelná mapa na lino, hack I2C expandéru a rozšíření na 6 senzorů čáry. |

---

## ⚠️ Důležitá pravidla pro práci v kurzu

1. **Python na počítači nespouštíme!**  
   Veškerý kód pro robota běží přímo na mikrokontroléru Pico:ed (případně micro:bit). Na svém počítači nespouštíte žádný `python.exe` (výjimkou jsou pouze offline unit testy, které budeme probírat v pokročilejší části kurzu).
2. **Přísný zákaz blokujícího `time.sleep()` v robotických úlohách!**  
   Autonomní robot musí neustále sledovat senzory čáry a reagovat na překážky. Pokud v programu použijete `time.sleep()`, robot „oslepne“ a havaruje. Všechny časové úlohy řešíme neblokujícími časovači `Timer` a `Period`.
3. **Přísný zákaz okamžité změny směru motorů (zákaz oficiálních kódů výrobce)!**  
   Okamžité přepnutí směru (např. z jízdy vpřed rovnou na zpátečku) vytvoří proudovou špičku a indukované napětí, které **spolehlivě zničí H-můstek na základní desce** robota. Vždy musíte nejprve nastavit PWM na 0 a nechat motor alespoň krátký okamžik doběhnout.
4. **Odevzdávání pouze přes Pull Requesty!**  
   Každý úkol kurzu se odevzdává jako samostatný Pull Request ze samostatné větve založené z čerstvého `main`.
