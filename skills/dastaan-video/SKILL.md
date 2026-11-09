---
name: dastaan-video
version: 0.2.0
description: |
  Make a finished short video for a founder or small business from their own words: a brief, their numbers or a CSV, their logo and photos, in English and/or Arabic, as 9:16, 4:5, 1:1 and 16:9 MP4s rendered by Dastaan. Use when: "make a video for my business", "turn this into a reel / short / story", "a launch video from these numbers", "a 15-second video in English and Arabic", "a video from my sales CSV". Chain dastaan-brand first when they give a website, dastaan-hooks to try other openings, dastaan-look to dress it in a style. NOT for: changing a video already made (use dastaan-edit), restyling a video (use dastaan-look), filmed footage, talking avatars, voice-over or AI-generated imagery, or a video whose facts the founder did not give.
argument-hint: "[the founder's brief or file] [seconds] [languages] [sizes]"
---

# Dastaan video: a founder's brief, told as a short video in their own words

You write the words; Dastaan does everything else (layout, colours readable from one brand colour, timing fitted
to the length, transitions, every size and English or Arabic right to left) and holds each word and number to the
founder's brief. It runs on Dastaan's hosted service, signed in with the founder's Siliqun Rotor account.

## Before you start

The tools are the `dastaan_*` tools of the hosted Dastaan MCP server (`dastaan`, connected by this plugin). They run on
Dastaan's service, signed in with the founder's Siliqun Rotor account (the same account as the Dastaan app): if a call
answers that sign-in is needed, ask the founder to authenticate the `dastaan` server (Claude Code: `/mcp`; Codex:
`codex mcp login dastaan`). Nothing is installed or run on this machine. Pictures and logos go in as https addresses
or data: URIs, a CSV as its text. `dastaan_account` says which account is signed in; `dastaan_library` lists its videos
and their ids. Never guess an id.

## Gather (ask only for what is missing)

- **The brief**: the founder's own words. What they do, their facts and numbers, the offer, the action. This is the
  only source the video may use. Never fill a gap with a guess; ask, or leave the scene out.
- Length (default 20 s), languages (`en`, `ar` or both), sizes (default all four), a brand colour (or run
  dastaan-brand on their site), pictures as https URLs or data: URIs (`{"logo": "...", "photo1": "..."}`).
- A CSV of their records, if they have one: give its text as `csv`; it is shaped into answers a `number`, `chart` or `parts`
  scene reads by id (`count`, `split`).

## Make it

1. `dastaan_brief {brief}` with no script. It answers `script_needed` with the writing rules and the script format.
   Read both. `references/writing.md` sums up what matters most.
2. Write the script: 2 to 7 scenes, each a `role` and its words. Open with the strongest hook the facts support (at
   most 8 words). Add `hooks`: two other openings of other hook types. Use only the founder's words and numbers.
3. `dastaan_brief {brief, script, ...}`. A refusal lists `rewrite` items by scene and field with the exact limit or
   the word that is not the founder's. Fix exactly those and call again. Never route around a refusal by inventing.
4. `dastaan_look {id}` and **look at every row of the frame sheet** (each language you made). A check that passes
   does not prove a good video: look for a weak opening, a crowded scene, a line that reads wrong. Fix with
   dastaan-edit's patch (`dastaan_edit`).
5. `dastaan_render {id, sizes: "all", langs: "all"}` (or what the founder asked). Use `draft: true` for a quick
   half-size look first. Hand back the download links (they last 24 hours) and each file's fingerprint.
6. `dastaan_open {id}` saves the video to the founder's Dastaan library and answers a link that opens it in the app.


## Read when needed

- `references/writing.md`: the roles, the hook, the founder's-words rule, and the refusals you will meet.
- `references/quality.md`: what to look for on the frame sheet before you call it done.
- The full rules come back from `dastaan_brief` without a script.
