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

Rozšíření instalujete kliknutím na ikonu **Extensions** (čtverce na levé liště, případně zkratkou `Ctrl+Shift+X`) a vyhledáním podle názvu.

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

---

## 3. Vytvoření a příprava pracovního adresáře

Zdrojové kódy svých programů budete mít uložené na svém pevném disku (např. v `Dokumenty/joyCarProjekt`). Tuto složku budeme verzovat v Gitu.

1. Vytvořte na disku novou prázdnou složku, například `joyCarProjekt`.
2. Stáhněte si připravený inicializační archiv kurzu:  
   🔗 **[vsc_init_circuitPythonProject-main.zip](https://github.com/JanChaloupek/vsc_init_circuitPythonProject/archive/refs/heads/main.zip)**
3. Stažený ZIP rozbalte a jeho obsah nakopírujte do své nové složky `joyCarProjekt`.  
   Složka musí obsahovat:
   - `.vscode/` – konfigurační soubory editoru, skripty pro nahrávání (`copy.ps1`, `copy.sh`) a seznam doporučených rozšíření `extensions.json`.
   - `lib/` – složka pro knihovny hardwaru robota JoyCar.
   - `lib_vsc_only/` – pomocné typové stuby pouze pro VS Code na PC (nepřenášejí se na robota).
   - `.gitignore` – seznam souborů, které se nemají nahrávat na GitHub.

---

## 4. Otevření projektu ve VS Code

1. Spusťte VS Code.
2. V horním menu zvolte **File** → **Open Folder...** (nebo použijte zkratku `Ctrl+K Ctrl+O`).
3. Vyberte svůj připravený pracovní adresář (např. `joyCarProjekt`).
4. VS Code automaticky detekuje soubor `.vscode/extensions.json`. Pokud se v pravém dolním rohu zobrazí výzva *„Do you want to install the recommended extensions?“*, potvrďte kliknutím na **Install**.

Nyní máte nainstalovaný editor i základní kostru projektu. V dalším kroku připojíme desku Pico:ed a nastavíme automatické nahrávání:  
👉 **Pokračujte na: [2. Práce s Pico:ed a CircuitPythonem](2-nastaveni-picoed.md)**
