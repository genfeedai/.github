<p align="center">
  <a href="https://genfeed.ai"><img src="https://raw.githubusercontent.com/genfeedai/.github/master/profile/assets/banner.png" alt="Genfeed.ai — The open-source content agent" width="100%"></a>
</p>

<p align="center"><strong>The open-source content agent.</strong></p>

<p align="center">Create on-brand videos, images and posts, then review and publish to your connected channels.<br>Work in Genfeed or connect the AI agent you already use.</p>

<p align="center">
  <a href="https://genfeed.ai">Website</a> ·
  <a href="https://app.genfeed.ai">Hosted app</a> ·
  <a href="https://docs.genfeed.ai">Docs</a> ·
  <a href="https://genfeed.ai/pricing">Pricing</a>
</p>

<p align="center">
  <a href="https://github.com/genfeedai/genfeed.ai/blob/master/LICENSE"><img src="https://img.shields.io/badge/license-AGPL--3.0--or--later-blue.svg" alt="License: AGPL-3.0-or-later"></a>
  <a href="https://github.com/genfeedai/genfeed.ai/releases/latest"><img src="https://img.shields.io/github/v/release/genfeedai/genfeed.ai?label=release" alt="Latest release"></a>
  <a href="https://github.com/genfeedai/genfeed.ai/stargazers"><img src="https://img.shields.io/github/stars/genfeedai/genfeed.ai?style=social" alt="GitHub Stars"></a>
</p>

---

## What is Genfeed.ai?

An AI content agent that makes the posts, images and videos your brand publishes. Describe what you need, review the draft, and schedule it to your connected channels. Everything runs on the same open-source code in three modes:

| Mode | Who it is for | How you get it |
|------|---------------|----------------|
| **SaaS** | Teams who want it hosted | [app.genfeed.ai](https://app.genfeed.ai) |
| **Community** | Self-hosters, one organization | Checksummed Docker bundle from [GitHub Releases](https://github.com/genfeedai/genfeed.ai/releases/latest) |
| **Desktop** | Solo creators on a Mac | Signed macOS builds, or `brew install --cask genfeedai/tap/genfeed` |

- **Generate** images, video, voice, audio and text through pluggable model providers, or your own keys
- **Work from any agent** — drive the same loop from the web app, the CLI, the REST API, or Claude, Codex, Cursor, Gemini CLI and more over [MCP](https://github.com/genfeedai/agent)
- **Approval-first publishing** — agents can generate, draft and schedule; publishing waits for a human
- **Brand and workflows** — brand profile, content library, visual workflow editor, scheduling and publishing to your social channels

Genfeed is `0.x` and under active development. Breaking changes ship with an upgrade note in the release body.

## Repositories

| Repo | Description |
|------|-------------|
| **[genfeed.ai](https://github.com/genfeedai/genfeed.ai)** | The platform monorepo: web app, API, workers, MCP server, desktop, CLI and shared packages. Next.js + NestJS, AGPL-3.0. |
| **[agent](https://github.com/genfeedai/agent)** | Genfeed for AI agents: playbook skill, MCP connector manifests and install paths for Claude, Codex, Cursor, Gemini CLI, Grok and ChatGPT. |
| **[skills](https://github.com/genfeedai/skills)** | Content skills for strategy, SEO, ads, social, image and video prompting. Work standalone with Claude Code; work better with Genfeed. |
| **[benchmark](https://github.com/genfeedai/benchmark)** | An independent benchmark for image and video models: public tasks, blind pairwise judging, Elo. Season One is announced and the ladder is still empty. |

## Quick start

**Self-host (Community):**

```bash
curl -fLO https://github.com/genfeedai/genfeed.ai/releases/latest/download/genfeed-selfhosted.tar.gz
tar -xzf genfeed-selfhosted.tar.gz && cd genfeed-selfhosted-v*
cp .env.example .env && docker compose --env-file .env -f compose.yml up -d
```

Then open `http://localhost:3000`. See the [self-hosting guide](https://github.com/genfeedai/genfeed.ai/blob/master/docs/self-hosting.md) for providers, auth and upgrades.

**Connect your agent (Claude Code):**

```text
/plugin install genfeed --marketplace genfeedai/agent
```

**Add the content skills:**

```bash
bunx skills add genfeedai/skills
```

## Stack

Bun + Turborepo monorepo · Next.js 16 · NestJS 11 · PostgreSQL (Prisma) · Redis + BullMQ · Better Auth · Docker.

## Contribute

Issues and PRs are welcome on [genfeed.ai](https://github.com/genfeedai/genfeed.ai). Read [CONTRIBUTING.md](https://github.com/genfeedai/genfeed.ai/blob/master/CONTRIBUTING.md) first; agent-authored PRs are accepted when disclosed. Report security issues per [SECURITY.md](https://github.com/genfeedai/genfeed.ai/blob/master/SECURITY.md), never in a public issue.

## Links

- [Website](https://genfeed.ai) · [Hosted app](https://app.genfeed.ai) · [Product docs](https://docs.genfeed.ai)
- [Releases](https://github.com/genfeedai/genfeed.ai/releases) · [Project board](https://github.com/orgs/genfeedai/projects/12)
- [Discussions](https://github.com/genfeedai/genfeed.ai/discussions)
