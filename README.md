# EstimAI — Property Value Estimator 🏠

> AI-powered real estate estimation for Pakistan's property market. Instant breakdowns, tax summaries, mortgage calculations, ROI projections, and PDF export — all in a single HTML file.

## 🏆 Recognition

> **Megacode War — HITEC University**
> Secured **4th Position** overall with a perfect **5/5 score in UI/UX** at the inter-university web development competition.

![EstimAI Hero](headervideo.mp4)

---

## ✨ Features

- **Instant Estimation** — Enter property details and get a real-time value estimate based on city multipliers, property type, age, and size.
- **Price Breakdown** — See a visual split between land cost and construction value via an interactive bar chart.
- **Insights Strip** — Price per Marla vs city average, estimated monthly rent, yield %, 5-year projection, and affordability index.
- **Detailed Summary Modal** — Tax breakdown (transfer tax + agency fee), multi-currency conversion (USD, GBP, EUR), and a QR code to share the estimate.
- **Mortgage Calculator** — Compute monthly installments based on down payment %, loan term, and interest rate.
- **ROI Projection Table** — Projected property value and gains at 1, 3, 5, 10, and 15 years.
- **Depreciation Curve** — Line chart showing value vs. property age.
- **City Benchmark** — Compare price/Marla against all supported Pakistan cities.
- **Affordability Index** — How many months of salary it takes to buy the property.
- **Comparable Listings** — Simulated nearby listings labeled Cheaper / Similar / Pricier.
- **Save & Compare** — Save up to 5 estimates and compare them in a table.
- **Estimate History** — Persisted in `localStorage`; reload past estimates in one click.
- **PDF Export** — Full property report with ROI projections via jsPDF.
- **WhatsApp Share** — Pre-formatted message with all key figures.
- **Shareable URL** — All inputs encoded in the query string; copy and share instantly.
- **Dark / Light Theme** — Toggleable, with smooth transitions throughout.
- **Multi-language** — English, اردو (Urdu), 中文 (Chinese), عربي (Arabic) with RTL support.
- **Mouse Trail Effect** — Subtle gold particle trail canvas overlay.
- **Confetti** — Fires on your first estimate of the session 🎉

---

## 🏙️ Supported Cities & Areas

| City | Areas |
|------|-------|
| **Islamabad** | F-7/F-8, DHA, G-11/G-13 |
| **Lahore** | DHA, Gulberg, Bahria Town |
| **Karachi** | DHA, Clifton |
| **Other** | Rawalpindi, Peshawar, Faisalabad, Multan, Quetta |

---

## 🏗️ Property Types

| Type | Multiplier |
|------|-----------|
| 🏠 House | 1.0× |
| 🏢 Apartment | 0.85× |
| 🌿 Plot | 0.7× |
| 🏪 Commercial | 1.4× |

---

## 🚀 Getting Started

EstimAI is a **zero-dependency, single HTML file** — no build step, no server required.

### 1. Clone the repository

```bash
git clone https://github.com/your-username/estimai.git
cd estimai
```

### 2. (Optional) Add a hero video

Place a file named `headervideo.mp4` in the same directory as `index.html`. If absent, the hero section will show a plain dark overlay — everything else works fine.

### 3. Open in browser

```bash
# macOS
open index.html

# Linux
xdg-open index.html

# Windows
start index.html
```

Or just drag `index.html` into any modern browser.

---

## 📁 Project Structure

```
estimai/
├── index.html          # Complete app — HTML, CSS, and JS in one file
├── headervideo.mp4     # (optional) Hero background video
└── README.md
```

All styles and scripts are inline. External resources loaded from CDN:

| Library | Purpose |
|---------|---------|
| [Chart.js 4.4.1](https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.1/chart.umd.min.js) | Bar and line charts |
| [jsPDF 2.5.1](https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js) | PDF report generation |
| [QRCode.js 1.0.0](https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js) | QR code for share modal |
| [Google Fonts](https://fonts.googleapis.com) | DM Serif Display + DM Sans |

---

## 🧮 Estimation Formula

```
Base = size (Marla) × 5,000,000 × city_multiplier × type_multiplier
Age Deduction = Base × 10%   (if property age > 10 years)
Bedroom Bonus = Base × 5%    (if bedrooms > 3)

Estimated Value = Base − Age Deduction + Bedroom Bonus
```

City multipliers range from **0.70** (Quetta) to **1.40** (F-7 Islamabad / Commercial).

> **Note:** Values are indicative estimates based on market averages. They are not a substitute for a professional property valuation.

---

## 💱 Currency Rates

Static approximations used for display only:

| Currency | Rate |
|----------|------|
| USD | 1 PKR ≈ 0.0036 |
| GBP | 1 PKR ≈ 0.0028 |
| EUR | 1 PKR ≈ 0.0033 |

---

## 🌐 Localization

Switch language via the top-right dropdown. Supported:

- 🌐 **English** (default, LTR)
- **اردو** — Urdu (RTL)
- **中文** — Simplified Chinese (LTR)
- **عربي** — Arabic (RTL)

All UI strings update instantly without a page reload.

---

## 🖨️ Print Support

Use `Ctrl+P` / `Cmd+P` — the stylesheet hides navigation, controls, modals, and the mouse trail, leaving a clean printable layout.

---

## 🛠️ Customization

All configuration lives in plain JavaScript at the top of the `<script>` block:

```js
// City multipliers
const CITY_MULT = { 'Islamabad_F7': 1.4, 'Lahore_DHA': 1.3, ... };

// City average price/Marla (PKR)
const CITY_AVG = { 'Islamabad_F7': 7000000, ... };

// Property type multipliers
const TYPE_MULT = { house: 1.0, apartment: 0.85, plot: 0.7, commercial: 1.4 };

// Base price per Marla (PKR)
const BASE = 5000000;

// Currency conversion rates
const RATES = { USD: 0.0036, GBP: 0.0028, EUR: 0.0033 };
```

Adding a new city requires one entry in `CITY_MULT`, one in `CITY_AVG`, one `<option>` in the `#city` `<select>`, and an optional short label in `CITY_LBL`.

---

## 🤝 Contributing

1. Fork the repo and create a feature branch: `git checkout -b feature/my-feature`
2. Make your changes in `index.html`
3. Test in at least one Chromium-based browser and Firefox
4. Open a pull request with a clear description of what changed

Bug reports and feature requests are welcome via [GitHub Issues](https://github.com/your-username/estimai/issues).

---

## 📄 License

MIT — free to use, modify, and distribute. Attribution appreciated.

---

## ⚠️ Disclaimer

EstimAI provides rough estimates based on simplified market multipliers. Values should not be used for legal, financial, or investment decisions without independent professional verification. Currency rates are static approximations and do not reflect live exchange rates.

---

*© 2025 EstimAI · Property Value Estimator · Pakistan*
