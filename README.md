# Annotator Shifts

A lightweight shift-management web app for a distributed data-annotation team — enter shifts, assign tasks (each with a link to work on), and let annotators check in, open their task, take breaks, and clock out. Leads get a live **Right Now** coverage board; annotators get a focused **My Day**.

## Live app

This runs as a **Claude Artifact** — its shared realtime database and identity come from the Claude runtime:

**https://claude.ai/artifact/8x2qkNzLDWpGGWrDTSu3n8**

> This repository is the **source / backup** of that Artifact. Opening `index.html` on its own (or via GitHub Pages) shows the interface but **not** the shared data — clock-ins, tasks and breaks only sync inside the Claude Artifact runtime (the `db` + `user` capabilities).

## Features

- Roster with per-person timezones; weekly shifts entered in each person's own local time
- One-tap **clock in / out**, plus **take a break / I'm back** (worked time excludes breaks)
- Tasks with a **link to work on**; assign / reassign; annotators are **alerted** on new assignments (in-app banner + toast + browser notification)
- Live **coverage board**: scheduled vs clocked-in, with gaps, late, absent, overdue and on-break surfaced
- **Guided first-run** for leads (add team -> set shifts -> create first task)
- Attendance history, light/dark theme, mobile-first

## Updating

The app is a single self-contained HTML file. To change the live tool, edit the HTML and **re-publish it as the Claude Artifact** above — publishing from Claude keeps the same link and its shared database.

## Tech

Vanilla HTML/CSS/JS, no build step. Uses the Claude Artifact `db` (shared document store) and `user` (identity) capabilities.
