# Privacy

The short version: **QiUD works on your computer and sends nothing anywhere.**

## What QiUD does with your data

- **It reads your files.** CSV, Excel and JSON files you open are read by QiUD's data engine (a Python process that runs on your computer) and held in memory.
- **It never changes your originals.** Cleaning happens on a working copy. It writes only what you ask it to: a CSV you export, a project, a saved chart, an exported report.
- **It does not upload, share or report anything.** QiUD itself contains no code that connects to the internet, and no analytics, telemetry or crash reporting. (The source was searched for network code and none was found in the program or in its data engine.)
- **It does not need an account**, and it has no licence server or activation.

## What the exported report contains

An exported web page is **one self-contained file**: its styles, its chart library and the numbers behind each chart are inside it. Opening it does not load anything from the internet. When someone opens it, nothing is sent anywhere.

What *is* in it is what you chose to include: your titles and text, the numbers behind the charts you saved, tables you saved, and (if you leave them on) the "how this was made" cleaning steps and the work log. **Read it before you share it.** In particular:

- The full folder of each dataset is **hidden by default** (only the file name is shown), so the report does not reveal where your files live on your computer. You can switch it on in **Whole report → Show**.
- The work log lists what you did in the project, with file names.
- Charts keep the *numbers that were drawn* (category names, values, points), not your whole dataset. But a chart of a column of names *is* a list of those names, so think about what a chart or table reveals before you share it.

## Files QiUD keeps on your computer

| What | Where |
|---|---|
| Your projects and saved charts | The folders you choose. |
| The list of recent projects and datasets | `%LOCALAPPDATA%\QiUD\recent.json` |
| Browser data for the report's live preview | `%LOCALAPPDATA%\QiUD\webview` |
| Temporary report pages (preview) | `%TEMP%\QiUD-live-preview` and `%TEMP%\QiUD-preview`. These contain your report's content; Windows clears the temp folder over time, and you can delete them yourself. |

Uninstalling QiUD does not delete any of these (see [Install](install.md#uninstall)).

## Components QiUD uses

- **Microsoft Edge WebView2** draws the live preview on the Report page. It is a Microsoft component with its own terms and settings; QiUD uses it only to show a page stored on your own computer.
- **Python, pandas, NumPy and openpyxl** run locally inside QiUD's private copy of Python.

## Downloading QiUD

The only network activity involved with QiUD is your own download of the installer from GitHub, which is subject to [GitHub's privacy statement](https://docs.github.com/site-policy/privacy-policies/github-general-privacy-statement).

## The licence

The [licence](../LICENSE.txt) says the same in legal terms (section 4, *Your data and your files*). This page is an explanation, not a contract.

## Questions

[Open an issue](https://github.com/stanfelixskz/QiUD/issues/new/choose) (without private data in it) or see [SECURITY.md](../SECURITY.md) for a security concern.
