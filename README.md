# ULTRAI

A Windows desktop app for AI work that keeps going. Four modes in one window — talk, build in a real project folder, design on a canvas, generate images and video — plus scheduling, multi-agent runs, and your phone as a second screen.

[English](./README.md) | [中文(简体)](./README.zh.md) | [中文(繁體)](./README.zht.md) | [한국어](./README.ko.md) | [Deutsch](./README.de.md) | [Español](./README.es.md) | [Français](./README.fr.md) | [Dansk](./README.da.md) | [日本語](./README.ja.md) | [Polski](./README.pl.md) | [Русский](./README.ru.md) | [العربية](./README.ar.md) | [Norsk](./README.no.md) | [Português (Brasil)](./README.br.md) | [ไทย](./README.th.md) | [Bosanski](./README.bs.md) | [Türkçe](./README.tr.md)

[![Latest Release](https://img.shields.io/github/v/release/UltraK18/ULTRAI?style=flat-square)](https://github.com/UltraK18/ULTRAI/releases/latest)
[![Downloads](https://img.shields.io/github/downloads/UltraK18/ULTRAI/total?style=flat-square)](https://github.com/UltraK18/ULTRAI/releases)
![Platform](https://img.shields.io/badge/platform-Windows%20x64-blue?style=flat-square)
![License](https://img.shields.io/badge/license-Freeware-green?style=flat-square)

> This repository is for **release distribution only**. The source code is not published here.

<!-- 스크린샷 자리. 넣으려면 이 저장소에 이미지를 먼저 올려야 한다 (지금 저장소에는
     README.md / README.ko.md 두 파일밖에 없다). 필요한 것:
       1. 앱 메인 화면 캡처 1장 — assets/screenshot-main.png
       2. 로고 — assets-preview/ultrai-logos/ultrai-logo.svg 를 올려서 쓰면 된다
     경로가 없는 <img> 를 미리 넣으면 저장소 페이지에 깨진 이미지가 뜨므로,
     자산이 올라간 뒤에 이 주석을 실제 태그로 바꾼다. -->

---

## Download

Windows 10 / 11 (x64). Requires the WebView2 runtime, which is already present on most Windows installs.

**[Download the latest release](https://github.com/UltraK18/ULTRAI/releases/latest)** — grab `ULTRAI_x.y.z_x64_en-US.msi` and run it.

After that the app takes care of itself: it checks for new versions on launch and periodically, tells you when one is available, and installs it in place.

## Four modes, one window

Each mode is a purpose-built screen with its own tools and its own agents — but one app, one set of settings, one place your history lives.

| Mode | The screen | What you do there |
| :--- | :--- | :--- |
| **Chat** | Conversation | Any provider and model, reasoning effort per message, deep research with citations, files and images in |
| **Code** | A real project folder | File tree, diffs in a review panel, a terminal beside the chat, permission prompts before anything touches disk |
| **Design** | Live canvas + designer agent | Screens render next to the chat as they are built; finished work hands off to Code as real files |
| **Studio** | Freeform canvas + chat | Generate images and video, place and rearrange them, drop your own files in, keep iterating on what is there |

Switching mode does not restart anything — each mode keeps its own conversations, and the sidebar shows the ones belonging to where you are.

## The interface is the point

Most tools in this space are a terminal or a web page in a wrapper. ULTRAI is a desktop app that was
designed, not assembled.

- **Glass that is actually glass** — floating surfaces run a small rendering engine, not a blur filter.
  It bakes a normal map for the bezel and draws specular highlights from it, and displaces what is
  behind the surface so edges refract. Controls like the toggle and the slider go further and solve
  Snell refraction with an index of refraction and a thickness, so the thumb bends the track under it.
  A CSS frost cannot do that, and the difference shows on every edge.
- **Squircle corners** — panels use a superellipse, not a circular arc, so the curve enters the
  straight edge without the flat spot you get from `border-radius`.
- **Two themes, both deliberate** — light and dark are built on one concrete-toned palette with a
  faint cool cast, tuned so nothing is glaring at either end. Every surface is a token, so the whole
  app moves together instead of drifting per screen.
- **Restraint on purpose** — no emoji anywhere in the product, no exclamation marks, no cheerleading.
  Panels carry a single surface each; separation comes from rim light and shadow rather than boxes
  drawn inside boxes.
- **Seamless window** — a 32px title bar in the Windows 11 metric that shares the app's background,
  so the chrome does not read as a separate strip above the content.
- **Mobile is a different layout, not a smaller one** — bottom sheets, full-width controls, and a
  touch-sized hit area, decided by the device rather than by window width.

## Generation, with real models

Studio is not a single image endpoint. It picks from a catalog per job and tells you which model it used and why.

- **Video** — Veo 3.1 and Veo 3.0 (plus their fast variants), Sora 2 and Sora 2 Pro, Grok Imagine Video, Gemini Omni Flash
- **Image** — GPT Image 2 and 1.5, Gemini 3 Pro Image, Gemini 3.1 Flash Image (and Flash Lite), Grok Imagine Image
- **Video in, video out** — hand it an existing clip as the input, not just a prompt
- **It checks its own work** — pulls frames back out of what it generated, looks at them, and decides whether to retry
- **Length, aspect ratio and quality are yours** — asked for 30 seconds and 30 seconds is what gets built, in the shape you asked for

Which models you can reach depends on the provider accounts you connect (Vertex AI, OpenAI, xAI).

## ULTRA mode — many agents, one job

For work too large for one context. ULTRA breaks the job into tasks, runs them across agents phase by phase, and has results **independently verified before they are merged** — a critic and adversarial checks, not the same agent grading itself. You watch the run and can step in at any point. Model and reasoning effort are set per role, so a cheap worker and an expensive verifier can be different providers on purpose.

## It keeps its appointments

Say "every weekday at 9" or "in two hours" and it becomes a real job, not a note. When it fires, the task arrives as a turn in that conversation and the AI starts working on it.

- A calendar and a list show everything registered; the next run sits at the bottom of the sidebar
- Closed when something was due? It works out what it missed and folds it into one catch-up run
- `/loop` repeats a task for as many rounds as you set

## Goals the AI cannot declare done

Set a goal for a conversation and an independent evaluation gates completion. The agent doing the work does not get to decide it finished.

## Research that digs, and questions before work

**Deep research** plans the angles, then searches and reads in parallel across sub-agents and cites what it found. Everyday search is unusually strict too: the model is told to search rather than guess, to use today's date instead of a year carried over from training, and to verify present-tense claims before answering. Findings are presented evenhandedly, with sources inline.

**Deep interview** — when a request is underspecified, it turns the conversation into a structured interview and pins down what you actually want before any work starts.

## Work that runs while you do something else

Long jobs do not hold the window hostage.

- **Background runs** — hand a task off and it runs isolated, as a fork of the conversation or as a
  sub-agent, and can ask for more permission mid-run if it hits a wall.
- **A live monitor** — a bar at the bottom shows everything in flight at once: your own background
  tasks, ones started elsewhere, running sub-agent calls, ULTRA runs, and any shell command that has
  been going a while. Click through to whichever one you want to watch.
- **Fork a conversation** — branch from any point to try something without losing the original, and
  jump between branches from the message index.

## Handoff between modes

Work does not get stuck in the mode it started in. Design hands finished screens to Code as real
files on disk. Code sessions pass questions and results to each other. Studio places what an agent
produced straight onto the canvas. Each handoff moves actual files or actual turns, not a copied
block of text.

## A workspace the AI can use without touching your files

Chat mode gets its own scratch space on disk. The AI can write, read, run and revise things there
freely — drafts, scripts, intermediate files — without prompting you for permission on every step and
without reaching into your folders. You never have to think about where that is; you just get the
result, and your own directories stay untouched unless you point at them.

## Sessions that talk to each other

In Code mode a session can hand a question or a result to another — the one working on the backend can ask the one that knows the frontend. Messages arrive as a real turn in the other conversation. You open the channel; nothing connects itself.

## Your phone is a second screen

Turn on the server and open ULTRAI from a phone browser on the same network. The mobile layout is built for touch — bottom sheets and full-width controls — not a shrunk-down desktop. Conversations, models and settings are shared, so you continue exactly where you left off.

## Make it yours

Everything below is a plain file on your disk that you can read, edit and version.

- **Agents** — `~/.ultrai/agents/*.md`. The frontmatter decides everything: which modes it appears in, which tools it may use, which prompt sections it gets, which features (research, goals, interview) it is allowed. Edit from Settings, and built-in agents can be restored to their original at any time.
- **Skills** — `~/.ultrai/skills/*/SKILL.md`. Reusable instructions the model can pull in, or you can invoke as a slash command. Toggle each one on or off.
- **Prompt modules** — the system prompt is assembled from a catalog, and each agent's frontmatter picks which sections it gets. Declare nothing and the agent's prompt is byte-identical to the default; opt in to change how it thinks. Each mode ships its own prompt built for that kind of work, rather than one prompt bent to fit everything.
- **MCP servers** — declared in `ultrai.jsonc`. Local or remote, with auth where needed, switchable per server.
- **Memory** — kept in three buckets (about you, topics, areas), summaries injected and details fetched on demand, with a periodic cleanup pass that merges duplicates and contradictions. Chat mode only, and you can see and delete every entry from Settings.
- **Providers** — Anthropic, OpenAI, Google, Google Vertex, xAI, OpenRouter and custom endpoints, with your own keys.

## Your data stays on your PC

Conversations and settings are stored **only on your machine**. There is no ULTRAI server — your conversations go only to the AI provider you connected yourself, using your own key.

Nothing is collected, and there is no telemetry.

## Quick Start

1. **Connect a provider** — add your API key under Settings → Providers.
2. **Pick a model** — model and reasoning effort sit on the right of the input bar.
3. **Pick a mode** — the tabs at the top of the sidebar.
4. **Start working** — open a folder in Code mode; in the other modes, just start talking.
5. **Hand something off** — say "sum up my day every night" and it will pick that up on its own.

## Tech Stack

A native Windows app built on Tauri 2. The interface is SolidJS; the backend runs as a single binary bundled with the app.

## Feedback

Bugs and feature requests go to [Issues](https://github.com/UltraK18/ULTRAI/issues).

## License

ULTRAI is freeware. Free for personal and commercial use. Source code is not publicly available.

ULTRAI began as a fork of [opencode](https://github.com/sst/opencode) and has been rebuilt well
beyond it, but it still includes opencode code, which is MIT licensed — Copyright (c) 2025 opencode.
The MIT license is quoted in full in the notices shipped with the app.
