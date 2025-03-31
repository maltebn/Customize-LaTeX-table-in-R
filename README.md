# Customize any LaTeX table in R
In LaTeX, you have endless table formatting options.
An R package intended to assist in the R-to-LaTeX-table process should be easy to use, and therefore should just give you a basic template.
But you still want to utilize all of LaTeX's formatting options, and you absolutely do NOT want to copy-paste anything from R into LaTeX!
That is, if you re-compile your R scripts with new numbers, you want your LaTeX-tables to be updated instantly.

To create such reproducible tables with detailed LaTeX-formatting, all you need is the R-package `xtable` combined with a semi-automated formatting step - all in R.

The procedure followed in this repository's R-markdown file (`custom-LaTeX-table-in-R.Rmd`) don't need anymore setting up than in standard LaTeX-table formatting.

With minimal R-knowledge, this procedure allows you to do anything you can do in plain LaTeX, since it is basically just building the LaTeX-code within R.

The principle simply is:
- Use `xtable` to generate a template containing your numbers.
- Save this template and use, e.g., `readr::read_lines()` to read in the template as a character vector.
- Extract the strings/entries you need from this vector.
- Manipulate these strings as needed.
- Insert extra strings of LaTeX-code at the relevant vector entries to get the formatting you want.
- Save the character vector as a TeX-file, e.g., by `readr::write_lines()`.

Now, if the resulting TeX-file was named `table1.tex`, you can simply use the LaTeX `subfiles`-package to insert your table's TeX-file by writing `\subfile{table1.tex}` on an appropriate line in your LaTeX document.
