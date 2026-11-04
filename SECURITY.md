# Security

## Reporting a problem

If you think you have found a security problem in QiUD (for example, a way a crafted data file, recipe file or project file could make QiUD do something it should not), please **do not open a public issue**.

Use one of these instead:

1. **GitHub private vulnerability reporting:** on this repository choose **Security → Report a vulnerability**.
2. Or email **escuetajohn21@gmail.com** with "QiUD security" in the subject.

Please include the QiUD version, what you did, what happened, and a small file that shows it if you can make one *without any private data in it*.

You will get a reply, and a fix will be released as soon as it is practical. QiUD is maintained by one person, so please be patient.

## What is in scope

- The QiUD program and installer you download from the [Releases](https://github.com/stanfelixskz/QiUD/releases) page.
- Files QiUD reads (data files, recipe files, project files) and what it does with them.
- Reports it exports (for example, text that could be treated as code in the HTML page).

## What to know about how QiUD is built

- QiUD runs on your computer and contains no code that connects to the internet.
- Recipe files are checked before use and contain no data.
- Everything typed into a report is shown as text, never as markup, and colours and fonts are validated before they reach the page.
- Text patterns that could make the engine run for a very long time are refused.
- The installer is currently **not code-signed**. Compare the SHA-256 on the [release page](docs/verify-download.md) with your download.

## Supported versions

Only the latest release is supported.
