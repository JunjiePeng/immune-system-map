# Immune Crosstalk Atlas

**▶ Open the live site: <https://junjiepeng.github.io/immune-system-map/>**

*Built by Junjie Peng · MIT licensed · questions, corrections and suggestions:
[open an issue](../../issues)*

An interactive map of how immune cells signal to one another, written so that
the same page works for a curious member of the public, an undergraduate
revising immunology, and a working immunologist.

Almost nothing in immunity is done by one cell alone. A cell detects, a second
carries the news somewhere useful, a third decides what kind of response to
mount, and a fourth carries it out. Break any link and the whole thing fails —
which is what most immune diseases turn out to be. This site is built around
those links rather than around a list of cell types.

## What it does

**A tissue-section map.** Twenty-one cells are placed in the compartment where
they actually work: airway surface, infected tissue, draining lymph node and
bloodstream. Forty-three connections join them, and each one carries the
molecule that really mediates it — `CXCL8`, `MHC II + CD80/86 + IL-12`,
`perforin, granzyme B, FasL`. Connection labels stay hidden until you hover
one or a scenario lights it, so the map never becomes a hairball.

**Three reading depths, switched in place.** One control rewrites every
explanation on the page:

| Depth | What you get |
| --- | --- |
| Curious reader | Plain language and analogies, no prior biology assumed |
| Student | Named cytokines, receptors and mechanisms, at undergraduate level |
| Immunologist | Surface phenotypes, transcription factors, the relevant inborn errors, and where current drugs act |

**Five responses played step by step**, with the timings they take in a real
body:

- **Flu virus in the airway** — nine steps from hour zero to lifelong memory
- **An mRNA vaccine in your arm** — why the arm aches, and why titre falling is not immunity failing
- **A splinter and Staph in the skin** — complement, neutrophils, Th17, and the scar
- **Pollen, and why hay fever exists** — silent sensitisation, degranulation, the late phase, and how immunotherapy retrains it
- **When it turns on you** — tolerance, how it is maintained, and what breaks

## Running it

There is nothing to install and nothing to build. The whole site is a single
self-contained `index.html` with no dependencies and no framework. Open the
file in any modern browser, or serve the folder:

```bash
python3 -m http.server 8000
```

Google Fonts is the only external request; everything else — data, layout,
drawing, interaction — ships in the file.

## How it is built

Four `<script>` blocks in order: cell and connection data, scenario data, map
rendering and interaction, then the reading panel, cell index and player.

- **Cells** carry `plain` / `student` / `clinical` prose plus surface markers
  and a clinical note. Adding a cell means writing all three depths, or it
  renders blank at that level.
- **Connections** carry the mediating molecule and a plain-language gloss, and
  are referenced by scenarios as `"cellA|cellB"` in either direction.
- **Cell glyphs** are hand-authored SVG resembling real morphology — the
  multilobed neutrophil nucleus, dendritic processes, mast cell granules, the
  plasma cell's clock-face nucleus. No icon font, no emoji.
- **Theming** is token-level, so the page follows light or dark preference and
  stays legible in both.

The palette is taken from histology rather than the usual web defaults:
haematoxylin ink, an eosin accent, and five lineage hues that encode cell
ancestry rather than decorate. Fraunces sets the display type, Public Sans the
body, and IBM Plex Mono is reserved for markers and cytokines so that
`CD4+CD25+FOXP3+` reads the way it does on a flow panel.

## Accuracy, and what is left out

Every connection shown carries the molecule that actually mediates it, and the
scenario timings follow the textbook course of each response in an average
adult. Real responses vary with dose, route, age and prior exposure.

Deliberate simplifications, named in the site footer as well as here: innate
lymphoid cells, γδ T cells, follicular dendritic cells, basophils and the bone
marrow compartment are described in the text but not drawn. The germinal
centre is compressed into a single B cell node. Cell positions are schematic,
not anatomical.

Built as a teaching aid. It is not medical advice.

## Contributing

Corrections to the immunology are especially welcome — open an issue saying
which cell or connection is wrong and what it should say. If you are adding
content, remember that every piece of prose exists three times, once per
reading depth.

## Licence

MIT. See [LICENSE](LICENSE).
