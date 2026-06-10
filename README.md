# Thesis LaTeX Project

This repository contains the LaTeX source files for a thesis report. The project is organized into separate folders for front matter, chapters, figures, metadata, references, and style configuration.

## Project Structure

```text
.
├── main.tex
├── thesisstyle.sty
├── references.bib
├── settings/
│   └── metadata.tex
├── frontmatter/
│   ├── 01_cover.tex
│   ├── 02a_sub_cover_kh.tex
│   ├── 02b_sub_cover_fr.tex
│   ├── 02c_sub_cover_en.tex
│   ├── 03_acknowledgement.tex
│   ├── 04a_abstract_kh.tex
│   ├── 04b_abstract_en.tex
│   └── 05_abreviation.tex
├── chapters/
│   ├── ch1_introduction.tex
│   ├── ch2_presentation_of_the_project.tex
│   ├── ch3_literature_review.tex
│   ├── ch4_methodology.tex
│   ├── ch5_tool_and_technology.tex
│   ├── ch6_implementation.tex
│   ├── ch7_result_and_discussion.tex
│   └── ch8_coulusion_and_future_work.tex
├── figures/
│   ├── architectures/
│   ├── schools/
│   └── tools/
└── build/
```

## Main Files

### `main.tex`

This is the main entry point of the thesis. It loads the thesis style, metadata, references, front matter, chapters, table of contents, list of figures, list of tables, and bibliography.

Compile this file, not the chapter files directly.

### `thesisstyle.sty`

This file controls the thesis formatting, including:

* Fonts
* Khmer language support
* Page margins
* Line spacing
* Chapter and section title styles
* Table of contents formatting
* Figure and table numbering
* Bibliography style
* Hyperlinks
* Watermark
* Safe text wrapping commands

Do not put thesis content in this file. Only formatting commands should be placed here.

### `settings/metadata.tex`

This file stores reusable metadata such as:

* Student name
* Email
* Thesis title
* Academic year
* Department name
* Supervisor name
* Khmer, English, and French cover text

Use this file for text values that appear in multiple cover pages.

### `references.bib`

This file stores all bibliography entries in BibTeX format. Citations in the thesis should match the keys defined in this file.

Example:

```latex
\cite{breiman1996}
```

## Front Matter

The `frontmatter/` folder contains pages before Chapter 1.

| File                     | Purpose               |
| ------------------------ | --------------------- |
| `01_cover.tex`           | Main cover page       |
| `02a_sub_cover_kh.tex`   | Khmer sub-cover       |
| `02b_sub_cover_fr.tex`   | French sub-cover      |
| `02c_sub_cover_en.tex`   | English sub-cover     |
| `03_acknowledgement.tex` | Acknowledgement       |
| `04a_abstract_kh.tex`    | Khmer abstract        |
| `04b_abstract_en.tex`    | English abstract      |
| `05_abreviation.tex`     | List of abbreviations |

For unnumbered chapters such as acknowledgement and abstract, use:

```latex
\clearpage
\phantomsection
\chapter*{ACKNOWLEDGEMENT}
\addcontentsline{toc}{chapter}{ACKNOWLEDGEMENT}
```

For Khmer titles, use:

```latex
\clearpage
\phantomsection
\chapter*{\texorpdfstring{{\khmoul អត្ថបទសង្ខេប}}{អត្ថបទសង្ខេប}}
\addcontentsline{toc}{chapter}{អត្ថបទសង្ខេប}
```

## Chapters

The `chapters/` folder contains the main thesis chapters.

| File                                  | Chapter                                |
| ------------------------------------- | -------------------------------------- |
| `ch1_introduction.tex`                | Chapter 1: Introduction                |
| `ch2_presentation_of_the_project.tex` | Chapter 2: Presentation of the Project |
| `ch3_literature_review.tex`           | Chapter 3: Literature Review           |
| `ch4_methodology.tex`                 | Chapter 4: Methodology                 |
| `ch5_tool_and_technology.tex`         | Chapter 5: Tools and Technology        |
| `ch6_implementation.tex`              | Chapter 6: Implementation              |
| `ch7_result_and_discussion.tex`       | Chapter 7: Results and Discussion      |
| `ch8_coulusion_and_future_work.tex`   | Chapter 8: Conclusion and Future Work  |

