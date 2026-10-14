# Hey, this is GoSimple 👋

We build software that takes a legal obligation and turns it into one API call.

## Tezga — fiscalization for Serbia

![Tezga eKasa](./assets/tezga-logo-light.svg#gh-light-mode-only)
![Tezga eKasa](./assets/tezga-logo-dark.svg#gh-dark-mode-only)

**[Tezga](https://tezgafiskal.com)** is a cloud ESIR that works with the Serbian Tax
Administration's virtual processor of fiscal receipts (V-PFR). Your platform calls a REST
API; Tezga issues and fiscalizes the receipt and returns the **PFR number, QR payload,
verification URL and a public PDF**. No local installation, no hardware, no card readers.

It covers fiscal receipts and e-invoices (SEF), advances, voids and refunds, costing and
price changes, the product and customer catalogue, webhooks and bank transactions.
Approved ESIR, IB 1597.

## Official SDKs

| Language | Package | Repository |
| --- | --- | --- |
| JavaScript / TypeScript | `tezga-sdk` | [tezga-sdk-js](https://github.com/GoSimple-agency/tezga-sdk-js) |
| PHP | `gosimple/tezga` | [tezga-sdk-php](https://github.com/GoSimple-agency/tezga-sdk-php) |

Both are thin clients over the same REST API, written directly against the official
contract so they cannot drift from the docs.

## Documentation

- [Fiscalization API](https://tezgafiskal.com/en/fiscalization-api) — guides, flows and the integrator FAQ
- [OpenAPI specification](https://tezgafiskal.com/api/openapi.json) — the source of truth
- [MCP connector](https://tezgafiskal.com/mcp-konektor) — issue test receipts from Claude, Cursor or Codex while you build

## Reliability

- **Approved ESIR**, registration number **1597** with the Serbian Tax Administration.
- **Sandbox and simulation** environments — build and test without issuing real receipts.
- SDKs are **published from CI with npm provenance**, so each release is traceable to the
  exact commit it was built from.
- Releases require **two-factor authentication** (trusted publishing), and CI runs the
  full test suite on **Node.js 22–24** and **PHP 8.1–8.5** before anything ships.
- **Idempotency** on every receipt (`externalId`) — a retried call never issues twice.

## What teams build with Tezga

Integration patterns from production projects — branded webshop receipts, a full back
office with stock and refunds, clean Excel exports for accounting, excise goods from
proforma to SEF e-invoice, and subscriptions settled with linked advances.

See **[the full write-up](https://github.com/GoSimple-agency/.github/blob/main/USE-CASES.md)**.

## Apps

Tezga on [iOS](https://apps.apple.com/rs/app/tezga-ekasa/id6815615096) and
[Android](https://play.google.com/store/apps/details?id=rs.gosimple.tezga).

## Work with us

We build and run production software for retail, hospitality and services.
Reach us at **info@gosimple.agency** or at [gosimple.agency](https://gosimple.agency).

Questions about integrating? Ask in [Discussions](https://github.com/orgs/GoSimple-agency/discussions).
See [SUPPORT](https://github.com/GoSimple-agency/.github/blob/main/SUPPORT.md) for where to take what,
[VERSIONING](https://github.com/GoSimple-agency/.github/blob/main/VERSIONING.md) for our deprecation policy, and
[SECURITY](https://github.com/GoSimple-agency/.github/blob/main/SECURITY.md) to report a vulnerability.
