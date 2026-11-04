# Reference

A complete list of what QiUD does, and what it does not. For a guided introduction, start with the [tutorials](../README.md#learn-it-in-an-afternoon).

## The window

| Part | What it is |
|---|---|
| **Home** | Start a project, open one, or explore a file without a project. Lists recent projects and datasets. |
| **Project** | The datasets, saved charts and analyses, recipes and history of the open project. |
| **Report** | Design and export the project's report, with a live preview. |
| **Data** | Open a file, then Data, Preview, Summary, Quality, Group by, Correlation, Outliers and Charts tabs, with the **Clean** panel on the left. |
| **Close project** | Saves and closes the open project (needs one to be open). |
| **Dark mode** | The switch at the bottom left. Changes the whole app, including charts. |

Toolbar on the Data page: **Open file**, **Export CSV**, **Undo**, **Redo**, **Reset to original**, and **Check Python** (see [troubleshooting](faq.md#troubleshooting)).

Keyboard: `Ctrl+Z` undo, `Ctrl+Y` redo, `Enter` in the search box searches.

## Files

| Kind | Notes |
|---|---|
| **CSV, TSV, TXT** | Delimiter detection (comma, semicolon, tab, pipe), quoted fields, UTF-8 BOM, Windows-1252 fallback with a note. |
| **Excel** (`.xlsx`, `.xlsm`) | Sheet picker with an Excel-numbered preview and header-row detection. One sheet at a time. Not supported: `.xls`, `.xlsb`, `.ods`, password-protected files. |
| **JSON** (`.json`, `.jsonl`, `.ndjson`) | Lists of records, wrapped lists, JSON Lines. Nested objects become `a.b` columns. Lists inside records are kept as text. UTF-8 only. |

Your original file is only ever read. QiUD can also be started with a path: `QiUD.exe data.csv` (relative paths work), or a project folder.

## Looking at data

- Detected column types: integer, decimal, true/false, date/time, text. Missing values per column.
- **Sort** by clicking a header (all rows; numbers as numbers, dates as dates).
- **Filter** one column: contains, equals, does not equal, greater than, less than, is empty, is not empty. Values are checked against the column's type.
- **Search** all columns (literal text).
- Rows shown 200 at a time.
- **Summary:** count, missing, unique, mean, standard deviation, min, quartiles, median, max, date range, most common value.
- **Quality:** exact duplicate rows, empty or mostly-missing columns, columns with one value, numbers or dates stored as text. Findings are observations with no automatic fix.

## Cleaning (always previewed first)

| Step | Notes |
|---|---|
| Keep only rows with missing values / Remove rows with missing values | All columns or one. |
| Replace missing values with… | A typed value, the mean, the median, or the most common value. |
| Remove duplicate rows | All columns or one; the first occurrence is kept. |
| Rename a column… | |
| Change a column's type… | Text, integer, decimal, true/false, date/time. Shows what cannot convert and warns about lost leading zeros. |
| Remove rows where… | Up to 10 conditions combined with *all* (AND) or *any* (OR): contains, equals, does not equal, greater than, less than, is empty, is not empty. |
| Move a column… | Start, end, before or after another column. Also by dragging a column header. |
| Add a column… | Date part, arithmetic, time between two dates, text operations (incl. patterns), group a number into ranges, join columns. Placed after its source or at the end. |

Every step is recorded, listed under **Changes to working copy**, and can be undone and redone. **Reset to original** takes back all of them. **Export CSV** writes the working copy and never overwrites the original.

Text patterns (regular expressions) refuse patterns that repeat a repeated group, such as `(a+)+`, and patterns longer than 500 characters, because those can take a very long time.

## Exploring

- **Group by:** one or two columns; the row count per group and Sum, Mean, Median, Min, Max or Std dev of a numeric column. Up to 500 groups.
- **Correlation:** Pearson or Spearman, up to 40 numeric columns; heatmap, strongest pairs and matrix.
- **Outliers:** IQR or Z-score on one numeric column; the flagged rows are listed and nothing is changed.

## Charts

Bar chart (optionally split, stacked or side by side), line chart, summary line (optionally split), area chart, scatter plot (colour and size), histogram, most common values, box plot, pie, donut, Pareto, average with error bars, heatmap. See [Make charts](tutorials/04-charts.md).

## Projects and recipes

- A project is a folder (`project.json` plus a `charts` folder). Datasets are referenced, never copied.
- Saved: charts (picture, settings and numbers), group-by, correlation and outlier results, dataset summaries, each with **your note** kept apart from computed results; recipes; history; the report layout.
- Reopening a dataset offers to **restore the steps you had applied**.
- **Recipes** replay a list of cleaning steps, all or nothing, by column name. They can be exported to and imported from `*.recipe.json` files, which contain no data.

## Reports

Described in [Build a report](tutorials/06-build-a-report.md). In short: blocks (charts, analyses, summaries, datasets, recipes, work log, your own text and headings) in an order you choose; titles, captions, intro and closing text; accent colour, chart colours, font and background; per-chart colours, axis names, legend, height, value labels and smoothing; a live preview; and export as one self-contained interactive HTML file (printable to PDF) or as Markdown.

## Known limits

These are things QiUD does not do, or does within a limit. They are listed so you are not surprised.

**General**
- Windows only (10 or 11, 64-bit).
- The whole file is read into memory, and a cleaning step may briefly need a second copy. A 1,000,000-row × 4-column CSV (about 25 MB) was tested and loads in about a second on a development computer; much wider or larger files are limited by your memory.
- Rows with a different number of fields, or unbalanced quotes, stop a file from opening, with an explanation.
- "Missing" means an empty cell. Placeholders such as `N/A` or `-` stay as text.
- Dates are not detected when a file loads: a date column opens as text and the Quality tab suggests converting it. `03/04/2026` is read as month/day/year; there is no day/month option yet.
- Integers beyond 2^53 lose precision if converted from text. Exported numbers are normalised (`1.50` becomes `1.5`).
- If you cancel a long operation or it times out, the data engine is restarted and the open file must be opened again.
- Undo and redo work within the current session of an open file; the undo stack is not saved (applied steps are, per dataset, in a project). Filter, search and chart choices are not remembered between sessions.

**Analysis and charts**
- Correlation uses at most 40 columns; group-by at most two columns and 500 groups.
- A bar chart shows the 30 largest categories; line and scatter charts thin to 5,000 evenly spaced points.
- Split charts show at most 8 colours or lines (those with the most rows), and there is no way yet to choose *which* values to draw.
- A summary line has one aggregation and one value column per chart.
- A pie, donut or Pareto chart shows counts or totals only (not averages), and not negative totals.
- There are no free-form formulas in derived columns; a text pattern extracts only its first group.

**Files**
- Excel: one sheet at a time; formulas read as the values last saved.
- JSON: UTF-8 only; lists inside records are kept as text, not exploded into rows; only one list is used from a wrapper object; whole-number floats such as `2.0` and `2` are not told apart.

**Projects and reports**
- Moving a project folder is fine; moving a *data file* needs **Locate…**.
- Editing one project from two QiUD windows at once is not supported (the last save wins).
- Charts saved by versions before 0.4.0 have only a picture in reports.
- The live preview needs Microsoft Edge WebView2.
- There is no direct PDF or Word export: print the HTML report to PDF from a browser.

**Not in QiUD (yet)**
- SQL, statistical tests, database connectors and machine learning. These are being considered but are **not** promised.
- Code signing, so Windows shows its unknown-publisher notice on first run.
