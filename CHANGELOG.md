# Changelog

All notable changes to QiUD, newest first. Dates are when a version was built.

## 0.4.0: first public release (November 2026)

The first version published here. Earlier development builds were not released. In this version:

**Open and inspect**
- CSV/TSV, Excel (`.xlsx`, `.xlsm`, with a sheet picker and header-row detection) and JSON / JSON Lines (nested fields become columns).
- Sorting, filtering and searching across all rows; per-column types and missing counts.
- A Summary tab and a Quality tab (duplicates, empty columns, numbers or dates stored as text).

**Clean, with previews**
- Fill missing values (a value, mean, median or most common value), remove duplicates, remove rows where conditions match (up to 10, all or any), rename, retype and move columns (including by dragging a header).
- Add columns: date parts, arithmetic, time between dates, text operations and patterns, number ranges (with open ends), and joined columns.
- Every step is previewed, recorded, undoable and redoable. Original files are never changed.
- **Export the cleaned data as CSV, an Excel workbook (`.xlsx`), JSON or JSON Lines.** Excel keeps real number and date types and never turns text into a formula; JSON keeps every digit of every number; anything that could not be written exactly is reported.

**Explore and chart**
- Group-by summaries, correlation (heatmap, strongest pairs, matrix) and outlier inspection.
- Charts: bar (split, stacked or side by side), line, summary line (split into lines), area, scatter (coloured and sized by other columns), histogram, most common values, box plot, pie, donut, Pareto, averages with error bars, and heatmaps.

**Projects and recipes**
- Projects keep datasets, saved charts and analyses with your notes, a history, and the steps you applied (offered again when you reopen a dataset).
- Recipes: save cleaning steps, replay them on another file, and share them as `*.recipe.json` files.

**Reports**
- A **Report page** with a **live preview**: choose and order blocks, write your own text and headings, and change titles, captions, colours, fonts, backgrounds and per-chart style.
- Export **one self-contained interactive HTML file** (opens offline; printable to PDF), or a Markdown report.
- Saved charts keep their numbers so a report can redraw them in your colours.

**Installer and app**
- A normal Windows setup program (per-user, no administrator rights, with the licence shown), uninstallable from Settings → Apps.
- The QiUD icon, a dark mode, and an in-app **Check Python** diagnostic.
- Third-party licence notices ship with the program.

**Fixes worth knowing about** (made during development of this version)
- Column headers with an underscore (such as `order_id`) are shown exactly as written.
- Cancelling the Excel sheet picker returns you to the page you came from instead of leaving an empty Data page.
- A dataset left open from one project is no longer silently added to a different project.
- Axis names on report charts are no longer cut off.
