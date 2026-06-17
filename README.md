# Thesis LaTeX Project

## Python Libraries for Clusterwise Predictive Models: KFCProcedure and GradientCOBRA

This repository contains the LaTeX source code for the engineering degree thesis titled:

**Python Libraries for Clusterwise Predictive Models: KFCProcedure and GradientCOBRA**

The thesis presents the design, implementation, and experimental evaluation of a Python-based machine learning framework for clusterwise supervised learning and COBRA-based ensemble aggregation.

The project was developed as part of an internship at the **Research and Data Analytics Laboratory (ReDA Lab)**, Department of Applied Mathematics and Statistics, Institute of Technology of Cambodia.

---

## Purpose of This Repository

This repository is mainly prepared for readers, advisors, committee members, and future students who want to understand, review, or compile the thesis document.

It contains:

* The complete LaTeX source code of the thesis.
* Front matter pages, including cover pages, acknowledgement, abstracts, and abbreviations.
* Eight main thesis chapters.
* Figures used in the thesis.
* Bibliography entries.
* Custom thesis style configuration.
* A compiled PDF output inside the build folder.

The main document should be compiled from:

```text
main.tex
```

---

## Audience

This README is intended for:

* Thesis advisors and reviewers who want to inspect the LaTeX source.
* Committee members who want to understand the structure of the thesis.
* Students who want to learn how the thesis document is organized.
* Future maintainers who may update the thesis content, figures, references, or formatting.

---

## Thesis Overview

The thesis focuses on two connected machine learning components:

### 1. KFCProcedure

KFCProcedure is a clusterwise supervised learning framework. It follows three main steps:

* **K-step:** Detects cluster structures in the input data using divergence-based clustering.
* **F-step:** Trains local predictive models inside each cluster.
* **C-step:** Combines the predictions from different divergence-based configurations.

### 2. GradientCOBRA Subsystem

The GradientCOBRA subsystem provides COBRA-based aggregation methods, including:

* **GradientCOBRA** for regression aggregation.
* **MixCOBRARegressor** for mixed input-space and prediction-space regression aggregation.
* **CombinedClassifier** for classification aggregation.

Together, these components form a reusable and modular Python framework for studying clusterwise learning and prediction aggregation.

---

## Thesis Chapter Structure

The thesis is organized into eight chapters.

| Chapter   | Title                               | Purpose                                                                                        |
| --------- | ----------------------------------- | ---------------------------------------------------------------------------------------------- |
| Chapter 1 | Introduction                        | Presents the internship, organization, and project context.                                    |
| Chapter 2 | Presentation of Project             | Describes the project problem, objectives, and planning.                                       |
| Chapter 3 | Literature Review                   | Reviews ensemble learning, COBRA methods, GradientCOBRA, and KFCProcedure.                     |
| Chapter 4 | Methodology                         | Explains the research methodology, system design, and experimental design.                     |
| Chapter 5 | Tools and Technologies              | Presents the programming tools, libraries, and platforms used in the project.                  |
| Chapter 6 | Implementation                      | Describes the source-code architecture, modules, software design, testing, and CI/CD workflow. |
| Chapter 7 | Experimental Results and Discussion | Reports classification and regression experiment results.                                      |
| Chapter 8 | Conclusion and Future Work          | Summarizes the work, limitations, contributions, and future improvements.                      |

---

## Repository Structure

```text
thesis/
├── main.tex
├── thesisstyle.sty
├── references.bib
├── README.md
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
│   ├── ch7_experimental_and_discussion.tex
│   └── ch8_conlusion_and_future_work.tex
├── appendices/
│   └── appendix_a.tex
├── figures/
│   ├── architectures/
│   ├── schools/
│   ├── tools/
│   └── timeline.png
├── build/
│   └── main.pdf
├── .vscode/
└── .devcontainer/
```

---

## Main Files Explained

### `main.tex`

This is the main entry point of the thesis. It loads the style file, metadata, front matter, chapters, references, and appendices.

Compile only this file. Do not compile individual chapter files directly.

---

### `thesisstyle.sty`

This file controls the thesis formatting, including:

* Page margins.
* Fonts.
* Khmer language support.
* Chapter and section styles.
* Table of contents style.
* Figure and table numbering.
* Bibliography formatting.
* Hyperlink formatting.
* Watermark and page layout.

Content should not be written directly inside this file unless it is related to formatting.

---

### `settings/metadata.tex`

This file stores reusable thesis information, such as:

* Student name.
* Thesis title.
* Academic year.
* Department name.
* Advisor name.
* Enterprise name.
* Cover-page text in Khmer, English, and French.

When the title, name, date, or advisor information needs to be updated, this file should be checked first.

---

### `references.bib`

This file stores all bibliography entries in BibTeX format.

Citations in the thesis should use citation keys from this file, for example:

