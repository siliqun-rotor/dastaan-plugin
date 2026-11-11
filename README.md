# Dastaan for Claude Code and Codex

Short videos for founders, made from their own words: a brief, their numbers or a CSV, their logo. They come out in
English and Arabic, in 9:16, 4:5, 1:1 and 16:9. This plugin gives an agent six skills and the `dastaan-director` agent:

| Skill | For |
| --- | --- |
| `dastaan-video` | a finished video from a brief |
| `dastaan-edit` | changing the words, scenes or timing of a video |
| `dastaan-hooks` | trying other openings |
| `dastaan-look` | dressing a video in a built-in look |
| `dastaan-brand` | the brand colour and logo from a website |
| `dastaan-library` | finding, reopening and continuing saved videos |

The work runs on Dastaan's hosted service (`https://mcp.dastaan.hazirgenie.com/mcp`), and nothing is installed on your
machine. You sign in once with your **Dastaan account**, the same account as the Dastaan app at
https://dastaan.hazirgenie.com/app/. New accounts sign up there, with an invite code.

## Install

**Claude Code**

```bash
claude plugin marketplace add siliqun-rotor/dastaan-plugin
claude plugin install dastaan@dastaan
```

Then run `/mcp`, choose `dastaan` and Authenticate.

**Codex**

```bash
codex mcp add dastaan --url https://mcp.dastaan.hazirgenie.com/mcp
codex mcp login dastaan
```

Then copy `skills/*` into your skills folder, and `codex/agents/dastaan-director.toml` into `~/.codex/agents/`.

**Any MCP client** that speaks streamable HTTP with OAuth:

```json
{ "type": "http", "url": "https://mcp.dastaan.hazirgenie.com/mcp" }
```

## The rules every skill holds

- **The founder's facts only.** Every word, number and claim comes from what the founder gave. When something is
  missing, the agent asks; it never invents.
- **Refusals are repaired, not routed around.** A refusal names the scene, the field and the limit.
- **Look before done.** The agent looks at the frame sheet before handing a video back.

Licence: Apache-2.0.
