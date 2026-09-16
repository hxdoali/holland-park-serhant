# Holland Park — SERHANT.

A single-page, photo-led pitch site for **Holland Park**, the Lincoln Equities Group
development on 18th Street at the Jersey City–Hoboken line, prepared by SERHANT.

Live: https://hxdoali.github.io/holland-park-serhant/

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

## Sources

Renderings, site plans and drawings courtesy of Lincoln Equities Group.
Neighborhood asking rents reflect publicly advertised listings as of September 2026.
