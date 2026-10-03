# magicscreenshots

Search real App Store listing screenshots and preview videos for design inspiration, then generate, restyle or localize the user's own App Store screenshots with MagicScreenshots. Use for App Store screenshot design, listing research, localization and app preview references.

Publisher contact: **blake@humanleap.com**. Public source is maintained in the Humanleap GitHub organisation.

## Install the skill

```bash
pnpm dlx skills add Humanleap/agent-skills --skill magicscreenshots
```

## Claude Code

```text
/plugin marketplace add Humanleap/magicscreenshots-agent-plugin
/plugin install magicscreenshots@magicscreenshots-agent
```

## Other clients

- Cursor: `.cursor-plugin/plugin.json` and its MCP config.
- Grok Build: `.grok-plugin/plugin.json` and its MCP config; a marketplace review is separate from this source package.
- Gemini CLI: `gemini extensions install https://github.com/Humanleap/magicscreenshots-agent-plugin`.
- Portable agents: root `plugin.json` and `mcp.json`. A public package is not proof of official store approval.
- Other MCP clients: connect the Streamable HTTP endpoint `https://www.magicscreenshots.com/api/mcp`.

## Access and network

Public library reads need no key. Generation and Pro tools use a user-authorised key and may require payment.

This instruction/configuration package has no hooks, shell server, bundled runtime, post-install script or hidden background process. It calls the product endpoint above through the client's MCP integration. Additional providers, payment or delivery destinations are used only for an authorised product workflow described in the skill.

## Skill layout

Following the Postiz agent packaging pattern, the canonical root `SKILL.md` is mirrored byte-for-byte at `skills/magicscreenshots/SKILL.md`. Both use installation, hard rules, authentication, core workflow, essential tools, common patterns, supporting resources, gotchas and a quick reference. This copies the packaging/workflow formula, not Postiz-specific operations. The homepage is inside frontmatter `metadata` for strict skill-validator compatibility.

Company-wide discovery collection: https://github.com/Humanleap/agent-skills.

License: MIT. Product service terms and pricing still apply.
