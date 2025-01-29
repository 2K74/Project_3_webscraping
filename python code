import requests
from bs4 import BeautifulSoup
import csv
import argparse
import os

# Funkce pro získání HTML obsahu stránky
def fetch_html(url):
    response = requests.get(url)
    response.raise_for_status()
    response.encoding = 'utf-8'  # Oprava kódování pro správnou diakritiku
    return response.text

# Funkce pro scrapování seznamu obcí
def scrape_villages(url):
    html = fetch_html(url)
    soup = BeautifulSoup(html, 'html.parser')
    table_rows = soup.find_all('tr')[2:]
    villages = []
    for row in table_rows:
        cols = row.find_all('td')
        if len(cols) >= 2:
            code = cols[0].text.strip()
            location = cols[1].text.strip()
            link = cols[0].find('a')['href'] if cols[0].find('a') else None
            if link:
                full_link = f"https://www.volby.cz/pls/ps2017nss/{link}"
                villages.append((code, location, full_link))
    return villages

# Funkce pro scrapování dat pro jednotlivý okrsek včetně politických stran
def scrape_voting_data(village):
    code, location, link = village
    html = fetch_html(link)
    soup = BeautifulSoup(html, 'html.parser')
    try:
        tables = soup.find_all('table')

        # Získání základních dat o voličích
        main_data = tables[0].find_all('td', class_='cislo')
        registered = main_data[3].text.strip().replace('\xa0', '')  # Čtvrtá buňka
        envelopes = main_data[4].text.strip().replace('\xa0', '')  # Pátá buňka
        valid = main_data[7].text.strip().replace('\xa0', '')      # Osmá buňka

        # Získání dat o politických stranách (z obou tabulek)
        party_names = []
        party_votes = []

        for table in tables[1:3]:  # Scrapujeme dvě tabulky s politickými stranami
            names = [name.text.strip() for name in table.find_all('td', class_='overflow_name')]
            votes = [votes.text.strip().replace('\xa0', '') for votes in table.find_all('td', class_='cislo')[1::3]]
            party_names.extend(names)
            party_votes.extend(votes)

        # Sestavení řádku pro CSV
        data_row = [code, location, registered, envelopes, valid] + party_votes
        return data_row, party_names
    except (IndexError, AttributeError) as e:
        print(f"Chyba při parsování dat pro {location}: {e}")
        return [code, location, '', '', ''] + [''] * len(party_names), party_names

# Hlavní funkce
if __name__ == "__main__":
    parser = argparse.ArgumentParser(description="Scraper výsledků voleb 2017")
    parser.add_argument("--url", required=True, help="URL hlavní stránky voleb")
    parser.add_argument("--output", required=True, help="Název výstupního CSV souboru")
    
    args = parser.parse_args()

    # Nastavení cesty pro výstupní soubor
    output_path = os.path.join("C:\\Users\\witcher\\OneDrive\\Desktop\\Folder", args.output)

    # Scrapování seznamu obcí
    villages = scrape_villages(args.url)

    # Scrapování dat pro každou obec
    collected_data = []
    party_names = []
    for village in villages:
        data, parties = scrape_voting_data(village)
        collected_data.append(data)
        if not party_names:  # Uloží názvy stran pouze jednou
            party_names = parties

    # Uložení do CSV souboru
    with open(output_path, mode='w', newline='', encoding='utf-8') as file:
        writer = csv.writer(file, delimiter=';')
        writer.writerow(["code", "location", "registered", "envelopes", "valid"] + party_names)
        writer.writerows(collected_data)

    print(f"Data byla úspěšně uložena do souboru {output_path}!")
    
