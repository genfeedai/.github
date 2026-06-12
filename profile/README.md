<h1 align="center">Genfeed.ai</h1>

<p align="center"><strong>The open source AI OS for content creation.</strong></p>

<p align="center">Create, Remix, Publish, Repeat.</p>

<p align="center">
  <a href="https://github.com/genfeedai/genfeed.ai/blob/master/LICENSE"><img src="https://img.shields.io/badge/license-AGPL--3.0-blue.svg" alt="License: AGPL-3.0"></a>
  <a href="https://github.com/genfeedai/genfeed.ai/stargazers"><img src="https://img.shields.io/github/stars/genfeedai/genfeed.ai?style=social" alt="GitHub Stars"></a>
  <a href="https://discord.gg/genfeedai"><img src="https://img.shields.io/discord/placeholder?label=Discord&logo=discord&color=5865F2" alt="Discord"></a>
</p>

---

## What is Genfeed.ai?

A self-hostable, AI-powered content creation platform. Generate images, video, voice, music, and text through a visual workflow editor, then schedule and publish to any platform from a single interface. Deploy with Docker in minutes.

- **AI Content Generation** — images, video, text, voice, and music via pluggable model providers
- **Visual Workflow Editor** — chain generation, transforms, and publishing into reusable pipelines
- **Multi-Platform Publishing** — Twitter/X, LinkedIn, Instagram, TikTok, YouTube, Discord, Telegram, Slack, Fanvue, and more
- **Scheduling & Automation** — calendar-based scheduling with cron and event-driven triggers
- **Studio, Gallery, Editor** — quick generation, asset management, and media composition
- **Desktop & Mobile** — native Electron apps and a React Native / Expo mobile app
- **Self-Hosted GPU** — bring your own GPU with ComfyUI integration

## Repositories

Everything lives in **one monorepo** now. The platform is fully open source.

| Repo | Description |
|------|-------------|
| **[genfeed.ai](https://github.com/genfeedai/genfeed.ai)** | The platform monorepo — every app, service, and package. Next.js + NestJS, Docker-deployable, AGPL-3.0. |
| **[skills](https://github.com/genfeedai/skills)** | AI skills for content creation, SEO, advertising, image prompting, and strategy. Works standalone with Claude Code — works better with Genfeed.ai. |

> The former `core`, `cloud`, `cli`, `docs`, and `packages` repos have been consolidated into the [genfeed.ai](https://github.com/genfeedai/genfeed.ai) monorepo.

## Quick Start

```bash
git clone https://github.com/genfeedai/genfeed.ai.git
cd genfeed.ai/docker
cp .env.example .env
docker compose up
```

Install the skills with the [`skills`](https://github.com/genfeedai/skills) CLI:

```bash
bunx skills add genfeedai/skills
```

## Stack

Turborepo + Bun monorepo · Next.js · NestJS (12 microservices) · PostgreSQL (Prisma) · Redis + BullMQ · Docker.

## Links

- [Website](https://genfeed.ai)
- [Documentation](https://docs.genfeed.ai)
- [Discord](https://discord.gg/genfeedai)
- [Status](https://genfeed.statuspage.io/)
