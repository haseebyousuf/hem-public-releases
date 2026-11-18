# Hem

**Your MacBook trackpad's edges and corners, turned into controls.**

Slide up the right edge to turn the volume up. Slide the left edge for brightness. Double-tap a corner
to play or pause, flick in from the right for Notification Center. Hem keeps the edges asleep while
you type, ignores palms and ordinary pointing, and shows what happened in a HUD that grows out of the
notch.

The notch is also an island you can use: hover for a peek, click to open it, click away or press
Escape to close. Clicking the bare notch opens its home, with what's playing, your day and a Pomodoro as
tabs, and two-finger swipes on it work too: down opens, up closes, sideways skips the song. It shows the
music you're playing (the Music app, Spotify, and YouTube Music, Spotify or Apple Music in a browser,
with artwork and controls; videos and calls never show), your battery when you plug in or run low, your
AirPods or other headphones with their battery when they connect, a Pomodoro (focus, then a break, each
starting by itself) you start from the island, the menu bar or a corner, Caps Lock, a muted microphone,
and Keep awake; two at once share it, the second in its own bubble (middle-click the island to bring the
next one forward). A Mirror tab shows your front camera for a quick look before a call (nothing is
recorded). Screens without a notch get a small pill in the menu bar instead.

In Hem's window, the **Island** group in the sidebar has a page for each activity, and **Behavior**
chooses the shape, whether hovering opens it, whether it steps aside for full-screen apps, which tab it
opens on and the tabs' order, or turns the island off altogether. On Screen › **Hide from screen recordings and sharing** keeps the island and
Hem's levels out of screenshots and shared screens.

The island also has a shelf: drag files to the notch to keep them for later, and drag them out again
when you need them (hold Option to keep a copy on the shelf). Hold a drag over the notch to open the
Shelf tab, where you can drop onto AirDrop too. Click a file and press Space for Quick Look. Files stay
where they are; images and photos that come without a file are kept in Hem's folder. macOS may ask once
whether Hem can open files from Desktop, Documents or Downloads.

It can show your calendar too (Island › Calendar, off until you turn it on; macOS asks for calendar
access then): your next event beside the notch with a countdown, a card with **Join** for Zoom, Meet,
Teams, Webex and FaceTime calls when it starts, and a ring while it runs. Swipe up to put an event
away. The Calendar tab shows the rest of your day, or the next day with events when today is clear,
and can list the reminders due today: click a reminder's circle to tick it off. Your calendars and
reminders never leave your Mac.

If you use Claude Code, the island can show your Claude plan's limits too (Island › Claude, off until you
connect it): the current session and the week, with when each resets, and a warning beside the notch when
the session passes 80%. Hem reads them from Claude Code's status line through a small helper; your own
status line keeps working, and **Disconnect** puts the setting back. Nothing is sent anywhere.

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
   list that opens. Setup moves on by itself once it's allowed. A second part shows the island's
   gestures and lets you choose what it shows. Both guides are under Settings › General › Help.

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
| **Automation** (asked when first needed) | To see what's playing and control it in Music, Spotify and browser tabs, and to switch dark mode. In Ardia, Hem uses Ardia's own command-line tool when it's installed. |
| **Audio capture** (only for one app's volume) | To pass one app's sound through at the level you set. Nothing is recorded. |
| **Calendars** (only for Calendar) | To show your next event and the rest of your day on the island. |
| **Reminders** (only for reminders in the Calendar tab) | To list the reminders due today, and tick one off when you click it. |
| **Bluetooth** (only for Headphones) | To see when headphones connect, with their name and battery. |
| **Camera** (only for the Mirror) | To show your front camera while the Mirror tab is open. Nothing is recorded. |

Hem explains each of these before macOS asks. Claude usage needs no permission: connecting it changes
one setting in `~/.claude/settings.json` (a copy is kept as `settings.json.hem-backup`).

Hem has no accounts, analytics or tracking. It goes online for two things only:
- asking GitHub whether a newer release is out, when you click **Check for Updates** (Hem › About), or
  once a day if you turn that on (it's off by default);
- while a song plays in Spotify or on YouTube Music, fetching its artwork from Spotify's or YouTube's image
  servers (turn it off under Island › Now Playing; Music's artwork never leaves your Mac).

Nothing about you or your Mac is sent. Your settings, touch log and daily
counts stay on your Mac in `~/Library/Application Support/Hem`.

## Troubleshooting

**"Hem is damaged and can't be opened" or "Apple could not verify Hem"**
Run the command from step 2 of Install, then open Hem again.

**Hem 0.11.0 quits as soon as it opens**
With Headphones on and Bluetooth audio connected, 0.11.0 can close right after opening on macOS 27.2.
Download 0.11.1 or later from the [latest release](https://github.com/haseebyousuf/hem-public-releases/releases/latest),
replace Hem in Applications, and run the command from step 2 of Install again.

**The edges do nothing**
- Check that Hem is on: its menu bar icon shows pause bars when it's paused.
- Check **System Settings › Privacy & Security › Accessibility**: Hem must be in the list and turned
  on. If it's on but Hem still doesn't react, remove it with the **–** button, then open Hem again and
  allow it.
- Open Hem › Advanced › **Troubleshooting** to see which parts are working.

**A slide or tap happens when I didn't mean it**
Open Hem › **Activity**: it lists every touch Hem acted on or ignored, and why. Feel › **Edge width**
makes the edges narrower. Under Advanced, **Strict mode** makes a slide count only after you rest or
click first.

**The island gets in the way**
It takes clicks only on its own black shape, never beside it. If it still bothers you, turn off
**Open on hover** under Island › Behavior, switch off the activities you don't want there, choose a
different HUD style on the On Screen page, or turn **Show the island** off altogether.

**Now playing doesn't show a browser tab**
Only music sites show: YouTube Music, Spotify's web player and Apple Music (each can be switched off
under Island › Now Playing). YouTube videos, calls and other sites are left out on purpose.
Hem reads tabs by scripting the browser: allow it under System Settings › Privacy & Security ›
Automation. In Chrome and similar browsers, YouTube Music shows only while no YouTube video, call or
other video site is open in that browser, since Hem can't tell which tab the sound comes from (in Ardia,
Hem reads the music tab itself).

**I want Hem's HUD for the keyboard's volume keys**
On Screen › **Use Hem's HUD for the keyboard keys**. Hem then handles the volume, brightness
and keyboard-light keys; anything it can't handle still goes to macOS.

**The calendar doesn't show**
Check that Calendar is on under Island › Calendar, and that Hem is allowed under System Settings ›
Privacy & Security › Calendars (and › Reminders, for reminders). All-day events, events you've
declined and calendars you switched off on the Calendar page don't show.

**Seeking doesn't work in a browser tab**
For sites other than YouTube, the browser must allow JavaScript from Apple Events (in Chrome-based
browsers: View › Developer › Allow JavaScript from Apple Events).

## Uninstall

1. Quit Hem and move it from Applications to the Trash.
2. Remove it from **System Settings › Privacy & Security › Accessibility** (select it, click **–**).
3. Optionally delete its data: `~/Library/Application Support/Hem` and `~/Library/Logs/Hem`.

## Feedback

Found a bug or have an idea? [Open an issue](https://github.com/haseebyousuf/hem-public-releases/issues).
Screenshots of Advanced › Troubleshooting help.

---

Hem is provided as is, without warranty of any kind. © 2026 Haseeb Yousuf.
