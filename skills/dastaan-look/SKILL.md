---
name: dastaan-look
version: 0.2.0
description: |
  Dress a Dastaan video in one of the built-in looks (editorial, gradient, neon, paper, swiss, terminal), or take it back to plain, and check how it reads in every size and language. Use when: "apply the neon look", "restyle my video", "make it look more editorial", "try another style". NOT for: writing or changing a video's words (use dastaan-video or dastaan-edit), picking brand colours from a site (use dastaan-brand), or designing a new look from scratch (that runs in the Dastaan app).
argument-hint: "[video id] [look]"
---

# Dastaan look: the same words, in another style

A look is a set of scene sheets that the founder's words fill: any video written in Dastaan's standard roles plays in
any look, so a style can change without a rewrite.

## Before you start

The tools are the `dastaan_*` tools of the hosted Dastaan MCP server (`dastaan`, connected by this plugin). They run on
Dastaan's service, signed in with the founder's Dastaan account (the same account as the Dastaan app): if a call
answers that sign-in is needed, ask the founder to authenticate the `dastaan` server (Claude Code: `/mcp`; Codex:
`codex mcp login dastaan`). Nothing is installed or run on this machine. Pictures and logos go in as https addresses
or data: URIs, a CSV as its text. `dastaan_account` says which account is signed in; `dastaan_library` lists its videos
and their ids. Never guess an id.

## Apply a look

1. `dastaan_style {}` lists the looks.
2. `dastaan_style {id, look}` dresses the video. Scenes map by role (`open` to `hook`, a point to `claim`, a number to
   `stat`, a list to `list`, the close to `cta`); a scene a look cannot hold keeps its own form.
3. `dastaan_look {id}` and look at every row, in each language: the words must read in a second at every size.
4. `dastaan_style {id, look: "none"}` takes it back.
