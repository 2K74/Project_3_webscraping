# Project_3_webscraping
## Election Results Scraper

Using this Python script, you can retrieve the election results for any territorial unit from the official website of the Czech Republic's elections: [Election Results 2017](https://www.volby.cz/pls/ps2017nss/ps3?xjazyk=CZ). This script is designed to extract data from the 2017 elections to the Chamber of Deputies.

Požadavky
📌 1. Nainstalovaný Python
Ujistěte se, že máte nainstalovaný Python (verze 3.8 nebo novější). Zkontrolujete to pomocí:
python --version
Pokud Python není nainstalován, stáhněte jej z oficiální stránky.


📌 2. Virtuální prostředí
Pro izolaci knihoven projektu se doporučuje 
Vytvořit virtuální prostředí.
Windows (PowerShell): python -m venv .venv
macOS/Linux: python3 -m venv .venv

Aktivujte virtuální prostředí:
Windows (PowerShell):  .venv\Scripts\activate
macOS/Linux: source .venv/bin/activate



📌 3. Instalace potřebných knihoven
Po aktivaci virtuálního prostředí nainstalujte požadované knihovny:
pip install -r requirements.txt
Pokud soubor requirements.txt neexistuje, vygenerujte jej pomocí:
pip freeze > requirements.txt

Spuštění skriptu
Jak získat odkaz na územní celek?
1.	Otevřete webovou stránku volby.cz.
2.	Klikněte na křížek „X“ ve sloupci "Výběr obce" pro požadovaný územní celek.
3.	Zkopírujte URL adresu z adresního řádku prohlížeče.
Spuštění skriptu s argumenty:
python main.py --url "URL_ADRESA_UZEMNIHO_CELKU" --output "NAZEV_VYSTUPNIHO_SOUBORU.csv"
📌 Příklad pro Prostějov:
python main.py --url "https://www.volby.cz/pls/ps2017nss/ps32?xjazyk=CZ&xkraj=12&xnumnuts=7103" --output "vysledky_prostejov.csv"
Pokud nejsou zadány argumenty správně
•	Skript upozorní uživatele a nepokračuje v běhu.
•	Uživatel musí zadat oba argumenty ve správném pořadí.
________________________________________
📊 Práce s výsledky
Otevření CSV souboru
•	VS Code: Otevřete soubor a použijte rozšíření „Excel Viewer“.
•	Excel: Při otevírání zvolte "Oddělovač: středník (;)", kódování UTF-8, aby byla zachována správná diakritika.
📌 Pozor: Pokud CSV otevřete přímo v Excelu bez nastavení oddělovače, mohou se zobrazit špatné znaky.
________________________________________
📝 Další poznámky
•	Kód je napsán tak, aby správně scrapoval všechny dostupné tabulky s politickými stranami.
•	Je třeba mít aktivované virtuální prostředí při spuštění skriptu.
•	Pokud narazíte na chybu ModuleNotFoundError, nainstalujte chybějící knihovny pomocí: 
•	pip install -r requirements.txt


