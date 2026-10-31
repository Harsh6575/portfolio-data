---
title: "Invoxa - Quotation and Billing App"
slug: invoxa
description: "Quotations and bills for a small Indian shop, with per-item GST, financial-year numbering and A4 printing."
category: Full-Stack
status: In Progress
date: "Sep 2026 - Present"
technologies:
  - Next.js
  - React
  - TypeScript
  - MUI
  - Tailwind CSS
  - Vitest
features:
  - Quotations with GST set per item, so one quotation can mix 18%, 12%, 5% and 0% items
  - Quotation numbers that restart every April and carry the financial year, such as QTN/26-27/0001
  - Quotation list scoped to the Indian financial year, with search, validity filter, sorting and a running total
  - Customers and products, with quotations keeping a snapshot of both
  - Printed A4 quotation with a GST breakdown by rate, through the browser's print dialog
  - Money math in paise so totals never drift, covered by unit tests
links: []
order: 4
hidden: false
---

Invoxa is a quotation and billing tool for one small business in India. The shop owner keeps customers and products, writes quotations, and prints them on A4 with their own letterhead. It is deliberately not an accounting system: no ledgers, no payment tracking, and no full GST invoice compliance.

The interface, quotation workflow and calculations are built and tested against sample data. The PostgreSQL schema is designed and documented, and connecting it with Drizzle on Neon is the next step, followed by invoices.

## How It Works

```mermaid
flowchart LR
    C["Customer"] -- "snapshot at creation" --> Q["Quotation QTN/26-27/0001"]
    P["Product"] -- "snapshot per line" --> L["Line items, GST per line"]
    L --> Q
    Q --> T["Totals + GST by rate"]
    Q --> PR["A4 print / Save as PDF"]
```

- GST lives on each line item, never on the quotation as a whole, so one quotation can mix rates. The printed quotation groups taxable amounts and GST by rate.
- Prices are GST-exclusive. Each line's taxable amount, GST and total are rounded to the paisa once, when the line is calculated. Document totals are plain sums of those rounded values, never rounded again. Sums are done in whole paise to avoid floating-point drift, and unit tests pin the edge cases, such as half-paise values that binary floats store just under the half.
- Quotation numbers restart every 1 April and carry the financial year. Editing a quotation never changes its number, so its date can only move within that year. Deleting one never frees its number.
- A quotation stores a snapshot of the customer and of each product as they were when it was written, so editing or deleting a customer or product never changes an old quotation.
- The quotation list opens on the current financial year and can switch to earlier years, all years or custom dates. It searches by number or customer, filters to valid or expired quotations, sorts by date or amount, shows the count and total quoted, and keeps its filters when you open a quotation and go back.
- Printing uses one print stylesheet and the browser's own dialog for both paper and Save as PDF, so there is no PDF library. The page carries only the shop's letterhead, with no Invoxa branding.

## Key Highlights

- Per-item GST with a rate-wise breakdown on the printed quotation
- Financial-year quotation numbering that never reuses a number
- Paise-exact money math with unit tests for rounding edge cases
- Snapshots keep old quotations correct after customers or products change
- "Bill book" design with ruled lines, indigo ink on warm paper, and Indian number and date formats
- Public pages are indexed, while the app, sign-in and settings are hidden from search engines

## Tech Stack

- **Next.js** App Router with **React** and **TypeScript**
- **MUI** for components, with **Tailwind CSS** for layout
- **Vitest** for unit tests of the calculations, financial years and the quotation list
