# FAQ and troubleshooting

## Questions

**Is QiUD really free?**
Yes. You can use it for any lawful purpose, including at work, for free, and share the unmodified installer. You may not sell it, modify it or reverse engineer it. See [LICENSE.txt](../LICENSE.txt).

**Is it open source?**
No. The source code is not published. This repository holds the documentation, sample data and downloads.

**Does it send my data anywhere?**
No. QiUD contains no code that connects to the internet. See [Privacy](privacy.md).

**Does it change my files?**
No. Your original data files are only read. Cleaning happens on a copy in memory; **Export CSV** writes a *new* file.

**Why does Windows say "Windows protected your PC"?**
QiUD is not code-signed, so Windows treats it as coming from an unknown publisher. That is about the publisher, not a problem found in the file. Choose **More info → Run anyway**, and if you like, [check the download's SHA-256](verify-download.md).

**Which versions of Windows?**
Windows 10 and 11, 64-bit. There is no Mac or Linux version.

**Do I need to install Python, .NET or Excel?**
No. QiUD carries its own runtime and its own private copy of Python, and it does not touch any Python you have. Excel is not needed to read `.xlsx` files.

**How big a file can it open?**
The whole file is read into memory. A one-million-row, four-column CSV (about 25 MB) was tested and loads in about a second. Wide or very large files depend on your computer's memory.

**Can it make a PDF?**
Export the report as a web page, open it in a browser and print it to PDF (`Ctrl+P`). A block set to *Start on a new page* begins a fresh page. See [Build a report](tutorials/06-build-a-report.md).

**Can I send a report to someone who does not have QiUD?**
Yes: **Export web page…** writes one `.html` file that opens offline in any browser. It does not reveal where your files are stored unless you switch that on.

**Can several people work on one project?**
Not at the same time. A project is a folder; two copies of QiUD editing it at once is not supported (the last save wins). You can share the folder, and share cleaning steps as a [recipe file](tutorials/05-projects-and-recipes.md#recipes-replay-your-cleaning).

**What happens to my work if QiUD closes unexpectedly?**
The project is saved when you leave its page, close it or exit, and after actions that record history. A cleaning step you had previewed but not applied is not saved. Your original data is always intact.

**Where does QiUD keep things on my computer?**
Your projects are in the folders you chose. The list of recent projects is `%LOCALAPPDATA%\QiUD\recent.json`; the report preview keeps its browser data in `%LOCALAPPDATA%\QiUD\webview`, and temporary preview pages in `%TEMP%\QiUD-live-preview` and `%TEMP%\QiUD-preview`.

**Will you add SQL, statistics tests or machine learning?**
They are being considered, but nothing is promised. [Open a feature request](https://github.com/stanfelixskz/QiUD/issues/new/choose) to say what you need.

## Troubleshooting

**The first start is slow.**
The first start after installing can take noticeably longer while Windows scans the new files and the data engine starts. Later starts are quicker. If *every* start is slow, security software scanning the install folder can be the cause.

**"Python engine" errors, or a file will not open.**
On the Data page choose **Check Python**. It starts the engine and reports `Python engine ready: Python …, pandas …, NumPy …`. If it fails, the message names the problem. Closing and reopening QiUD restarts the engine. If an error mentions a traceback, include it in a [bug report](https://github.com/stanfelixskz/QiUD/issues/new/choose).

**A file will not open.**
QiUD explains why in plain words: the file is empty, is not a table, has rows with a different number of fields, is password-protected (Excel), or is in an unsupported format (`.xls`, `.xlsb`, `.ods`: save as `.xlsx`). For text files with unusual encodings it falls back to Windows-1252 and tells you.

**A date column is treated as text.**
Dates are not detected on load. Use **Change a column's type…** and convert it to DateTime (see [tutorial 2](tutorials/02-clean-your-data.md)). Check the day/month order first: `03/04/2026` is read as month/day/year.

**A number column is treated as text.**
Usually one cell is not a number (a `Total`, a `-`, or `N/A`). The Quality tab names the exceptions. Remove those rows or fix them, then change the column's type.

**A chart says a column is not available.**
Charts offer only suitable columns. A chart over time needs a date column (convert the type first); a chart that averages needs a number column.

**A recipe fails.**
Recipes apply by column name and are all or nothing. The message names the step and the reason (for example, a column that is not in this file). Nothing is partly applied.

**The Report page says the preview needs WebView2.**
The live preview uses the Microsoft Edge WebView2 Runtime. Windows 11 and most up-to-date Windows 10 computers have it; if yours does not, install the *Evergreen Runtime* from Microsoft. Meanwhile **Open in browser** and **Export web page…** work without it.

**The report shows a chart as a picture and I can't change its colours.**
The chart was saved by an older version, which kept only a picture. Create it again on the Data page and save it again.

**The installer was blocked by SmartScreen or antivirus.**
See [Install](install.md). The program is unsigned, so some security products are cautious with a new file. Verify the [SHA-256](verify-download.md), and report false alarms to your security vendor.

**I want to start fresh.**
Uninstall QiUD (Settings → Apps). Delete `%LOCALAPPDATA%\QiUD` to clear the recent list and the preview cache. Your projects are in the folders you chose; delete those yourself if you want them gone.

## Still stuck?

[Open an issue](https://github.com/stanfelixskz/QiUD/issues/new/choose). Tell us the QiUD version (the installer name), what you did, what you expected and what happened. **Please do not attach files containing private data.** If you can reproduce the problem with the [sample data](../sample-data), say so.