Recommended improvement: rename `ch8_coulusion_and_future_work.tex` to:

```text
ch8_conclusion_and_future_work.tex
```

If renamed, also update the corresponding `\input{...}` line in `main.tex`.

## Figures

All images should be stored in the `figures/` folder.

Recommended usage:

```latex
\begin{figure}[htbp]
    \centering
    \includegraphics[width=0.8\textwidth]{figures/architectures/kfc.png}
    \caption{KFC Procedure Architecture}
    \label{fig:kfc_architecture}
\end{figure}
```

Use clear labels:

```latex
\label{fig:kfc_architecture}
\label{tab:classification_summary}
\label{ch:methodology}
```

Then refer to them using:

```latex
Figure~\ref{fig:kfc_architecture}
Table~\ref{tab:classification_summary}
Chapter~\ref{ch:methodology}
```

## Khmer Text

This project uses XeLaTeX with `polyglossia` and Khmer fonts.

Use this environment for Khmer paragraphs:

```latex
\begin{khmer}
អត្ថបទជាភាសាខ្មែរ...
\end{khmer}
```

Use `\khmoul` for Khmer Moul titles:

```latex
{\khmoul អត្ថបទសង្ខេប}
```

Avoid using `\emph{}` with Khmer Moul text because Khmer OS Muol Light may not support italic style.

## Code and Technical Names

For long technical names, class names, package names, function names, and file paths, use the safe commands defined in `thesisstyle.sty`.

Use:

```latex
\code{KFCProcedure}
\code{GradientCOBRA}
\code{MixCOBRARegressor}
\code{CombinedClassifier}
\filepath{kfc_procedure/core/kfc.py}
```

Avoid using raw long `\texttt{...}` text too often because it may overflow the page margin.

## Bibliography

This project uses `biblatex` with `biber`.

The bibliography package should be configured in `thesisstyle.sty`:

```latex
\RequirePackage[
    backend=biber,
    style=ieee,
    sorting=none
]{biblatex}

\DefineBibliographyStrings{english}{%
    bibliography = {REFERENCES},
    references = {REFERENCES},
}
```

The bibliography file is loaded in `main.tex`:

```latex
\addbibresource{references.bib}
```

At the end of `main.tex`, print the bibliography using:

```latex
\clearpage
\phantomsection
\printbibliography[heading=bibintoc]
```

Do not use old BibTeX commands:

```latex
\bibliographystyle{plain}
\bibliography{references}
```

## Build Instructions

This thesis should be compiled with XeLaTeX and Biber.

Recommended build sequence:

```bash
xelatex main.tex
biber main
xelatex main.tex
xelatex main.tex
```

The first XeLaTeX pass creates auxiliary files. Biber generates references. The final XeLaTeX passes update citations, table of contents, list of figures, and list of tables.

## VS Code LaTeX Workshop Recipe

Recommended build recipe:

