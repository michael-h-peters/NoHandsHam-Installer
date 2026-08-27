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
.\NoHandsHam-1.1.7-x64.exe /quiet                     # silent
.\NoHandsHam-1.1.7-x64.exe /quiet ADDTOPATH=1         # also put nohandsham.exe on the PATH
.\NoHandsHam-1.1.7-x64.exe /quiet DESKTOPSHORTCUT=0   # skip the desktop shortcut
.\NoHandsHam-1.1.7-x64.exe /uninstall /quiet          # remove it
```

Upgrades replace the installed copy where it stands. Nothing to uninstall first, and
your settings, keys, licence and transcripts live under `%AppData%` and are not
touched by an install, an upgrade or a removal.

The version is at the foot of the window beside the copyright, and is the first
thing worth quoting in a bug report. The program checks once a day whether a newer
release has been published here and says one line when there is one. It never
downloads or installs anything on your behalf, and unticking **Check version** on
the top strip of the window switches the checking off for good.

---

## Releases

### 1.1.7 — 27 August 2026

**The four sliders start somewhere different.** If you have never touched them this
changes what NoHandsHam does; if you have, your settings are kept and none of it
reaches you.

| slider | was | now |
|---|---|---|
| **Gain** | 0 | 0 — unchanged |
| **Utterance length** | 25 s | **10 s** |
| **Gate** | −42 dBFS | **−60 dBFS** |
| **Margin above room noise** | +8 dB | **0 dB** |

- **Changed:** the gate is open. The two sensitivity sliders together mean speech has
  to beat whichever is higher of −60 dBFS and the measured room noise — and with the
  margin at 0, that is the room noise itself with no gap above it. The old +8 dB gap
  was protecting against something a radio feed does not have: this program is for a
  receiver patched in on a cable, a line feed has no room noise, and the gap only
  cost you the quiet stations. It does not switch the adapting off — the limit still
  follows the noise up and down as the band changes, it just sits level with it.
- **Changed:** an utterance is cut after 10 seconds rather than 25. A turn is
  transcribed only once it ends, so that ceiling is the longest you can wait to see a
  line of text; a talker who never pauses now appears in ten seconds. The price is
  the model seeing less of the turn at once, which is why it stays a slider.
- **The case these are wrong for is an open microphone in front of a loudspeaker** —
  the gate will trip on the room. Raise **Margin** to +4, then +8. Both manuals now
  say so where you would look for it.
- **Fixed:** fifteen places in the manuals quoted the old numbers, and some advice had
  become nonsense against the new floor — *"missing weak stations? lower the Gate
  toward −50"* when it now starts at −60. Both slider walkthroughs, both worked
  examples of the live reading, the chunking formula, the too-hot-and-too-cold section
  and both symptom tables are rewritten rather than renumbered.
- **Fixed:** two sentences still said settings are written only when you close the
  window, which stopped being true when 1.1.4 started saving them every ten seconds.

### 1.1.6 — 27 August 2026

**If the right-hand side of the window has been off the edge of your laptop screen,
this is the fix.**

- **Fixed:** the window opens at a size the screen can actually show. It was not
  about the width of anything inside it — the window was opening bigger than the
  display. NoHandsHam measures the screen at start-up and cuts its opening size
  down to fit, but it decided both dimensions together and abandoned the cut on
  *both* if either looked implausible. An ordinary laptop is too short by that
  measure: a 1366×768 panel at 150% scaling has about 450 of the units the app
  counts in, against a threshold of 560. So the measurement was rejected, the width
  cut went with it, and the window opened at its full 880 units on a screen 781
  wide. Only 100% scaling escaped. Each dimension is judged on its own now, against
  what a real desktop reports rather than what a roomy window would prefer.
- Seven ordinary laptop configurations were checked, from 1366×768 at 100% through
  1920×1080 at 250%. All of them now open inside the screen, title bar and borders
  included.
- Why it took a few goes: 1.1.4 and 1.1.5 made the window and the settings inside it
  able to *become* small, and both were real fixes — the window can be dragged to
  454 units and the form fits in 436, which is what makes this cut safe at any
  screen size. Neither addressed the window still *opening* too large, which is what
  put the right edge off the display.

### 1.1.5 — 27 August 2026

- **Fixed:** the settings now fit inside the window, however small you make it.
  1.1.4 let the window be dragged narrow but left the form inside it wanting 719
  units of width, so on a laptop the settings had to be scrolled sideways to be
  read. The form asks for 436 now — less than the narrowest the window can be — so
  the sideways scrollbar is there and never needed, and no setting is cut off at any
  size.
- **Changed:** the station row is two rows — *Call sign* and *Location* on the
  first, *Freq* and *Band* on the second. *Park/Location* is now **Location** and
  *Frequency* is now **Freq**, and each box is sized to what goes in it: a POTA
  reference is `K-1234`, a band is `1.25m`. The call sign box keeps room for a
  suffixed call like `KD2ABC/P`.
- **Changed:** three tick boxes had whole sentences for labels. They have short
  labels now with the sentence on the line underneath — moved, not dropped. *Send a
  radio word list* keeps its guidance about stray words that way, and *Police
  phonetics* keeps "Adam Boy Charles", which is the part you recognise. The two
  transcription options lost only words the help line directly beneath them already
  said. Nothing was removed and no setting moved section.
- **Fixed:** two faults in the wrapping rows 1.1.4 introduced, which were costing 78
  units of blank space below the top of the settings — a height that could only grow
  once it had been measured at a narrow width, and a wrapped row that never told the
  layout above it that it had grown.

### 1.1.4 — 27 August 2026

**Two bug fixes, both worth taking.**

- **Fixed:** settings no longer disappear when you upgrade. Most of what you set —
  the call sign, the mode, the microphone, every slider, the transcription engine,
  and the window's own size and position — used to be written only when you closed
  the window. An upgrade never closes it politely: Windows Installer stops the
  running copy so it can replace the files underneath it, and everything changed
  since launch went with it. So did a crash's worth, or a flat battery's. Settings
  are now written while you work: the pane is checked against the file every ten
  seconds and saved when the two differ, so the most any of them can cost is the
  last ten seconds. An untouched window writes nothing at all. The API key and the
  QRZ password were never affected — they are sealed separately and were always
  saved on the press.
- **Fixed:** the window can be made small. A window cannot be dragged narrower than
  its contents need, and the widest row that could not break held it at 741 units —
  wider than a 13-inch laptop has to spare at 200% display scaling, so on those
  machines it opened wider than the screen and could not be shrunk at all. The top
  strip and the row of buttons at the foot now wrap onto a second line instead of
  holding the window open, and the settings pane scrolls sideways rather than
  setting a floor of its own. Where 1.1.3 snapped back to 794 pixels whatever you
  asked for, 1.1.4 takes 520.
- The trade on that second one: pull the window in far enough and it needs to be a
  little taller, because those rows have wrapped and genuinely need the line.
  Nothing moves at ordinary sizes.
- **Changed:** the engine badge sits after the **?** on the top strip rather than in
  the middle of it, which is what lets that row wrap.

### 1.1.3 — 26 August 2026

**If you are on 1.1.1 or 1.1.2, take this one.**

- **Fixed:** the main window resized itself and then refused to be resized. The
  engine badge 1.1.1 added to the top strip is a text label, and a text label asks
  for exactly the width its current words need — which the toolkit enforces on the
  window in both directions, growing one that is too narrow and refusing to let you
  drag below it. So the narrowest the window could be went from 719px to 836px, and
  a window left narrower than that was pushed out at launch and would not go back.
- **Fixed:** worse, the limit *moved*. The three captions are different lengths, so
  it was 836px reading `Engine: OpenAI` and 814px reading `Engine: CPU` — switching
  engine resized the window, and a width you could drag to a minute ago you
  suddenly could not. The badge is also rewritten when you tick *Use the graphics
  card* and whenever the transcription server starts or stops, none of which you
  would connect to the top strip, which is why it looked random.
- The badge may now shorten with an ellipsis, which uncouples its width from its
  text. The floor is 741px and no longer moves — within 22px of what it was before
  any of this existed, checked across every engine and graphics-card state. The
  caption still shows in full unless you drag the window right in.
- Nothing else changes: not how transcription works, not what gets downloaded, not
  what the badge says.

### 1.1.2 — 25 August 2026

- **Fixed:** the **Use the graphics card** tick-box explains itself instead of
  disappearing. On a computer with no NVIDIA card — most computers, and every
  machine with AMD or Intel graphics — 1.1.1 simply left it out, and nothing
  anywhere else mentioned graphics either, so the feature and the absence of the
  feature looked identical. A control that is missing cannot say why it is missing.
  It is shown greyed now, reading *no NVIDIA card on this computer* or *its driver
  is too old* in its own label, which is where anyone hunting for it is looking.
- **Fixed:** a box that cannot be ticked no longer shows a tick. Settings move
  between machines, and a ticked box on a computer with no card read as "the card
  is in use" on hardware that has none.
- **Fixed:** a choice you were never offered is no longer recorded as one. Whether
  the preference is saved was decided by asking whether the box was on screen, and
  now that it is always on screen every machine without a card would have written
  "not the graphics card" — which, restored onto a desktop that has one, would have
  arrived having already declined it.
- Nothing changes about how transcription works on either engine, or about what
  gets downloaded.

### 1.1.1 — 25 August 2026

- **New:** the top strip of the window says which engine is in use —
  **`Engine: OpenAI`**, **`Engine: CPU`** or **`Engine: GPU`**. 1.1.0 added the
  graphics card and then said so only in the *Transcription* row, which is on a
  settings pane taller than the window: "is my card actually being used" cost a
  scroll and a read, which is a poor answer to a question you ask precisely because
  you are not sure. It is now visible with *Settings* collapsed and needs nothing
  pressed.
- It reports the **running server**, not the tick-box. The transcription server
  stays up between sessions so that pressing *Start listening* again does not reload
  half a gigabyte, so ticking *Use the graphics card* mid-session leaves the badge
  reading `Engine: CPU` until the process it describes really is the card's. A badge
  that followed the tick-box would have been claiming hardware that was not doing
  the work.
- `CPU` and `GPU` rather than the *processor* and *graphics card* the pane spells
  out: everything on that strip competes with how narrow the window can be dragged,
  and this is the first thing up there to set that minimum — 719px before, 836px
  now, against the 880px the window opens at. The longer phrasing would have left
  3px of that margin.
- Nothing changes about how transcription works on either engine. This release only
  says what was already true.

### 1.1.0 — 25 August 2026

- **New:** **transcribe on the graphics card.** Transcribing on this computer
  arrived in 1.0.0 and has run on the processor ever since. If the machine has an
  NVIDIA card, a **Use the graphics card** box appears in the *Transcription* row and
  the work goes there instead — quicker at the arithmetic that is most of the job, and
  it leaves the processor free for the microphone, which matters because audio capture
  runs in the same program and a dropped buffer loses words for good. It is the same
  model either way: faster, not more accurate.
- **What it costs, named before you press anything.** There is one ready-made Windows
  build of whisper.cpp for NVIDIA and it carries NVIDIA's own maths libraries inside
  it, so nothing has to be installed separately: 671 MB to download against the
  processor build's 8 MB, and about a gigabyte on disk. The line under the model
  pulldown names *both* figures first, and the tick-box is the consent — the same rule
  the model download has always followed.
- **An installation that already works is left alone.** Upgrading from 1.0.0 does not
  replace a working processor build with a 671 MB download. The card is mentioned,
  with what it would cost, and the choice stays yours. The two builds sit in separate
  folders and share the speech models, so ticking the box never re-downloads a model.
- **NVIDIA only, and only on Windows**, because whisper.cpp publishes no ready-made
  Windows build for AMD or Intel graphics — a limit of what there is to download, not
  a judgement about the hardware. On those machines the box does not appear. The
  driver must be 528.33 or newer; an older one is named alongside the version needed,
  since that is usually a ten-minute update rather than a dead end.
- **New:** at the command line, `-local-cpu` declines the card, for a metered
  connection or a small disk. `-local` on its own picks it up when there is one.
- **Changed:** the **Running** line on the settings pane describes the server that is
  actually running rather than whatever the pulldowns currently say. The server stays
  up between sessions on purpose, so that pressing *Start listening* again does not
  reload half a gigabyte — which meant changing the model mid-evening left the pane
  describing one thing and a process doing another. It now names the model that is
  loaded and says when your choice has moved on from it.

### 1.0.0 — 23 August 2026

- **New:** **transcribe on this computer**, for nothing a minute. Every minute of
  audio used to be billed — by the minute of *audio*, not by the word, so a three-hour
  net that was mostly silence cost three hours. A new **Transcription** row on the
  settings pane offers *This computer* instead of *OpenAI*, and with it chosen no API
  key is used, nothing is sent anywhere, and a session works with the internet
  unplugged.
- **New:** the server and the model are fetched for you, once, when you press
  **Download** — not because you clicked a radio button, because half a gigabyte is
  not a side effect. Four models to choose from: tiny.en 74 MB, base.en 141 MB,
  small.en 465 MB (the default, and the best trade for radio) and medium.en 1.4 GB.
  They live under `%AppData%`, which an install never touches, so an upgrade does not
  re-download them.
- **What it costs**, said in the pane and in the manual rather than found out during a
  net: call signs through noise are harder for a model on your desk than for the
  hosted one, and there is no live partial text — text arrives one finished utterance
  at a time. The status line does not claim otherwise.
- The server is [whisper.cpp](https://github.com/ggml-org/whisper.cpp), MIT-licensed
  and fetched from upstream, pinned by version and checked against a SHA-256 recorded
  in the program — this downloads an executable and then runs it. It binds to loopback
  so nothing on your network can reach it, opens no console window, and closes when
  NoHandsHam does.
- **Changed:** with *This computer* chosen the API key line reads **not in use** rather
  than reporting a fault. The local server has no key to check, and a working setup
  should not be labelled rejected.
- **New:** at the command line, `-local` and `-local-model`. The window and the command
  line have always been the same program underneath, and neither should be able to do
  something the other cannot.
- OpenAI stays the default, and nothing about an existing install changes unless you
  touch the new row.

### 0.20.0 — 23 August 2026

- **New:** checking a station into the net log is one click. Every entry in the
  transcript that names a station now carries a second box beside the roster's, and
  ticking it is the whole check-in — at the time the entry was heard, with the number
  the station took said at the foot of the window. It used to cost a dialog: click the
  entry, wait for the editor, tick *In the net log*, press **Save**.
- **New:** one station is usually on several entries, and they all agree. Tick the box
  on any of them and every other entry naming that station shows ticked; untick any
  one and they all clear. The net log window need not be open for it, or at all — tick
  your way through the net and read the list at the end.
- *In the net log* is still in the entry editor, for the check-in you make while
  putting a mis-heard call sign right. Both boxes are the same act.
- **New:** **call signs to ignore**, on the Mode row and kept between runs — for the
  repeater identifier, the club name read out, the frequency spoken as letters. One on
  that list is dropped where it is first heard rather than tidied up afterwards: it
  never reaches the transcript, the roster, the prompt, a QRZ lookup or a check-in box.
- **Changed:** the version check moved to the top strip of the control window, beside
  *Getting started* and *Manual*. It was the last row of the settings pane, which is
  taller than the window, so on a laptop-fitted window it sat the better part of eight
  hundred pixels below the fold — the one launch in a month that had news put the news
  where nobody was looking.

### 0.19.0 — 23 August 2026

- **Fixed:** running a second net without pressing **Clear** first published it under
  the *first* net's identifier, writing over it. Three nets went up as one row. Clear
  now always ends the net, including on a list already emptied by hand, which was the
  hole behind it.
- **New:** the publish line names the net and when it started — *Published “Tuesday
  Traffic Net” to nohands.net at 20:14:07, net started 19:58.* The start time is the
  tell: a net that says it began this morning when you called this one ten minutes ago
  is the fault above, visible without opening a browser.
- **Changed:** everyone signed in to nohands.net can now read every net published to
  it, including the stations who checked in. Accounts there are approved by hand, so
  it is a shared log among approved accounts on one site rather than the open web;
  there is still no public link, and deleting a net you published is yours alone.
- **Changed:** because that replaces a promise the old wording made, the dialog goes
  up once more with the new text if you already have publishing switched on. Keep
  publishing or stop; stopping leaves what is already on the server where it is.

### 0.18.0 — 23 August 2026

- **New:** **Publish to nohands.net** — the net log can go on the web while the net
  runs, updating as the list changes. Sign in at nohands.net to see it; only you can,
  and there is no public link.
- **Off unless you tick it**, and it asks first. This is the first thing NoHandsHam
  sends anywhere that is not yours — other stations' call signs, names and towns — so
  upgrading never switches it on.
- Needs a licence key; a copy on trial cannot publish.
- **New:** a dropped connection costs nothing. The net carries on, the window says it
  is still trying, and the next send catches the server up.

### 0.17.1 — 23 August 2026

- **Changed:** the net log's small print is behind a **Help** pull-down at the top of
  the window — three topics, plus the manual. It was a paragraph above the table,
  read once and then charging four lines of table for the life of the install.
- **Changed:** the topics say *more* than the paragraph did. A dialog has room for
  what a strip above a table has to cut.
- The **Save…** reminder stayed on the window, beside the count. Of the four things
  that paragraph said it is the only one with a deadline, and learning it from a menu
  you never opened means learning it after closing the app on an evening's work.
- About twelve check-ins are visible at once, up from eleven.

### 0.17.0 — 23 August 2026

- **New:** the net log has a header — the net's name, net control's call sign, name
  and QTH, and the frequency and band. All of it is written into the saved file.
- **New:** the call sign, frequency and band in that header *are* the ones on the
  settings pane. Change either and both follow, so you can retune from whichever
  window is in front of you.
- **New:** your own name and QTH are looked up on QRZ.com — the one lookup the
  program never used to make. Both stay editable, and what you type is not
  overwritten by an answer arriving later.
- **Changed:** the net log window opens larger, and its two paragraphs of small
  print became one, to pay for the height the header takes. About eleven check-ins
  are visible at once.

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
