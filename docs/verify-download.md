# Check your download

Each release lists a **SHA-256** checksum for the installer. Comparing it takes a few seconds and shows that the file you have is exactly the one that was published.

## Windows PowerShell

Open PowerShell in the folder where you saved the installer and run:

```powershell
Get-FileHash .\QiUD-0.4.0-Setup.exe -Algorithm SHA256
```

The long value under **Hash** must be the same as the one on the release page (and in the `.sha256` file published with it). Capitals or lower case does not matter.

## Version 0.4.0

```
b7cf2f8130850fba4a5c8d5f7597a02cf5c5eae544f9fc826bc5ae00e7da9a58  QiUD-0.4.0-Setup.exe
```

If the values differ, do not run the file. Download it again from the [Releases page](https://github.com/stanfelixskz/QiUD/releases), and [open an issue](https://github.com/stanfelixskz/QiUD/issues/new/choose) if it still does not match.

## What the checksum does and does not tell you

- It shows the file was not damaged or swapped on its way to you.
- It does not prove who made it. QiUD is **not code-signed**, which is why Windows shows its "unknown publisher" notice on the first run. Code signing is something this project may add later.
