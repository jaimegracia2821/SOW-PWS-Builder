# Maintenance

The tool is one file (`index.html`). Regulatory content lives in a few clearly
marked constants near the top of the `<script>` block. Editing them requires no
build step — change, save, re-upload.

## Quarterly review checklist

1. **Check for changes** at [acquisition.gov/far-overhaul](https://www.acquisition.gov/far-overhaul)
   — model deviation text by Part, especially Part 16.
2. **Update the two date stamps** (search for `MAINTENANCE:` in the file):
   ```js
   const ASOF     = "Jul 2026";       // shown on every citation token
   const REVIEWED = "18 July 2026";   // shown in the footer
   ```
3. **Verify the EO 14402 thresholds** in the `AGENCIES` object. Each entry has a
   `threshold` (agency-head approval tier) and a `devSeries` label.
4. **Verify the citation pairs** in the `CITES` object. Each key maps a concept
   to `{legacy, rfo}` — the codified FAR cite and its RFO model-deviation
   counterpart. If a Part is renumbered upstream, this is the only place to fix it.
5. **Verify the `AUTHORITIES` register** — the EO / OMB / deviation-guidance
   entries that populate Section 1.4 of generated documents.
6. Bump the version string in the footer and note the change below.

## Where things live

| What | Where to look |
|---|---|
| Date stamps | `ASOF`, `REVIEWED` constants (marked `MAINTENANCE:`) |
| Agency thresholds & deviation series | `AGENCIES` object |
| Legacy ↔ RFO citation pairs | `CITES` object |
| EO / OMB / guidance register | `AUTHORITIES` array |
| Domain behavior (IT, services, construction, A/E, R&D) | `DOMAINS` object + `domain*()` functions |
| A/E fee ceiling (6% / 10% DoD) | `aeFeePct()` |

## Design rules to preserve

These are load-bearing. Changing them breaks the tool's core promise.

- **Never** write staffing, SOC codes, CLINs, or the 16.104 justification into
  the document renderer. Export functions must read only `renderDocumentHTML()`.
- **Never** hardcode regulatory *text* — cite and link instead. The tool stays
  publishable precisely because it doesn't reproduce or interpret the FAR.
- **Never** infer an agency's class deviation number. The user asserts it.
- Every RFO citation carries a visible date.

## Change log

| Date | Change |
|---|---|
| 2026-07-18 | Initial public release. Content reviewed against RFO model text and EO 14402 implementation guidance. |
