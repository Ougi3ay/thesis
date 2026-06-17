# Thesis LaTeX Project

This repository contains the LaTeX source files for a thesis report. The project is organized into separate folders for front matter, chapters, figures, metadata, references, style configuration, and Docker-based development.

The thesis should be compiled from `main.tex`.

---

## Project Structure

```text
.
├── .devcontainer
│   ├── Dockerfile
│   └── devcontainer.json
├── .gitignore
├── .vscode
│   └── settings.json
├── README.md
├── build
│   ├── chapters
│   ├── frontmatter
│   ├── main.aux
│   ├── main.bbl
│   ├── main.bcf
│   ├── main.blg
│   ├── main.lof
│   ├── main.log
│   ├── main.lot
│   ├── main.pdf
│   ├── main.run.xml
│   ├── main.synctex.gz
│   ├── main.toc
│   └── settings
├── chapters
│   ├── ch1_introduction.tex
│   ├── ch2_presentation_of_the_project.tex
│   ├── ch3_literature_review.tex
│   ├── ch4_methodology.tex
│   ├── ch5_tool_and_technology.tex
│   ├── ch6_implementation.tex
│   ├── ch7_result_and_discussion.tex
│   └── ch8_coulusion_and_future_work.tex
├── figures
│   ├── architectures
│   │   ├── gradientcobra.png
│   │   ├── hybrid.png
│   │   └── kfc.png
│   ├── schools
│   │   ├── ams.png
│   │   ├── itc.png
│   │   ├── kasegro.png
│   │   ├── moey.png
│   │   ├── reda-logo.png
│   │   ├── reda-organization.png
│   │   ├── schedule.png
│   │   └── watermark.png
│   ├── timeline.png
│   └── tools
│       ├── Jupyter.png
│       ├── git.png
│       ├── joblib.png
│       ├── logo.png
│       ├── matplotlib.png
│       ├── numpy.png
│       ├── python.png
│       ├── scipy.png
│       ├── seaborn.png
│       ├── sklearn.png
│       └── vscode.png
├── frontmatter
│   ├── 01_cover.tex
│   ├── 02a_sub_cover_kh.tex
│   ├── 02b_sub_cover_fr.tex
│   ├── 02c_sub_cover_en.tex
│   ├── 03_acknowledgement.tex
│   ├── 04a_abstract_kh.tex
│   ├── 04b_abstract_en.tex
│   └── 05_abreviation.tex
├── indent.log
├── main.tex
├── references.bib
├── settings
│   └── metadata.tex
└── thesisstyle.sty
```

---

## Main Files

### `main.tex`

This is the main entry point of the thesis. It loads the thesis style, metadata, references, front matter, chapters, table of contents, list of figures, list of tables, and bibliography.

Compile this file only:

```bash
xelatex main.tex
```

Do not compile chapter files directly.

---

### `thesisstyle.sty`

This file controls the formatting of the thesis, including:

* Fonts
* Khmer language support
* Page margins
* Line spacing
* Paragraph indentation
* Chapter and section title styles
* Table of contents formatting
* Figure and table numbering
* Bibliography style
* Hyperlinks
* Watermark
* Safe text wrapping commands
* List formatting

Do not write thesis content in this file. Only formatting and style settings should be placed here.

---

### `settings/metadata.tex`

This file stores reusable thesis information such as:

* Student name
* Student email
* Thesis title
* Academic year
* Department name
* Supervisor name
* Advisor name
* Enterprise name
* Khmer, English, and French cover text

Use this file for values that appear in multiple cover pages.

Example:

```latex
\newcommand{\StudentNameEN}{POV Ougi}
\newcommand{\StudentNameKH}{ពៅ អ៊ូជី}
\newcommand{\StudentEmail}{e20201146@itc.edu.kh}
```

---

### `references.bib`

This file stores all bibliography entries in BibTeX format.

Example citation entry:

```bibtex
@article{breiman1996,
  author  = {Breiman, Leo},
  title   = {Bagging Predictors},
  journal = {Machine Learning},
  year    = {1996}
}
```

Use the citation key in the thesis:

```latex
\cite{breiman1996}
```

---

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

For unnumbered front matter chapters, use this structure:

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

The command `\texorpdfstring` prevents PDF bookmark errors when using custom Khmer fonts.

---

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

Recommended correction:

```text
ch8_coulusion_and_future_work.tex
```

should be renamed to:

```text
ch8_conclusion_and_future_work.tex
```

If renamed, update the corresponding line in `main.tex`:

```latex
\input{chapters/ch8_conclusion_and_future_work}
```

---

## Figures

All images should be stored inside the `figures/` folder.

Recommended image usage:

```latex
\begin{figure}[htbp]
    \centering
    \includegraphics[width=0.8\textwidth]{figures/architectures/kfc.png}
    \caption{KFCProcedure Architecture}
    \label{fig:kfc_architecture}
\end{figure}
```

