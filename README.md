# Election Results Scraper

Pomocí tohoto kódu můžeš získat výsledky voleb pro libovolný územní celek z oficiálních stránek voleb v ČR v roce 2017:
[Election Results 2017](https://www.volby.cz/pls/ps2017nss/ps3?xjazyk=CZ). 

**Požadavky**
*1. Nainstalovaný Python*
Ujisti se, že máte nainstalovaný Python (verze 3.8 nebo novější). Zkontrolujete to pomocí:
python --version

*2. Virtuální prostředí*
Pro izolaci knihoven tohoto projektu doporučuji vytvořit virtuální prostředí.
Windows (PowerShell): python -m venv .venv
macOS/Linux: python3 -m venv .venv
Virtuální prostředí po vytvoření aktivuj:
Windows (PowerShell):  .venv\Scripts\activate
macOS/Linux: source .venv/bin/activate

*3. Instalace potřebných knihoven*
Po aktivaci virtuálního prostředí nainstaluj požadované knihovny:
pip install -r requirements.txt
který je součástí filu Project_3_webscraping

**Jak získat odkaz na územní celek?**
1.	Otevřete webovou stránku [Election Results 2017](https://www.volby.cz/pls/ps2017nss/ps3?xjazyk=CZ).
2.	Klikněte na křížek „X“ ve sloupci "Výběr obce" pro požadovaný územní celek.
3.	Zkopírujte URL adresu z adresního řádku prohlížeče.
   
**Spuštění skriptu s argumenty ve správném pořadí:**
1. argument: URL_ADRESA_UZEMNIHO_CELKU
2. argunet: NAZEV_VYSTUPNIHO_SOUBORU.csv

finaální ukázka: python NAZEV_SOUBORU.py --url "URL_ADRESA_UZEMNIHO_CELKU" --output "NAZEV_VYSTUPNIHO_SOUBORU.csv"

**Konkrétní příklad pro územní celek Prostějov:**
python webscaper.py --url "https://www.volby.cz/pls/ps2017nss/ps32?xjazyk=CZ&xkraj=12&xnumnuts=7103" --output "vysledky_prostejov.csv"

**Pokud nejsou zadány argumenty správně**
•	Skript tě upozorní a nepokračuje v běhu.
•	Musíš zadat oba argumenty ve správném pořadí.

**Práce s výsledky**
Scrapovaná data jssou automaticky uložena do CSV souboru.POzor - stahování zabere cca 1-2 minuty.
Otevření CSV souboru
•	VCS: Otevři soubor přímo v VCS a použij rozšíření „Excel Viewer“.
•	Excel: Pokud CSV stáhneš do počítače a otevřeš přímo v Excelu mohou se zobrazit špatné znaky.
Je nutné CSV data do Excelu nahrát přes "Data"/"Načíst data"/"Ze souboru"/"Z Text/CSV"

**Další poznámky**
•	Kód je napsán tak, aby scrapoval libovolné územní celky kliknutím na „X“ ve sloupci "Výběr obce".
POZOR: Kliknutím na jiný odkaz (např. "Kód" nebo "Výběr PM") a zkopírováním url adresy jako prvního argumentu nebude fungovat. 
•	Je třeba mít aktivované virtuální prostředí při spuštění skriptu.
•	Pokud narazíte na chybu ModuleNotFoundError, nainstalujte chybějící knihovny pomocí: 
pip install -r requirements.txt