```latex
\cite{breiman1996}
```

---

## Front Matter

The `frontmatter/` folder contains all pages before Chapter 1.

| File                     | Description            |
| ------------------------ | ---------------------- |
| `01_cover.tex`           | Main cover page        |
| `02a_sub_cover_kh.tex`   | Khmer sub-cover page   |
| `02b_sub_cover_fr.tex`   | French sub-cover page  |
| `02c_sub_cover_en.tex`   | English sub-cover page |
| `03_acknowledgement.tex` | Acknowledgement        |
| `04a_abstract_kh.tex`    | Khmer abstract         |
| `04b_abstract_en.tex`    | English abstract       |
| `05_abreviation.tex`     | List of abbreviations  |

---

## Figures

All figures are stored in the `figures/` folder.

The figure folders are organized by purpose:

```text
figures/
├── architectures/
├── schools/
├── tools/
└── timeline.png
```

Use the following LaTeX pattern to insert a figure:

```latex
\begin{figure}[H]
    \centering
    \includegraphics[width=0.75\textwidth]{figures/architectures/kfc.png}
    \caption{KFCProcedure Clusterwise Framework Architecture}
    \label{fig:kfc_architecture}
\end{figure}
```

When referring to the figure in the thesis text, use:

```latex
As shown in Figure~\ref{fig:kfc_architecture}, ...
```

---

## Tables

Tables should be written using clear captions and labels.

Example:

```latex
\begin{table}[H]
    \centering
    \caption{Software Environment Used in the Experiment}
    \label{tab:software_environment}
    \begin{tabular}{ll}
        \toprule
        Component & Version \\
        \midrule
        Python & 3.12.13 \\
        NumPy & 2.0.2 \\
        Scikit-learn & 1.6.1 \\
        \bottomrule
    \end{tabular}
\end{table}
```

When referring to the table in the thesis text, use:

```latex
Table~\ref{tab:software_environment} summarizes the software environment.
```

---

## How to Compile the Thesis

This thesis uses custom fonts and Khmer text support, so it should be compiled with **XeLaTeX**.

From the thesis folder, run:

```bash
xelatex main.tex
biber main
xelatex main.tex
xelatex main.tex
```

Alternatively, if `latexmk` is installed, run:

```bash
latexmk -xelatex main.tex
```

The final PDF will be generated as:

```text
main.pdf
```

In this project, a compiled version is also available inside:

```text
build/main.pdf
```

---

## Recommended Editing Workflow

For normal thesis editing, follow this workflow:

1. Edit only the relevant chapter file inside `chapters/`.
2. Update figures inside `figures/` if needed.
3. Add or update references in `references.bib`.
4. Compile from `main.tex`.
5. Check the generated PDF.
6. Verify the table of contents, list of figures, list of tables, and references.

Avoid editing the `build/` folder manually because it contains generated files.

---

## Citation and Reference Notes

All academic sources should be added to `references.bib`.

Use citation commands such as:

```latex
\cite{key}
```

or

```latex
\parencite{key}
```

depending on the citation style configured in the thesis style file.

After adding new references, run `biber` and compile the thesis again.

---

## Notes for Reviewers

This LaTeX project is organized so that thesis content and formatting are separated.

* Thesis content is mainly in `frontmatter/`, `chapters/`, and `appendices/`.
* Formatting is mainly controlled by `thesisstyle.sty`.
* Reusable metadata is stored in `settings/metadata.tex`.
* References are stored in `references.bib`.
* Figures are stored in `figures/`.

This structure makes it easier to review, update, and maintain the thesis document.

---

## Notes for Future Students

This project can be used as a reference structure for organizing a thesis in LaTeX. The main idea is to keep each part of the thesis in a separate file instead of writing everything in one long document.

A good practice is to keep:

* One main file for compilation.
* One style file for formatting.
* One metadata file for repeated information.
* One folder for front matter.
* One folder for chapters.
* One folder for figures.
* One bibliography file for references.

This makes the thesis easier to edit, review, debug, and compile.

---

## Project Information

**Institution:** Institute of Technology of Cambodia
**Department:** Department of Applied Mathematics and Statistics
**Laboratory:** Research and Data Analytics Laboratory
**Thesis Topic:** Python Libraries for Clusterwise Predictive Models KFCProcedure and GradientCOBRA
**Specialty:** Data Science
**Academic Year:** 2025–2026

---

## Final Output

The expected final output of this repository is a complete thesis PDF containing:

* Cover pages in Khmer, French, and English.
* Acknowledgement.
* Khmer and English abstracts.
* Table of contents.
* List of figures.
* List of tables.
* List of abbreviations.
* Eight main chapters.
* References.
* Appendices.

The PDF should be checked carefully before submission to ensure that formatting, page numbering, figures, tables, citations, and references are correct.
