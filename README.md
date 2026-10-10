# Varimi 🌱

> An offline-first mobile app connecting Zimbabwe's smallholder farmers with researchers, extension officers, and lenders.

*Varimi* is Shona for "farmers". The app puts weather, crop knowledge, market prices, farm records, and loan readiness in one low-data, multilingual tool built for low-end Android phones.

![Status](https://img.shields.io/badge/status-planning-yellow)
![Platform](https://img.shields.io/badge/platform-Android-green)
![License](https://img.shields.io/badge/license-MIT-blue)

---

## Table of Contents

- [Features](#features)
- [Supported Languages](#supported-languages)
- [User Roles](#user-roles)
- [Architecture](#architecture)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [Roadmap](#roadmap)
- [Data Sources](#data-sources)
- [Privacy and Compliance](#privacy-and-compliance)
- [Contributing](#contributing)
- [License](#license)

---

## Features

| # | Module | Description |
|---|--------|-------------|
| 1 | **Weather** | Current conditions, 7-day and seasonal forecasts, rainfall, temperature, humidity, wind, frost and drought alerts, and planting-window advice by Natural Region (I–V) and district. Latest data cached offline. |
| 2 | **Crop Library** | Guides for maize, small grains, sorghum, groundnuts, cotton, tobacco, soya, horticulture, and more: varieties, soils, planting dates, spacing, fertilizer, pests and diseases, harvest, storage. Text, audio, and illustrated formats. Downloadable per language and crop. |
| 3 | **Farmer Chatrooms** | Groups by district, crop, and language, plus an "Ask an Expert" channel. Text, voice notes, and photos (pest and disease identification). Moderation, reporting, and offline message queuing. |
| 4 | **Market Prices** | Official produce prices from AMA, GMB, and the Ministry of Lands, Agriculture, Fisheries, Water and Rural Development. Filter by commodity and market, view trends, set alerts. Shows last-updated date and works offline. |
| 5 | **GPS Land Measurement** | Walk-the-boundary and map-tap tools to compute field area (hectares and acres). Save boundaries offline and link each field to crops, records, and loan profile. |
| 6 | **Pfumvudza / Conservation Agriculture** | Step-by-step guides (planting basins, mulching, rotation, input quantities), a 1/16-hectare plot planner (39 m × 16 m), checklists, audio/video tutorials, and progress tracking. Fully offline in every language. |
| 7 | **Farm Records** | Expenses, inputs, labor, yields, sales, livestock, and income per field and season. Voice or icon-based entry, profit/loss summaries, and PDF export. |
| 8 | **Loan Access** | Verifiable farmer profile and credit-readiness score built from records and field data. Shared with banks, microfinance institutions, and suppliers only with explicit consent. Includes loan guides and application-document generation. |
| 9 | **Indigenous Knowledge Hub** | Farmers and elders upload practices (seed preservation, pest control, weather signs, soil care) as text, audio, photo, or video. Includes location tags, researcher verification, contributor credit, community voting, and consent controls. |

**Researcher link:** researchers can publish findings, run surveys, push alerts, and receive anonymized, consented field data and indigenous knowledge for study.

---

## Supported Languages

Zimbabwe's 16 constitutionally recognised official languages:

Chewa · Chibarwe · English · Kalanga · Khoisan · Nambya · Ndau · Ndebele · Shangani · Shona · Sign Language · Sotho · Tonga · Tswana · Venda · Xhosa

Content packs are downloadable per language and crop. Audio and illustrated content support low-literacy users; Sign Language content is delivered as video.

---

## User Roles

- **Farmer**: records, weather, library, chat, prices, loans
- **Researcher**: publish research, surveys, alerts, access consented data
- **Extension officer**: answer questions, verify content, support groups
- **Lender**: view consented farmer profiles, process applications
- **Admin**: content management, moderation, user management

---

## Architecture

**Principles:** offline-first, low bandwidth, low RAM, small APK, icon-driven UI.

| Layer | Suggested Stack |
|-------|-----------------|
| Mobile app | Flutter or React Native |
| Local storage | SQLite (with sync queue and conflict resolution) |
| Backend | Node.js + PostgreSQL (or Supabase) |
| Maps / GPS | Offline-capable map tiles (e.g., OpenStreetMap) |
| Notifications | Push + SMS/USSD fallback |
| Auth | Phone-number login with OTP, role-based access |
| Admin | Web dashboard |

---

## Project Structure

```
varimi/
├── index.html            # App (HTML, CSS, JS)
├── sw.js                 # Service worker (offline)
├── manifest.webmanifest  # PWA install settings
├── icon.svg
├── netlify.toml          # Netlify config
├── LICENSE
└── README.md
```

---

## Getting Started

The current build is a static Progressive Web App (no build step).

```bash
git clone https://github.com/<your-username>/varimi.git
cd varimi
python3 -m http.server 8080   # then open http://localhost:8080
```

**Deploy to Netlify:** push to GitHub, then in Netlify choose *Add new site → Import from Git*. Leave the build command empty and the publish directory as `.` (already set in `netlify.toml`).

**Current MVP:** weather with offline cache, crop basics (English, with Shona and Ndebele names), GPS land area, Pfumvudza guide, farm records with CSV export and loan-readiness hint, and local indigenous-knowledge notes. Translations need review by native speakers.

---

## Roadmap

- [ ] **Phase 0:** Requirements, personas, farmer interviews, data-source agreements
- [ ] **Phase 1 (MVP):** Weather, crop library with offline download, farm records
- [ ] **Phase 2:** GPS land measurement, Pfumvudza module, market prices
- [ ] **Phase 3:** Chatrooms, Ask an Expert, researcher accounts
- [ ] **Phase 4:** Loan readiness profile and lender portal
- [ ] **Phase 5:** Indigenous knowledge hub, SMS/USSD alerts, full 16-language coverage
- [ ] **Ongoing:** Field testing with farmers, accessibility and performance tuning

---

## Data Sources

Partnerships and licensing must be confirmed before use. Candidates:

- **Weather:** Meteorological Services Department (Zimbabwe), with a global provider such as Open-Meteo as backup
- **Market prices:** Agricultural Marketing Authority (AMA), Grain Marketing Board (GMB), Ministry of Lands, Agriculture, Fisheries, Water and Rural Development
- **Agronomy and Pfumvudza content:** Agritex, universities, and research institutes (e.g., ICRISAT, CIMMYT, FAO)
- **Maps:** OpenStreetMap contributors

---

## Privacy and Compliance

- Complies with Zimbabwe's **Cyber and Data Protection Act** (2021)
- Explicit, revocable consent for sharing data with lenders and researchers
- Encrypted local and server storage
- Contributor control and attribution for indigenous knowledge, with community-benefit principles

---

## Contributing

Contributions are welcome, especially translations, agronomy content review, and UX testing with farmers.

1. Fork the repository
2. Create a branch: `git checkout -b feature/your-feature`
3. Commit your changes and open a pull request

Please open an issue first for major changes.

---

## License

Released under the [MIT License](LICENSE). Indigenous knowledge contributions remain the property of their contributors and are governed by consent settings in the app.
