# Election Results Scraper

Pomocí tohoto kódu můžeš získat výsledky voleb pro libovolný územní celek z oficiálních stránek voleb v ČR v roce 2017:
[Election Results 2017](https://www.volby.cz/pls/ps2017nss/ps3?xjazyk=CZ). 

Požadavky
1. Nainstalovaný Python
Ujisti se, že máte nainstalovaný Python (verze 3.8 nebo novější). Zkontrolujete to pomocí:
python --version
Pokud Python není nainstalován, stáhněte jej z oficiální stránky.


2. Virtuální prostředí
Pro izolaci knihoven tohoto projektu doporučuji vytvořit virtuální prostředí.
Windows (PowerShell): python -m venv .venv
macOS/Linux: python3 -m venv .venv
Virtuální prostředí po vytvoření aktivuj:
Windows (PowerShell):  .venv\Scripts\activate
macOS/Linux: source .venv/bin/activate

3. Instalace potřebných knihoven
Po aktivaci virtuálního prostředí nainstaluj požadované knihovny:
pip install -r requirements.txt
který je součástí filu Project_3_webscraping

Spuštění skriptu
Jak získat odkaz na územní celek?
1.	Otevřete webovou stránku volby.cz.
2.	Klikněte na křížek „X“ ve sloupci "Výběr obce" pro požadovaný územní celek.
3.	Zkopírujte URL adresu z adresního řádku prohlížeče.
Spuštění skriptu s argumenty:
python main.py --url "URL_ADRESA_UZEMNIHO_CELKU" --output "NAZEV_VYSTUPNIHO_SOUBORU.csv"

Příklad pro Prostějov:
python main.py --url "https://www.volby.cz/pls/ps2017nss/ps32?xjazyk=CZ&xkraj=12&xnumnuts=7103" --output "vysledky_prostejov.csv"
Pokud nejsou zadány argumenty správně
•	Skript upozorní uživatele a nepokračuje v běhu.
•	Uživatel musí zadat oba argumenty ve správném pořadí.

Práce s výsledky
Otevření CSV souboru
•	VS Code: Otevřete soubor a použijte rozšíření „Excel Viewer“.
•	Excel: Pokud CSV otevřete přímo v Excelu mohou se zobrazit špatné znaky.
Je nutné CSV data do Excelu nahrát přes "Data"/"Načíst data"/"Ze souboru"/"Z Text/CSV"

Další poznámky
•	Kód je napsán tak, aby správně scrapoval všechny dostupné tabulky s politickými stranami.
•	Je třeba mít aktivované virtuální prostředí při spuštění skriptu.
•	Pokud narazíte na chybu ModuleNotFoundError, nainstalujte chybějící knihovny pomocí: 
•	pip install -r requirements.txt


