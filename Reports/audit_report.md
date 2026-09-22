# Audit Report

The dataset contains 3,732 product records, of which 453 are marked as out of stock, resulting in an overall stock-out rate of 12.14%.

Stock-out rates vary considerably across categories, with Biscuits at 28.57%, followed by Beverages and Dairy, Bread & Batter at 21.71%.

The analysis also identified several high-value unavailable products, including Patanjali Cow's Ghee with an MRP of ₹565.00 and MamyPoko diapers with an MRP of ₹399.00, based on the dataset's apparent price units.

Discounting and inventory distribution also vary across categories, providing additional areas for inventory and pricing review.

## Inventory Health

| Metric         |  Value |
| -------------- | -----: |
| Total products |  3,732 |
| Available      |  3,279 |
| Out of stock   |    453 |
| Stock-out rate | 12.14% |

453 of the 3,732 product records are currently marked as out of stock, representing a 12.14% stock-out rate.

A meaningful portion of the listed assortment is unavailable, which may represent potential lost sales opportunities if customer demand exists for these products.

## Stock-Out Analysis

| Category              | Stock-out rate |
| --------------------- | -------------: |
| Biscuits              |         28.57% |
| Beverages             |         21.71% |
| Dairy, Bread & Batter |         21.71% |
| Meats, Fish & Eggs    |         19.05% |
| Health & Hygiene      |         13.40% |
| ...                   |            ... |

Stock availability differs substantially across categories. Biscuits have the highest stock-out rate at 28.57%, while Personal Care and Paan Corner have the lowest rates at 6.10%.

This indicates that inventory availability is not uniform across the assortment. Categories with higher stock-out rates may require further investigation into replenishment frequency, demand patterns, or inventory allocation.

## High-Value Unavailable Products

| Product              | Category           |   MRP | Discount | Selling Price |
| -------------------- | ------------------ | ----: | -------: | ------------: |
| Patanjali Cow's Ghee | Munchies           | 56500 |       0% |         56500 |
| Patanjali Cow's Ghee | Cooking Essentials | 56500 |       0% |         56500 |
| MamyPoko Diapers     | Paan Corner        | 39900 |       7% |         36900 |
| ...                  | ...                |   ... |      ... |           ... |

Several relatively high-value products are unavailable. The highest-MRP unavailable product in the extracted results is Patanjali Cow's Ghee.

High-value stock-outs may deserve additional attention because product unavailability affects the ability to sell those products while they remain listed in the assortment.

## Discount Analysis

Discounting varies significantly across categories. Fruits & Vegetables has the highest average discount at 15.46%, while Home & Cleaning has the lowest average discount at 5.68%.

Categories with higher discount levels may warrant further investigation to determine whether discounting is aligned with inventory availability and product demand.

## Inventory Distribution

Available inventory is concentrated in several categories. Munchies and Cooking Essentials each contain 2,186 available units, while Meats, Fish & Eggs has the lowest total available inventory at 152 units.

This distribution should be interpreted alongside stock-out rates because a large total inventory does not necessarily mean that all products within a category are sufficiently stocked.

## Conclusion

The overall inventory health shows a 12.14% stock-out rate, with availability varying widely across categories. Biscuits, Beverages, and Dairy, Bread & Batter stand out as the most stock-out-prone categories, while high-value products such as Patanjali Cow's Ghee and MamyPoko Diapers remain unavailable despite being listed. Discounting is skewed toward Fruits & Vegetables, and inventory is unevenly concentrated in Munchies and Cooking Essentials. These findings point to clear opportunities for improving replenishment, prioritization, and pricing decisions.

The visual report is available in the Excel file here: `../Excel/Quick_Commerce_Inventory_Analysis`