# Variation Import Issue in WooCommerce

## Context

During the development of this WooCommerce store,  
variable products were imported using the default CSV importer.

Parent products were created successfully.  
However, variations were not properly recognized by the system.

---

## Observed Behavior

- Parent products existed
- Attribute values were visible
- Variation rows were included in the CSV
- Some products appeared as **Out of stock**
- Variations were not selectable or purchasable

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

As a result:

- Variations may exist in the system
- But the product is not fully synchronized
- The product can appear non-purchasable or out of stock

The issue was not incorrect CSV formatting,  
but incomplete post-import synchronization.

---

## Resolution

- Parent products were imported via CSV
- Variations were re-saved in the admin panel to trigger synchronization
- Once synchronized, products became selectable and purchasable

For larger-scale imports, a dedicated import tool or automated post-import rebuild process is recommended.

---

## Key Takeaway

Importing variable products in WooCommerce is not only about importing data —  
it also requires proper rebuilding of product relationships.

Without that rebuild step, products may exist but remain functionally invalid.
