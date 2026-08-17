# SOW / PWS Builder

A free, self-contained browser tool that walks a program office through scope
decisions and assembles a contract-file-ready **Statement of Work** or
**Performance Work Statement** — aware of the Revolutionary FAR Overhaul (RFO)
and Executive Order 14402.

**▶ Live tool:**https://claude.ai/public/artifacts/1dd25fd9-adc8-4ff3-ae09-9c37555b6ada

No install, no account, no backend. Everything runs in the browser; nothing you
type is uploaded or stored anywhere.

---

## What it does

Make the scope decisions; the tool assembles the document.

**Five acquisition domains**, each reshaping the questions, derivation logic,
citations, and assembled sections:

| Domain | What changes |
|---|---|
| **IT / Systems** | Build-vs-buy, integration count, migration, automation, service-desk workload |
| **Services (non-IT)** | Service Contract Labor Standards gate, personal-services check (FAR 37.104) |
| **Construction** | FAR Part 36, Davis-Bacon wage determinations, magnitude disclosure (36.204), Miller Act bonding |
| **Architect-Engineer** | Brooks Act qualifications-based selection, SF-330, 6% / 10% (DoD) design fee ceiling |
| **Research & Development** | FAR Part 35 structure, rights in data (Part 27), level-of-effort vs. defined deliverable |

**Regulatory awareness**

- Every citation resolves to **either** codified FAR **or** RFO model deviation
  text, depending on the regime you select — each stamped with an "as of" date
  and linked to acquisition.gov rather than asserted as authority.
- **EO 14402 fixed-price gate** flags covered contracts and surfaces the
  FAR 16.104 justification path, with preloaded agency-head approval thresholds
  (DoD $100M · NASA $35M · DHS $25M · all others $10M).
- Agency class deviation number and effective date are **user-entered, not
  inferred** — the tool never guesses which instrument governs your action.

**The firewall (inherited from the upstream framework, preserved intact)**

Staffing (FTEs, SOC codes), CLIN structure, and the FAR 16.104 justification
**never** enter the requirement document body. They are emitted as separate,
clearly-marked workpapers. This is the whole point: FAR 37.102(d) requires the
requirement be described in terms of results, not hours or numbers of people.
The export functions read only the document renderer, so the separation is
structural rather than a matter of user discipline.

---

## What it is not

- **Not an official Government system.** Independent drafting aid.
- **Not legal or contracting advice.** A contracting officer owns the document.
- **Not a compliance verdict.** It drafts structure and resolves citations; it
  does not certify that anything is compliant.
- **Not a generator of regulatory text.** It links to the authoritative source
  instead of reproducing it — deliberately, so it degrades gracefully as the
  model text changes.

Generated documents contain **marked placeholders** everywhere a human must
write. That is by design.

---

## Regulatory currency

The RFO model text moves constantly. This tool is dated, not evergreen.

- **Regulatory content last reviewed:** 18 July 2026
- **Review cadence:** quarterly, plus ad hoc when a deviation or EO changes
- Every RFO citation displays its own "as of" stamp in the UI
- The landing screen and footer both tell users to verify at
  [acquisition.gov/far-overhaul](https://www.acquisition.gov/far-overhaul)
  before any solicitation release

Maintaining currency is the maintainer's standing commitment. See
[MAINTENANCE.md](MAINTENANCE.md) for exactly which lines to update.

**Found something stale?** Open an issue. Regulatory-currency reports are the
most useful contribution you can make.

---

## Usage

Open `index.html` in any modern browser. That's it.

To self-host: drop `index.html` on any static host (GitHub Pages, Netlify,
Cloudflare Pages, S3, or your own web space). No build step.

Users can **Save draft** to download a JSON file and **Load** it later — there
is no server, so nothing persists unless the user saves it themselves.

---

## Credit

Built on the open-source federal contracting skills framework by
**James Jenrette** — [1102tools.com](https://1102tools.com) (MIT).

The upstream framework contributed the decision-tree logic, the derivation
approach, and the staffing/CLIN firewall design. See [NOTICE.md](NOTICE.md).

Maintained independently by **The Wolverine Group, Inc.** Issues with this tool
belong here, not upstream.

## License

MIT — see [LICENSE](LICENSE).
