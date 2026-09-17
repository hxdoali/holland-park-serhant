# Holland Park — SERHANT.

A single-page, photo-led pitch site for **Holland Park**, the Lincoln Equities Group
development at Jersey Avenue and Grove Street on the Jersey City–Hoboken line,
prepared by SERHANT.

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

1. **Holland Park** — the cover, a new connected district
2. **The Vision** — the site, and what the overlay bonus permits
3. **The Public Realm** — the neighbourhood at eye level
4. **The Plan** — Lincoln's site plan, massing, section, platform elevation
5. **A Day Here** — the resident experience
6. **The District** — aerial, walk-radius map, transit
7. **The Market** — who owns the submarket and what it leases for
8. **Why SERHANT.** — the New Development division in numbers
9. **Selected Work**
10. **The Audience** — reach
11. **The Engine** — ID Lab, Studios, ADX
12. **Proven Results**
13. **The Close**

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

Every claim on the deck was verified against a primary source in September 2026.

### Holland Park

Checked against the **Jersey Avenue Light Rail Redevelopment Plan as adopted —
"Amended May 26, 2021 – Ord. 21-035"** (the version the Division of City Planning
publishes on Jersey City Open Data, 39pp). An earlier pass used the 6 April 2021
draft amendments; the adopted text was pulled and every figure re-checked against
it. They match.

The plan never uses the name "Holland Park" or "Lincoln Equities" — the site is
**Block 6002, Lot 7**, and the mechanism is the **Light Rail Station Overlay
Bonus**. The plan area is about 52 acres in northern Downtown Jersey City, with
Hoboken immediately to the north and 14th Street, exiting the Holland Tunnel, to
the south.

Verified verbatim from the adopted ordinance:

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
- The bonus is **conditional**: it applies only to a Designated Redeveloper under a
  recorded Redevelopment Agreement with the JCRA. Without that, the site falls back
  to the ordinary High Rise District standards.

**The site.** Block 6002, Lot 7 is **677 Grove Street, 3.38 acres, assessed as
vacant land**, and its tax mailing address is One Meadowlands Plaza, Suite 803,
East Rutherford — Lincoln Equities Group's own office. The station lot next door,
Block 6002 Lot 3, is 866 Jersey Avenue, 1.56 acres. Source: Jersey City parcel
data and the municipal assessment record.

**The locator was corrected.** The deck opened on "18th Street & Jersey Avenue",
the name the project carries in press coverage. The ordinance defines the bonus
area as property "with frontages on at least Jersey Avenue and Grove Street", and
the parcel record puts it on Grove. The cover now reads **Jersey Avenue & Grove
Street**; 18th Street is where the plaza connects, not where the site fronts.

**800 units stays off the deck, and so does 1,200.** The 800 figure comes from
February 2021 press coverage of Lincoln's rezoning request, not from the plan. The
1,200 figure comes from a Cushman & Wakefield capital markets listing for roughly
$49.3 million (64% LTV) of bridge financing for the recapitalisation and
predevelopment of Holland Park — but that listing anticipated a **Spring 2016**
groundbreaking, so it predates the 2021 rezoning by five years and is stale. The
adopted ordinance is explicit that density "is not regulated by units per acre or
floor area ratios" and is set by the building envelope. No unit count is citable,
so none is cited.

**Rebuild by Design.** The nearly $300 million flood-protection project on the
Hoboken–Jersey City line was re-engineered to preserve this station: Greenman-
Pedersen recommended micropile foundations alongside the resist structure, and the
State committed roughly $997,500 — under 0.5% of the project budget — to cover it,
after which Jersey City released the remaining easements (Hudson County View,
2024). The adopted ordinance carries the matching rule: the setback along the lot
line with Block 6002 Lot 3 is "to be determined by NJ Transit" and exists to
"ensure an appropriate buffer between development and the Rebuild by Design resist
structure." This is why the deck can say the station is buildable rather than
merely drawn.

