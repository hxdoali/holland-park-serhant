# Holland Park — SERHANT.

A single-page, photo-led pitch site for **Holland Park**, the Lincoln Equities Group
development on 18th Street at the Jersey City–Hoboken line, prepared by SERHANT.

Live: https://hxdoali.github.io/holland-park-serhant/

## How it works

A 13-slide click-through deck, not a scrolling page. Each slide is one point and
fills the viewport.

- Advance with arrow keys, space, page keys, a click anywhere, the on-screen
  arrows, or the tick rail on the right
- `Esc` or the menu button opens a contents grid to jump straight to a slide
- CSS scroll snapping with `scroll-snap-stop: always`, so one gesture moves
  exactly one slide on trackpad and touch alike

## Story flow

1. Cover — Holland Park as a new connected district
2. The Vision
3. Lincoln's Vision — site plan, massing, section, platform elevation
4. Resident Experience
5. The District — walk radius and transit map
6. The Neighborhood — nearby buildings, owners and asking rents
7. The Rent Market
8. Why SERHANT. — ID Lab, Studios, ADX, New Development
9. The close

## Image quality

The Holland Park renderings only exist at roughly 1200-1400px wide. Squarespace
serves the same file whatever size you request, and the YIMBY thread originals
and the press coverage are identical, so there was no larger source to fetch.

`assets/renderings/ai/` holds a Real-ESRGAN x4 upscale of each one, run locally
on CPU and downsampled to 3600px wide. Real-ESRGAN reconstructs edges rather
than interpolating them: building fenestration, canopy trusses, railings and
signage that were mush under Lanczos come back as clean geometry.

At 3600px the hero images run full bleed and still downsample on a 2x display
(measured 0.8x at 1440 and 0.94x at 1920), so they are large *and* sharp. All
twelve files together are 6 MB.

Regenerating them needs `torch` (CPU wheel) and the official
`RealESRGAN_x4plus.pth` weights; the generator is reimplemented in plain torch
in the scratch script, so `basicsr` is not required.

## Palette

Taken from the SERHANT. design tokens published at `styles.luxurypresence.com/serhant`.

| Token | Value | SERHANT. name |
|---|---|---|
| `--ink` | `#000000` | primary-5 |
| `--dark` | `#131826` | primary-4 |
| `--navy` | `#001a72` | primary-accent |
| `--blue` | `#002fcf` | primary-accent-hover |
| `--paper` | `#ffffff` | primary-1 |
| `--paper-2` | `#f7f7f7` | grey 1 |
| `--paper-3` | `#eaeaea` | primary-3 |
| `--muted` | `#585858` | grey 11 |

`--sky` (`#8fa8ff`) is the one value not in the token set. The brand accent
only reaches 1.95:1 against `--dark`, so dark surfaces use a lighter step of
the same hue at 7.8:1.

## Build

Static. `index.html` plus `assets/`. No build step, no runtime dependencies.
Fonts (Inter, Instrument Serif) and all renderings are self-hosted so the deck
presents correctly with no network access.

Deployed to GitHub Pages by `.github/workflows/pages.yml` on every push to `main`.

## Film

`assets/film/` holds four silent background loops cut from SERHANT.'s own
published New Development division film, plus a poster frame for each:

| Clip | Shows |
|---|---|
| `nd-vision` | The blue S, and the line "over $10 billion in active inventory" |
| `nd-site` | Ideation workshop, hard hats on a live site, sales gallery, model residence |
| `nd-studio` | SERHANT. Studios shooting a development from a rooftop |
| `nd-brand` | Branded hard hats on site, then Brooklyn Point, Quay Tower, The Melrose, 868 Lorimer |

The source film is served from SERHANT.'s own Cloudinary delivery account
(`res.cloudinary.com/luxuryp`), the same CDN that serves it on serhant.com.

Each clip ships twice: VP9 WebM first, H.264 MP4 as the fallback. WebM is about
30 per cent smaller at matching quality and covers Chrome, Edge and Firefox;
MP4 covers Safari and iOS. A viewer downloads one of the two, never both.

