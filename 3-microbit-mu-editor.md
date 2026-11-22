# 3. Úvodní práce s Micro:bitem a Mu Editorem

Tato kapitola je **samostatná a informativní**. Slouží výhradně pro úvodní cvičení na začátku semestru, kde si vyzkoušíme desku **BBC micro:bit v2** a ukážeme si rozdíl mezi **MicroPythonem** a **CircuitPythonem**.

Pro tuto úvodní část nepoužíváme složité nastavování ve VS Code, ale jednoduchý a spolehlivý oficiální **Mu Editor**.

---

## 1. Proč na začátku zkoušíme Micro:bit a Mu Editor?

- **Rychlý start bez konfigurace:** BBC micro:bit s editorem Mu funguje okamžitě po zapojení bez nutnosti instalovat Python, kompilátory či složité pluginy.
- **Rozdíl v přístupu:**
  - **BBC micro:bit (MicroPython):** Kód se do desky nahrává jedním kliknutím na tlačítko *Flash*. V počítači nevzniká žádný virtuální disk typu `CIRCUITPY`.
  - **Pico:ed (CircuitPython):** Kód se nahrává jako soubory na USB disk `CIRCUITPY` a robot nabízí výrazně větší výkon procesoru RP2040 a bohaté možnosti pro řízení motorů JoyCaru.

---

## 2. Stažení a instalace Mu Editoru

1. Navštivte oficiální stránky editoru: **[codewith.mu](https://codewith.mu/)**.
2. V sekci **Download** stáhněte instalátor pro váš operační systém (**Windows Installer**, **macOS** nebo **Linux**).
3. Spusťte instalaci a dokončete ji podle pokynů na obrazovce.
4. Po dokončení spusťte program **Mu**.

---

## 3. První program na Micro:bitu

1. Připojte desku BBC micro:bit k počítači microUSB kabelem.
2. V editoru Mu klikněte vlevo nahoře na tlačítko **Mode** (Režim).
3. Vyberte režim **BBC micro:bit** a potvrďte tlačítkem **OK**.
4. Do editoru vložte jednoduchý demonstrační kód:
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
5. Klikněte na tlačítko **Flash** na horní liště.
   - Žlutá LED dioda na zadní straně micro:bitu se rychle rozbliká.
   - Během několika sekund se program přenese a micro:bit začne ihned rolovat text na svém 5×5 displeji.
   - Po stisku tlačítka A se usměje, po stisku B se zamračí.

---

## 4. Práce s konzolí (REPL) a Plotterem

V editoru Mu máte k dispozici dva skvělé nástroje:
- **Tlačítko REPL:** Otevře ve spodní části interaktivní MicroPython terminál, kde můžete přímo spouštět příkazy nebo sledovat výstupy z `print()`.
- **Tlačítko Plotter:** Pokud v programu vypisujete číselné hodnoty (např. z akcelerometru nebo teploměru), Plotter z nich automaticky v reálném čase vykresluje graf.

---

## 5. Shrnutí a návrat k hlavnímu robotovi JoyCar

Vyzkoušeli jste si základní chování mikrokontroléru. Pro zbytek semestru a stavbu autonomního robota JoyCar však budeme potřebovat výrazně vyšší výkon, 8 senzorů, řízení motorů a profesionální vývojové prostředí.

Proto se nyní vrátíme k **Pico:ed** a editoru **Visual Studio Code**:  
👉 **Pokračujte na: [4. Práce s Git a GitHubem (Odevzdávání úkolů)](4-prace-s-gitem.md)**
