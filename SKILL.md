---
name: magicscreenshots
description: Search real App Store listing screenshots and preview videos for design inspiration, then generate, restyle or localize the user's own App Store screenshots with MagicScreenshots. Use for App Store screenshot design, listing research, localization and app preview references.
metadata: {"homepage":"https://www.magicscreenshots.com/agents","openclaw":{"emoji":"🪄","requires":{"bins":[],"env":[]}}}
---

# MagicScreenshots

Research real App Store marketing images and preview videos from a library refreshed daily. Choose a reference, then generate or localize screenshots for the user's own app.

## Installation

Install this skill with `pnpm dlx skills add Humanleap/agent-skills --skill magicscreenshots`. Connect remote MCP to `https://www.magicscreenshots.com/api/mcp`.

CLI alternative (Node 18+):

```bash
pnpm dlx magic-screenshots search --category finance --chart grossing
pnpm dlx magic-screenshots app duolingo
pnpm dlx magic-screenshots screens duolingo --out ./reference
```

## Four Hard Rules — Read First

1. **Reference real results.** Do not invent apps, chart ranks, screenshot styles or history.
2. **Use third-party assets as references.** Their developers own them. Never ship another app's screenshots or preview footage as the user's work.
3. **Review paid generation.** Show any required payment/sign-in handoff and the overview. Call `approve_restyle` only after the human approves it.
4. **Keep output truthful.** Generated screenshots must represent the user's actual app; a pending job is unfinished.

## Authentication

Public library search/read tools need no key. Generation, live lookup, video downloads and history use a key through `Authorization: Bearer` or secure CLI `MAGICSCREENSHOTS_API_KEY` configuration. If the user requests generation and has no key, `create_api_key` returns a token and `claim_url`; keep the token private and give the human the claim URL. Do not enter payment details.

## Core Workflow

1. **Define the brief.** Identify the app category, audience and desired feel. Read `list_directory_categories` or `list_directory_tags` when needed.
2. **Search references.** Use `list_directory_apps` by query, category, chart (`free` or `grossing`) and style tag, setting `platform: "ios"` for App Store research. Select relevant apps from actual results.
3. **Inspect the images.** Read `get_directory_app` and `get_directory_screens` for a few candidates. Compare headline, colour, device treatment and order of benefits; cite the apps you inspected.
4. **Prepare the user's generation.** Use `get_screenshots` to identify the user's app, then `create_restyle` with its `source_app` and chosen `inspiration_slug`.
5. **Review and finish.** Poll `get_job_group` for `overview_url`, show it, and call `approve_restyle` only after approval. Poll again for final output URLs.

## Essential Tools

| Tools | Use |
|---|---|
| `list_directory_categories`, `list_directory_tags` | Discover categories and listing looks. |
| `list_directory_apps` | Search app listings; returned slugs identify apps. |
| `get_directory_app`, `get_directory_screens` | Listing details and ordered screenshots. |
| `get_app_videos`, `get_app_history` | Preview references or past listings; Pro access applies to downloads/history. |
| `get_screenshots` | Identify the user's source app/screenshots. |
| `create_restyle`, `create_localize` | Start requested screenshot generation or translation. |
| `get_job_group`, `approve_restyle`, `list_results` | Inspect jobs, approve the overview and retrieve output. |

## Common Patterns

- **Design inspiration:** compare 3–6 relevant apps and explain patterns visible in their actual screenshot sequences.
- **Restyle:** use the chosen reference slug, for example `{"source_app":{"query":"My App"},"inspiration_slug":"duolingo","limit":5}`, after confirming the user's app identity.
- **Localization:** use `create_localize` with the user's selected `target_locales`, such as `["JPN","DEU","FRA"]`, and poll for each locale's output.
- **Preview reference:** search with `has_video: true`; compare opening seconds, pacing, captions and closing message. Do not reuse footage. Pro mp4 links expire after an hour.

## Supporting Resources

- Agent setup: https://www.magicscreenshots.com/agents
- Library: https://www.magicscreenshots.com/apps
- Charts: https://www.magicscreenshots.com/top
- Pricing: https://www.magicscreenshots.com/pricing

## Common Gotchas

- The library contains App Store listing marketing screenshots, rather than arbitrary in-app UI captures.
- A library reference is not evidence that the user's app offers the same features.
- Show the returned claim/payment URL when a tool asks for access; do not guess entitlement or pay automatically.
- An overview is a review stage, not the final rendered screenshot set.

## Quick Reference

**Search → inspect real references → identify user's app → create → show overview → human approves → retrieve completed output.**
