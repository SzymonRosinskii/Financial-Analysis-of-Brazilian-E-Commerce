# Financial-Analysis-of-Brazilian-E-Commerce
# Brazilian E-Commerce — Business Insights

> A data analysis project exploring what drives sales, which products are most profitable, and who the most valuable customers are on the Olist marketplace (2016–2018).

**Author:** Szymon Rosiński
**Status:** Completed April 2026
**Dataset:** [Brazilian E-Commerce Public Dataset by Olist (Kaggle)](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) — 100k+ orders
**Access to the [Scope of Work](docs/Scope_of_Work.pdf)**
**Access to [Methodology](docs/Methodology.pdf)**

---

## Table of Contents

1. [Background and Overview](#1-background-and-overview)
2. [Data Structure Overview](#2-data-structure-overview)
3. [Executive Summary](#3-executive-summary)
4. [Insights Deep Dive](#4-insights-deep-dive)
5. [Recommendations](#5-recommendations)

---

## 1. Background and Overview

Olist is a Brazilian marketplace that connects small merchants to major e-commerce platforms. Its public dataset captures over **100,000 real orders** placed between 2016 and 2018 across every Brazilian state, spanning order details, customers, products, payments, reviews, and geolocation.

This project treats Olist as a stakeholder and asks four concrete business questions:

1. **What drives sales?** — geography, shipping, and product categories
2. **Which products are most profitable?** — revenue vs. units sold, category outliers
3. **Who are the most valuable customers?** — payment habits, order frequency, revenue contribution
4. **How can the business increase sales?** — three data-driven recommendations

> **Out of scope:** demographic customer profiling (sex, age, earnings) and behavioural/psychographic analysis.

### Deliverables

| Milestone | Description |
| --- | --- |
| Data extraction | All needed data pulled from the dataset via SQL |
| Metrics | Statistical metrics and customer analysis complete |
| Presentation | Slide deck finalised against deliverables |
| Ship final analysis | Buffer for revisions and polish |

### Limitations

- Timespan is limited to 2016–2018 and does **not** reflect COVID-era e-commerce behaviour.
- Real product IDs are anonymised in the Olist dataset — product-level deep dives are constrained.
- Demographic customer data (age, sex, income) is unavailable and intentionally out of scope.

---

## 2. Data Structure Overview

| Property | Value |
| --- | --- |
| Source | Olist via Kaggle |
| Timeframe | 2016 – 2018 |
| Orders | ~100,000 |
| Currency | Brazilian Real (R$) |
| Type | Real commercial data |

The analysis follows the Google Data Analytics framework (*Ask → Prepare → Process → Analyze → Share → Act*), compressed into three artefacts:

1. **Ask + Prepare → `Scope_of_Work.docx`** — purpose, scope, deliverables, and success criteria defined up front.
2. **Process + Analyze → SQL queries + Python notebooks** — Kaggle CSVs imported into BigQuery, joined across Olist's relational schema, then cleaned in pandas (decimal separator normalisation, column renaming for Tableau compatibility).
3. **Share + Act → Final slide deck** — stakeholder-facing deck built to Google Data Analytics presentation guidelines, with Tableau maps, Sheets charts, and curated speaker notes.

### Tech Stack

| Stage | Tools |
| --- | --- |
| Storage & extraction | **Kaggle**, **Google BigQuery (SQL)** |
| Analysis | **Python** (`pandas`, `numpy`), manual cleaning |
| Visualisation | **Tableau**, **Google Sheets** |
| Presentation | **PowerPoint** with curated speaker notes |
| Workflow assist | AI-assisted query drafting & slide review |

---

## 3. Executive Summary

- **Geography is the single strongest sales predictor.** Order volume by state tracks closely with state nominal GDP, and São Paulo is a clear outlier driving a disproportionate share of activity.
- **Delivery performance is a quiet competitive edge.** A 97.3% successful delivery rate beats the ~95% industry benchmark and points to high operational quality.
- **Category choice explains most of the sales-volume variance** (R² ≈ 0.64), but the most *profitable* categories (watches, computers) are not the highest-volume ones (garden tools).
- **Top spenders are frequency-driven, not ticket-driven.** They actually spend *less* per order than the average customer but buy ~9× more often — each top spender is worth roughly nine single-time shoppers.
- **Three levers can lift revenue:** better support for high-ticket orders, incentives for *boleto* payments, and a loyalty/first-purchase reward system.

---

## 4. Insights Deep Dive

### 4.1 What drives sales — geography and shipping

Order counts are highly concentrated in the industrialised south-east. São Paulo (SP) is a dominant outlier, followed by Minas Gerais (MG) and Rio de Janeiro (RJ). The spatial pattern mirrors state-level nominal GDP almost one-to-one — consumer income, not Olist's marketing footprint, is the structural driver of where orders come from.

<img width="1784" height="1214" alt="orders-by-state-map" src="https://github.com/user-attachments/assets/b62e98a2-14a8-44bd-9a87-55bca0af05fc" />

<br>

On the operational side, delivery is a strength rather than a weakness: **97.3% of orders are delivered successfully**, compared to a ~95% industry average. That's a silent satisfaction driver visible in repeat-purchase behaviour further down the funnel.

### 4.2 Which products are most profitable — revenue vs. units

Across the 72 product categories in the dataset, category membership alone explains **~64% of the variation in units sold** (R² = 0.64). But the plot below reveals something more interesting: four categories sit well above the regression line — **Furniture, Watches, Health & Beauty, and Bed & Bath** — meaning they generate more revenue than their unit volume would predict.

<img width="1784" height="1214" alt="Zrzut ekranu 2026-04-17 224220" src="https://github.com/user-attachments/assets/d6530940-5892-41ff-9619-4e3efc1cbda2" />

<br>

**Volume leader:** garden tools drive the bulk of units sold.
**Margin leaders:** computers and watches carry the largest per-unit revenue.
The gap between "sells a lot" and "makes a lot" is the opportunity space in section 5.

### 4.3 Who are the most valuable customers

Two very different customer profiles emerge when the customer base is split by spending cohort:

| Segment | Avg. Order Value | Avg. # Orders |
| --- | --- | --- |
| Average customer | **R$156.18** | 1.03 |
| Top spenders | R$110.59 | **9.40** |

Top spenders actually pay *less* per order than the average customer — their value comes from **frequency**. Over the observed window, one top spender generates roughly **R$1,000 in profit, equivalent to nine single-time shoppers**.

Payment behaviour is just as telling: top spenders overwhelmingly use **credit cards**, with **no debit card usage** observed in the top cohort. *Boleto* (Brazil's common bank-slip payment method) is under-used relative to its potential as a retention lever.

---

## 5. Recommendations

1. **Improve high-end sales.** High-ticket orders are an under-served segment — invest in platform functionality, support, and checkout flows that specifically cater to them. Computers and watches in particular punch above their weight on margin.
2. **Adjust payment methods.** Actively incentivise **boleto** usage (e.g. small discount or cashback). Boleto is associated with higher customer lifetime value and can convert more single-purchase shoppers into repeat buyers.
3. **Launch a customer reward system.** Reward returning customers with small recurring benefits to reinforce the frequency pattern that makes top spenders valuable. Pair it with a **first-time purchase bonus** to widen the top of the funnel in lower-GDP states where order volume is currently thin.
