Selected projects, 2026

# Shimi Goldshlak

I build AI agents, automation pipelines and desktop apps. Each one does the repetitive part of a job and hands the decision back to a person.

Israel [github.com/ShimiG](https://github.com/ShimiG)

[Is It Real?AI and scam detection](#is-it-real) [Music ManagerDesktop app](#music-manager) [Job AgentsMulti-agent pipeline](#job-agents) [LinkedIn post pipelineContent automation](#linkedin-pipeline) [readme-autoupdateRepo maintenance](#readme-autoupdate)

Projects

Each strip shows how the project moves work from input to result. filled a person decides here

Open source · Apache-2.0

## Is It Real?

An on-device detector for AI-generated text, images and video, built to help people, especially older adults, spot AI-driven scams. It ships as a Claude plugin and as a standalone browser extension that share one detection core.

[Repository](https://github.com/ShimiG/is-it-real) [Evaluation report](https://github.com/ShimiG/is-it-real/blob/main/EVAL.md)

1. page, message, picture or video
2. scam warning signs
3. Content Credentials (C2PA)
4. metadata and statistics
5. picture model, photos only
6. one of four outcomes

Outcomes: Made with AI, Likely made with AI, No clear signs, Not checked. It never says "real" or "human".

- **Algorithms decide.** Provenance, metadata, statistics and signal processing produce the verdict. A language model is used only to explain it.
- **Nothing leaves the computer.** No accounts, no uploads, no tracking. Every check still works with all outside hosts blocked.
- **It refuses to guess.** A second model first decides whether a picture is a plain photo. Drawings, screenshots and memes are marked "not checked".

Measured

| Scam test messages flagged | 40 of 40 |
| --- | --- |
| Everyday text messages wrongly flagged | 0 of 4,827 |
| Texts by non-native English writers wrongly flagged | 0 of 266 |
| Non-AI images wrongly flagged | 6 of 1,065 |
| Texts from a 2026 model caught | 13 of 100 |
| Face-swap videos caught | 0 of 49 |

From the project's evaluation report, engine 0.8.0-m6. The misses are published next to the catches, and every number can be reproduced with one command.

pnpm monorepo · ONNX Runtime · C2PA · MCP server · sharp · ffmpeg · Chrome extension

Open source · MIT

## Music Manager

A desktop music player that puts YouTube, SoundCloud, Audius, Deezer and the music files on your computer in one library. A React interface runs in a Tauri window and talks to a local API that finds the audio, converts it and streams it to the player.

[Repository](https://github.com/ShimiG/youtube-music)

1. React UI in Tauri
2. Express API
3. one provider per service
4. yt-dlp
5. ffmpeg to MP3
6. stream and disk cache

Playlists and play history live in a local SQLite file.

- **One shape for every service.** Each source sits behind the same interface and returns the same playlist and track records. Adding a service takes one provider file, one database row and one client entry.
- **A strict matching engine.** Services that offer a catalog but no audio are matched to a YouTube upload first. Only official uploads count, the title and artist must match exactly, and the length must agree within 5 seconds.
- **Real account handling.** Local accounts with JWT, Google OAuth, SoundCloud OAuth 2.1 with PKCE, and service credentials stored encrypted.
- **Ships as one app.** The server is built as a Node single executable and bundled with ffmpeg and yt-dlp. Sync between computers through a Cloudflare Worker is in progress.

React · Vite · Tauri (Rust) · Node.js 22 · Express 5 · SQLite · yt-dlp · ffmpeg · Jest · Supertest

Public repository · TypeScript

## Job Agents

A job search pipeline built from four AI agents that share one SQLite database, with a local web page that coordinates each run. Scout finds and scores postings, Tailor writes the CV and cover letter, Submitter fills in the forms, and Archiver files the replies.

[Repository](https://github.com/ShimiG/job-search-agent-wf)

1. job boards and alert emails
2. Scout
3. shortlist
4. you pick
5. Tailor
6. you approve
7. Submitter
8. sent

1. replies in your inbox
2. Archiver
3. filed under each application

- **Tailored, then fact-checked.** Every highlight in the master CV has an id. The Tailor cites those ids, so each reworded claim is traced back to something the CV already says. It never adds a figure.
- **Mail stays on the machine.** The Archiver reads email with a local model through Ollama. Scoring can run locally too, at no cost.
- **Tested against look-alike forms.** The Submitter runs in headless Chrome against local pages modeled on Greenhouse and Lever, including CAPTCHA, sign-in and emailed security codes.
- **Runs with or without LangGraph.** The same agents run as LangGraph graphs when its server is up, so every run is visible in LangGraph Studio.

TypeScript · Node.js 22 · LangGraph · Claude API · Ollama · SQLite · headless Chrome · node:test

Public repository · Python

## LinkedIn post pipeline

Three times a week, GitHub Actions drafts a LinkedIn post from free sources, checks it against those sources, translates it to Hebrew and opens a GitHub issue for approval. There is no server, no database and no paid service.

[Repository](https://github.com/ShimiG/linkedin-post-pipeline)

1. Sun, Tue, Thu
2. Hacker News or Wikipedia
3. draft
4. guardrail
5. Hebrew translation
6. image
7. GitHub issue
8. /approve
9. LinkedIn

Review happens in issue comments: /approve, /schedule, /rewrite, /image, /reject, /block.

- **A guardrail before review.** Every number and every outlet named in a draft must appear in its sources. No links, at most three hashtags, and no wording copied from the writing examples.
- **The issues are the record.** What was drafted, which sources were used and what was published all live in GitHub issues. Approval works from the GitHub app on a phone.
- **Built for Hebrew.** Hebrew and English go out as separate posts in their own time slots. Hebrew lines that open with an English word get a right-to-left mark so LinkedIn shows them correctly.
- **Fallbacks throughout.** Groq writes and Gemini takes over when it fails. An AI illustration is only made for safe topics, and a branded card is drawn otherwise.

Python · GitHub Actions · Groq · Gemini · Cloudflare Workers AI · pytest

Private repository · GitHub Actions

## readme-autoupdate

A weekly workflow that goes over every repository I own, has Claude Code compare each README with the code, and opens a pull request wherever the README no longer describes the project.

1. Mondays
2. repos pushed in the last 8 days
3. Claude Code reads the code
4. README edit
5. pull request
6. you merge

- **Narrow permissions.** Claude can read and search files and edit the one README file. It has no shell, no network tools and no MCP servers, and the step that runs it never holds the repository token.
- **No repeated proposals.** A repository is skipped while its last proposal is still based on the current default branch. Unchanged projects cost nothing.

GitHub Actions · Claude Code

## What the projects have in common

### A review step in the middle

Posts wait in a GitHub issue, applications wait on a review page, README changes arrive as pull requests. The automation prepares the work and a person signs it off.

### Limits written down

Is It Real? publishes what it misses next to what it catches. Job Agents and Music Manager each keep a list of known limitations in the README.

### Local and free first

SQLite files, on-device models and free tiers. Most of these projects run on one computer or inside GitHub Actions, with no server to keep alive.

Shimi Goldshlak · [github.com/ShimiG](https://github.com/ShimiG) Written from the repositories' READMEs, November 2026
