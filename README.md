# UPI Transaction Reliability \& Failure Resolution Intelligence

**A BFSI data analytics portfolio project | PostgreSQL · SQL · Power BI
· DAX · Power Query**

## Overview

This project analyses UPI-style digital payment activity for **PayFlow
Technologies**, a fictional Indian digital payments company. It
investigates transaction failures, retry outcomes, bank-level patterns,
reversal performance, and customer complaints through SQL analysis and
interactive Power BI dashboards.

> \*\*Data disclaimer:\*\* This is an educational project built entirely
> with synthetic data. PayFlow Technologies, bank names, transaction
> records, patterns, and findings are fictional. The results do not
> represent actual UPI, NPCI, RBI, bank, or payment-network performance.

## Business Questions

* How often do transaction attempts succeed, fail, or remain pending?
* How often do payment requests eventually succeed after retries?
* Which failure reasons, banks, transaction types, and hours show
higher failure rates?
* What transaction value is associated with failed attempts?
* How are reversal cases progressing, and how long do completed
reversals take?
* What is the status of customer complaints?

## Tools \& Technologies

* **PostgreSQL / SQL:** Database design, data validation, business
analysis, reporting views
* **Power BI / DAX:** Data model, KPI measures, interactive dashboards
* **Power Query:** Data cleaning, transformation, and date/type
preparation

## Dataset

The database contains seven tables and **950,137 rows**:

Table                    Description                                        Rows

\---

`dim\_customers`          Customer attributes                              10,000
`dim\_banks`              Fictional bank reference data                        15
`dim\_date`               Calendar dimension (1 Apr 2025--1 Apr 2026)         366
`fact\_payment\_intents`   Customer payment requests                       400,000
`fact\_transactions`      Individual transaction attempts                 500,000
`fact\_reversals`         Reversal records                                 22,125
`fact\_complaints`        Customer complaint records                       17,631

**Grain matters:** One payment intent can contain multiple transaction
attempts. Attempt-level metrics and payment-intent-level metrics
therefore use different denominators.

## Power BI Dashboards

### 1\. Executive Overview

Monitors transaction volume, attempt success and failure rates,
payment-intent success, retry recovery, transaction-attempt value,
failed-attempt value, average attempts per payment intent, and monthly
success trends.

### 2\. Transaction Failure Analysis

Examines technical and insufficient-balance failure rates, failure
reasons, bank-wise performance, P2P/P2M differences, hourly failure
patterns, and the Top 10 customers by failed attempts.

### 3\. Reversal \& Customer Experience

Tracks reversal amount and status, completed reversal rate, pending
reversal amount, failed reversals, average reversal turnaround time,
P2P/P2M SLA compliance, complaint volume, and complaint resolution.

## Key Findings

All figures below are calculated from the synthetic project dataset.

Metric                                                        Result

\---

Transaction attempts                                         500,000
Payment intents                                              400,000
Attempt success rate                                          71.68%
Attempt failure rate                                          27.85%
Payment-intent success rate                                   89.60%
Retry recovery rate                                           62.76%
Total transaction-attempt value                      ₹183,469,981.11
Failed-attempt value                                  ₹51,158,659.50
Technical failures as a share of failed attempts              44.60%
Bank A payer-bank failure rate                                29.67%
Bank O payer-bank failure rate                                26.94%
Total reversal amount                                  ₹8,116,124.58
Completed reversal rate                                       88.13%
Pending reversal amount                                  ₹635,260.91
Average reversal TAT                                     41.07 hours
P2P reversal SLA compliance                                   82.10%
P2M reversal SLA compliance                                   84.33%
Total customer complaints                                     17,631
Complaint resolution rate                                     64.27%

### Interpretation Notes

* Failed-attempt value is not automatically lost revenue; a later
retry may succeed.
* Total transaction-attempt value includes retries and is not unique
payment value.
* Technical failure share is based on three mapped reasons:
`TECHNICAL\_TIMEOUT`, `BANK\_SERVER\_UNAVAILABLE`, and `NETWORK\_ERROR`.
* The project's illustrative reversal targets are 24 hours for P2P and
120 hours for P2M. These are analytical assumptions, not regulatory
determinations.
* Reversal TAT is measured from the original transaction timestamp to
reversal completion.

## Disclaimer

This project is for educational and portfolio purposes only. It is not
affiliated with NPCI, RBI, any bank, or any payment service provider.
All data and findings are synthetic and must not be interpreted as
real-world payment-system performance or regulatory compliance.

