# Weekday Price Tracker

[![Bright Data](https://img.shields.io/badge/Powered%20by-Bright%20Data-blue?style=flat-square)](https://brightdata.de)
[![Weekday Price Tracker](https://img.shields.io/badge/Weekday%20Price%20Tracker-Managed%20Solution-orange?style=flat-square)](https://brightdata.de/products/insights/price-tracker/weekday)
[![Python](https://img.shields.io/badge/Python-3.9%2B-yellow?style=flat-square)](https://python.org)

[![Bright Insights Price Tracker](https://raw.githubusercontent.com/danielshashko/bright-insights-assets/main/price-tracker-hero-v2.png)](https://brightdata.de/products/insights/price-tracker/weekday)

Echtzeit-Preisverfolgung für Weekday – eine schwedische Streetwear-Marke der H&M Group. Zwei Möglichkeiten für den Einstieg: eine **vollständig verwaltete** Intelligence-Plattform oder ein **benutzerdefinierter Scraper**, erstellt mit Bright Data's AI Scraper Builder.

---

## Option 1: Bright Insights - KI-gestütztes Price Tracking (Empfohlen)

**[Bright Insights](https://brightdata.de/products/insights/price-tracker/weekday)** ist Bright Data's vollständig verwaltete Plattform für Retail Intelligence. Keine Scraper zu erstellen, keine Infrastruktur zu warten – nur strukturierte, analysebereite Preisdaten, die an Dashboards, Data Feeds oder Ihre BI-Tools geliefert werden.

**Warum Teams Bright Insights wählen:**
- 🚀 **Kein Setup** - In wenigen Minuten live mit sofort einsatzbereiten Dashboards und Data Feeds
- 🤖 **KI-gestützte Empfehlungen** - Ein konversationeller KI-Assistent verwandelt Millionen von Datenpunkten sofort in umsetzbare Erkenntnisse
- ⚡ **Echtzeit-Monitoring** - Stündliche bis tägliche Aktualisierungsraten mit sofortigen Alerts (E-Mail, Slack, webhook)
- 🌍 **Unbegrenzte Skalierung** - Jede Website, jede Geografie, jede Aktualisierungsfrequenz
- 🔗 **Plug-and-play-Integrationen** - AWS, GCP, Databricks, Snowflake und mehr
- 🛡️ **Vollständig verwaltet** - Bright Data übernimmt Schemaänderungen, Website-Updates und Datenqualität automatisch

**Wichtige Anwendungsfälle:**
- ✅ **Saisonale Rabatte verfolgen** und Sale-Events bei Weekday
- ✅ **Wettbewerberpreise überwachen** und Trends identifizieren
- ✅ **Preis-Alerts automatisieren**, wenn Artikel unter den Zielpreis fallen
- ✅ Einhaltung der MAP-Richtlinie überwachen und Preisverstöße erkennen
- ✅ Wettbewerberaktionen und Aktionsdynamiken verfolgen
- ✅ Saubere, harmonisierte Daten direkt in dynamische Preisalgorithmen oder KI-Modelle einspeisen

> **Ab $250/Monat - [Individuelles Angebot anfordern →](https://brightdata.de/products/insights/price-tracker/weekday)**

---

## Option 2: Erstellen Sie Ihren eigenen Weekday Scraper

Keine vorgefertigte Weekday scraper API? Kein Problem. Bright Data's **AI Scraper Builder** generiert in nur wenigen Klicks einen benutzerdefinierten Weekday Scraper — ganz ohne Programmierung.

### Erstellen Sie Ihren Weekday Scraper in wenigen Minuten

**[Öffnen Sie den Weekday AI Scraper Builder →](https://brightdata.de/products/web-scraper/weekday)**

Wählen Sie die Domain, beschreiben Sie Ihre Datenanforderungen, und lassen Sie unseren AI Scraper Builder die API automatisch erstellen.

1. **Beschreiben Sie den Datenbedarf in einfachem Englisch**
2. **Die KI generiert sofort die scraper API**
3. **Führen Sie API-Anfragen für sofortige Ergebnisse aus**
4. **Bearbeiten Sie den Code in der integrierten IDE**, falls nötig

Sobald Ihr Scraper erstellt ist, erhält er eine **Web Scraper ID** (`gd_xxxxxxxxxxxx`) — kopieren Sie sie für den Setup-Schritt unten.

### Voraussetzungen

- Python 3.9 oder höher
- Ein [Bright Data account](https://brightdata.de) (kostenlose Testversion verfügbar)
- Ein Bright Data **API token** ([so erhalten Sie einen](https://docs.brightdata.de/general/account/account-settings#api-token))
- Eine **Web Scraper ID** für Weekday (aus dem obigen Build-Schritt)

### Setup

1. **Dieses repository klonen**

   ```bash
   git clone https://github.com/bright-data-de/weekday-price-tracker.git
   cd weekday-price-tracker
   ```

2. **Abhängigkeiten installieren**

   ```bash
   pip install -r requirements.txt
   ```

3. **Zugangsdaten konfigurieren**

   Kopieren Sie `.env.example` nach `.env` und tragen Sie Ihre Werte ein:

   ```bash
   cp .env.example .env
   ```

   ```env
   BRIGHTDATA_API_TOKEN=your_api_token_here
   BRIGHTDATA_DATASET_ID=your_dataset_id_here
   ```

   > **Ihre Web Scraper ID**
   > Fügen Sie die Web Scraper ID aus Ihrem [AI Scraper Builder dashboard](https://brightdata.de/products/web-scraper/weekday)
   > in `BRIGHTDATA_DATASET_ID` ein (Format: `gd_xxxxxxxxxxxx`).

---

## Verwendung

Sobald Ihr Weekday Scraper erstellt und Ihre Web Scraper ID in `.env` konfiguriert ist, funktioniert die Python-Schnittstelle auf die gleiche Weise:

### 1. Bestimmte Produkte per URL verfolgen

Übergeben Sie eine Liste von Weekday-Produkt-URLs, um strukturierte Preisdaten abzurufen:

```python
from price_tracker import track_prices

urls = [
    "https://www.weekday.com/en/products/sample-product-123456",
    # Add more product URLs here
]

results = track_prices(urls)
for item in results:
    print(f"{item.get('title')} - {item.get('final_price', item.get('price'))} {item.get('currency', '')}")
```

Oder direkt ausführen:

```bash
python price_tracker.py
```

### 2. Produkte per Keyword entdecken

Finden Sie Produkte, die einer Keyword-Suche entsprechen:

```python
from price_tracker import discover_by_keyword

results = discover_by_keyword("laptop", limit=50)
```

### 3. Produkte per Kategorie-URL durchsuchen

Sammeln Sie alle Produkte von einer Weekday-Kategorieseite:

```python
from price_tracker import discover_by_category

results = discover_by_category(
    "https://weekday.com/category/example",
    limit=100,
)
```

---

## Ausgabefelder

Jeder Ergebnisdatensatz enthält die folgenden Felder:

| Field | Description |
|-------|-------------|
| `url` | Produktseiten-URL |
| `title` | Produktname |
| `brand` | Marke |
| `initial_price` | Originalpreis |
| `final_price` | Sale- / aktueller Preis |
| `currency` | Währungscode |
| `discount` | Rabatt |
| `in_stock` | Verfügbarkeit |
| `color` | Verfügbare Farben |
| `size` | Verfügbare Größen |
| `category` | Produktkategorie / Abteilung |
| `images` | Produktbild-URLs |
| `description` | Produktbeschreibung |
| `timestamp` | Zeitstempel der Erfassung |

### Beispielausgabe

```json
[
  {
    "url": "https://www.weekday.com/en/products/sample-product-123456",
    "title": "Example Product Name",
    "brand": "Example Brand",
    "initial_price": 59.99,
    "final_price": 44.99,
    "currency": "USD",
    "discount": "25%",
    "in_stock": true,
    "rating": 4.5,
    "reviews_count": 1234,
    "images": ["https://weekday.com/images/product1.jpg"],
    "description": "Product description text...",
    "timestamp": "2025-01-15T10:30:00Z"
  }
]
```

---

## Erweiterte Optionen

Die Funktion `trigger_collection()` akzeptiert optionale Parameter zur Steuerung der Datenerfassung:

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `limit` | integer | - | Maximale Anzahl der zurückzugebenden Datensätze |
| `include_errors` | boolean | `true` | Fehlerberichte in die Ergebnisse einschließen |
| `notify` | string (URL) | - | Webhook-URL, die aufgerufen wird, wenn der Snapshot bereit ist |
| `format` | string | `json` | Ausgabeformat: `json`, `csv` oder `ndjson` |

Beispiel mit Optionen:

```python
from price_tracker import trigger_collection, get_results

inputs = [{"url": "https://www.weekday.com/en/products/sample-product-123456"}]
snapshot_id = trigger_collection(inputs, limit=200, notify="https://your-webhook.com/hook")
results = get_results(snapshot_id)
```

---

## Ressourcen

- 🌟 [Weekday Price Tracker - Bright Insights (Managed)](https://brightdata.de/products/insights/price-tracker/weekday)
- 🏗️ [Einen Weekday Scraper erstellen](https://brightdata.de/products/web-scraper/weekday)
- 📖 [Bright Data Web Scraper API Documentation](https://docs.brightdata.de/scraping-automation/web-scraper-api/overview)
- 🗄️ [Web Scrapers Control Panel](https://brightdata.de/cp/scrapers)
- 🔑 [So erhalten Sie einen API token](https://docs.brightdata.de/general/account/account-settings#api-token)
- 🌐 [Bright Data Homepage](https://brightdata.de)

---

*Erstellt mit [Bright Data](https://brightdata.de) - der branchenführenden Plattform für Webdaten.*