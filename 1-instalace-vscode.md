# 1. Instalace a nastavení Visual Studio Code

Tento průvodce vás krok za krokem provede instalací editoru **Visual Studio Code (VS Code)**, výběrem správných rozšíření pro náš kurz a přípravou pracovního adresáře.

---

## 1. Instalace Visual Studio Code

1. Navštivte oficiální web [code.visualstudio.com/download](https://code.visualstudio.com/download).
2. Stáhněte instalátor pro váš operační systém (**Windows**, **macOS** nebo **Linux**).
3. Spusťte instalátor a dokončete instalaci (ve Windows doporučujeme zaškrtnout volby *„Přidat akci Otevřít pomocí Code do kontextové nabídky“* a *„Přidat do proměnné PATH“*).
4. Po instalaci spusťte VS Code.

---

## 2. Instalace potřebných rozšíření

> [!TIP]
> **Superrychlá automatická instalace pomocí `setup.bat` (Windows):**  
> Pokud pracujete na Windows a stáhnete si připravenou výchozí strukturu projektu (viz [Krok 3](#3-získání-výchozí-struktury-projektu)), **nemusíte tato rozšíření instalovat ručně jedno po druhém**. Stačí ve složce projektu spustit skript **`setup.bat`**, který všechna potřebná i doporučená rozšíření, Python nástroje i konfiguraci `Run on Save` nainstaluje a nastaví plně automaticky!  
> Následující seznam slouží jako přehled pro ruční kontrolu nebo pro uživatele jiných operačních systémů (macOS/Linux).

Rozšíření ručně instalujete kliknutím na ikonu **Extensions** (čtverce na levé liště, případně zkratkou `Ctrl+Shift+X`) a vyhledáním podle názvu.

### Povinná rozšíření:

1. **Python**
   - Základní podpora pro jazyk Python (zvýrazňování syntaxe, linting, ladění).
   - *Název:* `Python`
   - *Autor:* `Microsoft` (součástí je i jazykový server `Pylance`)

2. ⚠️ **CircuitPython v2 Cursor AI** *(VELMI DŮLEŽITÉ!)*
   - Rozšíření zajišťující práci s CircuitPythonem na desce Pico:ed a přístup ke knihovnám.
   - *Název:* `CircuitPython v2 Cursor AI`
   - *Autor:* `wmerkens` (vyžadována verze **0.3.3**)
   - > [!CAUTION]
     > **Pozor na záměnu rozšíření!**  
     > Ujistěte se, že instalujete přesně rozšíření **`CircuitPython v2 Cursor AI`** od autora `wmerkens`.  
     > **NEINSTALUJTE** obecné rozšíření „CircuitPython v2“ (od joedevivo ani jiné s vyšším číslem verze) – s naším prostředím a deskou Pico:ed **nefunguje**! Pokud ho již máte nainstalované, odinstalujte ho.

3. **Run on Save**
   - Automaticky spouští skript při každém stisku `Ctrl+S` (uložení souboru). Slouží k bleskovému zkopírování změněného souboru do Pico:edu.
   - *Název:* `Run on Save`
   - *Autor:* `EmeraldWalk`

4. **PlantUML**
   - Umožňuje přímo v editoru prohlížet a generovat UML diagramy tříd, které budeme v kurzu kreslit pro návrh architektury robota.
   - *Název:* `PlantUML`
   - *Autor:* `jebbs`

---

### Doporučená rozšíření (usnadní vám práci):

1. **GitLens – Git supercharged**
   - Zobrazuje historii změn řádek po řádku přímo v editoru, porovnává commity a větve.
   - *Autor:* `GitKraken` (bezplatná edice *Community* plně postačuje).

2. **GitHub Pull Requests**
   - Umožňuje kontrolovat a spravovat Pull Requesty přímo z postranního panelu VS Code.
   - *Autor:* `GitHub`

3. **Output Colorizer**
   - Barevně zvýrazňuje text v okně OUTPUT a v terminálu, což pomáhá v rychlé orientaci při ladění chyb.
   - *Autor:* `IBM`

4. **MagicPython**
   - Pokročilé gramatické zvýrazňování syntaxe Pythonu.
   - *Autor:* `MagicStack Inc.`

5. **CodeSnap-plus-fix**
   - Vytváří elegantní obrázky (snapshoty) vybraného kódu se zachovaným barevným tématem a čísly řádků pro vkládání do odevzdávaných Pull Requestů na GitHubu. Oproti základnímu CodeSnapu umožňuje navíc kliknutím na číslo řádku stěžejní řádky barevně zvýraznit (režimy Focus, Git-Add a Git-Remove).
   - *Název:* `CodeSnap-plus-fix`
   - *Autor:* `eugenejeon`

---

## 3. Získání výchozí struktury projektu

Celá připravená výchozí struktura projektu je součástí repozitáře kurzu na GitHubu. Nemusíte nic ručně konfigurovat – projekt už přímo obsahuje:
- **`setup.bat`** – jednorázový instalační a konfigurační skript pro Windows (automaticky zkontroluje a nainstaluje Python, pip, mpremote, všechna potřebná i doporučená rozšíření z Marketplace, vestavěný balíček MicroPython Panelu a nakonfiguruje `Run on Save`).
- **`.vscode/`** – připravená konfigurace editoru (`settings.json`), doporučená rozšíření (`extensions.json`), pravidla ignorování souborů (`.ignoreCopy`), instalační skript (`setup.ps1`), balíček `dist/micropython-panel.vsix` a nahrávací skripty:
  - `copy.ps1` (autorský skript mentora kurzu Jana Chaloupka pro Windows pro bleskové nahrávání na disk `CIRCUITPY`)
  - `copy.sh` (skript studenta Robina Bortlíka upravený Janem Chaloupkem pro macOS a Linux)
  - pomocné skripty pro MicroPython (`upload.ps1`, `repl.ps1`, `list.ps1`, `wipe.ps1`, `mpy.ps1` atd.)
- **`_fake/`** – mock moduly hardware (`board`, `picoed`, `pwmio`, `digitalio`, `neopixel`, `time`), které umožňují spouštět a testovat kód offline přímo na PC bez připojeného robota.
- **`_stubs/`** – interní složka s typovými definicemi CircuitPythonu pro bezchybnou nápovědu (IntelliSense) ve VS Code.
- **`lib/`** – složka pro ovladače a knihovny hardware JoyCaru (včetně `picoed_v2_lib` pro MicroPython).
- **`pyrightconfig.json`** – konfigurace analyzátoru Pylance/Pyright pro přesné našeptávání a typovou kontrolu bez falešných chybových hlášení.
- **`code.py`** – hlavní program pro CircuitPython na desce Pico:ed.
- **`main.py`** – výchozí program pro MicroPython.
- **`.gitignore`** – pravidla verzování zamezující nahrávání mezipaměti a dočasných souborů do Gitu.

---

### Jak projekt získat do počítače:

Máte k dispozici dvě cesty podle toho, zda již ovládáte Git, nebo chcete začít rychle bez něj:

#### Varianta A: Přes Git (doporučený a profesionální postup)
Pokud již pracujete s Git a GitHubem (podrobný návod pro odevzdávání přes Pull Requesty najdete v [4. Práce s Git a GitHubem](4-prace-s-gitem.md)):
1. Otevřete terminál (PowerShell / Bash) a přejděte do složky pro projekty (např. `cd C:\Projekty`).
2. Naklonujte repozitář kurzu:
   ```bash
   git clone https://github.com/Global-Classes-CZE/robot-programming3.git joyCarProjekt
   ```
   *(Pokud již máte vytvořený svůj vlastní fork podle [4. Práce s Git a GitHubem](4-prace-s-gitem.md), naklonujte URL svého forku).*
3. Klonovat lze také přímo z prostředí VS Code: stiskněte zkratku `Ctrl+Shift+P`, vyberte **Git: Clone**, vložte adresu repozitáře a vyberte složku na disku.

#### Varianta B: Ruční stažení ZIP archivu z GitHubu (pro úplné začátečníky)
Pokud zatím Git neovládáte a chcete si nejprve osahat hardware a psaní kódu:
1. Otevřete v prohlížeči oficiální repozitář kurzu na GitHubu (např. [github.com/Global-Classes-CZE/robot-programming3](https://github.com/Global-Classes-CZE/robot-programming3)).
2. V pravé horní části klikněte na zelené tlačítko **`<> Code`**.
3. V rozbalené nabídce zvolte položku **`Download ZIP`**.
4. Stažený soubor ZIP rozbalte na svůj disk (např. do složky `joyCarProjekt`).
5. K nastavení Gitu a odevzdávání úkolů přes Pull Requesty se můžete vrátit kdykoliv později podle [4. Práce s Git a GitHubem](4-prace-s-gitem.md).

---

## 4. Otevření projektu ve VS Code a rychlá příprava (`setup.bat`)

1. Spusťte VS Code.
2. V horním menu zvolte **File** → **Open Folder...** (nebo stiskněte zkratku `Ctrl+K Ctrl+O`).
3. Vyberte složku projektu (např. `joyCarProjekt`).
4. **Automatická instalace a příprava prostředí (`setup.bat`):**  
   V kořenu projektu poklepejte na soubor **`setup.bat`** (nebo jej spusťte v terminálu).  
   Tento skript za vás plně automaticky:
   - zkontroluje a případně nainstaluje Python a nástroj pip,
   - nainstaluje nástroj `mpremote` pro MicroPython,
   - nainstaluje vestavěné rozšíření **MicroPython Panel**,
   - hromadně nainstaluje všechna potřebná rozšíření z Marketplace (včetně `CircuitPython v2 Cursor AI 0.3.3`, `Run on Save`, Pylance, cSpell s češtinou a Indent Rainbow),
   - automaticky nakonfiguruje `Run on Save` pro okamžité odesílání kódu do robota při stisku `Ctrl+S`,
   - zkontroluje připojenou desku (USB disk `CIRCUITPY` i COM porty).
5. Zkontrolujte, zda v levém panelu Průzkumníka vidíte složky `.vscode`, `_stubs`, `_fake`, `lib` a soubory `pyrightconfig.json`, `code.py` i `main.py`.

Nyní máte připravený editor i kompletní strukturu projektu. V dalším kroku připojíme desku Pico:ed:  
👉 **Pokračujte na: [2. Práce s Pico:ed a CircuitPythonem](2-nastaveni-picoed.md)**