Use clear labels:

```latex
\label{fig:kfc_architecture}
\label{fig:gradientcobra_architecture}
\label{tab:classification_summary}
\label{ch:methodology}
```

Refer to them using:

```latex
Figure~\ref{fig:kfc_architecture}
Table~\ref{tab:classification_summary}
Chapter~\ref{ch:methodology}
```

After adding or changing labels, compile at least two times.

---

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

Instead of:

```latex
\emph{{\khmoul ឈ្មោះ}}
```

use:

```latex
{\khmoul ឈ្មោះ}
```

---

## Safe Code and Technical Names

For long technical names, class names, function names, package names, and file paths, use the safe commands defined in `thesisstyle.sty`.

Use:

```latex
\code{KFCProcedure}
\code{GradientCOBRA}
\code{MixCOBRARegressor}
\code{CombinedClassifier}
\code{WeightedMeanAggregator}
\code{register_all_sklearn_models()}
\filepath{kfc_procedure/core/kfc.py}
```

Avoid writing long technical names directly inside `\texttt{...}` too often, because long code words may overflow outside the page margin.

Recommended:

```latex
The repository implements the \code{KFCProcedure} framework.
```

Not recommended:

```latex
The repository implements the \texttt{KFCProcedure} framework.
```

---

## Bibliography

This project uses `biblatex` with `biber`.

The bibliography configuration should be placed in `thesisstyle.sty`:

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

Those commands are not valid when using `biblatex`.

---

## Build Instructions

This thesis should be compiled with XeLaTeX and Biber.

Recommended build sequence:

```bash
xelatex main.tex
biber main
xelatex main.tex
xelatex main.tex
```

The first XeLaTeX pass creates auxiliary files. Biber generates the bibliography. The final XeLaTeX passes update citations, references, table of contents, list of figures, and list of tables.

The generated PDF will be created in the `build/` folder if using the configured VS Code LaTeX Workshop setup:

```text
build/main.pdf
```

---

## Run with Docker Dev Container

This project includes a Docker Dev Container setup under:

```text
.devcontainer/
├── Dockerfile
└── devcontainer.json
```

The Dev Container provides a consistent LaTeX environment for building the thesis. It is useful when working across different computers or when avoiding local LaTeX installation problems.

---

### Requirements

Before using the Dev Container, install:

* Docker Desktop
* Visual Studio Code
* VS Code extension: Dev Containers
* VS Code extension: LaTeX Workshop

---

### Open the Project in Dev Container

1. Open the thesis folder in VS Code.
2. Press:

```text
Ctrl + Shift + P
```

On macOS:

```text
Cmd + Shift + P
```

3. Search for:

```text
Dev Containers: Reopen in Container
```

4. Wait for Docker to build the container.
5. After the container opens, compile `main.tex`.

---

### Build the Thesis inside the Container

Run:

```bash
xelatex -interaction=nonstopmode -synctex=1 -shell-escape -output-directory=build main.tex
biber --input-directory=build --output-directory=build main
xelatex -interaction=nonstopmode -synctex=1 -shell-escape -output-directory=build main.tex
xelatex -interaction=nonstopmode -synctex=1 -shell-escape -output-directory=build main.tex
```

The final PDF will be generated at:

```text
build/main.pdf
```

---

### Clean Build inside the Container

If the table of contents, list of figures, list of tables, or references are not updating correctly, do a clean rebuild:

```bash
rm -rf build
mkdir build

xelatex -interaction=nonstopmode -synctex=1 -shell-escape -output-directory=build main.tex
biber --input-directory=build --output-directory=build main
xelatex -interaction=nonstopmode -synctex=1 -shell-escape -output-directory=build main.tex
xelatex -interaction=nonstopmode -synctex=1 -shell-escape -output-directory=build main.tex
```

---

## VS Code LaTeX Workshop Recipe

Recommended `.vscode/settings.json`:

```json
{
  "latex-workshop.latex.autoBuild.run": "onSave",
  "latex-workshop.latex.outDir": "%DIR%/build",

  "latex-workshop.latex.recipe.default": "xelatex + biber + xelatex x2",

  "latex-workshop.latex.recipes": [
    {
      "name": "xelatex + biber + xelatex x2",
      "tools": [
        "xelatex",
        "biber",
        "xelatex",
        "xelatex"
      ]
    },
    {
      "name": "xelatex fast",
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

  "latex-workshop.latex.autoClean.run": "never",

  "latex-workshop.intellisense.package.enabled": true,
  "latex-workshop.latex.autoBuild.interval": 1000,

  "[latex]": {
    "editor.formatOnSave": false,
    "editor.wordWrap": "on",
    "editor.rulers": [100]
  }
}
```

---

## Important Build Notes

Do not automatically delete these files during normal writing:

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

---

## Recommended `.gitignore`

