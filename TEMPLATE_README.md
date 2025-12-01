# Dual-Mode LaTeX Template: Report + Presentation

Creates **both** a detailed report and presentation from the same source files, with clickable hyperlinks from slides to specific report sections.

## Files

| File | Purpose |
|------|----------|
| `template_main.tex` | Configuration, title, author, packages |
| `template_report_sections.tex` | Full report content |
| `template_presentation_slides.tex` | Slide content |
| `template_shared_elements.tex` | **Reusable figures/tables/equations** |
| `compile.bat` | Compilation script |
| `figures/` | Image files |

## Quick Start

1. **Compile**: `.\compile.bat` → generates `report.pdf` + `presentation.pdf`
2. **Customize** `template_main.tex`: title, author, institution
3. **Add content** to `template_report_sections.tex` and `template_presentation_slides.tex`
4. **Recompile**: `.\compile.bat`

## Key Feature: True Content Sharing

Define figures/tables/equations **once** in `template_shared_elements.tex`, use in **both** formats:

```latex
% In template_shared_elements.tex - define once:
\newcommand{\figureMyPlot}{\includegraphics{figures/plot.png}}
\newcommand{\tableResults}{\begin{tabular}...\end{tabular}}
\newcommand{\eqModel}{y = mx + b}

% In report - use it:
\begin{figure}
    \figureMyPlot
    \caption{...}
\end{figure}

% In presentation - same command:
\begin{frame}
    \figureMyPlot
\end{frame}
```

Change once → updates everywhere!

## GitHub Pages Hyperlinks (Optional)

1. Push to GitHub and enable Pages (Settings → Pages → main branch)
2. Update `\reporturl` in `template_main.tex` with your GitHub Pages URL
3. Recompile and push PDFs

**Result:** Slides link to specific report sections online!

## Customization Examples

**Change theme:** Edit `\usetheme{Madrid}` in `template_main.tex`  
**Add section:** Copy existing section pattern in report/slides, update `\hypertarget{}`  
**Add figure:** Define `\newcommand{\figureX}{...}` in `template_shared_elements.tex`, use in both formats

## How It Works

`template_main.tex` checks `\ifdefined\ispresentation`:
- **NO** → `\documentclass{article}` → loads `template_report_sections.tex` → `report.pdf`
- **YES** → `\documentclass{beamer}` → loads `template_presentation_slides.tex` → `presentation.pdf`

Both load `template_shared_elements.tex` for reusable content.

## PowerPoint Conversion

**Recommended method:** Use [Adobe's free PDF to PowerPoint converter](https://www.adobe.com/acrobat/online/pdf-to-ppt.html)

1. Upload `presentation.pdf` to Adobe's converter
2. Download the converted `.pptx` file
3. Clean up any formatting as needed
4. Merge with team slides in PowerPoint

## Troubleshooting

- **No pdflatex**: Install [MiKTeX](https://miktex.org)
- **Errors**: Check `.log` files
- **Hyperlinks fail**: Verify GitHub Pages URL in `\reporturl`

---

**Template v1.0** - December 2025
