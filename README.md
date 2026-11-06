# PulseLedger — Complex Data Dashboard with D3.js + SVG

A modern financial intelligence dashboard made with React + TypeScript and **D3.js**, with browser-native SVG interactivity.

## Features

- 24 months × 3 regions of deterministic, synthetic financial data
- Period and region filters recompute revenue, profit, customers and margin
- D3 `scalePoint`, `scaleLinear`, `line`, `area`, `pie`, `arc` and interpolation
- Inspect points with SVG hover hit areas and precise chart tooltip
- Toggle revenue / expenses SVG layers; clickable donut slices drill into channels
- Interactive transaction search, amount sorting, channel filter and CSV export
- `src/data.ts` is an isolated pure data transformation layer; no API requests

## Run

```bash
npm install
npm run dev
npm run build
npm run test
npx playwright install chromium
npm run test:ui
npm run bench
```

The benchmark produces console JSON (`loadMs`, `filterMs`, `svgPathCount`) for easy aggregation in CI. Limits are deliberately broad as performance varies by machine.

Read `evals/README.md` for objective pass/fail criteria and `benchmarks/README.md` for a reproducible evaluation protocol.

## Expected data

- Months: **2024-11 through 2026-10** (24 months)
- Default filter: **All regions, last 12 months**
- Testable identities: `profit = revenue − expenses`, regional amounts sum to global amounts, channel shares sum to 100%
- Displayed records and values are completely synthetic and not linked to an account

## Structure

`src/data.ts`: deterministic test fixtures and aggregation · `src/charts.tsx`: SVG/D3 visualizations · `src/App.tsx`: dashboard UI and interactions · `tests/dashboard.spec.ts`: user flow assertions · `benchmarks/measure.spec.ts`: timings.
