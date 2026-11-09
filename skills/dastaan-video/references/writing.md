# Writing a Dastaan script

A script is words and what each scene is for. Nothing about layout, colour, timing or motion: Dastaan decides those.

```json
{ "langs": ["en"], "seconds": 20, "brand": { "color": "#1f5a3a" },
  "scenes": [
    { "role": "open", "kicker": "Corner Bakery", "headline": "Bread worth waking up for" },
    { "role": "list", "heading": "Every morning", "items": ["Baked at 5", "Local flour", "No shortcuts"] },
    { "role": "close", "action": "Order before 9", "handle": "@cornerbakery" } ],
  "hooks": [ { "type": "value", "headline": "Baked at 5." } ] }
```

## Roles (`dastaan guide` has every field and limit)

| Role | For | Words |
|---|---|---|
| `open` | the hook, always first | `kicker`?, `headline` (at most 8 words) |
| `point` | one idea in big words | `phrases` (1 to 6) |
| `list` | features, what is included | `heading`?, `items` (2 to 6) |
| `steps` | a process | `heading`?, `steps` [{title, line}] |
| `number` | one figure | `value` (or `answer` from a CSV), `label`, `unit`? |
| `chart` / `parts` | a split from a CSV | `answer`, `heading` |
| `compare` | plans or before/after | `heading`?, `columns`, `rows`, `highlight`? |
| `quote` | a customer's words they gave you | `quote`, `name`, `title`? |
| `offer` | a promotion | `headline`, `big`, `note`? |
| `timeline`, `places` | dates, places | see the guide |
| `photo`, `logo` | a picture they gave | `picture` (its name), `headline`/`tagline`? |
| `close` | the action, only when they gave one | `action`, `handle`?, `note`? |

Every text is a string, or `{"en": "...", "ar": "..."}` with one entry per language in `langs`.

## The founder's words, and nothing else

Every statement on screen must be the founder's, in their words or a plain rewording. That rules out: who does the
work ("our experts"), where or how fast ("same day") when they did not say it, gifts, limits, amounts in words
("hundreds of"), slogans and calls to action they did not write. Numbers must appear in the brief, in `numbers`,
or in the CSV.

## The hook

The first scene decides in under three seconds whether anyone keeps watching. Use the strongest type their facts
support: **value** (a figure or result: "48 hours."), **desire** (the outcome: "Your 3D site model in 48 hours."),
**loss** (their problem or wait as a question, only if they named it), or **information** (a gap the next scene
answers). Never open on a logo or a greeting. Pay the hook off honestly in the scenes after it.

## Refusals you will meet

| Code | Means | Do |
|---|---|---|
| `script_needed` | no script yet | read the rules and format it returns, then write one |
| `rewrite` / `unsupported_words` | a word is not the founder's | use their word, or drop the line |
| `rewrite` / `unsupported_number` | a number is not theirs | remove it; never round or estimate |
| `rewrite` with a limit | the words do not fit | shorten to the limit named |
| `check` | a frame fails a gate | change the words or scene the finding names |
