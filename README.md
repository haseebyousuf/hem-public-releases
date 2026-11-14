# Hem

**Your MacBook trackpad's edges and corners, turned into controls.**

Slide up the right edge to turn the volume up. Slide the left edge for brightness. Double-tap a corner
to play or pause, flick in from the right for Notification Center. Hem keeps the edges asleep while
you type, ignores palms and ordinary pointing, and shows what happened in a HUD that grows out of the
notch.

**[Download the latest version](https://github.com/haseebyousuf/hem-public-releases/releases/latest)**

This repository holds Hem's releases and this guide. Hem is free to use; its source isn't public yet.

## Requirements

- macOS 27 on an Apple silicon Mac
- The built-in trackpad (a Magic Trackpad should work but hasn't been tested yet)

## Install

1. Download **Hem-x.y.z.dmg** from the
   [latest release](https://github.com/haseebyousuf/hem-public-releases/releases/latest), open it, and
   drag **Hem** into **Applications**.

2. Hem isn't signed by Apple, so macOS blocks it the first time. Open **Terminal** and run:

   ```sh
   xattr -dr com.apple.quarantine /Applications/Hem.app
   ```

   This removes the "downloaded from the internet" mark from Hem only. If you'd rather not use
   Terminal: open Hem once, then go to **System Settings › Privacy & Security**, scroll down and click
   **Open Anyway**.

3. Open Hem. It walks you through a short setup and asks for **Accessibility**: turn on Hem in the
   list that opens. Setup moves on by itself once it's allowed.

Hem then runs in the background. Its icon in the menu bar has quick controls and opens the full
window, where you choose what each edge and corner does.

## Update

From version 0.3.0, Hem updates itself: **Hem › About › Check for Updates**, then **Update Now**. Hem
downloads the new version, checks that it's signed by the same developer (a tampered download is
refused), replaces itself and restarts. No Terminal command; your settings and permissions stay.

Turn on **Check automatically once a day** in About to hear about new versions without asking.

**Updating from 0.2.0 or earlier** (once, by hand):
1. Quit Hem (menu bar icon › Quit Hem).
2. Download the new DMG and drag Hem into Applications, replacing the old one.
3. Run the command from step 2 of Install again.

## Permissions and privacy

| Permission | Why |
| --- | --- |
| **Accessibility** (required) | To know that a key went down (never which key) so the edges sleep while you type, and to send shortcuts, move windows and open Notification Center. |
| **Automation** (asked when first needed) | To read and set the playback position in Music, Spotify and browser tabs, and to switch dark mode. |
| **Audio capture** (only for one app's volume) | To pass one app's sound through at the level you set. Nothing is recorded. |

Hem has no accounts, analytics or tracking. It goes online for one thing only: asking GitHub whether a
newer release is out, when you click **Check for Updates** (Hem › About), or once a day if you turn
that on (it's off by default). Nothing about you or your Mac is sent. Your settings, touch log and daily
counts stay on your Mac in `~/Library/Application Support/Hem`.

## Troubleshooting

**"Hem is damaged and can't be opened" or "Apple could not verify Hem"**
Run the command from step 2 of Install, then open Hem again.

**The edges do nothing**
- Check that Hem is on: its menu bar icon shows pause bars when it's paused.
- Check **System Settings › Privacy & Security › Accessibility**: Hem must be in the list and turned
  on. If it's on but Hem still doesn't react, remove it with the **–** button, then open Hem again and
  allow it.
- Open Hem › Settings › More › **Troubleshooting** to see which parts are working.

**A slide or tap happens when I didn't mean it**
Open Hem › **Activity**: it lists every touch Hem acted on or ignored, and why. Settings › Feel ›
**Edge width** makes the edges narrower. Under Settings › More › Advanced settings, **Strict mode**
makes a slide count only after you rest or click first.

**Seeking doesn't work in a browser tab**
For sites other than YouTube, the browser must allow JavaScript from Apple Events (in Chrome-based
browsers: View › Developer › Allow JavaScript from Apple Events).

## Uninstall

1. Quit Hem and move it from Applications to the Trash.
2. Remove it from **System Settings › Privacy & Security › Accessibility** (select it, click **–**).
3. Optionally delete its data: `~/Library/Application Support/Hem` and `~/Library/Logs/Hem`.

## Feedback

Found a bug or have an idea? [Open an issue](https://github.com/haseebyousuf/hem-public-releases/issues).
Screenshots of Settings › More › Troubleshooting help.

---

Hem is provided as is, without warranty of any kind. © 2026 Haseeb Yousuf.
