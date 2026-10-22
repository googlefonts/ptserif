# PT Serif

No source of this family was ever published: the fonts Google Fonts ships
were its only form. The sources in `sources/` were converted from those
fonts with [babelfont-rs](https://github.com/felipesanches/babelfont-rs/tree/2026-10-22), and
build with [gftools-builder](https://github.com/simoncozens/gftools-rust)
and fontc.

The fonts they were converted from remain in the git history.

How these sources were checked against the released fonts (the tools, this family's plan and the logs): https://github.com/felipesanches/gf-source-modernization.

## Known differences from the released fonts

These sources rebuild the fonts Google Fonts ships, except for the following, which were reviewed and deliberately left as they are:

- The releases kern through a GPOS kern feature and also carry a legacy `kern` table (20730 to 21078 pairs per style). Shapers read the GPOS feature, which these sources keep; the legacy table, read only by software without GPOS support, is not carried.
- The released fonts are hinted (TrueType instructions; googlefontdirectory-hg kept ParaType's own TTFs, ofl/ptserif/src/PTF55F.ttf and its siblings, at 52f780bc9d19). These sources carry no TrueType instructions, so the build is hinted by ttfautohint: the outlines, spacing and layout are the release's, its rendering at small sizes under a TrueType interpreter is not. Hinting is not compared by the gates.
