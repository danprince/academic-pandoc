# Academic Pandoc
Last year, I decided that I was going to break out of the Academic LaTeX convention and write my Masters dissertation in Markdown. I've collected these resources to help others bootstrap a new academic project with Pandoc and Markdown.

For the unfamiliar, [Pandoc][1] is a document conversion tool that can turn a carefully thought out superset of Markdown into a PDF (via a compile to LaTeX). It's perfect for writing reports and short papers, but the documentation can be sparse and it can be especially difficult to find examples of LaTeX interop for more involved writing.

This repo comes with everything you need for:

* Multiple Chapters
* References & Citations
* Figures & Listings
* Appendix

[Here's an example][3] of the kind of PDF this will generate.

## Getting Started
To get started you'll need to [install Pandoc, Citeproc and LaTeX][2]. 

```bash
sudo apt-get install pandoc texlive
```

Then clone this repository.

```bash
git clone https://github.com/danprince/academic-pandoc.git 
```

To compile a PDF, run `./scripts/build` then find the output at `publish/publish.pdf`.

## References & Citations
You can collect your references in a [BibTeX][5] format in the [references.bib][4] file and many research tools will provide you with an option to export to BibTeX format. Alternatively, some services like [Google Scholar][6] will provide BibTeX ready references for citations.

For example, if we wanted to cite Chris Okasaki's Purely Functional Data Structures, then we can [run a search on Google Scholar][7], click the cite link and choose the BibTeX option to end up with the following:

```bibtex
@book{okasaki1999purely,
  title={Purely functional data structures},
  author={Okasaki, Chris},
  year={1999},
  publisher={Cambridge University Press}
}
```

Copy that reference and add it to your `references.bib` file.

Pandoc's markdown format has been enhanced to allow pandoc-citeproc to recognize citations in the following format.

```markdown
@okasaki1999purely

Or you can cite a specific page

[@okasaki1999 p. 104]

Or a range of pages

[@okasaki1999purely, pp 45-48]
```

## Figures & Listings
Pandoc's markdown format makes it easy to insert images and code blocks, but without LaTeX you won't be able to caption, list or reference them. However, you can embed LaTeX commands into your Markdown to make this possible.

```markdown
![Some Figure Caption\label{fig:unique-name}](figures/misc/some-figure.pdf)
```

Then you can reference the figure from elsewhere, using the `\ref` command.

```markdown
See \ref{fig:unique-name}.
```

The end result should look something like this.

![](https://camo.githubusercontent.com/bcab163f29f63dbc2cc3706164c37c3bcf9232fd/68747470733a2f2f692e696d6775722e636f6d2f786234456234342e706e67)

Creating a reference to a listing for a code block is similar.

    ```{caption="Listing Caption" label=lst:unique-name}
    (defn menu [state]
      (render [this]
        (dom/ul nil
          (map (fn [item]
            (dom/li nil item))
            (:items state)))))
    ```

It can be referenced in the same way.

```markdown
See Listing \ref{lst:unique-name}.
```

Which will generate the following.

![](https://camo.githubusercontent.com/c535edb3ff8a3641cd0ea980fabe2bc2e48e0536/68747470733a2f2f692e696d6775722e636f6d2f4f54686c6535732e706e67)

It's not enforced, but it's good practice to prefix your labels with `lst:` and `fig:`. This will help prevent naming collisions.

[1]: http://pandoc.org/
[2]: http://pandoc.org/installing.html
[3]: https://github.com/danprince/academic-pandoc/blob/master/publish/report.pdf
[4]: https://github.com/danprince/academic-pandoc/blob/master/references.bib
[5]: http://www.bibtex.org/
[6]: https://scholar.google.com/
[7]: https://scholar.google.co.uk/scholar?hl=en&q=purely+functional+data+structures&btnG=&as_sdt=1%2C5&as_sdtp=
