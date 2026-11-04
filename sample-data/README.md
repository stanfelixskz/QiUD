# Sample data

Invented data for the [tutorials](../README.md#learn-it-in-an-afternoon). **None of it is real:** no real shop, customers or sales. It is free to use for trying out QiUD, in demos and in training.

It describes a small coffee shop with four stores, from 2 January to 30 June 2026, and it has **realistic problems put in on purpose**, so the tutorials have something to find and fix.

## The files

| File | Use it for |
|---|---|
| [`coffee-shop-sales.csv`](coffee-shop-sales.csv) | The main file: tutorials [1](../docs/tutorials/01-open-and-inspect.md) to [6](../docs/tutorials/06-build-a-report.md). 529 data lines and 13 columns. |
| [`coffee-shop-sales.xlsx`](coffee-shop-sales.xlsx) | The same orders as a workbook with the table starting on **row 4** (a title above it), two quarters on two sheets (`Q1 2026`, `Q2 2026`) and a text-only `About` sheet. For [tutorial 7](../docs/tutorials/07-excel-and-json.md). |
| [`coffee-shop-orders.json`](coffee-shop-orders.json) | 80 of the orders as JSON records with **nested fields** (`customer.ageGroup`, `item.product`) and a `tags` list. For [tutorial 7](../docs/tutorials/07-excel-and-json.md). |

## The columns of the CSV

| Column | Meaning |
|---|---|
| `order_id` | The order number. |
| `date` | The day of the order (`yyyy-mm-dd`). Opens as text; convert it to a date. |
| `hour` | The hour of the day, 6 to 18. |
| `store` | `Downtown`, `Harbor`, `Uptown` or `Airport`. |
| `product`, `category` | What was sold (`Latte`, `Cappuccino`, `Espresso`, `Cold Brew`, `Croissant`, `Muffin`, `Bagel`) and whether it is a `Drink` or `Food`. |
| `units`, `unit_price` | How many, and the price of one. Prices rise by 0.25 from April. |
| `discount_pct` | The discount, 0, 5, 10 or 15 per cent. |
| `payment` | `card`, `mobile` or `cash`. |
| `customer_age` | The customer's age in years. |
| `rating` | A 1 to 5 rating, when the customer gave one. |
| `notes` | A free-text note, when there is one. |

## The problems on purpose

| Problem | What to expect | Where it is dealt with |
|---|---|---|
| **Test rows** | Two rows with store `TEST` and product `TEST ITEM`. | [Tutorial 2, step 1](../docs/tutorials/02-clean-your-data.md#step-1-remove-the-test-rows) |
| **A `Total` line** | The last line has `order_id` `Total` and the sum of all units. | [Step 2](../docs/tutorials/02-clean-your-data.md#step-2-remove-the-total-line) |
| **Duplicates** | Six orders appear twice (exact copies). | [Step 3](../docs/tutorials/02-clean-your-data.md#step-3-remove-duplicate-rows) |
| **Missing values** | About 30 `discount_pct`, 20 `payment` and 40 `customer_age` values are blank; most `rating` values (170) and about half of the `notes` are blank. | [Steps 4 and 5](../docs/tutorials/02-clean-your-data.md#step-4-fill-the-missing-discounts) |
| **Dates as text** | `date` has to be converted before it can be used on a time axis. | [Step 6](../docs/tutorials/02-clean-your-data.md#step-6-turn-the-dates-into-real-dates) |
| **Inconsistent spelling** | `payment` has `card`, `Card` and `CARD`, and `mobile` and `Mobile`. | [Step 7](../docs/tutorials/02-clean-your-data.md#step-7-add-a-cleaned-payment-column) |
| **Impossible ages** | One age of `140` and one of `0`. | [Tutorial 3, outliers](../docs/tutorials/03-explore.md#outliers-unusual-values) |
| **A probable typing mistake** | One order has `units` of `40`, most likely meant to be 4. | An outlier in `units` |

There are also real patterns to find: weekends are busier, the shop grows through the half year, Downtown is the busiest store, lattes are the most popular product, and prices step up in April.

If you want to start again, just download the file again: QiUD never changes it.
