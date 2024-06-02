---
layout: distill
title: Writing a thesis in LaTeX
date: 2024-05-30
description: Why you should write your thesis in LaTeX? Start here and give it a try!
tags: formatting thesis latex template stem
categories: LaTeX
featured: true

authors:
    - name: Martina Lucà
---

## Why LaTeX?

What is LaTeX, and why should you use it to write your thesis? LaTeX is a typesetting system widely used in academia, particularly for technical and scientific documents, which offers a series of advantages over traditional word processors:

1. **Superior Typesetting Quality and Consistent Formatting.** One of LaTeX's best qualities is its consistency, which ensures that your thesis not only reads well but also looks professional. 
2. **Great Handling of Mathematical Content.** Thesis in STEM fields often involve an extensive use of mathematical formulas and equations. LaTeX provides a powerful equation editor that allows you to write and format complex equations with ease; moreover, referencing them is easy, thanks to the labeling system.
3. **Efficient Citation Management.** Thanks to tools like BibTeX and BibLaTeX, managing references and citations is fast and efficient.
4. **Flexibility and Customization.** LaTeX offers many customization options. You can tailor the appearance of your thesis to meet specific guidelines or personal preferences. You can change the look of a whole document in a matter of seconds, and it will keep its consistency. 
5. **Learning and Community Support.** Although LaTeX has a steeper learning curve than traditional word processors, the investment in learning it pays off. Moreover, a vast community of LaTeX users and a wealth of resources are available, including tutorials, templates, and forums where you can seek and share advice.

## Ok, but where do I start?

With that said, where should you start when trying to learn LaTeX? In my opinion, the easiest way is to use an online editor like [Overleaf](https://it.overleaf.com/), which does not require you to install anything and allows for real-time collaboration for free. This has its limitations (it's slow at compiling, and the free plan also has a compilation time limit), but it's a great starting point. Pair this with the hundreds of templates already available on this and other websites, and you will be writing documents in no time. 

In this article, I will explain how to use my particular template, which can be found here, but you can try to follow along with similar templates. One I highly suggest taking a look at once you grasp LaTeX basics is [Classic Thesis](https://it.overleaf.com/latex/templates/classic-thesis-style-v4-dot-2-by-andre-miede/dwgtvykzvdtk) by André Miede.

### The Title Page

Once you downloaded the zip and opened it with your preferred editor (on Overleaf, you can start a new project by simply uploading the zip file), you will see the following file structure:

```
.
├── backmatter/
│   └── acknowledgements.tex
├── chapters/
│   └── introduction.tex
├── figures
├── frontmatter/
│   ├── abstract.tex
│   ├── dedication.tex
│   ├── logo.png
│   └── titlepage.tex
├── settings/
│   ├── fonts
│   └── commands.tex
├── main.tex
├── ref.bib
└── SciThesis.cls
```

Once you understand how this structure works, you can easily add and remove things. First, let's change the Title Page! Open the relative file `titlepage.tex`: here, you can insert your university name, department, course, title, supervisors' name, academic year, and your name and matriculation number. 

**Warning**

This template uses custom fonts! You will have to change the compiler from pdfLaTeX to either XeLaTeX or LuaLaTeX! 

To do so in overleaf, click the Menu button in the top left corner. You will find the compiler option in the Settings section.

### Managing and adding chapters

As you can see, I added a dedication page. You can choose to remove it by removing or commenting the following lines in the `main.tex` file:

```latex
% Dedication
\include{frontmatter/dedication}
    
% insert blank page
\newpage
\thispagestyle{empty}
\mbox{}
\newpage
```

To modify other sections, like the abstract or the introduction, you can go to their respective files: `./frontmatter/abstract.tex` and `./chapters/introduction.tex`. If you want to add other section, do so by creating the relative tex file in the appropriate folder; the add it to the main document by including it in the `main.tex` file: `\include{path/to/document.tex}`.

<!-- Tip Alert -->
<div class="alert alert-tip">
  <i class="fa-regular fa-lightbulb"></i><strong class="note-title">Tip</strong>
  <p>
    If you are having trouble with anything, I suggest you refer to the Overleaf tutorials. Usually, you can find everything you may need there. Moreover, I suggest the <a href="https://github.com/PacktPublishing/LaTeX-Cookbook">LaTeX Cookbook</a> by Stefan Kottwitz, a book that teaches you how to solve common problems when using LaTeX.
  </p>
</div>

### Customization

You can customize how things look in the `SciThesis.cls`file. Here, you can manage packages and other layout preferences.

You can customize how theorems, code portions, labels, and other things look. 

The easiest thing you can customize is the main color for the Chapters and links: 

```latex
40 \definecolor{maincolor}{RGB}{51,127,128}
```

Here, you can change the RGB definition to any color you want. The default one is teal.

## What's next?

This is just an introductory post to get this template up and running. In the next weeks, I will write more specific tutorials on how to handle common situations you may encounter when writing your thesis, starting with bibliography management. 

See you next time!