```json
{
  "latex-workshop.latex.autoBuild.run": "onSave",
  "latex-workshop.latex.outDir": "%DIR%/build",
  "latex-workshop.latex.recipe.default": "xelatex + biber (full)",
  "latex-workshop.latex.recipes": [
    {
      "name": "xelatex + biber (full)",
      "tools": [
        "xelatex",
        "biber",
        "xelatex",
        "xelatex"
      ]
    },
    {
      "name": "xelatex (fast)",
      "tools": [
        "xelatex"
      ]
    }
  ],
  "latex-workshop.latex.tools": [
    {
      "name": "xelatex",
      "command": "xelatex",
      "args": [
        "-interaction=nonstopmode",
        "-halt-on-error",
        "-synctex=1",
        "-shell-escape",
        "-output-directory=%OUTDIR%",
        "%DOC%"
      ],
      "env": {}
    },
    {
      "name": "biber",
      "command": "biber",
      "args": [
        "--input-directory=%OUTDIR%",
        "--output-directory=%OUTDIR%",
        "%DOCFILE%"
      ],
      "env": {}
    }
  ],
  "latex-workshop.view.pdf.viewer": "tab",
  "latex-workshop.synctex.afterBuild.enabled": true,
  "latex-workshop.formatting.latex": "latexindent",
  "latex-workshop.latex.autoClean.run": "never",
  "latex-workshop.intellisense.package.enabled": true,
  "latex-workshop.latex.autoBuild.interval": 1000,
  "[latex]": {
    "editor.formatOnSave": false,
    "editor.wordWrap": "on",
    "editor.rulers": [
      100
    ]
  }
}
```

## Important Build Notes

Do not automatically delete these files during writing:

```text
main.aux
main.toc
main.lof
main.lot
main.bbl
main.bcf
```

They are needed for:

* Table of contents
* List of figures
* List of tables
* Cross-references
* Citations
* Bibliography

If the table of contents or references are missing, compile the thesis two or three times.

## Common Problems and Fixes

### Table of contents is empty

Compile multiple times:

```bash
xelatex main.tex
biber main
xelatex main.tex
xelatex main.tex
```

Also make sure the build process is not deleting `.toc`, `.lof`, `.lot`, `.aux`, or `.bbl` files.

### Citation is undefined

Check that the citation key exists in `references.bib`.

Example:

```latex
\cite{breiman1996}
```

The key `breiman1996` must exist in `references.bib`.

Then compile using the full XeLaTeX and Biber recipe.

### Figure reference is undefined

Make sure the figure has a label:

```latex
\label{fig:schedule}
```

Then refer to it using:

```latex
Figure~\ref{fig:schedule}
```

Compile at least twice.

### TikZ error: unknown function `of`

Make sure this is included in `thesisstyle.sty`:

```latex
\usetikzlibrary{
    positioning,
    arrows.meta,
    shapes.geometric,
    shapes.misc,
    calc,
    fit
}
```

### Text overflows outside the page margin

Use the safe code command:

```latex
\code{VeryLongTechnicalClassName}
```

For file paths:

```latex
\filepath{kfc_procedure/core/kfc.py}
```

### Cover page goes to a second page

The cover content is too tall. Use `\singlespacing` inside the cover page and reduce vertical spacing such as:

```latex
\vspace{0.3cm}
```

Avoid large values such as:

```latex
\vspace{1cm}
```

inside dense cover pages.

## Writing Guidelines

Use consistent academic wording throughout the thesis.

Recommended structure for paragraphs:

1. Start with the main idea.
2. Explain the evidence or implementation.
3. Link the idea back to the thesis objective.

Avoid unsupported claims. If something is not visible in the repository, source code, notebook, or experiment result, state it clearly instead of assuming.

Example:

```text
Not observable from the provided materials.
```

## Suggested Workflow

1. Edit one chapter at a time.
2. Compile using the fast XeLaTeX recipe for quick layout checks.
3. Use the full XeLaTeX + Biber recipe before final review.
4. Check the PDF for:

   * Page overflow
   * Figure placement
   * Missing references
   * Missing citations
   * Table of contents entries
   * List of figures and tables
5. Before submission, delete the old `build/` folder and compile cleanly using the full recipe.

## Final Submission Checklist

Before submitting the thesis, check:

* [ ] Cover pages are correct in Khmer, French, and English.
* [ ] Student name, supervisor name, and academic year are correct.
* [ ] Table of contents is complete.
* [ ] List of figures is complete.
* [ ] List of tables is complete.
* [ ] All figures have captions and labels.
* [ ] All tables have captions and labels.
* [ ] All citations appear correctly.
* [ ] References section appears as `REFERENCES`.
* [ ] No important LaTeX errors remain.
* [ ] PDF is generated from a clean full build.
