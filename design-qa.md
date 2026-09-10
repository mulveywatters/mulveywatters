# Ardu image regression design QA

## Comparison target

- source visual truth paths:
  - `/var/folders/55/xy3x1mgd4znds6ncpg3d8y5c0000gn/T/codex-clipboard-1010aac2-f648-471c-a571-e065f2517eea.png`
  - `/var/folders/55/xy3x1mgd4znds6ncpg3d8y5c0000gn/T/codex-clipboard-454f34f7-0bf4-40d1-b817-a6c7cc59678b.png`
- implementation screenshot paths:
  - `/Users/stevenmulveywatters/Documents/Codex/2026-09-03/referenced-chatgpt-conversation-this-is-an/outputs/site-polish-audit/home-ardu-fixed.png`
  - `/Users/stevenmulveywatters/Documents/Codex/2026-09-03/referenced-chatgpt-conversation-this-is-an/outputs/site-polish-audit/ardu-habits-fixed.png`
  - `/Users/stevenmulveywatters/Documents/Codex/2026-09-03/referenced-chatgpt-conversation-this-is-an/outputs/site-polish-audit/home-ardu-fixed-mobile.png`
  - `/Users/stevenmulveywatters/Documents/Codex/2026-09-03/referenced-chatgpt-conversation-this-is-an/outputs/site-polish-audit/ardu-habits-fixed-mobile.png`
- routes: `/` and `/work/ardu/`
- state: fully loaded, default theme, relevant section in view

## Dimensions and normalization

- supplied regression captures: 2378 x 1856 pixels including browser chrome
- desktop implementation captures: 1440 x 1000 pixels at a 1440 x 1000 CSS viewport
- mobile implementation captures: 390 x 844 pixels at a 390 x 844 CSS viewport
- source and implementation were compared as focused content regions because the supplied captures include browser chrome and use a different display density.

## Full-view comparison evidence

The supplied regression captures and corrected browser captures were opened together. The homepage now uses the original approved PNG source and renders at its natural 1206:2622 aspect ratio without distortion or horizontal overflow. The Habits artwork is restored to the approved phone-only desktop treatment: promotional wording embedded above the device is outside the crop, while the centered two-column relationship with the site copy is preserved.

## Focused region comparison evidence

- Homepage Ardu phone: the compressed-looking presentation in the supplied capture is absent in the corrected capture; the phone and UI retain their intended proportions.
- Habits section: the embedded promotional heading is completely excluded and the frame focuses on the phone UI. The site heading and paragraph remain vertically centered alongside the image.
- Mobile: both sections preserve their established linear layout and have zero horizontal overflow.

## Required fidelity surfaces

- fonts and typography: unchanged from the approved Instrument Serif and DM Sans treatment.
- spacing and layout rhythm: surrounding grids, gaps, section heights and text alignment remain unchanged; only image source treatment and crop anchoring were corrected.
- colors and visual tokens: unchanged.
- image quality and asset fidelity: restored original PNG assets for the two affected visuals; no generated or approximate replacements are used.
- copy and content: unchanged.

## Interaction and accessibility checks

- desktop checked at 1440 x 1000
- mobile checked at 390 x 844
- horizontal overflow: none on either affected route
- browser console warnings and errors: none
- Astro production build: passed

## Findings and comparison history

- P1 resolved: homepage Ardu phone looked enlarged/compressed after the optimisation pass. Restored the original PNG source treatment and verified natural aspect ratio in-browser.
- P2 resolved: Habits artwork exposed duplicated promotional wording rather than using the previously approved phone-only crop. Restored the close device crop and verified that the embedded heading is no longer visible.
- Post-fix comparison found no remaining P0, P1 or P2 issues in the affected regions.

## Follow-up polish

None required for these regressions.

final result: passed
