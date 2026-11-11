---
name: dastaan-edit
version: 0.2.0
description: |
  Change a Dastaan video that already exists: its words, a number the founder updated, a scene added, removed or moved, its length, a language added, a different opening, then re-render only what changed. Use when: "change the price in my video", "make it 10 seconds", "add an Arabic version", "swap scene 2 and 3", "the number is now 60", "remove the offer". NOT for: making a new video from a brief (use dastaan-video), trying alternative openings with previews (use dastaan-hooks), restyling (use dastaan-look), or editing an MP4 or footage that Dastaan did not make.
argument-hint: "[video id] [the change, in the founder's words]"
---

# Dastaan edit: one change, as one patch, checked before it is kept

A Dastaan video is its script (the founder's words by scene) plus what Dastaan made from it. You change the
script; Dastaan re-lays, re-times and re-checks, and answers which scenes changed. A refused change keeps the video
exactly as it was.

## Before you start

The tools are the `dastaan_*` tools of the hosted Dastaan MCP server (`dastaan`, connected by this plugin). They run on
Dastaan's service, signed in with the founder's Dastaan account (the same account as the Dastaan app): if a call
answers that sign-in is needed, ask the founder to authenticate the `dastaan` server (Claude Code: `/mcp`; Codex:
`codex mcp login dastaan`). Nothing is installed or run on this machine. Pictures and logos go in as https addresses
or data: URIs, a CSV as its text. `dastaan_account` says which account is signed in; `dastaan_library` lists its videos
and their ids. Never guess an id.

## Change it

1. `dastaan_check {id}` answers the current script. Find the scene and field to change (`references/patch.md`).
2. Write one RFC 6902 patch on the script with every change the founder asked for, and call `dastaan_edit {id,
   patch}`. A new fact from the founder ("we now bake 60") goes in `brief` with the patch: the words on screen are held
   to everything they said.
3. A refusal names the scene and field (a word that is not theirs, a limit, a figure that a percentage depended on).
   Fix that and call again. A stale-figure refusal ("change 40 here too") means one fact appears twice: change both.
4. `dastaan_look {id, scene}` for each changed scene, then the whole sheet once. Then `dastaan_render` again.


## Read when needed

- `references/patch.md`: script paths by role, and patches for the usual requests.
