# Resume Template

One-page resume/CV skeleton with reusable commands for contact information,
entries, publications, and skills.

## Build

Compile from the repository root:

```bash
pdflatex resume/main.tex
```

Or compile from this directory:

```bash
pdflatex main.tex
```

The template uses `fontawesome5`, `roboto`, `tabularx`, `titlesec`, `enumitem`,
`hyperref`, `geometry`, and `parskip`.

## Structure

The main reusable commands are defined near the top of `main.tex`:

| Command | Purpose |
| --- | --- |
| `\resumeHeader{name}{email}{github-url}{website-url}` | Builds the centered name and contact block. |
| `\resumeEntry{title}{date}{subtitle}{items}` | Creates a dated entry. Use `{}` for `items` when there are no bullets. |
| `\publication{...}` | Formats a hanging-indent publication line. |
| `\skillrow{category}{skills}` | Adds one skills row to the `tabularx` skills table. |

Example entry with bullets:

```tex
\resumeEntry
  {Role Title}
  {Start Date -- End Date}
  {Organization, Location}
  {
    \item Describe a responsibility, accomplishment, or impact.
    \item Describe another responsibility, accomplishment, or impact.
  }
```

Example entry without bullets:

```tex
\resumeEntry
  {Institution Name}
  {Start Date -- End Date}
  {Degree or program}
  {}
```

## Customization

- Edit section names or remove sections directly in `main.tex`.
- Adjust margins with the `geometry` package line.
- Adjust section spacing with `\titlespacing*{\section}{...}`.
- Add or remove contact fields by editing `\resumeHeader`.