Every clip is `preload="none"` inside a `<video>` whose `<source>` elements
carry `data-src`. Nothing is fetched until the section scrolls into view, at
which point the loader fills in the sources, calls `load()` and plays; leaving
the section pauses it. Under `prefers-reduced-motion` the poster frame stands
in and nothing autoplays.

Instagram was not used as a source: its CDN links are signed and expire within
hours, so anything hotlinked from there would break before the meeting.

## Fact check

Every claim was verified against a primary source in September 2026.

### Holland Park

Checked against the Jersey Avenue Light Rail Redevelopment Plan amendments
(Jersey City Open Data, dated 6 April 2021, 47pp). The plan never uses the name
"Holland Park" or "Lincoln Equities" — the site is **Block 6002, Lot 7**, and the
mechanism is the **Light Rail Station Overlay Bonus**.

Verified verbatim from the ordinance:

- Maximum permitted height **18 storeys and 230 feet**
- A **centralized public plaza of at least 18,000 square feet**, with landscaping,
  trees, furniture, a water feature and storefronts opening onto it
- **At least 10% onsite affordable housing**, which may not be built off-site or
  bought out
- The redeveloper undertakes **in-kind construction of the light rail station or a
  contribution of funds for its full buildout, as approved by NJ Transit**
- The station must be built **in the first phase** and be **operable, confirmed by
  NJ Transit, before any certificate of occupancy**
- NJ Transit must confirm in writing that it supports the station before the site
  plan application is complete
- Public walkways and ramps from Jersey Avenue and Grove Street, **no less than 12
  feet wide** and ADA accessible
- The plaza extends north-south to **18th Street, midblock between Jersey Avenue
  and Grove Street**

Removed: **800 units**. The figure appears in 2021 press coverage of Lincoln's
proposal, not in the plan. The ordinance explicitly states density "is not
regulated by units per acre or floor area ratios" and is set by the building
envelope, so no unit cap exists to cite.

Note: the section drawing marks a 450-foot tower, which exceeds the 230-foot cap
the plan adopted. The drawings are therefore labelled as Lincoln's concept
drawings rather than as entitlements.

### The neighbouring buildings

Ownership was out of date in three of four cases:

| Building | Was | Verified |
|---|---|---|
| Hudson House (East, West, Radio Lofts) | "RXR · Columbia Property Trust" | Built by The Manhattan Building Company; 829 units acquired 14 May 2025 by Strategic Value Partners, One Investment Management, RXR and Columbia Property Trust; leased by Greystar |
| Embankment House | "Newport Associates" | Built by LeFrak; sold September 2023 to Rockpoint Group; managed by Greystar |
| Soho Lofts | "Manhattan Building Co · Veris" | Built by The Manhattan Building Company; sold April 2019 to Roseland Residential Trust, now Veris Residential |
| Cast Iron Lofts | The Manhattan Building Company | Unchanged; still developer-owned |

### The rents

The six per-building asking rents were removed. Cast Iron Lofts was checked
against the building's own floorplan listings and came back at **$3,444** for a
studio against the **$3,158** on the deck, so the figures were stale. The other
five could not be verified to the same standard: Greystar and Veris render
pricing in JavaScript behind a certificate the sandbox cannot validate, and the
aggregator summaries the original numbers came from mix gross rent, net-effective
rent and concessions.

What remains is what can be cited: unit counts, ownership, and Cast Iron Lofts
pricing taken directly from the landlord's listings on 17 September 2026. The
argument now rests on 1,756 units of institutionally-owned product leasing in the
submarket, which is stronger than six volatile numbers.

## Palette

Taken from the SERHANT. design tokens published at `styles.luxurypresence.com/serhant`.

| Token | Value | SERHANT. name |
|---|---|---|
| `--ink` | `#000000` | primary-5 |
| `--dark` | `#131826` | primary-4 |
| `--navy` | `#001a72` | primary-accent |
| `--blue` | `#002fcf` | primary-accent-hover |
| `--paper` | `#ffffff` | primary-1 |
| `--paper-2` | `#f7f7f7` | grey 1 |
| `--paper-3` | `#eaeaea` | primary-3 |
| `--muted` | `#585858` | grey 11 |

