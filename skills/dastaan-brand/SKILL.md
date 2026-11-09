---
name: dastaan-brand
version: 0.2.0
description: |
  Bring a founder's brand into their Dastaan videos: read their business name, brand colours and logo from their website or logo file, confirm them with the founder, and make a video in that colour with their logo scene. Use when: "use my brand colours", "here is my website, make it match", "put my logo in the video", "make the video look like us". NOT for: designing a logo or a brand identity from scratch, brand guidelines or brandbooks, or a reusable video style (use dastaan-look).
argument-hint: "[website URL or logo file] [then the brief]"
---

# Dastaan brand: their colour and their logo, confirmed, never assumed

Dastaan solves a whole readable palette (page, ink, night, accent) from **one** brand colour, so the founder's choice
is a single colour plus their logo. A colour read from their site is a proposal: never apply it without their yes.

## Before you start

The tools are the `dastaan_*` tools of the hosted Dastaan MCP server (`dastaan`, connected by this plugin). They run on
Dastaan's service, signed in with the founder's Siliqun Rotor account (the same account as the Dastaan app): if a call
answers that sign-in is needed, ask the founder to authenticate the `dastaan` server (Claude Code: `/mcp`; Codex:
`codex mcp login dastaan`). Nothing is installed or run on this machine. Pictures and logos go in as https addresses
or data: URIs, a CSV as its text. `dastaan_account` says which account is signed in; `dastaan_library` lists its videos
and their ids. Never guess an id.

## Steps

1. `dastaan_brand {site: "https://..."}` reads the page and up to three stylesheets: the business name, up to three
   brand colours (the page's declared theme colour first, then the most used), and the logo's URL. With a logo file:
   `{logo: "/path/logo.svg"}` (its colours too). A site that does not answer is not a reason to guess: ask the founder.
2. Show the founder the name, the colours and the logo, and ask which colour is theirs. Use only what they confirm.
3. Make the video (dastaan-video) with `brand.color` set to that colour, the logo in `pictures` (`{"logo": "<file or
   https URL>"}`), and a `logo` scene (`{"role": "logo", "picture": "logo", "tagline": ...}`) where it helps, usually
   before the close. A tagline is the founder's words too.
4. `dastaan_look` and check the logo reads on its ground and the colour carries through every scene.


## Read when needed

- `references/colour.md`: how one colour becomes a readable palette, and what to do with a pale or grey brand.
