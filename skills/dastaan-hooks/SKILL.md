---
name: dastaan-hooks
version: 0.2.0
description: |
  Write and test alternative openings (hooks) for a Dastaan video, by hook type (value, desire, loss, information), each held to the founder's own words, preview their first frames side by side, and swap the chosen one into the video (undoable). Use when: "try another hook", "a stronger opening", "give me 3 openings", "which first line works best", "A/B the intro". NOT for: changing anything after the opening (use dastaan-edit), making the video (use dastaan-video), or ad copy, captions or thumbnails outside the video.
argument-hint: "[video id] [hook types to try]"
---

# Dastaan hooks: the first three seconds, tried several ways

The opening decides in under three seconds whether anyone keeps watching. A good hook is short (at most 8 words),
on screen from the first frame, built only from the founder's facts, and paid off honestly by the next scenes.

## Before you start

The tools are the `dastaan_*` tools of the hosted Dastaan MCP server (`dastaan`, connected by this plugin). They run on
Dastaan's service, signed in with the founder's Siliqun Rotor account (the same account as the Dastaan app): if a call
answers that sign-in is needed, ask the founder to authenticate the `dastaan` server (Claude Code: `/mcp`; Codex:
`codex mcp login dastaan`). Nothing is installed or run on this machine. Pictures and logos go in as https addresses
or data: URIs, a CSV as its text. `dastaan_account` says which account is signed in; `dastaan_library` lists its videos
and their ids. Never guess an id.

## Try openings

1. `dastaan_hooks {id}`: the current opening and the hooks already offered (the writer gives two with the script).
2. Read `references/hooks.md`. Write one hook per type the founder's facts support. A type their facts do not
   support (a loss they never named, a figure they never gave) is left out, not invented.
3. `dastaan_hooks {id, hooks: [...], preview: true}`. Each offered hook comes back with its problems (a word that is
   not the founder's, too many words); the ones without problems join the list. Look at `hooks.png`: every opening's
   first second, side by side (in the video's look, if it has one).
4. Show the founder the openings and let them choose. `{id, use: <index>}` swaps it into scene 1; the old opening
   joins the list, so using it again undoes the swap.
5. `dastaan_look {id, scene: "s1"}`, then render again.


## Read when needed

- `references/hooks.md`: the four types with examples, the rules, and the research they come from.