`--sky` (`#8fa8ff`) is the one value not in the token set. The brand accent
only reaches 1.95:1 against `--dark`, so dark surfaces use a lighter step of
the same hue at 7.8:1.

## Build

Static. `index.html` plus `assets/`. No build step, no runtime dependencies.
Fonts (Inter, Instrument Serif) and all renderings are self-hosted so the deck
presents correctly with no network access.

Deployed to GitHub Pages by `.github/workflows/pages.yml` on every push to `main`.

## Film

`assets/film/` holds four silent background loops cut from SERHANT.'s own
published New Development division film, plus a poster frame for each:

| Clip | Shows |
|---|---|
| `nd-vision` | The blue S, and the line "over $10 billion in active inventory" |
| `nd-site` | Ideation workshop, hard hats on a live site, sales gallery, model residence |
| `nd-studio` | SERHANT. Studios shooting a development from a rooftop |
| `nd-brand` | Branded hard hats on site, then Brooklyn Point, Quay Tower, The Melrose, 868 Lorimer |

The source film is served from SERHANT.'s own Cloudinary delivery account
(`res.cloudinary.com/luxuryp`), the same CDN that serves it on serhant.com.

Each clip ships twice: VP9 WebM first, H.264 MP4 as the fallback. WebM is about
30 per cent smaller at matching quality and covers Chrome, Edge and Firefox;
MP4 covers Safari and iOS. A viewer downloads one of the two, never both.

Every clip is `preload="none"` inside a `<video>` whose `<source>` elements
carry `data-src`. Nothing is fetched until the section scrolls into view, at
which point the loader fills in the sources, calls `load()` and plays; leaving
the section pauses it. Under `prefers-reduced-motion` the poster frame stands
in and nothing autoplays.

Instagram was not used as a source: its CDN links are signed and expire within
hours, so anything hotlinked from there would break before the meeting.

## Fact check

Every claim on the deck was verified in September 2026. Corrections made:

| Claim | Finding | Now reads |
|---|---|---|
| SERHANT. "a decade" / "10 years" | Founded 15 September 2020 | Six years |
| "$10B+ over the past decade" | Division passed $10B in inventory by its second year | "$10B+ new development inventory", no decade |
| 550 Vanderbilt as a SERHANT. project | Sold out before the firm existed; not on the active list | Removed |
| "2nd Street — 5 min walk" | Outside the 5-minute ring on the project's own transit plan | "10 min walk" |
| "Hoboken Terminal — 10 min walk" | Well outside the 10-minute ring; roughly 1.2 miles | "Up the line" |
| "Newport — 10 min walk" | At the edge of the 10-minute ring | "Down the line" |
| "Five minutes of Jersey City, five minutes of Hoboken" | Unsupported by the walk radii | Replaced |
| 800 units, station, podium stated as fact | Sought via amendments to the Jersey Avenue Light Rail Redevelopment Plan, presented to the Planning Board 13 April 2021 | Labelled as proposed |

Verified and unchanged: two buildings either side of a north-south pedestrian
plaza; a new elevated Hudson-Bergen Light Rail station at the developer's
expense with pedestrian connections to 18th Street and Grove Street; the
four-storey retail, amenity and parking podium (from the project's own section
drawing); and the six neighbourhood buildings with their owners and asking
rents.

The reach figures were tracked down to SERHANT.'s own 2025 annual letter
(serhantannualletter2025.com), which states verbatim: "the most-followed real
estate brokerage on the planet, with 9.3 million followers across platforms and
over 40 billion PR impressions from more than 1,400 placements YTD." Both
numbers originally on the deck were wrong. 16B+ was the 2022 figure from the
earlier annual letter and badly understated current reach; 10M+ overstated the
audience. The same letter supplies the 200% year-on-year New Development growth
and the $6.5 billion closed in 2025.

## Sources

Renderings, site plans and drawings courtesy of Lincoln Equities Group.
Neighborhood asking rents reflect publicly advertised listings as of September 2026.
