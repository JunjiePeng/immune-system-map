# Immune Crosstalk Atlas

**▶ Open the live site: <https://junjiepeng.github.io/immune-system-map/>**

*Built by Junjie Peng · MIT licensed · questions, corrections and suggestions:
[open an issue](https://github.com/junjiepeng/immune-system-map/issues)*

An interactive reference for immune-cell communication, with one professional
reading flow that builds from definitions to mechanisms, marker guides and
biological context. Numbered references accompany the explanations.

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
`CXCL8`, `peptide–MHC II + CD80/86`,
`perforin, granzyme B, FasL`. Connection labels appear when you hover a connection,
select an entry or follow a scenario. Paths route around measured cell names
and headings; connection labels leave the arrows and arrowheads unobstructed.
Compartment borders include padding beneath the cell names.

**One complete explanation.** Cells and scenario steps use a definition or
overview, mechanism and biological context. Marker guides explain how cells
are identified and where interpretation depends on tissue or assay. There is
no reading-level selector and no detail hidden behind a different audience mode.

**Foundations and key terms.** The header links to an introductory guide covering
recognition, adaptive responses, communication and the distinction between cell
identity, state and dataset cluster. A glossary defines 28 concepts and
abbreviations. Explanations offer relevant terms in an expandable definition
list without changing the main reading flow.

**Contextual references.** All 21 entries, 43 interactions, 34 scenario steps and
57 subtype profiles have sources. The shared bibliography contains 55 references
with source type and scope notes. Numbered links open the source in a new tab;
the reference list distinguishes educational introductions, primary studies and
consensus material. Source presence is not a claim of systematic evidence review.

**Five responses played step by step**, with illustrative phases:

- **Influenza in the airway** — local sensing, adaptive responses and memory.
- **An mRNA vaccine** — antigen expression, germinal centres and immune memory.
- **A bacterial skin wound** — microbial recognition, recruitment and repair.
- **An IgE-associated allergy** — sensitisation, re-exposure and inflammation.
- **Tolerance and autoimmunity** — tolerance and an illustrative lupus-like network.

Use **Next** to read at your own pace or **Play** for automatic progression.

**Inspect without losing your place.** Choosing a cell during a scenario pauses
playback. Use **Back to scenario** to return to the same step, or **Resume
scenario** to continue. Escape pauses playback and clears cell inspection;
**Free explore** exits the scenario. Click anywhere on the map outside a cell
to clear the highlight and pause playback; the selected scenario and step are
kept, and **Play** restores the step’s connections.

**A lineage explorer.** Select an entry, then choose **Explore subtypes** (or
**Explore cell states**, **antibody classes**, or **complement pathways**).
Thirteen focused maps contain 57 distinct reference profiles, with some memory
profiles shared across maps. Click a profile to read its role, location and
sources, with family context, marker clues and interpretation in the same view.
Search within a family by name or marker, or switch families inside the explorer.
**Back to atlas** or Escape returns to your saved selection, zoom and scenario
position. If the explorer search contains text, Escape first clears the search.

These are curated human reference groupings, not clusters calculated from an
uploaded dataset or a fixed developmental tree. Cell identities, activation
states and tissue phenotypes are labelled explicitly. Eosinophil and neutrophil
states retain their study and tissue context; proteins have classes/pathways.
References include primary human atlas studies, IMGT and educational resources.

**A searchable index.** Find entries by cell name, marker or connected signal,
including `Treg`, `CD4`, `IL-5` and `IFN-gamma`. Search filters the index without
changing the selected scenario. Keyboard users can skip directly to the index.

**Responsive layout.** The map fits the available width automatically when the
window changes size or moves between monitors. The details panel uses a flexible
side column on wide windows and moves below the map on smaller ones. **+** and
**−** change zoom in 5% steps for closer inspection; **Fit** shows the whole map
again. When zoomed in, hold the left mouse button and drag to pan, or swipe on a
touchscreen. A normal click still selects a cell; releasing a drag does not.
Resizing preserves your selected cell, zoom and scenario progress.

## Running it

There is nothing to install and nothing to build. The whole site is a single
self-contained `index.html` with no dependencies and no framework. Open the
file in any modern browser, or serve the folder:

```bash
python3 -m http.server 8000
```

Google Fonts is the only external request needed for the page styling; data,
layout, drawing and interaction ship in the file. The app works with fallback
fonts offline. External scientific references open only when followed.

## How it is built

Four `<script>` blocks in order: cell and connection data, scenario data, map
rendering and interaction, then the reading panel, cell index and player.

- **Cells** use `summary`, `mechanism`, `context`, `markers`, `refs` and
  `contextRefs`. Short `mapSub` labels keep map geometry separate from the fuller
  role descriptions in the reading panel.
- **Connections** use `sig`, `summary` and `refs`, with explanations identifying
  indirect pathways. Scenarios use `"cellA|cellB"` for either direction or
  `"cellA>cellB"` for an exact direction. Active edge endpoints are highlighted.
- **Scenario steps** use the same unified prose fields as cells. Captions show
  the summary; the panel provides the mechanism, context and linked signals.
- **References** live in the shared `SOURCES` object: `title`, `url`, `kind`
  and `scope`. Every content entry requires a valid reference array. References
  are deduplicated within each reading panel; citation numbers are shared across
  the page and explorer.
- **Glossary** entries in `GLOSSARY` include a term, definition and matching
  phrases. These drive both the foundations glossary and contextual definitions.
- **Cell portraits** are scalable SVG with softly shaded cytoplasm, outlined
  membranes and a shared nuclear stain palette. Distinctive features include
  segmented neutrophil nuclei, bilobed eosinophil nuclei, dendritic processes,
  mast-cell granules and an eccentric plasma-cell nucleus. T-cell subtype
  badges spell out CD4, CD8, Th1, Th2, Th17, Treg and Tfh; they are identifiers,
  not microscopic features; the shared memory node
  depicts both B and T cells. Selecting an entry shows a larger portrait.
  Drawings are schematic and not to scale. Morphology references:
  [ASH Image Bank: eosinophil](https://imagebank.hematology.org/image/60933/eosinophil?type=atlas)
  and [University of Utah: plasma cell](https://webpath.med.utah.edu/HISTHTML/NORMAL/NORM168.html).
- **Explorer data** live in `SUBTYPE_PROFILES`, `LINEAGE_MAPS`, `LINEAGE_LINKS`
  and the shared `SOURCES` bibliography. Profiles are reusable across family maps; each atlas
  entry has an explicit destination. The native dialog keeps the main map state
  intact and supports keyboard navigation and small screens.
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
and prior exposure. Each explanation links to scoped evidence; this curation
is not a systematic review. Human and animal experiments are distinguished
where relevant, and study-specific states are not presented as universal lineages.

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
unified explanations, scenario edge references, explorer coverage, glossary
entries and citation references. It also rejects obsolete reading-level fields.
It checks structure and coverage, not scientific correctness or browser behavior.

See [PROJECT_REVIEW.md](PROJECT_REVIEW.md) for the refinement report, scoped
scientific corrections, verification details and a prioritized roadmap.

## Contributing

Corrections to the immunology are especially welcome — open an issue saying
which cell or connection is wrong and what it should say. If you are adding
content, begin with a definition, add the mechanism and context, explain essential
terms and attach evidence that supports the particular claims. Avoid treating
a single marker or dataset cluster as a universal cell identity.

## Licence

MIT. See [LICENSE](LICENSE).
