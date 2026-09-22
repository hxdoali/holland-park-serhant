# Holland Park × SERHANT.

A cinematic, 13-section partnership pitch for Lincoln Equities Group.

Live: https://hxdoali.github.io/holland-park-serhant/

## Story

The first nine sections introduce SERHANT.'s scale, relevant assignments and
proposed development marketing. The closing four bring in Holland Park research
and invite Lincoln to share its vision in the meeting.

1. Big vision. Meet SERHANT.
2. Company momentum, with dated and scoped figures
3. Brand audience and reported media exposure
4. Jersey City and Hoboken: Charlie, One Jones Park, Columbus House
5. New York: Brooklyn Point, Quay Tower, 200 Amsterdam
6. Interactive capabilities: ID Lab, Studios, ADX, New Development
7. Creative direction and the official development marketing reel
8. Interactive marketing phases, proposed deliverables and measures
9. Built around Lincoln
10. What we have learned about Holland Park
11. Interactive resident-story concepts
12. What this tells us, with an optional neighborhood map and research appendix
13. Meeting discussion: vision, milestones and partnership goals

The close is for an in-person meeting. Project cases distinguish the published
service role, development scale and dated results. The supplied proposal informed
the four-phase marketing approach; historical collateral metrics are not passed
off as current. See [FACTS.md](FACTS.md) and the presentation's source links.

## Controls and accessibility

- Scroll through the presentation; taller sections expand to fit their content.
- Left/right arrows or Page Up/Page Down move between sections.
- Up/down arrows and space retain native scrolling.
- The contents button or M key opens the index. Escape closes native dialogs.
- Tabs support left/right arrows, Home and End, with one focusable selected tab.
- Dialogs provide native modal focus behavior. Deck shortcuts leave links,
  buttons, details, videos and map controls alone.
- Reduced motion disables automatic film loading and number animation.
- Films pause off-screen, behind dialogs and in background tabs. The full reel
  loads only after the viewer opens it and uses native play/pause controls.
- Deep links: #serhant, #local-work, #work, #launch and #holland-park.

## Build and deployment

Static index.html; no build step. GitHub Pages deploys main through
.github/workflows/pages.yml. Fonts, project images, film excerpts and renderings
are self-hosted. The full development reel uses the original media source linked
from SERHANT.'s official developers page; it needs a network connection.

The optional map loads Leaflet 1.9.4 from unpkg with integrity checks and uses
OpenStreetMap tiles with attribution. If the map cannot load, all six addresses,
source links and available rent details remain accessible. Pins show approximate
neighborhood locations, not property boundaries or entrances.

## Media

Inter and Instrument Serif are under the SIL Open Font License 1.1.
Film clips and posters in assets/film/ are existing excerpts from SERHANT.'s
published New Development material. This revision displays nd-site and nd-studio.
The older nd-vision inventory headline is not shown.

The six photographs/renderings in assets/projects/ come from the relevant
LCOR or SERHANT. project/listing pages; captions identify their context.
Holland Park renderings remain labeled published concepts. The older AI-upscaled
files in the repository are not used by this presentation.

## Verification

Checked September 21, 2026: HTML/JavaScript structure, local assets, all five tab
groups, keyboard navigation, dialogs, controlled reel loading, reduced motion,
map error fallback, and seven markers using the actual Leaflet library under
jsdom. The computer-use browser runtime failed to start, so these checks are not
a substitute for visual browser/device inspection.
