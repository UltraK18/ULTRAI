# ULTRAI

An AI desktop app where work carries on. Chat, hand off code, design, generate, and schedule it — all in one window.

[한국어](./README.ko.md)

[![Latest Release](https://img.shields.io/github/v/release/UltraK18/ULTRAI?style=flat-square)](https://github.com/UltraK18/ULTRAI/releases/latest)
[![Downloads](https://img.shields.io/github/downloads/UltraK18/ULTRAI/total?style=flat-square)](https://github.com/UltraK18/ULTRAI/releases)
[![Platform](https://img.shields.io/badge/platform-Windows%20x64-blue?style=flat-square)]()
[![License](https://img.shields.io/badge/license-Freeware-green?style=flat-square)]()

> This repository is for **release distribution only**. The source code is not published here.

---

## Why ULTRAI?

**A conversation ending doesn't mean the work is done.** Most AI apps are built around one question and one answer. ULTRAI is built around what comes after — work that keeps running, splits across agents, moves to your phone, and comes back when it's due.

- **Four modes, one app** — Chat, Code, Design, and Studio. Each gets a purpose-built screen and its own tools, but it's still one window and one set of settings.
- **Not just one agent** — ULTRA mode breaks a large job into tasks and runs them across multiple agents in phases, with independent verification before results are merged. In Code mode, separate sessions can talk to each other directly.
- **It keeps its appointments** — schedule work and the app picks the conversation back up at that time on its own, even after being closed.

## What makes it different

**ULTRA mode — task-based multi-agent orchestration.** For work too large for one context, ULTRA decomposes the job into tasks, assigns them across agents phase by phase, and has the results independently verified before they are merged. You watch it run and step in whenever you want.

**Sessions that talk to each other.** In Code mode, one session can hand a question or a result to another — a session working on the backend can ask the one that knows the frontend. You approve the channel; nothing opens itself.

**Design mode — a canvas with a designer.** Build screens on a live canvas with a designer agent, iterating in the sidebar chat while the result renders next to it. Finished work hands off to Code mode as real files.

**Studio mode — generate on a canvas.** Produce images and video from a chat next to a freeform canvas, arrange them, drag your own files in, and keep iterating on what's already there.

**Your phone is a second screen.** Turn on the server and open ULTRAI from a phone browser on the same network — with a layout built for touch, not a shrunk-down desktop. Sessions, models, and settings are shared, so you pick up exactly where you left off.

**Scheduled and repeating work.** Say "every weekday at 9" or "in two hours" and it registers as a real job. When it fires, the task arrives as a turn in that conversation. A calendar and list show everything at a glance; the next run always sits at the bottom of the sidebar. If the app was closed when something was due, it works out what it missed and folds it into one catch-up run.

**Research that actually digs.** Deep research runs a real investigation — planning the angles, searching and reading in parallel across sub-agents, and citing what it found. The everyday search is unusually strong too: the model is told to search proactively rather than guess, to use today's date instead of a year carried over from training, and to verify present-tense claims before answering. Sources are cited inline, and findings are presented evenhandedly instead of as settled fact.

**Deep interview.** When a request is underspecified, it can turn the conversation into a structured interview first — pinning down what you actually want before any work starts.

**Goals that get checked.** Set a goal for a conversation and an independent evaluation gates completion — the AI doesn't get to declare itself done. A loop repeats a task for as many rounds as you set.

## Also included

**Code** — Open a real project folder to analyze and modify a codebase, with diffs in a review panel, a file tree, and a terminal alongside.

**Chat** — Switch freely between providers and models, and change reasoning effort per message.

**Memory and personalization** — Remembers what it learns about you and carries it forward, and can search your own past conversations. Build your own agents, attach skills and MCP servers, and manage what gets remembered from Settings.

## Installation

Windows 10 / 11 (x64). Requires the WebView2 runtime, which is already present on most Windows installs.

Download the latest `ULTRAI_x.y.z_x64_en-US.msi` from the [Releases](https://github.com/UltraK18/ULTRAI/releases/latest) page and run it.

The app checks for new versions on launch and periodically, tells you when one is available, and installs it in place.

## Quick Start

1. **Connect a provider** — add your API key under Settings → Providers.
2. **Pick a model** — choose the model and reasoning effort from the right side of the input bar.
3. **Pick a mode** — switch between Chat, Code, Design, and Studio from the tabs at the top of the sidebar.
4. **Start working** — open a folder in Code mode; in the other modes, just start talking.
5. **Hand something off** — say "sum up my day every night" and it will pick that up on its own.

## Tech Stack

A native Windows app built on Tauri 2. The interface is SolidJS; the backend runs as a single binary bundled with the app.

Conversations and settings are stored **only on your PC**. There is no ULTRAI server — your conversations go only to the AI provider you connected yourself.

## Feedback

Bugs and feature requests go to [Issues](https://github.com/UltraK18/ULTRAI/issues).

## License

ULTRAI is freeware. Free for personal and commercial use. Source code is not publicly available.
