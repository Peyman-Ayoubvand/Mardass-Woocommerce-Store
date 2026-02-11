
# Product Architecture

## Overview

This document outlines the product data structure implemented for the WooCommerce store.  
The focus is on structured catalog management, scalable SKU logic, and clean product organization.

---

## SKU Strategy

Format:
`[Category Prefix]-[Product Type (optional)]-[Sequential Number]`

Category Prefixes:
- DRS → Dresses
- KNT → Knits
- SET → Sets

Examples:
- KNT-DRESS-002
- DRS-COAT-003
- SET-007

In some cases, the product type segment was simplified when unnecessary.

This structure allows:
- Clear category identification
- Internal organization
- Scalable product expansion

---

## Product Types

Two product types are used:

- **Simple Products** → Single variation items  
- **Variable Products** → Products with Size and/or Color variations  

Variation Rules:
- Price assigned at variation level
- Stock managed per variation
- Parent product holds gallery images
- Featured status applied only to parent product

---

## Category Structure

Primary Categories:
- Dresses
- Knits
- Sets

Each product is assigned to a single primary category to maintain a clean taxonomy.

---

## Attributes

Standardized attributes:

- Size (Small, Medium, Large, One-size)
- Color (when applicable)

Attributes are structured consistently across products.

---

## CSV Import Logic

Products are structured using WooCommerce CSV format.

Implementation logic:
- Parent product defines structure and images
- Variations contain pricing and stock data
- Stock quantity managed per size
- Featured products controlled at parent level

This enables efficient bulk product management.

---

## Naming Convention

Product names follow a structured format:

`[Descriptor] + [Product Type]`

Examples:
- Red Cutout Neck Knit Dress
- Minimal Two-Piece Set
- Ribbed Knit Sweater

The naming approach improves clarity, consistency, and search relevance.

---

## Media

Product images are sourced from Unsplash for demonstration purposes.
