# What teams build with Tezga

Real integration patterns from production projects. Clients are anonymized, and every
flow below is built on the public [Tezga Fiscal API](https://tezgafiskal.com/en/fiscalization-api)
and its [SDKs](https://github.com/GoSimple-agency) — no custom back door, nothing you
cannot build yourself against the same contract.

Each pattern names the endpoints it uses, so you can tell whether your own case fits
before writing a line of code.

---

## 1. Branded receipts for an online store

**Who:** a Serbian e-commerce shop.

**The problem.** Every paid order has to become a legal fiscal receipt and reach the buyer
immediately — carrying the shop's own branding, not a generic one. Some orders are paid as
advances before the goods ship.

**What was built.** A server-to-server flow: each paid order calls `POST /order`, Tezga
fiscalizes it and returns the PFR number, QR payload and a **PDF that carries the shop's
logo**. Advance payments open an advance receipt through `POST /advance`. Delivery of the
PDF is configurable — sent by Tezga, or handed back so the shop sends it from **its own
mail system and domain** — so the customer only ever sees the shop's brand.

**Result.** Receipts are issued and delivered the moment an order is paid, with no manual
step, fully under the shop's brand.

---

## 2. A full back office for an online store

**Who:** a second e-commerce.

**The problem.** Beyond issuing receipts, the shop needed stock, returns and refunds, and
reporting — all driven from one integration instead of several disconnected tools.

**What was built.** `POST /order` for fiscalized receipts; the product catalogue and stock
kept in sync through `POST /products`; returns and money-back handled with `POST /refund`
(a full void, or a refund of selected items); and reporting and analysis assembled from
`GET /documents` and `GET /transactions`.

**Result.** Issuing, stock, refunds and reporting run from a single integration, so the
numbers in the reports always match the receipts that produced them.

---

## 3. Clean accounting exports for an enterprise

**Who:** an enterprise *d.o.o.* (limited company).

**The problem.** The accountant needed a tidy, detailed and accurate report — in Excel —
that reconciles without manual cleanup at month-end.

**What was built.** A reporting layer that pulls fiscal documents through `GET /documents`
and matches them against bank movements from `GET /transactions`, then renders a structured
Excel workbook the bookkeeper can use directly, accurate to the source documents.

**Result.** Month-end reporting arrives ready to use, so the bookkeeper spends the time on
the books instead of on cleaning up data.

---

## 4. Excise goods, from proforma to final receipt

**Who:** a distributor of excise goods.

**The problem.** The e-waybill, the fiscal receipt and the **SEF e-invoice** had to be
joined into one automated chain, so their own customers receive everything automatically —
from proforma all the way to the final receipt.

**What was built.** A pipeline that issues the proforma, then produces the fiscal receipt
and the SEF e-invoice from the same call using the `tok` flow (`fiskalni_i_sef` / `sef`) on
`POST /order`, tied to the waybill step, so each customer document is created and delivered
in the right order without manual handling.

**Result.** The whole document chain — proforma → fiscal receipt → SEF e-invoice — runs
automatically for every order.

---

## 5. Subscriptions settled with linked advances

**Who:** a subscription business.

**The problem.** Customers pay in several instalments over a period, and at the end it must
all become **one** final fiscal receipt — without any payment ever being counted twice.

**What was built.** Each instalment opens an advance receipt through `POST /advance`, and
all advances for one subscription are linked. At the end, a single call with
`zatvori: true` refunds the advances and issues one final fiscal receipt that consolidates
them. If that closing refund does not go through, the final receipt is not issued — so
turnover can never be double-counted.

**Result.** Several advance payments (typically five to ten) collapse into one correct
final receipt, exactly as the Tax Administration expects for linked advances.

---

These are integration patterns, not fixed products — the exact flow is tailored per
project. Building something similar? Reach us at **info@gosimple.agency**.
