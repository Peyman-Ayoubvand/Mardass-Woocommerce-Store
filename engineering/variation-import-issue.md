# Variation Import Issue in WooCommerce

## Problem

While importing variable products using the default WooCommerce CSV importer,  
parent products were created successfully, but variations were not properly built.

Observed behavior:

- Parent products existed
- Attribute data was present
- Variation rows existed in CSV
- Products appeared as **Out of stock**
- Variations were either missing or not purchasable

---

## Investigation

The following elements were validated:

- Product types (`variable` / `variation`)
- Parent–variation relationship (SKU and ID mapping)
- Correct global attributes (`pa_size`, `pa_color`)
- Attribute term consistency (slug vs label)
- Stock and manage_stock columns
- Lookup table regeneration

All structural CSV data appeared correct.

---

## Root Cause

The WooCommerce CSV importer does not always trigger  
the internal synchronization process required to fully register variations.

Specifically, the method:

WC_Product_Variable::sync()

was not consistently executed after import.

As a result:

- Variation metadata existed
- But variation relationships were not fully indexed
- Products were treated as non-purchasable
- Stock status appeared inconsistent

The issue was not incorrect CSV formatting,  
but incomplete post-import synchronization.

---

## Resolution

- Parent products were imported via CSV
- Variations were validated and manually saved to trigger synchronization
- Confirmed limitation of default WooCommerce importer

For large-scale or production imports,  
a dedicated import solution or automated post-import sync process is recommended.

---

## Key Takeaway

In WooCommerce, importing data is not only about fields and values —  
it is about correctly building relational product structures.

If internal synchronization is not completed,  
products may exist but remain functionally invalid.

