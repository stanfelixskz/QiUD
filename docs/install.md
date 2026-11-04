# Install QiUD

## Requirements

- Windows 10 or Windows 11, 64-bit.
- About 300 MB of free disk space (the program is about 280 MB installed, and the download is about 75 MB).
- Nothing else. QiUD carries its own runtime and its own private copy of Python, and it does not use or change any Python you already have.
- Optional: the **Microsoft Edge WebView2 Runtime**, which draws the live preview on the Report page. Windows 11 and most up-to-date Windows 10 computers already have it. Without it, the preview area says so, and *Open in browser* and *Export* still work.

## Install

1. Go to the [latest release](https://github.com/stanfelixskz/QiUD/releases/latest) and download **`QiUD-0.4.0-Setup.exe`**.
   (Optional: [check the download](verify-download.md).)
2. Double-click the file.
3. **Windows may say "Windows protected your PC".** That message appears for any program from a publisher Windows does not know yet. QiUD is not code-signed. Choose **More info**, then **Run anyway**.
4. Read the licence and accept it to continue.
5. Choose **Next** through the pages. The default folder is inside your own user profile, so **no administrator rights are needed**.
6. Tick **Create a desktop shortcut** if you want one, then **Install**, then **Finish** (leave "Start QiUD" ticked to open it).

The first time QiUD starts it can take noticeably longer, while Windows scans the new files and the data engine starts. After that it opens in a few seconds.

QiUD is added to the Start menu and to **Settings → Apps → Installed apps**.

## Update

Run a newer `QiUD-…-Setup.exe`. It replaces the program files in place. Your projects, data files and the list of recent projects are not touched. It also replaces an installation made with the older script installer, so QiUD is listed only once.

If QiUD is running, the installer asks you to close it first.

## Uninstall

**Settings → Apps → Installed apps → QiUD → Uninstall.**

This removes the program only. **Your projects, data files, exports and reports are never deleted.** The small list of recent projects QiUD keeps lives in `%LOCALAPPDATA%\QiUD` and is also left in place; delete that folder yourself if you want it gone.

## Silent install (for IT)

```
QiUD-0.4.0-Setup.exe /VERYSILENT /SUPPRESSMSGBOXES /NORESTART /DIR="D:\Tools\QiUD"
```

The licence page is skipped in a silent install, so whoever runs it has accepted the [licence](../LICENSE.txt) on behalf of the people who will use it.

## If something goes wrong

See [FAQ and troubleshooting](faq.md#troubleshooting).
