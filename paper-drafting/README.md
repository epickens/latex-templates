# Paper Drafting Template

General-purpose rough drafting template for papers.

This template is based on the Carleton Essay Template from Overleaf:
https://www.overleaf.com/latex/templates/carleton-essay-template/tzxprxwxxygb

The original style file credits Andrew Gainer-Dewar and is licensed under the
Creative Commons Attribution 4.0 International License. This version keeps the
basic paper formatting and adds rough-drafting helpers for comments, line
numbers, section stubs, and placeholder figures and tables.

## Build

Compile from this directory so `ccpaper.sty` is on LaTeX's search path:

```bash
pdflatex ccpaper.tex
```

Or use `latexmk`:

```bash
latexmk -pdf ccpaper.tex
```

`latexmk` writes generated files to `build/`.

## Modes

The template exposes common toggles near the top of `ccpaper.tex`, before
`custom_defs.tex` is loaded:

```tex
\newif\ifdraft
\drafttrue

\newif\ifdyslexic
\dyslexicfalse
% \dyslexictrue
```

Use these combinations for common workflows:

| Workflow                      | Draft Toggle  | Dyslexia Toggle  | Compiler   |
| ----------------------------- | ------------- | ---------------- | ---------- |
| Rough draft                   | `\drafttrue`  | `\dyslexicfalse` | `pdflatex` |
| Clean shareable draft         | `\draftfalse` | `\dyslexicfalse` | `pdflatex` |
| Dyslexia-friendly draft       | `\drafttrue`  | `\dyslexictrue`  | `xelatex`  |
| Clean dyslexia-friendly draft | `\draftfalse` | `\dyslexictrue`  | `xelatex`  |

Draft mode enables line numbers and displays draft-only comments, TODOs, and
reviewer notes. Final mode hides those draft-only annotations while keeping the
main document text.

## Drafting Helpers

These commands are defined in `custom_defs.tex`:

| Command                                          | Purpose                                                                            |
| ------------------------------------------------ | ---------------------------------------------------------------------------------- |
| `\needcite`                                      | Marks a missing citation.                                                          |
| `\placeholder{...}`                              | Adds a visible TODO placeholder.                                                   |
| `\revise{...}`                                   | Adds a visible revision note.                                                      |
| `\draftnote{...}`                                | Adds a margin TODO note.                                                           |
| `\addtext{...}`                                  | Shows proposed added text in blue during draft mode; keeps the text in final mode. |
| `\removetext{...}`                               | Shows struck-through removed text during draft mode; hides it in final mode.       |
| `\reviewerone{...}` through `\reviewerfive{...}` | Adds color-coded reviewer comments like `<<REVIEWER #1: COMMENT>>`.                |

Figure and table placeholders are also available:

```tex
\figureplaceholder{label}{Box text}{Caption}
\twopanelfigureplaceholder{Panel A caption}{Panel B caption}{Caption}
\basictableplaceholder{Caption}
\landscapetableplaceholder{Caption}
```

Longer drafts can be split into optional files under `sections/`. Uncomment the
matching `\input{sections/...}` line in `ccpaper.tex` when you want to use them.

## Dyslexia Mode

Dyslexia mode uses the project-local OpenDyslexic font files in `fonts/`.

Those files are not included in this release and must be downloaded from https://opendyslexic.org/.

Compile dyslexia mode with XeLaTeX or LuaLaTeX:

```bash
xelatex ccpaper.tex
```

The default font path is `fonts/`, which keeps the template portable and avoids
exposing any local filesystem path. If you want to use fonts from another
location, redefine `\opendyslexicfontpath` before `\input{custom_defs}`:

```tex
\renewcommand{\opendyslexicfontpath}{/path/to/fonts/}
```

If OpenDyslexic is not installed at that path, or if dyslexia mode is compiled
with pdfLaTeX, the document still compiles and emits a warning explaining what
is missing.

For Overleaf, keep the `fonts/` folder in the project, set the compiler to
XeLaTeX, and enable `\dyslexictrue`.
