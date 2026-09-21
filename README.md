# Holland Park × SERHANT.

A cinematic, 12-section partnership pitch for Lincoln Equities Group.

Live: https://hxdoali.github.io/holland-park-serhant/

## Story

The first eight sections make the case for SERHANT. The closing four introduce
our Holland Park research and invite Lincoln to share its vision in the meeting.

1. Big vision. Meet SERHANT.
2. The momentum: firmwide volume and New Development growth
3. The audience: brand following and reported media reach
4. Selected New Development projects
5. Interactive capabilities: ID Lab, Studios, ADX, New Development
6. Creative direction and campaign formats
7. A proposed launch plan
8. Built around Lincoln
9. What we have learned about Holland Park
10. Interactive resident-story concepts
11. What this tells us, with an optional neighborhood research appendix
12. Meeting discussion: vision, milestones and partnership goals

The close is intended for an in-person meeting. There is no email form or
scheduling integration.

## Controls and accessibility

- Scroll through the presentation; taller slides can expand to fit their content.
- Left/right arrows or Page Up/Page Down move between sections.
- Up/down arrows and space retain native scrolling.
- The contents button or M key opens the section index. Escape closes dialogs.
- The rail and bottom arrows provide additional navigation.
- Tabs support left/right arrows, Home and End, with a single focusable selected tab.
- Native dialogs provide modal focus behavior; keyboard shortcuts do not intercept
  links, buttons, details, form fields or map controls.
- Motion preference disables automatic video loading/playback. Play/pause controls
  are available, and off-screen/background videos pause.
- Deep links use section IDs; #serhant opens the pitch and #holland-park opens research.

## Build and deployment

Static `index.html` with local fonts, poster images, films and renderings. There is
no build step. GitHub Pages deploys through `.github/workflows/pages.yml` on main.

The optional map loads Leaflet 1.9.4 from unpkg with integrity checks and uses
OpenStreetMap tiles with attribution. If either service is unavailable, property
addresses, source links and rent details remain accessible. Map locations are
approximate neighborhood orientation, not boundaries or entrances.

## Sources and scope — reviewed September 21, 2026

### SERHANT.

- https://www.serhantannualletter2025.com/ — $6.5B closed firmwide sales volume was
  reported year to date in December 2025, not as a finalized annual total.
  The same letter reports 200% New Development growth year over year and 40B+
  PR impressions from 1,400+ placements year to date. It does not identify the
  specific financial metric underlying the division's growth percentage.
- https://serhant.com/blog/serhant-expands-across-california — the April 14, 2026
  announcement, published May 14, reports more than 10M followers.
- https://serhant.com/new-development and https://serhant.com/developers — service
  descriptions and current portfolio links. Named projects do not imply an
  identical scope, a guaranteed result or a rental comparable for Holland Park.

Company metrics retain their reporting dates and scope. Followers and media
impressions are not promised project exposure. Holland Park deliverables, working
rhythms, budgets, launch timing and team assignments are proposals for discussion.

The supplied marketing proposal informed the service narrative. Its historical
2023 metrics were not presented as current figures.

### Holland Park

- https://www.lincolnequities.com/holland-park — published project concept.
- https://njparcels.com/property/0906/6002/7 — 677 Grove Street, Block 6002 Lot 7,
  3.38 acres. A tax mailing address is not treated as independent title evidence.
- https://data.jerseycitynj.gov/explore/assets/jersey-avenue-light-rail-redevelopment-plan/
  — the 2021 overlay framework, also discussed in the supplied research report.
  Conditional planning provisions are separated from the project's current
  approvals, program and delivery schedule, which are questions for Lincoln.

No current unit count, construction start or station delivery date is asserted.
Resident-story tabs are explicitly illustrative creative concepts. Existing
published renderings are used as concepts; the AI-upscaled assets remain in the
repository but are not used in this revision. Old concept drawings depicting a
450-foot structure are not presented as the approved design.

### Neighborhood appendix

Six locations: Radio Lofts, Hudson House East, Hudson House West, Soho Lofts,
Cast Iron Lofts and Embankment House. Each has source-linked developer/acquisition
context, address, rent basis and snapshot date. Current legal title is not inferred
from a manager's identity or a historical press release.

- Soho's headline asking rents were refreshed September 21 from Veris Residential.
- Cast Iron CIL2_05L was refreshed September 21 from its direct leasing-page data:
  $3,613–3,838 base; $3,620.14–3,845.14 published monthly totals. Search-engine
  cached text had older figures; the direct page was used.
- Embankment E-A1: $3,315 base / $3,408 published total for a 12-month term,
  checked September 21.
- Hudson House's numeric listings could not be refreshed. The September 14
  snapshots are retained with an explicit date and refresh limitation, plus a
  link to current availability. They are not represented as September 21 quotes.

## Media

Inter and Instrument Serif are self-hosted under the SIL Open Font License 1.1.
Film clips and posters in `assets/film/` are existing excerpts from SERHANT.'s
published New Development film. This revision uses nd-site, nd-studio and nd-brand;
nd-vision, with its older inventory headline, is not shown.

Videos lazy-load when their section is visible. WebM is preferred with MP4 as a
fallback. Reduced-motion viewers initially see the poster and may opt into playback.
