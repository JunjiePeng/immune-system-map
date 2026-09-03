# Immune Crosstalk Atlas

**▶ Open the live site: <https://junjiepeng.github.io/immune-system-map/>**

*Built by Junjie Peng · MIT licensed · questions, corrections and suggestions:
[open an issue](https://github.com/junjiepeng/immune-system-map/issues)*

An interactive map of how immune cells signal to one another, written so that
the same page works for a curious member of the public, an undergraduate
revising immunology, and a working immunologist.

Almost nothing in immunity is done by one cell alone. A cell detects, a second
carries the news somewhere useful, a third decides what kind of response to
mount, and a fourth carries it out. Changes to these interactions can disrupt
immune responses. This site is built around those links rather than around a list of cell types.

## What it does

**A tissue-section map.** Twenty-one entries represent selected immune cells,
cell groups and two soluble components: antibody and complement. They are
placed in representative compartments: airway surface, infected tissue,
draining lymph node and bloodstream. Forty-three connections carry
labels describing signalling, differentiation or protein production —
`CXCL8`, `MHC II + CD80/86 + IL-12`,
`perforin, granzyme B, FasL`. Connection labels appear when you hover a connection,
select an entry or follow a scenario. Paths route around measured cell names
and headings; connection labels leave the arrows and arrowheads unobstructed.
Compartment borders include padding beneath the cell names.

**Three reading depths, switched in place.** One control switches the
explanatory prose throughout the page:

| Depth | What you get |
| --- | --- |
| Curious reader | Plain language and analogies, no prior biology assumed |
| Student | Named cytokines, receptors and mechanisms, at undergraduate level |
| Immunologist | Surface phenotypes, transcription factors, the relevant inborn errors, and where current drugs act |

**Five responses played step by step**, with illustrative biological timings:

- **Flu virus in the airway** — nine steps from initial exposure to immune memory
- **An mRNA vaccine in your arm** — why the arm aches, and why titre falling is not immunity failing
- **A splinter and Staph in the skin** — complement, neutrophils, Th17, and the scar
- **Pollen, and why hay fever exists** — silent sensitisation, degranulation, the late phase, and how immunotherapy retrains it
- **When it turns on you** — tolerance, how it is maintained, and what breaks

**Inspect without losing your place.** Choosing a cell during a scenario pauses
playback. Use **Back to scenario** to return to the same step, or **Resume
scenario** to continue. Escape pauses playback and clears cell inspection;
**Free explore** exits the scenario. Click anywhere on the map outside a cell
to clear the highlight and pause playback; the selected scenario and step are
kept, and **Play** restores the step’s connections.

**A searchable index.** Find entries by cell name, marker or connected signal,
including `Treg`, `CD4`, `IL-5` and `IFN-gamma`. Search filters the index without
changing the selected scenario. Keyboard users can skip directly to the index.

**Responsive layout.** The map fits the available width automatically when the
window changes size or moves between monitors. The details panel uses a flexible
side column on wide windows and moves below the map on smaller ones. **+** and
**−** change zoom in 5% steps for closer inspection; **Fit** shows the whole map
again. When zoomed in, hold the left mouse button and drag to pan, or swipe on a
touchscreen. A normal click still selects a cell; releasing a drag does not.
Resizing preserves your selected cell, reading depth and scenario progress.

## Running it

There is nothing to install and nothing to build. The whole site is a single
self-contained `index.html` with no dependencies and no framework. Open the
file in any modern browser, or serve the folder:

```bash
python3 -m http.server 8000
```

Google Fonts is the only external request needed for the page styling; data,
layout, drawing and interaction ship in the file. The app works with fallback
fonts offline. Selected entries link to external scientific sources.

## How it is built

Four `<script>` blocks in order: cell and connection data, scenario data, map
rendering and interaction, then the reading panel, cell index and player.

- **Cells** carry `plain` / `student` / `clinical` prose plus surface markers
  and a clinical note. Adding a cell means writing all three depths, or it
  renders blank at that level.
- **Connections** carry a mechanism label and a plain-language gloss. Scenarios
  use `"cellA|cellB"` for either direction or `"cellA>cellB"` for an exact
  direction. Use a directed key when an undirected pair would be ambiguous.
  Active connection endpoints are included in the highlighted node list.
- **Selected sources** live in `SOURCES`. Add a `refs` array to a cell or a
  scenario step, with a source title, URL and a precise statement of what it
  supports. The current citations cover targeted corrections, not the full atlas.
- **Cell portraits** are scalable SVG with softly shaded cytoplasm, outlined
  membranes and a shared nuclear stain palette. Distinctive features include
  segmented neutrophil nuclei, bilobed eosinophil nuclei, dendritic processes,
  mast-cell granules and an eccentric plasma-cell nucleus. T-cell subtype
  badges are identifiers, not microscopic features; the shared memory node
  depicts both B and T cells. Selecting an entry shows a larger portrait.
  Drawings are schematic and not to scale. Morphology references:
  [ASH Image Bank: eosinophil](https://imagebank.hematology.org/image/60933/eosinophil?type=atlas)
  and [University of Utah: plasma cell](https://webpath.med.utah.edu/HISTHTML/NORMAL/NORM168.html).
- **Theming** is token-level, so the page follows light or dark preference and
  stays legible in both.

The palette is taken from histology rather than the usual web defaults:
haematoxylin ink, an eosin accent, and five lineage hues that encode cell
ancestry rather than decorate. Fraunces sets the display type, Public Sans the
body, and IBM Plex Mono is reserved for markers and cytokines so that
`CD4+CD25+FOXP3+` reads the way it does on a flow panel.

## Accuracy, and what is left out

This is a simplified teaching map. Some connections represent indirect effects,
differentiation or protein production rather than a direct ligand–receptor
interaction. Scenario timings are illustrative and vary with dose, route, age
and prior exposure. Selected entries include sources; a systematic evidence
review of the full atlas remains a priority.

Deliberate simplifications, named in the site footer as well as here: innate
lymphoid cells, γδ T cells, follicular dendritic cells, basophils and the bone
marrow compartment are described in the text but not drawn. The germinal
centre is compressed into a single B cell node. Cell positions show
representative compartments, not exclusive locations; cells migrate and effectors also act outside nodes.

Built as a teaching aid. It is not medical advice.

## Validation and development priorities

The optional validator requires Node.js and no packages:

```bash
node scripts/validate.mjs
```

It checks all four script blocks for syntax errors, unique IDs, complete
reading depths, scenario edge references and source links. It checks structure,
not scientific correctness or browser behavior.

See [PROJECT_REVIEW.md](PROJECT_REVIEW.md) for the refinement report, scoped
scientific corrections, verification details and a prioritized roadmap.

## Contributing

Corrections to the immunology are especially welcome — open an issue saying
which cell or connection is wrong and what it should say. If you are adding
content, remember that every piece of prose exists three times, once per
reading depth.

## Licence

MIT. See [LICENSE](LICENSE).
