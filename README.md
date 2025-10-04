# Arithmax Research LaTeX Template

This repository contains the unified LaTeX template for all Arithmax Research publications. The template provides consistent branding, formatting, and mathematical notation across all research papers.

## Files Overview

- `arithmaxresearch.cls` - Main LaTeX class file
- `arithmax-logo.sty` - Logo and branding package
- `Arithmax-research-logo.png` - Official Arithmax Research logo file
- `template.tex` - Sample template file for new papers
- `README.md` - This documentation

## Quick Start

### For New Papers

1. Copy the `template.tex` file
2. Choose your document style in the `\documentclass` line:
   - `\documentclass[twocolumn,ieee]{arithmaxresearch}` - IEEE-style two-column
   - `\documentclass[onecolumn,ieee]{arithmaxresearch}` - IEEE-style one-column  
   - `\documentclass[article]{arithmaxresearch}` - Standard article style

3. Update the title and author information:
```latex
\title{Your Research Paper Title}
\arithmaxauthor{Your Name}{Your Affiliation}{your.email@arithmax.com}
```

4. Compile with your LaTeX distribution (requires pdflatex or xelatex)

### For Existing Papers

Update your existing papers by:

1. Replace the `\documentclass` line with the appropriate Arithmax template option
2. Remove all package imports (they're included in the template)
3. Update author format to use `\arithmaxauthor{Name}{Affiliation}{Email}`
4. Add the official logo after `\maketitle` with:
```latex
\begin{center}
\vspace{-1em}
\arithmaxtitlelogo[4cm]
\vspace{0.5em}
\end{center}
```

## Document Class Options

### IEEE Style (`ieee` option)
- Uses IEEEtran base class
- Professional academic formatting
- Options: `twocolumn` or `onecolumn`
- Suitable for conference papers and journals

### Article Style (`article` option)
- Uses standard article class
- More flexible formatting
- Single column layout
- Suitable for working papers and reports

## Branding Features

### Logo Commands
- `\arithmaxtitlelogo[width]` - Main logo for title pages (e.g., `\arithmaxtitlelogo[4cm]`)
- `\arithmaxheaderlogo[width]` - Logo for page headers (automatically sized)
- `\arithmaxlogoscaled[width]` - General scaled logo (e.g., `\arithmaxlogoscaled[3cm]`)
- `\arithmaxinlinelogo[width]` - Small logo for inline text use
- `\arithmaxwatermark[opacity]` - Light watermark version for backgrounds

### Color Scheme
The template uses colors extracted from the official Arithmax Research logo:
- **Arithmax Blue** (`arithmaxblue`): RGB(53,73,123) - Dark navy blue from logo background
- **Arithmax Cyan** (`arithmaxcyan`): RGB(77,208,225) - Cyan/teal from logo charts
- **Arithmax Gray** (`arithmaxgray`): RGB(180,180,180) - Light gray for secondary text
- **Arithmax White** (`arithmaxwhite`): RGB(255,255,255) - White from logo text

### Headers and Footers
- Header: Arithmax logo (left), page number (right)
- Footer: "Arithmax Research - Confidential" (center)
- Professional styling with colored rules

## Mathematical Notation

The template includes standardized mathematical commands:

### Basic Mathematics
- `\R`, `\N`, `\Z`, `\Q`, `\C` - Number sets
- `\E[X]` - Expectation
- `\Var(X)` - Variance  
- `\Cov(X,Y)` - Covariance
- `\Prob(A)` - Probability

### Financial Mathematics
- `\price{t}` - Price at time t
- `\return{t}` - Return at time t
- `\vol{t}` - Volatility at time t
- `\drift` - Drift parameter

### Example Usage
```latex
The asset price follows: $\price{t} = \price{0} \exp((\drift - \frac{\vol{t}^2}{2})t + \vol{t}W_t)$

Expected return: $\E[\return{t}] = \drift \cdot \Delta t$
```

## Environments

### Theorems and Proofs
```latex
\begin{theorem}
Statement of the theorem.
\end{theorem}

\begin{proof}
Proof content.
\end{proof}
```

Available environments:
- `theorem`, `lemma`, `proposition`, `corollary`
- `definition`, `example`
- `remark`, `note`

### Algorithms
```latex
\begin{algorithm}
\caption{Algorithm Name}
\begin{algorithmic}[1]
\STATE Initialize parameters
\FOR{each iteration}
    \STATE Perform calculation
\ENDFOR
\RETURN result
\end{algorithmic}
\end{algorithm}
```

## Code Listings

The template includes styled code blocks:

```latex
\begin{lstlisting}[language=Python, caption=Sample Code]
def calculate_volatility(returns):
    return np.std(returns) * np.sqrt(252)
\end{lstlisting}
```

## Compilation Requirements

### Required LaTeX Distribution
- TeX Live 2020 or later
- MiKTeX 2.9 or later

### Required Packages
All packages are automatically loaded by the template:
- `amsmath`, `amssymb`, `amsfonts`, `amsthm`
- `graphicx`, `tikz`, `pgfplots`
- `algorithm`, `algorithmic`
- `hyperref`, `natbib`
- `booktabs`, `listings`

### Compilation Commands
```bash
pdflatex your-paper.tex
bibtex your-paper
pdflatex your-paper.tex
pdflatex your-paper.tex
```

Or for bibliography with natbib:
```bash
pdflatex your-paper.tex
bibtex your-paper
pdflatex your-paper.tex
pdflatex your-paper.tex
```

## Customization

### Adding New Mathematical Commands
Add to your document preamble (after `\begin{document}`):
```latex
\newcommand{\mycommand}[1]{\mathbf{#1}}
```

### Custom Colors
The template defines several colors. Add new ones with:
```latex
\definecolor{mycolor}{RGB}{255,0,0}
```

### Modifying the Logo
Edit `arithmax-logo.sty` to customize the logo appearance or create new logo variants.

## Examples

The repository includes four example papers demonstrating the template:

1. **HJB Market Making** (`HJB_MM/hjb_mm.tex`) - IEEE two-column format
2. **Sentiment HJB** (`Sentiment_hjb/sentiment_hjb.tex`) - IEEE two-column format  
3. **Leveraged Index Funds** (`Leveraged_Index_Funds/index_funds.tex`) - IEEE one-column format
4. **Pairs Trading** (`Pairs_Trading/pt_demostration.tex`) - Article format

## Troubleshooting

### Common Issues

**Error: "arithmax-logo.sty not found"**
- Ensure `arithmax-logo.sty` is in the same directory as your `.tex` file
- Or install it in your LaTeX distribution's style directory

**Logo not displaying**
- Check that TikZ package is properly installed
- Verify that the logo commands are used after `\begin{document}`

**Formatting issues with IEEE style**
- Ensure you're using the correct option: `ieee` in the documentclass
- Check that IEEEtran is installed in your LaTeX distribution

**Bibliography not formatting correctly**
- Use `natbib` commands: `\citep{}`, `\citet{}`
- Ensure proper compilation sequence (pdflatex → bibtex → pdflatex × 2)

### Getting Help

For technical issues with the template:
1. Check the example files for reference
2. Verify your LaTeX distribution is up to date
3. Contact: research@arithmax.com

## Version History

- **v1.0** (October 2025) - Initial unified template
  - IEEE and article document styles
  - Integrated logo and branding
  - Standardized mathematical notation
  - Professional formatting and layout

---

**Arithmax Research** - Advancing quantitative finance through rigorous mathematical research.
