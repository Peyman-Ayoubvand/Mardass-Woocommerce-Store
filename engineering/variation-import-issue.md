# Variation Import Issue in WooCommerce

## Context

During the development of this WooCommerce store,  
variable products were imported using the default WooCommerce CSV importer.

Parent products were created successfully.  
However, variations were not consistently built or recognized as purchasable.

---

## Observed Behavior

- Parent products existed
- Attribute values were visible
- Variation rows were included in the CSV
- Some products appeared as **Out of stock**
- Variations were not selectable in the product page

---

## Investigation

The following were verified:

- Correct product types (`variable` and `variation`)
- Proper parent–child linking (SKU / ID)
- Global attributes (`pa_size`, `pa_color`)
- Consistent attribute values
- Stock and manage stock fields
- Lookup table regeneration

All data appeared structurally correct.

---

## Root Cause

The default WooCommerce CSV importer does not always fully rebuild  
the internal structure of variable products after import.

In some cases, variations exist in the system  
but the product is not fully synchronized,  
which causes it to behave as non-purchasable or out of stock.

This was identified as a limitation/behavior of the default importer  
rather than an incorrect CSV structure.

---

## Resolution

To complete the project efficiently:

- Parent products were imported via CSV
- Variations were created and finalized manually in the admin interface
- This triggered WooCommerce to properly rebuild the variable product structure

For production-level or large-scale imports,  
a specialized import tool (e.g., WP All Import)  
or an automated post-import synchronization process would be recommended.

---

## Key Takeaway

Importing variable products in WooCommerce is not only about data fields —  
It requires the correct rebuilding of product relationships.

Understanding system behavior is essential when working with structured product data.
