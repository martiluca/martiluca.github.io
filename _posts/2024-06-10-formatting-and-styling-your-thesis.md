---
layout: distill
title: Formatting and styling your thesis
date: 2024-06-10
description:  Comprehensive guide on customizing the look and feel of your thesis, including fonts, headings, page layout, and margins. Present your work professionally and meet institutional formatting requirements!
tags: formatting thesis latex template stem
categories: LaTeX
featured: true

authors:
​    - name: Martina Lucà
---

<div class="alert alert-note">
    <div class="title">
        <span>Important</span>
        <span><i class="fa-regular fa-message"></i></span>
    </div>
    <p>
    	This post will refer mainly to how to do all these things using my template (<a href="https://github.com/martiluca/SciThesis">SciThesis</a>).
    </p>
    <p>
    	You can still follow along and implement them in your LaTeX document. Keep in mind that all these things will probably be more complicated to implement if you are using another template.
    </p>
</div>

## Fonts

Some Universities demand a specific font to be used in your thesis, while others leave the choice to you.  Selecting the right fonts can significantly impact the readability and overall feel of your thesis. LaTeX offers multiple ways to customize fonts, ranging from basic packages to advanced configurations.

### SciThesis: using `fontspec` with XeLaTeX or LuaLaTeX

I chose this method for my thesis and the template to achieve precise control over the fonts. The downside is that it requires using XeLaTeX or LuaLaTeX compilers. 

If you open the `SciThesis.cls` file, you will find the font configuration as follows:

```latex
% Fonts 
% !! Use XeLaTeX or LuaLaTeX compilers !!
\usepackage{fontspec}
\setmainfont{MinionPro-Regular.otf}[
    Path = ./settings/fonts/ ,
    BoldFont = MinionPro-Bold.otf ,
    ItalicFont = MinionPro-It.otf ,
    BoldItalicFont = MinionPro-BoldIt.otf ]

\setmonofont{JetBrainsMono-Light.ttf}[
    Path = ./settings/fonts/ ,
    BoldFont = JetBrainsMono-Bold.ttf ,
    ItalicFont = JetBrainsMono-Italic.ttf ,
    BoldItalicFont = JetBrainsMono-BoldItalic.ttf ]
```

You can see that I chose the MinionPro font as the main font and JetBrainsMono as the mono font (mainly to display code nicely). 

You can change fonts by downloading the appropriate files, putting them in the fonts folder, and changing the parameters of `\setmainfont` and `\setmonofont`. Don't forget to change also the font names for bold, italic, and bolditalic. 

### Other methods for setting fonts

For the sake of completeness, this section will include other methods for setting fonts. These are easier to use and do not require the use of XeLaTeX or LuaLaTeX.

You can find a comprehensive list of fonts for LaTeX in the [LaTeX Font Catalogue](https://tug.org/FontCatalogue/).

#### `times`and `mathptmx`

These packages provide a way to set Times New Roman as the main text font and to adjust math fonts accordingly.

```latex
\usepackage{times}
\usepackage{mathptmx}
```

#### `mathpazo` 

This package sets Palatino as the main text font and adjusts math fonts to match.

```latex
\usepackage{mathpazo}
```

####  `helvet` and `courier`

For setting Helvetica as the sans-serif font and Courier as the monospaced font.

```latex
\usepackage{helvet}
\renewcommand{\familydefault}{\sfdefault}
\usepackage{courier}
\renewcommand{\ttdefault}{\rmdefault}
```

####  `libertine`

This package provides a set of high-quality fonts, including Linux Libertine for text and Linux Biolinum for sans-serif text.

```latex
\usepackage{libertine}
\usepackage[libertine]{newtxmath}
```

#### Combining different font families with `sectsty`

You can use the `sectsty` package to change fonts for different sections of the document.

```latex
\usepackage{sectsty}
\sectionfont{\fontfamily{phv}\selectfont} % Helvetica for section titles
\subsectionfont{\fontfamily{ptm}\selectfont} % Times New Roman for subsections
```

### Include icons in your document with FontAwesome

[FontAwesome](https://fontawesome.com/) provides a collection of icons that can be easily integrated into your LaTeX document using the `fontawesome5` package. 

To use FontAwesome in your LaTeX document, add the following line to your preamble:

```latex
\usepackage[fixed]{fontawesome5}
```

You can then include icons in your text like this:

```latex
\faGithub  % GitHub icon
\faTwitter  % Twitter icon
\faEnvelope  % Envelope (email) icon
```

## Headings

Headings play a crucial role in the visual appeal and readability of your thesis. Here, I will tell you what I did in the template and how, and I will give you an alternative that gives you ready-to-use styles to choose from.

###  `titlesec` for custom chapter styles

In my template I chose to change just the chapter style. You can see it and change it in the `SciThesis.cls`  file:

```latex
% Chapter style %
\usepackage{titlesec, blindtext}
\newcommand{\hsp}{\hspace{20pt}}
\titleformat{\chapter}[hang]{\Huge\bfseries}{\thechapter\hsp\textcolor{teal!40!white}{$\vert$}\hsp}{0pt}{\Huge\bfseries}
```

This configuration:

- Utilizes the `titlesec` package.
- Defines a new command `\hsp` for horizontal space.
- Formats chapter titles with a hanging layout, large bold font, and a vertical teal line between the chapter number and title.

### `fncychap` fast and easy chapter styling

You can play with the `titlesec` package to achieve the precise style you want, but if you are a beginner, chances are that you don't know how to do that, and, more importantly, you don't want to spend time customizing everything. The `fncychap` package provides several predefined chapter styles that are easy to implement. 

Here's how you can use it:

```latex
% Chapter Style %
\usepackage[Bjarne]{fncychap} %Options: Sonny, Lenny, Glenn, Conny, Rejne, Bjarne, Bjornstrup
```

This package allows you to choose from the following styles: `Sonny`, `Lenny`, `Glenn`, `Conny`, `Rejne`, `Bjarne`, and `Bjornstrup`. Each of them offers a unique look for chapter headings. You can have a look [here](https://ctan.org/pkg/fncychap) to see some examples; the style I personally like the most is Bjarne.

## Page Layout

Sometimes, you need to comply with certain standards. The `geometry `package allows you to adjust the page geometry:

```latex
\usepackage{geometry}
\geometry{
    top=3.0cm,
    bottom=3.0cm,
    outer=3.0cm,
    inner=4.0cm
}
```

For personal preference, I chose to remove the paragraph indentation with the following command:

```latex
\setlength{\parindent}{0em} % no indentation
```

To bring it back, simply comment or remove this line.

Another useful package is `setspace`. It provides commands and environments for changing the spacing of your text. In my template, I used the following line to set it to 1.5.
`
```latex
\onehalfspacing % line-spacing
```

In general, the commands `\singlespacing`, `\onehalfspacing`, and `\doublespacing` can be used in the document preamble or within the document body to change the spacing in part or all of your document.

## Wrapping Up

These were the basics; many more portions of code control the document's style. Feel free to explore and experiment with them to learn more.

Next week we will learn more advanced layout customization, including page numbering, headers, and footers.

Happy writing, and see you next time!
