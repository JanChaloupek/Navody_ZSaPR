# Návody pro studenty – Základy stavby a programování robotů

Vítejte v kurzu **Základy stavby a programování robotů**!  
Tento repozitář obsahuje ucelené návody krok za krokem pro přípravu vývojového prostředí, práci s hardwarem a odevzdávání úkolů kurzu.

---

## 🤖 Používaný hardware v kurzu

Během kurzu budete pracovat se dvěma procesorovými deskami:

1. **Pico:ed v2 (s procesorem Raspberry Pi RP2040) a robot JoyCar** *(Hlavní platforma kurzu)*
   - Na této desce běží **CircuitPython** (verze 9 nebo vyšší).
   - Deska se k počítači připojuje jako USB disk s názvem **`CIRCUITPY`**.
   - Zde probíhá převážná většina výuky: řízení stejnosměrných motorů, čtení IR senzorů čáry, ovládání NeoPixel LED pásků, neblokující bzučák a maticový LED displej.
   - Jako hlavní vývojové prostředí používáme **Visual Studio Code**.

2. **BBC micro:bit v2** *(Úvodní srovnávací platforma)*
   - Na této desce běží **MicroPython**.
   - Slouží na začátku kurzu pro demonstraci rozdílů mezi MicroPythonem a CircuitPythonem.
   - Pro rychlý start s micro:bitem používáme jednoduchý **Mu Editor**.

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
| **Doplněk** | [3. Úvodní práce s Micro:bitem a Mu Editorem](3-microbit-mu-editor.md) | Informativní návod pro úvodní srovnání: instalace Mu Editoru a první program pro BBC micro:bit. |
| **Krok 3** | [4. Práce s Git a GitHubem (Odevzdávání úkolů)](4-prace-s-gitem.md) | Vytvoření forku, klonování, správa větví a **vytváření čistých Pull Requestů bez míchání starých úkolů**. |
| **Tipy (nepovinné)** | [5. Praktické tipy, mapy a vylepšení](5-tipy-vybaveni-a-mapy.md) | Magnetický USB kabel, tipy pro napájení, srolovatelná mapa na lino, hack I2C expandéru a rozšíření na 6 senzorů čáry. |

---

## ⚠️ Důležitá pravidla pro práci v kurzu

1. **Python na počítači nespouštíme!**  
   Veškerý kód pro robota běží přímo na mikrokontroléru Pico:ed (případně micro:bit). Na svém počítači nespouštíte žádný `python.exe` (výjimkou jsou pouze offline unit testy, které budeme probírat v pokročilejší části kurzu).
2. **Přísný zákaz blokujícího `time.sleep()` v robotických úlohách!**  
   Autonomní robot musí neustále sledovat senzory čáry a reagovat na překážky. Pokud v programu použijete `time.sleep()`, robot „oslepne“ a havaruje. Všechny časové úlohy řešíme neblokujícími časovači `Timer` a `Period`.
3. **Odevzdávání pouze přes Pull Requesty!**  
   Každý úkol kurzu se odevzdává jako samostatný Pull Request ze samostatné větve založené z čerstvého `main`.
