# Art Atlas — Data architecture

## Curated dataset
`artists-curated.js` is the **single authoritative curated artist dataset** (591 artists). It is loaded by the main 2D, 3D and research pages. Artist data is no longer duplicated inside those pages. Edit this file to change the published dataset. `legacy-datasets/` contains archived older exports; do not edit or publish those as the active dataset.

## Visitor submissions
`artist-submissions.json` is a **separate, initially empty, review-only file** for collecting exported submissions. Visitor entries are *not* written to this file automatically. On GitHub Pages, a static site cannot write to a repository file. The Add Artist page stores entries in the visitor's browser using localStorage (`art-atlas-community-artists-v1`), and visitors can export a JSON file. A curator can review these files and merge vetted records into `artists-curated.js` using a later editorial workflow.

### Visibility and vetting
Locally submitted artists appear in that visitor's own 2D and 3D Atlas, but are **not public or approved** merely by being submitted. Do not merge submissions into the curated dataset until reviewed. The separate `artist-submissions.json` is a template for a curator-managed review queue, not a shared live database. To support centralized automatic collection, an authenticated backend or submission service will be needed.

## Deployment
Upload the files together to GitHub Pages; `artists-curated.js` must be adjacent to the HTML files. The site should be served over HTTP(S) (e.g. GitHub Pages), not by opening files directly.
