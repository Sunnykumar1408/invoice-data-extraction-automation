# Combined Purchase + Sale Invoice Extractor & Register Generator

An end-to-end automated extraction and reconciliation pipeline built to eliminate manual data entry from vendor and customer invoices into reporting registers[cite: 2].

## Overview

The tool auto-detects, extracts, normalizes, and reconciles mixed batches of PDF invoices across disparate business systems[cite: 2]:
- **Sale Invoices:** Tally-generated Tax Invoices (e.g., East India Hospitality / Meghdoot Media)[cite: 2].
- **Purchase Invoices:** SAP-generated multi-page Tax Invoices (e.g., Bikaji Foods International)[cite: 2].

## Key Features

- **Format Auto-Detection:** Automatically inspects PDF metadata and layout to direct documents to the proper extraction parser[cite: 2].
- **Fuzzy Product Normalization:** Uses `difflib.SequenceMatcher` with regex cleansers to normalize cryptic SAP item descriptions (e.g., `N_Bikaneri Bhujia_59G_5.664`) against a Master Catalog containing Category, Flavour, Grammage, and Pack Sizes[cite: 2].
- **Batch Aggregation:** Consolidates multi-batch purchase line items into single product-level records with quantity-weighted averages for unit costs and discounts[cite: 2].
- **Automated 2-Pass Matching:**
  - **Exact Match:** Correlates sale reference fields directly back to source purchase invoice numbers[cite: 2].
  - **Fuzzy Match:** Pairs records based on normalized product keys and ship-to/bill-to party similarity scores[cite: 2].
- **Styled Excel Output:** Generates formatted workbooks featuring **Sale Summary**, **Purchase Summary**, and an audit-ready **Combined Register** with auto-calculated gross profit margins (`openpyxl`)[cite: 2].

## Tech Stack

- **Language:** Python
- **Libraries:** `pdfplumber`, `openpyxl`, `re`, `difflib`, `ipywidgets`[cite: 2]
- **Environment:** Google Colab / Jupyter Notebook[cite: 2]
