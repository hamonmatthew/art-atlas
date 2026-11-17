# Art Atlas dataset expansion

The bundled working atlas contains **140 curated artist records**. These are preserved. The project is ready to import additional records from Wikidata but **no live Wikidata records have been downloaded in this release**, because the build environment could not access the endpoint. Do not confuse the existing artist records with verified Wikidata records.

## Import on a network-connected computer

Install Python 3 and `requests` (`python -m pip install requests`). From this folder run:

```sh
python update_wikidata.py --fetch --limit 500
python update_wikidata.py --build
```

The first command writes `wikidata_artists.json` and `wikidata_movements.json`. The second merges artist records into `artists.json`, preserving existing curated tags and IDs, then embeds the data into `index.html`, `Art-Atlas-3D.html`, and `spatial.html` so the unified atlas works offline. The script will skip imported artists lacking birth years, and Wikidata-only records have no invented themes/aesthetics/processes. Review the imported records for duplicates, movement classification, and reliability.

`movements.json` stores fetched movement metadata, but the current movement network still derives its visible movement list from artist memberships and its existing curated network. Thus movement records without associated imported artists are **not yet rendered**. The import is a first phase, not a completed 100-movement network.

## Provenance and limitations

Wikidata properties: occupation P106, movement P135, birth P569, death P570, citizenship P27, inception P571. A Wikidata movement association is not proof of influence or similarity. No aesthetic or conceptual score is automatically asserted. Imported artists default to medium Other until curated. The public Wikidata Query Service has timeouts and usage limits; reduce `--limit` if queries fail.
