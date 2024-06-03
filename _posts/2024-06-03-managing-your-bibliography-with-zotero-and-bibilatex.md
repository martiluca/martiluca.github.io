---
layout: distill
title: Managing your bibliography with Zotero and BibLaTeX
date: 2024-06-03
description: Simplify your thesis writing process by managing your bibliography with Zotero and BibLaTeX. Learn how to set up, export, and customize your references seamlessly!
tags: bibliography thesis latex zotero biblatex
categories: LaTeX
featured: true

authors:
    - name: Martina Lucà
---

When writing your thesis, managing references and bibliographies can often become a daunting task. Mismanaging your references can lead to inconsistencies, errors, and a significant amount of wasted time. This is when Zotero comes in handy. First of all, what is it? It's an open-source reference management tool designed to help you collect, organize, cite, and share your research sources. Pair this with BibLaTeX, a package that provides advanced bibliographic features and formatting capabilities, and you have the power to manage and format your bibliographies with precision, ease, and consistency. 

## Prepare Zotero

You can download Zotero [here](https://www.zotero.org/). I suggest pairing it with the appropriate Zotero connector extension for your browser (you can find it [here](https://www.zotero.org/download/connectors)) to make it really easy to add articles, books, and web pages to your collections. 

Since we are looking to pair it with Biber, we will need to install a plug-in called Better BibTeX. To do so head over [here](https://github.com/retorquere/zotero-better-bibtex/releases) and download the most recent release. To install it head back to Zotero and perform the following steps:

1. In the main menu go to Tools > Add-ons
2. Select ‘Extensions’
3. Click on the gear in the top-right corner and choose ‘Install Add-on From File…’
4. Choose .xpi that you’ve just downloaded, and click ‘Install’
5. Restart Zotero if you’re using Zotero 6

After the initial installation, the plugin will auto-update to newer releases.

## Exporting Zotero to BibTeX

Start by launching Zotero and select the references you wish to export. This can include all references in a particular folder or specific ones highlighted using control-clicks and shift-clicks. 

Go to `File` and choose `Export Library`. In the dialog box that appears, select the better BibTeX format and click OK. If you are working locally, you can save this file directly in the directory of your project and select the option `Export Notes`. If you wish to update your .bib file every time you add a reference to your collection, select also the option `Keep updated`.

### Using Zotero with Overleaf

Last time, I suggested using Overleaf if you are a beginner. If you have a premium license, Overleaf offers a direct integration with Zotero. To link your Overleaf account to Zotero, you can follow Overealf's tutorial, which can be found [here](https://it.overleaf.com/learn/how-to/How_to_link_your_Overleaf_account_to_Mendeley_and_Zotero).

If you do not own a premium license, do not worry! You can simply follow the process described above and just upload the resulting .bib file to your project. To keep it updated, you can just copy and paste the content of your local copy to the one on Overleaf.

In my [Thesis template](https://github.com/martiluca/SciThesis), you already have a ref.bib file in which you can copy and paste the content of your Zotero-generated .bib file as you add references to your collection.

Your .bib file will look something like this:

```latex
@book{smith2020example,
  author    = {John Smith},
  title     = {An Example Book},
  year      = {2020},
  publisher = {Example Publisher},
  address   = {Example City}
}

@article{johnson2019example,
  author    = {Emily Johnson and Michael Doe},
  title     = {An Example Article},
  journal   = {Journal of Examples},
  year      = {2019},
  volume    = {10},
  number    = {2},
  pages     = {123-145},
  month     = {March},
  doi       = {10.1234/example.doi}
}

@inproceedings{doe2018example,
  author    = {Jane Doe},
  title     = {An Example Conference Paper},
  booktitle = {Proceedings of the Example Conference},
  year      = {2018},
  editor    = {Ann Editor},
  volume    = {1},
  series    = {Example Series},
  pages     = {50-60},
  address   = {Example Location},
  month     = {July},
  organization = {Example Organization},
  publisher = {Example Publisher}
}

@misc{unknown2021example,
  author       = {Anonymous},
  title        = {An Example Webpage},
  year         = {2021},
  howpublished = {\url{https://www.example.com}},
  note         = {Accessed: 2024-06-03}
}
```

## Using the references in your document

Now that you have built a collection and exported a .bib file, it's time to cite your sources in your LaTeX document.

To cite a source, use the `\cite{}` command, where the argument is the citation key for the reference you want to cite. The citation key is typically generated automatically by Zotero and can be found in the .bib file right after the @entry_type.

Here is an example of how to cite a source within your document:

```latex
As shown in previous studies \cite{smith2020example}, the results indicate significant improvements.
```

This command will insert a reference in the text and add the corresponding citation in the bibliography section.

**Inline citations**

If you need to include the author’s name as part of the narrative, you can use the `\textcite{}` command provided by BibLaTeX:

```latex
Smith et al. \textcite{smith2020example} demonstrated significant improvements in their study.
```

**Multiple citations**

To cite multiple references at once, include all the citation keys separated by commas within the `\cite{}` command:

```latex
Several studies have explored this phenomenon \cite{smith2020example, johnson2019example, doe2018example}.
```

If you are using the settings found in my template, your citations and bibliography will look like this:

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/citations.png" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/bib.png" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

## Customize the look of your citations and bibliography

You can find the bibliography settings at the bottom of the `SciThesis.cls` file:

```latex
%% BIBLIOGRAPHY %%
% Bibliography %
\usepackage[backend=biber, style=authoryear-comp, sorting=nyt, maxcitenames=2]{biblatex}
\addbibresource{ref.bib}
\renewcommand*{\nameyeardelim}{\addcomma\space} %Add comma between author and year
```

- `backend=biber` specifies that Biber should be used as the backend processor for managing and processing the bibliography. 
- `style=authoryear-comp`: sets the citation and bibliography style to a compact version of the author-year citation style that shows the author's name and year of publication in citations.
- `sorting=nyt`: defines the order in which the bibliography entries are sorted. The value `nyt` stands for:
  - `n`: Name of the author
  - `y`: Year of publication
  - `t`: Title of the work 

- `maxcitenames=2`: limits the number of author names displayed in a citation to two. If a work has more than two authors, it will show the first author followed by "*et al.*"

There are several styles you can choose from; you can find a list [here](https://www.overleaf.com/learn/latex/Biblatex_citation_styles). Here, you can also change how entries will be sorted in your bibliography and the maximum number of author names to display.

## Wrapping Up

Managing your bibliography effectively is crucial for maintaining the quality and credibility of your thesis. By using Zotero with BibLaTeX, you can streamline the process of collecting, organizing, and citing your sources, ensuring that your references are consistent and accurate. Whether you are working locally or using Overleaf, these tools can significantly simplify your writing workflow.

In this post, we covered the basics of setting up Zotero, exporting your references to a BibTeX file, and integrating them into your LaTeX document using BibLaTeX. We've also seen how to customize your citation and bibliography styles to fit your needs.

Next week, we will talk about customizing the look and feel of your thesis, including fonts, headings, page layout, and margins.

Happy writing, and see you next time!