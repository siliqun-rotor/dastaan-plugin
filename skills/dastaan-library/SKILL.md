---
name: dastaan-library
version: 0.2.0
description: |
  Find, reopen and continue the founder's saved Dastaan videos: which account is signed in, the videos in their Dastaan library with the links that open them in the app, and the videos this agent made that can still be changed. Use when: "what videos have I made", "open my launch video", "continue the video from yesterday", "send me the link to my video", "which account is this". NOT for: making a new video (use dastaan-video), changing words or scenes (use dastaan-edit), or restyling (use dastaan-look).
argument-hint: "[what the founder calls the video]"
---

# Dastaan library: the founder's saved videos

## Before you start

The tools are the `dastaan_*` tools of the hosted Dastaan MCP server (`dastaan`, connected by this plugin). They run on
Dastaan's service, signed in with the founder's Siliqun Rotor account (the same account as the Dastaan app): if a call
answers that sign-in is needed, ask the founder to authenticate the `dastaan` server (Claude Code: `/mcp`; Codex:
`codex mcp login dastaan`). Nothing is installed or run on this machine. Pictures and logos go in as https addresses
or data: URIs, a CSV as its text. `dastaan_account` says which account is signed in; `dastaan_library` lists its videos
and their ids. Never guess an id.

## Find a video

1. `dastaan_account {}`: the signed-in account (its email), how many videos it has made and how many are saved.
2. `dastaan_library {}`: the saved videos, newest first, each with the link that opens it in the Dastaan app, and the
   videos this agent made in this account that can still be changed here, by id.
3. Match what the founder says ("the launch video", "yesterday's") against titles and dates. When two could match,
   show both and ask. Never pick one silently.

## Do something with it

- **Open it in the app.** Give the founder its app link from the library.
- **Change it.** For a video listed as changeable by id, use dastaan-edit with that id.
- **A video made in the app.** If it is not changeable here, ask the founder to export its story from the app (Export,
  "Download the story file"). Then pass that text as `zedl` to `dastaan_brief` to continue it here.
- **Save a video made here.** `dastaan_open {id}` saves it to the library and answers its app link.
- **Files again.** `dastaan_render {id}` makes them; the links last 24 hours.