**The concept drawings check out.** The site plan is labelled by Lincoln with
"NEW HOLLAND PARK LIGHT RAIL STATION", "PROPOSED PEDESTRIAN AND BIKE CROSSING" to
the north-west and "PROPOSED ERIE STREET CONNECTION" to the south, which is what
the deck describes. Note that the section drawing marks a 450-foot tower, which
exceeds the 230-foot cap the plan adopted — so the drawings are labelled as
Lincoln's concept drawings throughout, never as entitlements.

### The neighbouring buildings

Ownership was out of date in three of four cases:

| Building | Was | Verified |
|---|---|---|
| Hudson House (East, West, Radio Lofts) | "RXR · Columbia Property Trust" | Built by The Manhattan Building Company; 829 units acquired 14 May 2025 by Strategic Value Partners, One Investment Management, RXR and Columbia Property Trust; leased by Greystar |
| Embankment House | "Newport Associates" | Built by LeFrak; sold September 2023 to Rockpoint Group; managed by Greystar |
| Soho Lofts | "Manhattan Building Co · Veris" | Built by The Manhattan Building Company; sold April 2019 to Roseland Residential Trust, now Veris Residential |
| Cast Iron Lofts | The Manhattan Building Company | Unchanged; still developer-owned |

Added: **LeFrak's Newport Associates Development Company holds final major site
plan approval (Planning Board, October 2021) for two ten-storey buildings at 650
and 659 Grove Street — 247 apartments, 11,050 sq ft of retail and 34,346 sq ft of
office.** 659 Grove Street is Block 6002 Lot 8, directly abutting the Holland Park
parcel; the ordinance sets a 3-foot setback along that shared line. Lincoln's own
site plan labels both flanking parcels "LEFRAK DEVELOPMENT". Construction status
is not claimed: the only reports of site activity are from a forum thread, which is
not a source.

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

### SERHANT.

| Claim | Finding | Now reads |
|---|---|---|
| SERHANT. "a decade" / "10 years" | Founded 15 September 2020 | Six years |
| "$10B+ over the past decade" | Division passed $10B in inventory by its second year | "$10B+ new development inventory", no decade |
| 550 Vanderbilt as a SERHANT. project | Sold out before the firm existed; not on the active list | Removed |
| "16B+ impressions" | The 2022 figure; badly understates current reach | 40B+ from 1,400+ placements |
| "10M+ audience" | Overstated | 9.3M followers |
| "2nd Street — 5 min walk" | Outside the 5-minute ring on the project's own transit plan | "10 min walk" |
| "Hoboken Terminal — 10 min walk" | Roughly 1.2 miles, well outside the ring | "Up the line" |
| "Newport — 10 min walk" | At the edge of the 10-minute ring | "Down the line" |
| "Five minutes of Jersey City, five minutes of Hoboken" | Unsupported by the walk radii | Replaced |

The reach figures were tracked down to SERHANT.'s own 2025 annual letter
(serhantannualletter2025.com), which states verbatim: "the most-followed real
estate brokerage on the planet, with 9.3 million followers across platforms and
over 40 billion PR impressions from more than 1,400 placements YTD." The same
letter supplies the 200% year-on-year New Development growth and the $6.5 billion
closed in 2025.

## Sources

- Jersey Avenue Light Rail Redevelopment Plan, amended 26 May 2021, Ord. 21-035 —
  Jersey City Open Data, Division of City Planning
- Jersey City parcel and assessment records, Block 6002
- Hudson County View, on Rebuild by Design and the 18th Street station, 2024
- Jersey Digs, on the February 2021 Holland Park rezoning request and on the
  650 / 659 Grove Street approvals
- SERHANT. 2025 annual letter
- Renderings, site plans and drawings courtesy of Lincoln Equities Group
- Neighborhood asking rents reflect publicly advertised listings as of September 2026
