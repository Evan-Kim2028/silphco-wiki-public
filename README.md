# silphco-wiki-public

Public slice of the private leftover catalog: generated HTML with prices already in
the page. No vault, no freezes, no emit scripts. **Prices work offline** — open it once on
wifi and every number keeps working on a convention floor with no signal.

- [Scan a card](scan.html) — type the collector number, get the price. Start here at a show; it needs no pictures, so it works fully offline.
- [The whole board](set-macro.html) — every mid-era set, which ones already ran
- [Leftovers](mid-sleeve-leftovers.html) · [Chase leftovers](chase-sleeve-leftovers.html) · [Show deals](show-deals.html)

## Reading a price

Prices are a **range**, never a single number, and every one carries a colour for
how much to trust it:

| | Means |
|---|---|
| green | Real sales — 5 or more behind the number |
| yellow | Few sales — 1 to 4, a rough guide |
| red | Estimated — no sales at all, a computer guess |
| purple | Sales and listings disagree — pay the listing price |
| grey | Not checked — outside the checked list |

Prices come from two independent sources: past **sales**, and what the card is
**listed** at right now. Where both exist they agree within 50% about three times
in four, which is the main reason to trust either. Where they disagree the page
says so and tells you to go with the listing.

## What is in this repo

Everything the pages need, so nothing is fetched at a show:

| Path | |
|---|---|
| `*.html` | the pages, with all prices already inline |
| `img/reverse/` | the handful of reverse-holo scans we host ourselves |
| `data/` | the same numbers as JSON and CSV — `cards.json`, `cards.csv`, `sets.json`, `meta.json` |
| `sw.js` | service worker; precaches all of the above for offline use |

`data/meta.json` names the freeze the snapshot came from and carries the field
descriptions. 1,381 prints across 712 cards.

**Card pictures load from the internet** (pokemontcg.io and PriceCharting) and are
cached as you browse. Caching all of them would be ~390 MB, so they are online-only
in practice. Scan, the set board and this page carry no images at all and work with
no signal; on the three browse pages the prices still work offline, only the
pictures need a connection.

Regenerate from the private `silphco-wiki` with `bash scripts/build_pages.sh`, then
copy these files. GitHub Pages serves the repo root.
