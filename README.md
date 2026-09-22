# Holland Park × SERHANT.

A cinematic, 14-section partnership pitch for Lincoln Equities Group.

Live: https://hxdoali.github.io/holland-park-serhant/

## Story

The first ten sections introduce SERHANT.'s scale, relevant assignments and
proposed development marketing. The closing four bring in Holland Park research
and invite Lincoln to share its vision in the meeting.

1. Big vision. Meet SERHANT. — with a published development commercial
2. Company momentum, with dated and scoped figures
3. Brand audience and reported media exposure
4. Campaigns in action: development ad, cinematic content, outdoor and local launch
5. Jersey City and Hoboken: Charlie, One Jones Park, Columbus House
6. New York: Brooklyn Point, Quay Tower, 200 Amsterdam, with campaign-film access
7. Interactive capabilities: ID Lab, Studios, ADX, New Development
8. Inside the production, with a four-film campaign cinema
9. How the campaign comes together: four visual marketing phases
10. Built around Lincoln
11. What we have learned about Holland Park
12. Interactive resident-story concepts
13. What this tells us, with a neighborhood map and research appendix
14. Meeting discussion: vision, milestones and partnership goals

The close is for an in-person meeting. Project cases distinguish the published
service role, development scale and dated results. The supplied proposal informed
the four-phase marketing approach; historical collateral metrics are not passed
off as current. See [FACTS.md](FACTS.md) and the presentation's source links.

## Controls and accessibility

- Each slide occupies exactly one viewport, with no vertical scrolling in the deck.
- Longer content flows into screen-sized continuation pages on small displays.
  Previous/next buttons advance pages before changing chapters. Text is retained;
  phones use native text sizes. Desktop layouts use modest fitting when needed.
- Safe-area padding and 44-pixel navigation controls accommodate phone screens.
- The neighborhood dialog starts with six clearly labeled rent cards. Each opens
  unit/plan details above the map on phones, with a return-to-overview button.
- Rent cards distinguish monthly totals from advertised starting rent; the
  six rent sources are the properties’ own leasing pages. Hudson House figures
  use its official published unit data, before promotional concessions.
- Arrow keys, Page Up/Page Down and space advance complete screens. Shift-space
  moves backward. Horizontal touch swipes and mouse wheels also advance screens.
- Resizing, rotating, loading fonts and switching tabs recalculate page breaks.
  Tab focus brings controls on continuation pages into view automatically.
- The contents button or M key opens the index. Escape closes native dialogs.
- Tabs support left/right arrows, Home and End, with one focusable selected tab.
- Dialogs provide native modal focus behavior. Deck shortcuts leave links,
  buttons, details, videos and map controls alone.
- Reduced motion disables automatic film loading and number animation.
- Films pause off-screen, behind dialogs and in background tabs. The campaign cinema
  loads films only on request. Native or official YouTube controls handle playback.
- “Let the visuals lead” hides the talking points while retaining credits and controls.
- Silent background clips use source-resolution desktop files and smaller mobile versions.
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

See [MEDIA.md](MEDIA.md) for original publications, source resolutions, excerpt
intervals and attribution. The campaign assets use actual SERHANT./project work.
No generated footage, mock advertising results or inferred campaign returns are
presented as evidence.

The Brooklyn Point background teaser and development marketing montage preserve
the original files. Other silent excerpts retain the source's 1920-pixel width.
Mobile versions are 960 pixels wide. On-demand films stream from their original
publishers. Quay Tower uses its official YouTube film. These external full-film
players need network access.

Inter and Instrument Serif use the SIL Open Font License 1.1. Holland Park
renderings remain labeled published concepts. The older AI-upscaled repository
files are not used in this presentation.

## Verification

Checked September 21, 2026: HTML/JavaScript structure, local assets, silent-media decoding, mobile renditions, all six tab
groups, keyboard navigation, dialogs, cinema cleanup and lazy loading, reduced motion,
map error fallback, and seven markers using the actual Leaflet library under
jsdom. The computer-use browser runtime failed to start, so these checks are not
a substitute for visual browser/device inspection.

The mobile/rent revision additionally checks all six numeric rent cards, source
and fee labels, detail/overview focus, popup prices, and interaction under eight
viewport configurations from 320 to 820 pixels. These are DOM checks with mocked
geometry, not screenshots or rendered layout tests.

## Viewport fitting verification

Checked September 22, 2026 in isolated headless Chrome: rendered layouts at
1920×1080, 1440×900, 1280×720, 1024×768, 820×1180, 390×844, 320×568 and 844×390.
All chapter/tab states, expanded planning/case notes, and every continuation page
were checked for text outside the viewport. Forward/back traversal, dialog closing,
fixed deck height and zero deck scrolling passed. Desktop and phone screenshots
were inspected. These browser checks supersede the earlier DOM-only layout checks;
physical Safari/iOS devices were not tested. Optional research/source dialogs retain
their own native scrolling.