Use `.gitignore` to avoid committing generated LaTeX build files.

Recommended:

```gitignore
# Build output
build/

# LaTeX temporary files
*.aux
*.bbl
*.bcf
*.blg
*.fdb_latexmk
*.fls
*.lof
*.log
*.lot
*.out
*.run.xml
*.synctex.gz
*.toc
*.xdv
*.nav
*.snm
*.vrb

# Latexindent
indent.log

# OS files
.DS_Store
Thumbs.db
```

If you want to keep the final generated PDF in Git, do not ignore:

```text
build/main.pdf
```

Otherwise, it is cleaner to generate the PDF locally and keep `build/` ignored.

---

## Common Problems and Fixes

### Table of contents is empty

Compile multiple times:

```bash
xelatex main.tex
biber main
xelatex main.tex
xelatex main.tex
```

Also make sure the build process is not deleting:

```text
main.toc
main.lof
main.lot
main.aux
main.bbl
```

---

### Citation is undefined

Check that the citation key exists in `references.bib`.

Example:

```latex
\cite{breiman1996}
```

The key `breiman1996` must exist in `references.bib`.

Then compile using the full XeLaTeX and Biber recipe.

---

### `\bibliographystyle` invalid for `biblatex`

This error happens when old BibTeX commands are used with `biblatex`.

Remove:

```latex
\bibliographystyle{plain}
\bibliography{references}
```

Use:

```latex
\printbibliography[heading=bibintoc]
```

---

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

---

### Chapter reference is undefined

Make sure the chapter has a label:

```latex
\chapter{METHODOLOGY}
\label{ch:methodology}
```

Then refer to it using:

```latex
Chapter~\ref{ch:methodology}
```

---

### TikZ error: unknown function `of`

This happens when TikZ positioning is used without loading the correct library.

Make sure this is included in `thesisstyle.sty` after `\RequirePackage{tikz}`:

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

---

### Text overflows outside the page margin

Use the safe code command:

```latex
\code{VeryLongTechnicalClassName}
```

For file paths:

```latex
\filepath{kfc_procedure/core/kfc.py}
```

Also check for accidental characters such as:

```text
““
```

or unnecessary manual quotation marks.

---

### Cover page goes to a second page

The cover content is too tall. Use `\singlespacing` inside the cover page and reduce large vertical spacing.

Example:

```latex
\begingroup
\singlespacing

% cover content here

\endgroup
```

Avoid too many large spacing commands such as:

```latex
\vspace{1cm}
```

Use smaller spacing:

```latex
\vspace{0.25cm}
\vspace{0.35cm}
```

---

### Khmer font error

If you see an error saying the main font does not contain Khmer script, make sure `\khmerfont` is defined in `thesisstyle.sty`:

```latex
\newfontfamily\khmerfont[
    Script=Khmer,
    Scale=1.0
]{Khmer OS Battambang}
```

Then Khmer paragraphs can use:

```latex
\begin{khmer}
អត្ថបទជាភាសាខ្មែរ...
\end{khmer}
```

---

### Khmer Moul italic warning

If you see:

```text
Font shape KhmerOSMuolLight italic undefined
```

remove `\emph{}` from Khmer Moul text.

Instead of:

```latex
\emph{{\khmoul ឈ្មោះ}}
```

use:

```latex
{\khmoul ឈ្មោះ}
```

---

## Writing Guidelines

Use clear academic writing throughout the thesis.

Recommended paragraph structure:

1. Start with the main idea.
2. Explain the evidence, implementation, or result.
3. Link the idea back to the thesis objective.

Avoid unsupported claims. If something is not visible in the repository, source code, notebooks, or experiment results, state it clearly.

Use:

```text
Not observable from the provided materials.
```

instead of guessing.

---

## Suggested Writing Workflow

1. Edit one chapter at a time.
2. Compile using the fast XeLaTeX recipe for quick layout checks.
3. Use the full XeLaTeX + Biber recipe before final review.
4. Check the generated PDF for:

   * Page overflow
   * Figure placement
   * Missing references
   * Missing citations
   * Table of contents entries
   * List of figures
   * List of tables
5. Before submission, delete the old `build/` folder and run a full clean build.

---

## Final Submission Checklist

Before submitting the thesis, check:

* [ ] Cover pages are correct in Khmer, French, and English.
* [ ] Student name is correct.
* [ ] Supervisor and advisor names are correct.
* [ ] Academic year is correct.
* [ ] Table of contents is complete.
* [ ] List of figures is complete.
* [ ] List of tables is complete.
* [ ] All figures have captions and labels.
* [ ] All tables have captions and labels.
* [ ] All citations appear correctly.
* [ ] References section appears as `REFERENCES`.
* [ ] No important LaTeX errors remain.
* [ ] PDF is generated from a clean full build.
* [ ] Final PDF is reviewed page by page before submission.
