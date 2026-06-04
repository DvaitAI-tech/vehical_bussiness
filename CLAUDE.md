# Delhi Cab Venture — Project Context (for AI assistants)

> Read this file first. It is **self-contained** — everything an AI needs to work on
> this repo is here. You should **not** need internet access or to re-read the full
> `index.html` to understand the project.

## What this is

A **single-page static website** that presents a **business proposal**: a 5-partner
shared investment to run a **CNG cab fleet in Delhi**, starting with one car and
scaling to a small fleet over 5 years. It is an internal pitch document for the
partners, not a web app.

- **No build step. No dependencies. No framework.** One self-contained HTML file with
  inline `<style>` and a tiny inline `<script>` (an IntersectionObserver for scroll
  fade-in animations). Fonts load from Google Fonts via `<link>`.
- Open `index.html` directly in any browser to view it.

## File structure

```
vehical_bussiness/
├── index.html     ← the entire proposal (HTML + CSS + JS, ~1,985 lines)
└── CLAUDE.md      ← this file
```

`index.html` was originally named `delhi-cab-proposal.html`; renamed to `index.html`
so GitHub Pages (or any static host) serves it at the site root.

## Page sections (in document order)

1. **Hero** — headline + key stats (₹1.6L/partner, ₹970/mo Y1 return, 5 cars Y3).
2. `#opportunity` (01/06) — market size, online-booking %, CNG fuel savings.
3. `#car` (02/06) — **vehicle choice: Maruti WagonR Tour CNG** (~₹7–7.5L, 34 km/kg).
   Rejects Alto (too small), Dzire (pricier), Innova (too costly to start).
4. `#ev` (02B · ALTERNATIVE) — **EV-vs-CNG comparison** (Tata Xpres-T EV). Added later.
   Head-to-head table, cash-flow delta, 4 EV-specific risk cards, CNG-vs-EV verdict.
5. `#investment` (03/06) — ₹46K/partner upfront, ₹6L loan, EMI ₹12,450/mo, bank options.
6. `#profit` (04/06) — monthly P&L: ₹96K revenue, ₹4,850 net (₹970/partner), 2-shift model.
7. Growth plan (05/06) — 1 car (Y1) → 8 cars (Y5).
8. `#licenses` (06/06) — permits, licenses, document checklists.
9. `#timeline` — 30-day launch roadmap.
10. Risks — driver, accident, app commission, partner disputes.
11. `#models` — 3 operation models (Own Driver / Own Driver+Incentive / Rent-to-Driver).
12. Closing + footer.

> Note: page numbers are hand-written labels (`01/06` … `06/06`). The EV section uses
> `02B · ALTERNATIVE` to avoid renumbering the rest. If you add a numbered section,
> either keep this "letter suffix" style or renumber every `.page-num` consistently.

## Key facts / numbers (so you don't have to re-derive them)

- **All figures are planning estimates**, framed as such in the document. CNG/EV prices
  and the Delhi EV Policy change over time — flag estimates and tell the user to confirm
  live prices with a dealer rather than inventing precise current values.
- CNG running cost ≈ ₹2.2/km; EV ≈ ₹1.0/km (home/depot charging).
- EV (Tata Xpres-T) is ~₹9,000/mo cheaper to run but EMI is ~₹7,250/mo higher → net
  ≈ +₹1,750/mo **only if it covers full daily km**. The core EV risk is **range vs the
  2-shift, 200 km/day model** — a charging car earns ₹0.
- Loan/SSH/identity details are in the **Git & hosting** section below.

## Design system (match this when editing — keep edits visually consistent)

Defined as CSS custom properties in `:root` at the top of `index.html`:

| Token | Value | Use |
|---|---|---|
| `--gold` / `--gold-light` | `#C9A84C` / `#E8C97A` | primary accent, headings, highlights |
| `--dark` / `--dark2` / `--dark3` / `--dark4` | `#0A0A0F` → `#22222E` | backgrounds (cards use `--dark2`) |
| `--white` | `#F5F3EE` | body text |
| `--muted` | `#8A8A9A` | secondary text |
| `--green` / `--red` / `--accent` | `#4CAF84` / `#E05A5A` / `#5B8CFF` | income/expense/info |

- **Fonts:** `Playfair Display` (serif headings), `DM Sans` (body), `DM Mono` (numbers/specs).
- **Reusable classes:** `.section`, `.section-label`, `.section-title`, `.section-desc`,
  `.scale-table` (comparison tables), `.risk-grid`/`.risk-card`, `.car-card`, `.pnl-*`,
  `.page-num`, `.divider`, `.fade-up` (add this class to make an element animate in on scroll).
- **Currency** is Indian Rupee `₹`, lakh notation (`₹7.5 L`, `₹1,60,000`).
- Layout is responsive; `@media (max-width: 768px)` collapses grids to single column.

### Editing conventions
- Keep everything in the **one file** — do not split CSS/JS out or add a build step.
- Reuse existing classes/tokens; avoid introducing new colors or fonts.
- New scroll-animated blocks need `class="fade-up"` to be observed by the script.
- Sections are separated by `<div class="divider"></div>`.

## Git & hosting

- **Remote:** `origin` → `git@dvaitai:DvaitAI-tech/vehical_bussiness.git`
  - Uses the SSH host alias **`dvaitai`** from `~/.ssh/config` (key `~/.ssh/git_dvaitAi`).
    The machine has 3 GitHub identities; this repo MUST use the `dvaitai` alias, not a
    raw `github.com` URL, so the correct key is selected.
- **Commit identity (repo-local, not global):** `DvaitAI <nk.dvaitai@gmail.com>`.
- **Default branch:** `master`.
- **Hosting status:** repo is **private**. GitHub Pages does **not** serve from a private
  repo on the free plan. Options discussed: keep private + open locally; private link with
  password via Netlify/Cloudflare Pages; or make the repo public for free GitHub Pages.
  Decision still open — confirm with the user before publishing anything outward-facing.
- Push is performed by the user (they manage the branch). Don't push unless asked.

## Working norms
- Commit messages on this repo end with the project's standard `Co-Authored-By` trailer.
- This is a confidential business proposal with partner financials — treat outward-facing
  actions (publishing, sharing links) as needing explicit confirmation.
