# Ideas for later

## Suggest a layout from a description (noted 2026-11-22)

Someone describes the event (how many people, seated or standing, buffet, dance floor and so on)
and the planner proposes a good starting layout they can then drag around.

Agreed direction, to keep in mind when adding other features:

- Do not train a model for this. There is too little layout data for one house, and language
  models place furniture without checking it.
- Split the job in three:
  1. Turn the request into a short brief: seated count, table preference, reserved spaces, floor.
     A simple form does this for most events; a language model with a prompt handles free text.
  2. Ordinary code builds candidate layouts with the planner's own tools (table patterns, seating,
     rows of chairs) and scores them with the layout check (doors, walkways, seats reached, capacity).
  3. Show the best two or three as normal editable plans.
- Saved real layouts are valuable as examples of what "good" means here (where the bar goes,
  how tightly tables are packed). Keep saving them.
- Cheap first version: a "Suggest a layout" button that asks for guest count and style and tries
  the table patterns room by room until the layout check is clean.

What this means for other work: keep the pattern, seating and layout-check code callable on its own
(no mouse needed), since the generator would reuse it.
