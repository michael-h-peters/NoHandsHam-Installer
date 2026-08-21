# NoHands — installer downloads

Speech to text for amateur radio operators: it listens, writes down what was
said, and pulls the call signs out of it. Windows, and it runs on the machine
rather than needing a browser open.

**[Download the newest installer](https://github.com/michael-h-peters/NoHands-Installer/releases/latest)**

This repository holds no source code. It exists to publish the installer and the
two manuals, so that downloading NoHands does not mean going anywhere near a
source tree. The program itself lives in
[michael-h-peters/NoHands](https://github.com/michael-h-peters/NoHands).

## What is in a release

| file | what it is |
|---|---|
| `NoHands-<version>-x64.exe` | the installer — this is the one to download |
| `GETTING-STARTED.pdf` | the short guide: install it, get a key, make a first entry |
| `README.pdf` | the full manual, every setting and every flag |

Both PDFs are installed alongside the program as well, and reachable from the
**Docs** button in the window, so there is nothing to keep track of after the
install.

## Installing

Double-click the `.exe` and answer the wizard. It carries everything it needs;
there is no runtime to install first.

For an install with no clicking:

```powershell
.\NoHands-0.13.2-x64.exe /quiet                     # silent
.\NoHands-0.13.2-x64.exe /quiet ADDTOPATH=1          # also put nohands.exe on the PATH
.\NoHands-0.13.2-x64.exe /quiet DESKTOPSHORTCUT=0    # skip the desktop shortcut
.\NoHands-0.13.2-x64.exe /uninstall /quiet           # remove it
```

## Which version am I running

The version is at the foot of the window, next to the copyright line, and it is
the first thing worth quoting in a bug report. The program also checks once a day
whether a newer release has been published here, says one line when there is one,
and says nothing the rest of the time. It never downloads or installs anything on
your behalf, and clearing the address in **Check version** switches the checking
off for good.
