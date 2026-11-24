# 3. Úvodní práce s Micro:bitem a MicroPythonem (Mu Editor a VS Code)

Tato kapitola je **samostatná a informativní**. Slouží pro úvodní cvičení na začátku kurzu, kde si vyzkoušíme desku **BBC micro:bit v2** a ukážeme si rozdíl mezi **MicroPythonem** a **CircuitPythonem**.

V kurzu máte pro MicroPython k dispozici **dvě cesty**:
1. **Jednoduchá cesta pro začátečníky:** Oficiální **Mu Editor** (vhodné pro okamžité seznámení s BBC micro:bitem bez nastavování).
2. **Pokročilá cesta ve VS Code:** Využití připravených skriptů a rozšíření přímo v našem výchozím projektu kurzu (podpora pro BBC micro:bit i Pico:ed s MicroPython firmwarem).

---

## 1. Proč na začátku zkoušíme Micro:bit a MicroPython?

- **Rychlý start bez složité konfigurace:** BBC micro:bit s editorem Mu funguje okamžitě po zapojení bez nutnosti instalovat Python, kompilátory či složité pluginy.
- **Rozdíl v architektuře firmware:**
  - **BBC micro:bit (MicroPython):** Kód se do desky nahrává flashováním nebo sériovým přenosem (přes `mpremote` či WebUSB). V počítači nevzniká virtuální flash disk typu `CIRCUITPY`.
  - **Pico:ed (CircuitPython):** Kód se nahrává jako běžné soubory na USB disk `CIRCUITPY`. Robot nabízí výrazně větší výkon procesoru RP2040 (dvoujádrový ARM Cortex-M0+ na 133 MHz) a bohaté možnosti pro řízení motorů a senzorů JoyCaru.

<img src="images/joycar-microbit-v2.jpg" width="380" alt="Robot JoyCar osazený procesorovou deskou BBC micro:bit v2">

---

## 2. Varianta A: Stažení a práce s Mu Editorem (Pro micro:bit)

> [!NOTE]
> **Je pro spuštění Mu Editoru potřeba mít nainstalovaný Python a pip?**  
> **Není!** Oficiální instalátor z [codewith.mu](https://codewith.mu/) pro Windows (`.exe`) i macOS (`.pkg`) je plně samostatná aplikace (standalone bundle), která má svůj vlastní Python runtime i všechny potřebné knihovny zabalené přímo v sobě. Student tedy nemusí instalovat Python, pip ani nic konfigurovat v příkazové řádce – stačí stáhnout a spustit instalátor.  
> *(Instalace přes `pip install mu-editor` se používá volitelně pouze na Linuxu nebo u pokročilých uživatelů, kteří chtějí provozovat Mu ve svém vlastním virtuálním prostředí).*

1. Navštivte oficiální stránky editoru: **[codewith.mu](https://codewith.mu/)**.
2. V sekci **Download** stáhněte instalátor pro váš operační systém (**Windows**, **macOS** nebo **Linux**).
3. Spusťte instalaci a otevřete program **Mu**.
4. Vlevo nahoře klikněte na tlačítko **Mode** (Režim), vyberte **BBC micro:bit** a potvrďte **OK**.
5. Vložte jednoduchý ukázkový kód:
   ```python
   from microbit import *

   display.scroll("ZSaPR")

   while True:
       if button_a.is_pressed():
           display.show(Image.HAPPY)
       elif button_b.is_pressed():
           display.show(Image.SAD)
       else:
           display.clear()
   ```
6. Připojte micro:bit USB kabelem a klikněte na tlačítko **Flash** na horní liště.
   - Žlutá LED dioda na zadní straně se rychle rozbliká.
   - Program se nahraje a deska začne rolovat text na svém 5×5 LED displeji.
7. **REPL a Plotter v Mu Editoru:**
   - **Tlačítko REPL:** Otevře interaktivní konzoli MicroPythonu pro ladění a výpisy z `print()`.
   - **Tlačítko Plotter:** Pokud do konzole vypisujete dvojice čísel, Mu z nich automaticky v reálném čase kreslí graf.

---

## 3. Varianta B: MicroPython přímo ve Visual Studio Code

Pokud nechcete přepínat mezi různými editory a chcete MicroPython používat přímo v profesionálním prostředí **Visual Studio Code**, máme v našem výchozím repozitáři projektu připravenou kompletní infrastrukturu skriptů i vlastní rozšíření pro VS Code.

### Co je v projektu pro MicroPython připraveno:

1. **Jednorázová příprava prostředí (`.vscode/setup.bat` / `setup.ps1`):**
   - Zkontroluje instalaci Pythonu a nástroje `pip`.
   - Automaticky nainstaluje komunikační balíček **`mpremote`** (oficiální nástroj MicroPythonu pro správu zařízení přes sériový port).
   - Nainstaluje do vašeho VS Code speciální rozšíření **MicroPython Panel** (`.vscode/dist/micropython-panel.vsix`).

2. **Rozšíření MicroPython Panel:**
   - V levém Activity Baru přidá ikonu mikrokontroleru s přehledným panelem tlačítek.
   - Ve spodním stavovém řádku (Status Bar) přidá barevná tlačítka pro okamžité spuštění:
     - 🟨 **⬆ Upload project** – spustí skript `.vscode/upload.ps1`, který podle konfigurace v `.vscode/upload_config.txt` přenese soubory (např. `main.py` a složku `lib`) na připojenou desku.
     - 🟩 **▶ REPL** – spustí `.vscode/repl.ps1` a otevře interaktivní terminál MicroPythonu.
     - 🟦 **📂 List files** – spustí `.vscode/list.ps1` a vypíše soubory uložené v paměti desky.
     - 🟥 **🗑 Wipe device** – spustí `.vscode/wipe.ps1` a bezpečně vymaže paměť desky pro čistý začátek.

3. **Knihovna hardware pro Pico:ed (`lib/picoed_v2_lib`):**
   - Pokud provozujete desku Pico:ed s MicroPython firmwarem, máte v adresáři `lib/picoed_v2_lib` k dispozici hotové ovladače:
     - `display.py` a `is31fl3731.py` pro LED maticový displej 7×17,
     - `button.py` pro tlačítka A a B,
     - `led.py` pro stavové LED,
     - `music.py` pro neblokující bzučák,
     - `ultrasonic.py` pro měření vzdálenosti.

4. **Typová nápověda Pylance (`_stubs/`):**
   - Ve složce `_stubs/` jsou připraveny soubory `machine.pyi` a `rp2.pyi`, takže Pylance ve VS Code nepodtrhává importy a nabízí plnohodnotné automatické doplňování kódu a parametrů pro mikrokontrolér RP2040.

---

## 4. Shrnutí a přechod k hlavnímu robotovi JoyCar

Vyzkoušeli jste si základní principy běhu MicroPythonu. Pro stavbu a programování našeho hlavního autonomního robota JoyCar však v dalších kapitolách budeme primárně využívat **CircuitPython na desce Pico:ed v2** pro jeho vynikající podporu knihoven, práci přes USB disk `CIRCUITPY` a přehledné řízení periferií.

👉 **Pokračujte na: [4. Práce s Git a GitHubem (Odevzdávání úkolů)](4-prace-s-gitem.md)**
