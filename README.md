# latex-templates

Reusable LaTeX templates.

## Templates

- `resume/main.tex`: a one-page resume/CV skeleton with reusable commands for
  entries, publications, contact details, and skills. See `resume/README.md`
  for usage notes.
- `paper-drafting/ccpaper.tex`: a paper-drafting template using the local
  `ccpaper.sty` style file. See `paper-drafting/README.md` for attribution and
  template-specific notes.

## Build

Compile the resume template directly with `pdflatex`:

```bash
pdflatex resume/main.tex
```

Compile directory-local templates from their own folder so local style files are
on LaTeX's search path:

```bash
cd paper-drafting
pdflatex ccpaper.tex
```

For documents with citations, run the normal LaTeX/BibTeX sequence or use
`latexmk` if available:

```bash
latexmk -pdf ccpaper.tex
```

The paper template includes a `.latexmkrc` that writes generated files to
`paper-drafting/build/`.

## Paper Drafting Helpers

The paper template includes rough-drafting helpers in
`paper-drafting/custom_defs.tex`.

- Switch between draft and final output with `\drafttrue` or `\draftfalse`.
- Switch dyslexia mode on or off with `\dyslexictrue` or `\dyslexicfalse`.
  When enabled, the template uses the OpenDyslexic LaTeX package if it is
  installed.
- Draft mode enables line numbers and displays comments.
- Use `\needcite`, `\placeholder{...}`, `\revise{...}`, and `\draftnote{...}`
  while drafting.
- Use reviewer comments like `\reviewerone{...}` through `\reviewerfive{...}`.
- Optional section files live in `paper-drafting/sections/`.
- Figure and table placeholders are available via `\figureplaceholder`,
  `\twopanelfigureplaceholder`, `\basictableplaceholder`, and
  `\landscapetableplaceholder`.
