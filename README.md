# KwachaWise

**Budget smarter. Spend wiser. Tailored for Zambian students.**

An **offline-first**, student-friendly budgeting app that supports flexible income (HELSB, allowances, ad-hoc side hustles), localized in **Zambian Kwacha (ZMW)**, and generates printable PDF insights. Designed to be a showcase-ready GitHub project with modern architecture, analytics, and UI polish.

---

##  Demo & Branding

![KwachaWise Logo](./assets/logo.png)  
*Logo: A sleek emblem integrating the ZMW currency symbol in a clean, modern layout—ideal for app icons and brand identity.*

---

## Problem & Vision

- **Problem**: Many budgeting apps assume fixed salaries, USD-denominated displays, and rigid workflows—misaligned with the realities of Zambian students.
- **Solution**: KwachaWise facilitates **variable incomes**, category-driven expense tracking, ZMW-native summaries, and printable reports with actionable insights—in an intuitive, offline-first experience.

---

## ​ Features

- **Flexible Income Inputs**  
  Track multiple monthly sources: bursaries, family support, campus hustles, refunds.

- **Smart Expense Capture**  
  Quick entries, recurring items, and group-split options tailored to student contexts (data, rent, social, transport).

- **Insight-Powered Analytics**  
  Visualize income vs expenses trends, detect spend spikes (>30% baseline filter), and get personalized cut suggestions—and highlight pocket leaks.

- **Localized Currency & Reports**  
  All interfaces and exports default to **Zambian Kwacha (ZMW)** using `en-ZM` formatting.

- **PDF & CSV Export**  
  Generate executive summaries featuring charts, insights, tips, and recommended category caps.

- **Customizable Themes**  
  Light/dark mode plus custom accent color—persisted per user.

- **Offline-First Design**  
  Full functionality with no internet; optional sync later.

- **Accessibility and Performance**  
  High-contrast UI, scalable fonts, fast load (PWA Lighthouse scores targeting ≥90), and lightweight footprint.

---

##  Tech Stack & Architecture

### Option A—PWA (Primary)

| Layer      | Stack / Tool                          |
|------------|----------------------------------------|
| Frontend   | Vue 3 + Vite, Pinia (state), Tailwind UI |
| Storage    | IndexedDB via Dexie                    |
| Charts     | Chart.js / Recharts                    |
| PDF Export | jsPDF / pdfmake + autoTable            |
| Deployment | GitHub Pages via GitHub Actions        |

### Option B—.NET MAUI (Future Native Wrapper)

- UI: .NET MAUI XAML + MVVM
- Storage: SQLite
- PDF: Render via WebView → Native Print-to-PDF
- Charts: SkiaSharp or Microcharts

---

##  Architecture & Project Layout

```text
KwachaWise/
├─ apps/
│  └─ web/              # PWA frontend
├─ packages/
│  ├─ core/             # domain logic, analytics
│  └─ ui/               # UI components
├─ .github/
│  └─ workflows/        # CI & deploy pipelines
├─ docs/                # Design docs / user guides
├─ scripts/             # Seed data + report generator
├─ assets/              # Logo and screenshots
├─ README.md
└─ LICENSE
