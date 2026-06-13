# Data Quality & Audit Report

## 1. Executive Summary
This document outlines the data-quality audit of the raw D2C personal-care brand datasets before building the retention predictive frameworks.

## 2. Structural Deficiencies Identified
* **Missing Value Analysis:** Structural fields such as `customers.gender` and historical marketing indices contain empty strings. High frequency of null variables observed in `orders.discount_code` (representing regular-price transactions without codes).
* **Duplicate Multiplicity:** Minor instances of temporal duplicates appear in `orders.csv` where identical product clicks registered twin backend logs simultaneously.
* **Outlier Deviations:** `orders.total_price` exhibits a severe right-skewed tail, pointing to major order-size variations from wholesale buyers or duplicate line-item tallies.
* **Invalid Field Integrity:** Negative integers located within item quantity categories and event time logs indicating future clock values out-of-bounds relative to the snapshot timeline.
* **Join & Mapping Inconsistencies:** Merging transactional `orders` and `support_tickets` against `customers.csv` revealed trace orphaned logs lacking verified user mapping.

## 3. Recommended Treatment Plan
1. **Null Values:** Impute critical continuous data using localized sample medians; preserve categorical absence via an explicit `"UNKNOWN"` tag.
2. **De-duplication:** Run exact matching criteria across transaction identifiers to drop redundant log records safely.
3. **Outlier Mitigation:** Utilize 95th-to-99th percentile capping barriers on financial metrics to suppress distortion in the machine-learning pipeline.
4. **Referential Integrity:** Standardize cascading removals on orphan foreign identifiers that cannot map back to active customer master nodes.
