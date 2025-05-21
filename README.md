# Perspective Count Aggregation Bug Reproduction

This project demonstrates a bug in the [Perspective Viewer](https://github.com/finos/perspective) where the aggregated "Total" count value becomes incorrect after a series of updates.

## 📋 Description

When updating a `perspective.table` with multiple rows that are filtered out using a `"not in"` filter, the aggregated count for a visible column behaves unexpectedly. Specifically:

- On first update, the "Total" count is **1** (correct).
- On second update, it becomes **0** (unexpected).
- On third update, it jumps to **4294967295** (clearly incorrect).

The expected result: The count should consistently remain **1** across all updates.

## 🧪 How to Reproduce

1. Clone or open the HTML file in a browser.
2. Observe the "Total" column value over time as the table updates with a 1-second delay between each update.

## 📦 Technologies Used

- [@finos/perspective](https://www.npmjs.com/package/@finos/perspective)
- [@finos/perspective-viewer](https://www.npmjs.com/package/@finos/perspective-viewer)
- CDN module imports (via jsDelivr)

## 🔁 Steps Demonstrated

- Viewer is loaded with a schema and an initial filter (`FieldB not in ["B-1", "B-2"]`)
- Aggregation is applied as `count` on `FieldA`
- Sequential updates are sent to the table
- The count value becomes invalid

## 🐛 Bug Summary

This bug may be related to how filtered-out rows are handled internally in the aggregation engine after repeated updates.

---

Feel free to open an issue or contribute if you have insights or solutions.
