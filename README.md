# Transfer of Status — *Scaling De Novo Design of Protein Nanoparticle Vaccines*

LaTeX source for Lorenzo Tarricone's Transfer of Status report (University of
Oxford, Department of Statistics). The structure mirrors the example report by
Qurat ul ain; the technical content (Methods, Results) is drawn from the
*Design-CP: Context Parallelism for Design of Protein Nanoparticles* paper.

## Repository layout

```
main.tex                     Master file: preamble, title page, TOC, bibliography
references.bib               Bibliography (verbatim copy of "references (5).bib")
sections/
  01_introduction.tex        Ch.1  Introduction (nanoparticle vaccines; protein design)
  02_computational_design.tex Ch.2  Computational design of PNP vaccines + project objective
  03_methods.tex             Ch.3  Methods (from the paper)
  04_results_discussion.tex  Ch.4  Results and discussion (from the paper)
  05_future_work.tex         Ch.5  Future work (+ Gantt chart)
figures/                     Drop figure PDFs/PNGs here (graphicspath points here)
```

## Compiling

**Overleaf:** create a new project → *Upload* this folder (or import from GitHub) →
Menu → Compiler → **pdfLaTeX**. Overleaf runs Biber automatically.

**Locally** (needs a TeX distribution with `biber` and the `pgfgantt` package):

```bash
latexmk -pdf main.tex
# equivalently: pdflatex main → biber main → pdflatex main → pdflatex main
```

## ⚠️ Before your first compile — fix two duplicate keys

`references.bib` is a **verbatim copy** of your original library and contains **two
duplicate citation keys** that Biber will reject:

- `li_robust_2026` — appears twice
- `lee_four-component_2025` — appears twice

Delete **one** entry of each pair (the two copies are the same paper), then compile.
Until you do, Biber will error with `Duplicate entry key`.

## References you may want to add (not currently in the .bib)

These spots are marked with `% TODO [FLAG ...]` in `sections/01_introduction.tex`.
No citation was invented — add the entry to `references.bib` and replace the TODO
with a `\parencite{...}`:

- **[FLAG A] A foundational mRNA-vaccine reference** for §1.1 (to frame nanoparticle
  vaccines as an improvement over mRNA vaccines). Suggestions: Pardi et al. 2018,
  *mRNA vaccines — a new era in vaccinology*; and/or Polack et al. 2020 (BNT162b2).
- **[FLAG B] (optional) A canonical physics-based de novo design reference** for
  §1.2.1, e.g. Kuhlman et al. 2003, *Design of a novel globular protein fold with
  atomic-level accuracy*.

## Placeholders to fill in

Search the sources for `TODO` to find everything that needs your attention:

- **Title page** (`main.tex`): college, co-supervisor(s)/assessors, and the term/date.
- **Figures** (`sections/04_results_discussion.tex`): export Figures 1–3 from the
  paper into `figures/` and uncomment the `\includegraphics` lines (framed
  placeholders are shown until then).
- **Scaling table** (`sections/04_results_discussion.tex`, Table 1) and a few
  numerical constants marked `% TODO: confirm` — reconcile against the paper.
- **Gantt chart** (`sections/05_future_work.tex`): adjust tasks, spans and dates.

## Citation style

Author–year (`biblatex` with `style=authoryear`, Biber backend). Use `\parencite{key}`
for parenthetical citations and `\textcite{key}` for in-text (author as subject).
