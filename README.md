# Combined Purchase + Sale Invoice Extractor & Register Generator

An end-to-end automated extraction and reconciliation pipeline built to eliminate manual data entry from vendor and customer invoices into reporting registers.

## Overview

The tool auto-detects, extracts, normalizes, and reconciles mixed batches of PDF invoices across disparate business systems:
- **Sale Invoices:** Standard Tally-generated Tax Invoices.
- **Purchase Invoices:** Enterprise SAP-generated multi-page Tax Invoices.

## Key Features

- **Format Auto-Detection:** Automatically inspects PDF metadata and layout to direct documents to the proper extraction parser.
- **Fuzzy Product Normalization:** Uses `difflib.SequenceMatcher` with regex cleansers to normalize coded ERP item descriptions against a Master Catalog containing Category, Flavour, Grammage, and Pack Sizes.
- **Batch Aggregation:** Consolidates multi-batch purchase line items into single product-level records with quantity-weighted averages for unit costs and discounts.
- **Automated 2-Pass Matching:**
  - **Exact Match:** Correlates sale reference fields directly back to source purchase invoice numbers.
  - **Fuzzy Match:** Pairs records based on normalized product keys and ship-to/bill-to party similarity scores.
- **Styled Excel Output:** Generates formatted workbooks featuring **Sale Summary**, **Purchase Summary**, and an audit-ready **Combined Register** with auto-calculated gross profit margins (`openpyxl`).

## Tech Stack

- **Language:** Python
- **Libraries:** `pdfplumber`, `openpyxl`, `re`, `difflib`, `ipywidgets`
- **Environment:** Google Colab / Jupyter Notebook
