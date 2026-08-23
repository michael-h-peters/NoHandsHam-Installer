# NoHandsHam — release notes

Speech to text for amateur radio operators: it listens to your radio, writes down
what was said, and pulls the call signs out of it. Windows, and it runs on the
machine rather than needing a browser open.

**[Download the newest installer](https://github.com/michael-h-peters/NoHandsHam-Installer/releases/latest)**

This repository holds no source code. It exists to publish the installer and the
manuals, so that downloading NoHandsHam does not mean going anywhere near a source
tree. The program itself lives in
[michael-h-peters/NoHandsHam](https://github.com/michael-h-peters/NoHandsHam).

Below is every release and what was in it, newest first. Each entry is a line or
two; the full notes for a release are on
[its own page](https://github.com/michael-h-peters/NoHandsHam-Installer/releases),
and the manual explains any of it properly. There is a
[PDF of this page](RELEASE-NOTES.pdf) if you would rather keep one.

**Releases from 0.13.2 are downloadable here.** Everything before that predates this
repository and is listed for the record — the version numbers are what the program
reports at the foot of its window, so an old copy can still be placed.

---

## What is in a release

| file | what it is |
|---|---|
| `NoHandsHam-<version>-x64.exe` | the installer — this is the one to download |
| `GETTING-STARTED.pdf` | the short guide: install it, get a key, make a first entry |
| `README.pdf` | the full manual, every setting and every flag |

Both PDFs are installed alongside the program as well, and reachable from the
**Documents** button in the window, so there is nothing to keep track of after the
install.

Double-click the `.exe` and answer the wizard. It carries everything it needs; there
is no runtime to install first. For an install with no clicking:

```powershell
.\NoHandsHam-0.17.0-x64.exe /quiet                     # silent
.\NoHandsHam-0.17.0-x64.exe /quiet ADDTOPATH=1         # also put nohandsham.exe on the PATH
.\NoHandsHam-0.17.0-x64.exe /quiet DESKTOPSHORTCUT=0   # skip the desktop shortcut
.\NoHandsHam-0.17.0-x64.exe /uninstall /quiet          # remove it
```

Upgrades replace the installed copy where it stands. Nothing to uninstall first, and
your settings, keys, licence and transcripts live under `%AppData%` and are not
touched by an install, an upgrade or a removal.

The version is at the foot of the window beside the copyright, and is the first
thing worth quoting in a bug report. The program checks once a day whether a newer
release has been published here and says one line when there is one. It never
downloads or installs anything on your behalf, and unticking **Check version** on
the settings pane switches the checking off for good.

---

## Releases

### 0.17.0 — 23 August 2026

- **New:** the net log has a header — the net's name, net control's call sign, name
  and QTH, and the frequency and band. All of it is written into the saved file.
- **New:** the call sign, frequency and band in that header *are* the ones on the
  settings pane. Change either and both follow, so you can retune from whichever
  window is in front of you.
- **New:** your own name and QTH are looked up on QRZ.com — the one lookup the
  program never used to make. Both stay editable, and what you type is not
  overwritten by an answer arriving later.
- **Changed:** the net log window opens larger and shows about a dozen check-ins at
  once.

### 0.16.0 — 22 August 2026

- **New:** a **net log** — a third window holding the stations that have checked in,
  numbered in the order they called, with the time, the call sign, and the
  operator's name and town. Stations go on it by ticking a box in the entry editor;
  unticking takes them off and the numbers close up.
- **New:** correcting a call sign corrects the check-in without renumbering the net.
- Save it before closing: this is the one record the program does not write to disk
  by itself, so that next week's net does not open with this week's still in it.

### 0.15.0 — 22 August 2026

- **Changed:** NoHands is now **NoHandsHam** — the name of the company that makes
  it. Same program, same people; the window, the Start Menu, the install folder, the
  manuals and the ADIF exports all say it.
- Installs over an existing NoHands where it stands: one entry in *Settings › Apps*,
  which changes its name. Your licence needs nothing re-entered.

### 0.14.1 — 22 August 2026

- **New:** correcting a call sign corrects **every** entry that named that station,
  along with the call sign log and the export. A station mis-heard once in a round
  was mis-heard the same way in the others, and correcting six entries by hand to
  reach a state the log had already assumed was six times the work.

### 0.14.0 — 21 August 2026

- **Changed:** the update-check address came off the settings pane. It was a box
  holding one value that only a release can change; what is left is the tick, which
  was the only real choice on that row.

### 0.13.3 — 20 August 2026

- **Fixed:** the update check asks this repository, which is public, rather than the
  source repository, which is not. Copies of 0.13.1 and 0.13.2 were asking a private
  repository and being told nothing at all.

### 0.13.2 — 20 August 2026

- No code changes — a version number and the documents stamped with it, so that
  0.13.1 installs had a release to notice.

### 0.13.1 — 20 August 2026

- **Changed:** the update check asks what the newest *release* is, rather than
  reading a version file kept by hand. A file nothing in the build reads is a file
  that goes stale.

### 0.13.0 — 20 August 2026

- **Fixed:** the update check shipped in 0.12.3 could not reach the file it asks
  for, because that file was in a private repository. No code changed; the
  repository did.

### 0.12.3 — 20 August 2026

- **New:** the app says when a newer version has been published — one line at the
  foot of the settings pane, once a day, and nothing the rest of the time. Nothing
  is downloaded or installed for you.

### 0.12.2 — 20 August 2026

- **New:** the American police alphabet on request. US public-service nets spell
  with *Adam Boy Charles*, and those words used to mean nothing to the program —
  "William one Adam William" came out as four names with no call sign found.

### 0.12.1 — 20 August 2026

- **New:** the contact tally says how many are still to tick — `10/20 contacts in
  the log` — so the boxes waiting for attention are a number rather than a scroll.

### 0.12.0 — 19 August 2026

- **New:** both windows reopen where you left them, at the size you left them, and
  maximised if that is how you left them. A window whose monitor has gone comes back
  centred rather than somewhere unreachable.

### 0.11.0 — 19 August 2026

- **Changed:** the licence agreement is shown and has to be read before a licence
  seat is spent. Activating used to claim the seat the moment the button was pressed,
  with the agreement a PDF you opened only if you thought to.

### 0.10.0 — 19 August 2026

- **New:** a **Documents** pull-down in the window header reaching all five shipped
  documents — the guide, the manual, and the cookie, DMCA and installer-licence
  policies. They install alongside the program, so they open offline.

### 0.9.5 — 18 August 2026

- **Changed:** the app says it transcribes the radio, not the operator. The empty
  transcript window used to read "as you speak", which sent new users talking into a
  headset and getting a transcript of the wrong end of the QSO.
- **Fixed:** the README pointed at an `.msi` the release page no longer offers.

### 0.9.4 — 18 August 2026

- **Fixed:** every link in the window looks like a link. Three of the five — the
  OpenAI key page, the QRZ subscription and where to buy a licence — were still the
  dimmest text on screen.

### 0.9.3 — 18 August 2026

- **Fixed:** the two document links at the foot of the window were nearly
  unreadable.
- **Changed:** *Model* and *Base URL* moved down the settings pane, below the
  sliders an operator returns to mid-session. Both have a working default and were
  charging two rows of height to everything under them.

### 0.9.1 — 18 August 2026

- **New:** the guide and the manual are linked at the foot of the window. Both
  install with the program and get a Start Menu entry, and nothing in the window
  said so.

### 0.9.0 — 17–18 August 2026

- **New:** *Getting Started* — a short guide covering installing, getting a key and
  setting the four sliders, for people who should not have to read a
  1,500-line manual first. Both PDFs now ship with every release.
- **New:** a failing session says *which* failure it is. A rejected API key, an
  expired licence and a dead microphone look identical from the operator's chair:
  Start is pressed and nothing arrives.
- **New:** every PDF is stamped with its version, so a manual on disk can be matched
  to the program that installed it.
- **Fixed:** the shipped binaries were four commits behind the release they were
  attached to.

### 0.8.5 — 16–17 August 2026

- **New:** the log export writes for **POTA, SOTA, Field Day** or as a plain generic
  log. It was POTA and nothing else, with POTA's own field hardcoded.
- **Changed:** the sliders that decide what is heard sit above the ones set once and
  left. The gate slider used to be several hundred pixels below the bottom of a
  laptop-sized settings pane.
- **Fixed:** text boxes and checkboxes got borders that can actually be found.

### 0.8.4 — 16 August 2026

- **Fixed:** field and checkbox edges were drawn at 1.3:1 against the window behind
  them — a boundary you have to find and click, rendered as a rumour. Now at the
  accessibility floor.

### 0.8.3 — 16 August 2026

- **Changed:** the level meter colours by where the bar is rather than by raw
  decibels. Nobody reads a meter in dBFS.

### 0.8.2 — 16 August 2026

- **New:** a live level meter under the gain slider. The slider shipped in 0.8.1
  with nothing to set it against, and "turn the microphone up by 12 dB" is not
  something anybody knows in advance.
- **Fixed:** the desktop app opened a black command window beside itself on every
  launch.

### 0.8.1 — 16 August 2026

- **New:** a microphone gain slider, for an input that is too quiet before anything
  else in the app can help it — a headset across the room, or a receiver patched in
  on a cable.

### 0.8.0 — 16 August 2026

- **New:** the licence block says what the licence *is* — who it is issued to, how
  many computers, the expiry date, the trial days left — rather than one line
  summarising it and throwing the rest away.

### 0.7.2 — 15 August 2026

- **New:** the app says when transcription is failing, and checks the stored key at
  start-up rather than letting a session discover it. A session that transcribes
  nothing looks exactly like a dead microphone.

### 0.7.1 — 15 August 2026

- **Changed:** the licence moved to the top of *Accounts* and says whose it is. A
  bare "Licence" beside OpenAI and QRZ.com invited the guess that it belonged to one
  of them.

### 0.7.0 — 15 August 2026

- **New:** licensing. A key goes in the settings, *Activate* claims this computer's
  seat, and the app validates in the background at start-up — so a slow or
  unreachable licence server never delays the window.

### 0.6.7 — 15 August 2026

- **Changed:** the two account blocks fold away. Filled in on the first run and then
  left alone, they were costing a third of the settings pane for the life of the
  install.
- **Fixed:** the window asked for more height than the screen could show, which left
  the mouse and the picture out of step until it was resized by hand.

### 0.6.6 — 15 August 2026

- **New:** the settings say which accounts the program wants — OpenAI's, for the
  transcription you pay for, and QRZ.com's — and link to the page that issues each.

### 0.6.5 — 14 August 2026

- **New:** a running contact count at the foot of the transcript window. It used to
  appear only at the end of an export, after four dialogs.

### 0.6.4 — 14 August 2026

- **Fixed:** a window launched straight into Dark came up with its labels and help
  lines in the light theme's near-black — dim to the point of unreadable — until the
  look was changed and changed back.

### 0.6.3 — 14 August 2026

- **New:** a log opened from disk can be exported. Opening one used to put text in
  the window and nothing in the records, and the export refused.

### 0.6.2 — 14 August 2026

- **Changed:** the light/dark choice moved to the top right corner, out of the
  settings pane. It was the one setting you had to scroll to in order to use, and the
  only one whose effect is visible the instant it changes.

### 0.6.1 — 13 August 2026

- **New:** light or dark by choice, not only whatever Windows is set to. A laptop set
  light for daylight work is the wrong thing to have open in a dark shack.

### 0.6.0 — 13 August 2026

- **New:** a call sign you corrected or typed in is looked up on QRZ.com. It was the
  one call sign on screen that was certainly right and the only one with no name
  beside it, because the lookup that was made was made for the mis-hearing.

### 0.5.3 — 13 August 2026

- **New:** click an entry to correct what was heard, or **Add entry…** for a contact
  the microphone missed. Transcription is wrong in whole letters, and until now that
  letter was permanent.

### 0.5.2 — 13 August 2026

- **Fixed:** the version line added in 0.5.1 shipped invisible — drawn in the
  theme's *disabled* colour.

### 0.5.1 — 13 August 2026

- **New:** the version at the foot of the window. It was in four places, none of them
  open at the moment something goes wrong.

### 0.5.0 — 13 August 2026

- **Changed:** your own station came back off every transcript line. 0.3.0 put it
  there; it is the same twenty-odd characters on every row, and it belongs in the
  record rather than in the text.

### 0.4.0 — 12 August 2026

- **New:** export the ticked contacts as an **ADIF** file POTA will take. The app had
  written a real log since 0.3.0 and getting it uploaded still meant retyping every
  line.

### 0.3.0 — 12 August 2026

- **New:** your station is recorded with every contact — call sign, park or location,
  frequency and band, in four boxes across the top of the settings. A call sign says
  who was worked; nothing said where from.

### 0.2.2 — 12 August 2026

- **Changed:** the QRZ answer moved to the end of its entry rather than a line below
  it, where it cost a row per answered call sign and read as a second entry.

### 0.2.1 — 12 August 2026

- The version the program reports, the number stamped into the MSI and the file
  names in the manual moved together, from one constant.

### 0.2.0 — 12 August 2026

- **Changed:** HamLog is now **NoHands** — the module, both binaries, the installer
  and its product and folder names.

### 0.1.5 — 12 August 2026

- **Changed:** the installer ships as an `.exe` wrapping the `.msi`. An `.exe` is
  what people expect to download, and what a browser or mail client is least likely
  to hold up.

### 0.1.4 — 12 August 2026

- **Fixed:** the installer shortcut is in the install folder as well as the Start
  Menu, so an installed copy's own directory has a way back to it.

### 0.1.3 — 12 August 2026

- **New:** the QRZ answer appears in the transcript window, which is the window an
  operator actually watches. It was only ever reported on the control window.

### 0.1.2 — 12 August 2026

- **Changed:** the call sign log records only the contacts you have ticked, and names
  them from QRZ. A mis-heard run of phonetics can produce a perfectly well-formed
  call sign that no station holds.

### 0.1.1 — 12 August 2026

- **New:** a Windows MSI installer. The program was two loose executables and a PDF,
  and installing it meant knowing which one to run.

### 0.1.0 — 12 August 2026

- First release. A Windows desktop app and a CLI that transcribe continuously
  through the OpenAI speech API, built around what a radio operator actually needs:
  phonetics read back as call signs, a log of who was worked, and no typing.
