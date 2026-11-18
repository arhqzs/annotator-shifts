# Annotator Shifts

A standalone shift-management web app for a distributed data-annotation team. Leads enter shifts and assign tasks (each with a link to work on); annotators check in, open their task, take breaks, and clock out — with a live coverage board, new-task alerts, and a guided setup.

## Two ways it runs

1. **Standalone website (this repo)** — hosted on GitHub Pages, backed by your own **Firebase Firestore**. Anyone with the link can use it in a plain browser, no claude.ai account.
   - Live (once Firebase is configured): https://arhqzs.github.io/annotator-shifts/
2. **Claude Artifact** — the original zero-setup version (`claude-artifact.html`), which uses Claude's built-in database and needs a claude.ai account.

## Set up the standalone site (one-time, ~5 min)

1. Open the [Firebase console](https://console.firebase.google.com/) and **Add project** (any name).
2. **Build -> Firestore Database -> Create database** -> Production mode -> pick a location.
3. **Firestore -> Rules** -> paste the contents of [`firestore.rules`](firestore.rules) -> **Publish**.
4. **Build -> Authentication -> Get started -> Sign-in method -> Anonymous -> Enable**.
5. **Project settings (gear) -> Your apps -> Web (</>)** -> register an app -> copy the `firebaseConfig`.
6. Paste that config into `index.html` (the `window.FIREBASE_CONFIG = { ... }` block near the top) and redeploy (commit + push).

Until the config is filled in, the site shows a "database not connected" screen.

## Security note

The site signs every visitor in anonymously, and the rules allow any signed-in visitor to read/write — i.e. **anyone with the link can use and edit the board** (the lead PIN only gates the management screens). That's fine for an internal team tool shared privately; for stronger control we'd add real accounts later.

## Features

- Roster with per-person timezones; weekly shifts in each person's own local time
- Clock in / out, take a break / I'm back (worked time excludes breaks)
- Tasks with a link to work on; assign / reassign; annotators alerted on new assignments
- Live coverage board (scheduled vs clocked-in; gaps, late, absent, overdue, on-break)
- Guided first-run for leads; attendance history; light/dark; mobile-first

## Tech

Vanilla HTML/CSS/JS, no build step. Standalone version uses the Firebase (Firestore + Anonymous Auth) web SDK.
