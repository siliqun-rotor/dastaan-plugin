# Patches on a script

Paths point into the script that `dastaan_check` answers: `/scenes/<index>/<field>`, counting from 0.
Ops: `replace`, `add`, `remove`, `move`, `copy`, `test` (RFC 6902).

| The founder says | The patch |
|---|---|
| "the number is now 60" | `[{"op":"replace","path":"/scenes/2/value","value":"60"}]` plus `brief: "we now bake 60 loaves a day"` |
| "change the headline" | `[{"op":"replace","path":"/scenes/0/headline","value":"..."}]` |
| "drop the list" | `[{"op":"remove","path":"/scenes/1"}]` |
| "swap scenes 2 and 3" | `[{"op":"move","from":"/scenes/2","path":"/scenes/1"}]` |
| "add our offer before the end" | `[{"op":"add","path":"/scenes/3","value":{"role":"offer","headline":"...","big":"20% off"}}]` |
| "make it 10 seconds" | `[{"op":"replace","path":"/seconds","value":10}]` |
| "add Arabic" | `[{"op":"replace","path":"/langs","value":["en","ar"]}]` and every text becomes `{"en": "...", "ar": "..."}` (their Arabic words in `brief`) |
| "a different brand colour" | `[{"op":"replace","path":"/brand/color","value":"#2f5f99"}]` |

Keep every word of a scene you do not change. A percentage or a total worked out from the founder's figures is
recalculated by Dastaan; if a change would make one untrue, the refusal says which, and the founder decides.
