---
layout: post
title: "Tufte-style Jekyll blog"
date: 2020-04-13 09:46:04
categories: jekyll css
---

is an attempt to create a website design with the look and feel of Edward Tufte's books and handouts. Tufte’s style is known for its extensive use of sidenotes, tight integration of graphics with text, and well-set typography.<!--more--> The idea for this project is essentially cribbed wholesale from Tufte and R Markdown's Tufte Handout format This page is an adaptation of the [Tufte Handout PDF](http://rmarkdown.rstudio.com/examples/tufte-handout.pdf).

## Jekyll customizations

### The SASS settings file

## Fundamentals

### Color

### Headings

Tufte CSS uses `<h1>` for the document title, `<p>` with class `code` for the document subtitle, `<h2>` for section headings, and `<h3>` for low-level headings. More specific headings are not encouraged. If you feel the urge to reach for a heading of level 4 or greater, consider redesigning your document:
[It is] notable that the Feynman lectures (3 volumes) write about all of physics in 1800 pages, using only 2 levels of hierarchical headings: chapters and A-level heads in the text. It also uses the methodology of _sentences_ which then cumulate sequentially into _paragraphs_, rather than the grunts of bullet points. Undergraduate Caltech physics is very complicated material, but it didn’t require an elaborate hierarchy to organize.
<cite>[http://www.edwardtufte.com/bboard/q-and-a-fetch-msg?msg_id=0000hB](http://www.edwardtufte.com/bboard/q-and-a-fetch-msg?msg_id=0000hB)</cite>

### Text

### Lists

Tufte points out that while lists have valid uses, they tend to promote ineffective writing habits due to their “lack of syntactic and intellectual discipline”. He is particularly critical of hierarchical and bullet-pointed lists. So before reaching for an HTML list element, ask yourself:

- Does this list actually have to be represented using an HTML ul or ol element?
- Would my idea be better expressed as sentences in paragraphs?
- Is my message causally complex enough to warrant a flow diagram instead?

This is but a small subset of a proper overview of the topic of lists in communication. A better way to understand Tufte’s thoughts on lists would be to read “The Cognitive Style of PowerPoint: Pitching Out Corrupts Within,” a chapter in Tufte’s book _Beautiful Evidence_, excerpted at some length by Tufte himself [on his website](http://www.edwardtufte.com/bboard/q-and-a-fetch-msg?msg_id=0002QF). The whole piece is information-dense and therefore difficult to summarize. He speaks to web design specifically, but in terms of examples and principles rather than as a set of simple do-this, don’t-do-that prescriptions. It is well worth reading in full for that reason alone.

For these reasons, Tufte CSS encourages caution before reaching for a list element, and by default removes the bullet points from unordered lists.

## Figures

### Full Width Figures

If you need a full-width image or figure, another custom liquid tag is available to use. Oddly enough, it is named 'fullwidth', and this markup:

`{{ "{% fullwidth 'assets/img/napoleons-march.png' 'Napoleon's March *(Edward Tufte’s English translation)*' "}} %}`

Yields this:

{% fullwidth 'assets/img/napoleons-march.png' "Napoleon's March *(Edward Tufte’s English translation)*" %}

### Main Column Figures

Besides margin and full width figures, you can of course also include figures constrained to the main column. Yes, you guessed it, a custom liquid tag rides to the rescue once again:

`{{ "{% maincolumn 'assets/img/export-imports.png' 'From Edward Tufte, *Visual Display of Quantitative Information*, page 92' "}} %}`

yields this:

{% maincolumn "assets/img/exports-imports.png" "From Edward Tufte, *Visual Display of Quantitative Information*, page 92" %}

## Sidenotes and Margin notes

One of the most prominent and distinctive features of Tufte's style is the extensive use of sidenotes and margin notes. Perhaps you have noticed their use in this document already. You are very astute.

There is a wide margin to provide ample room for sidenotes and small figures. There exists a slight semantic distinction between _sidenotes_ and _marginnotes_.

### Sidenotes

Sidenotes display a superscript. The _sidenote_ Liquid tag contains two components. The first is an identifier allowing the sidenote to be targeted by the twitchy index fingers of mobile device users so that all the yummy sidenote goodness is revealed when the superscript is tapped. The second components is the actual content of the sidenote. Both of these components should be enclosed in single quotes. Note that we are using the CSS 'counter' trick to automagically keep track of the number sequence on each page or post. On small screens, the sidenotes disappear and when the superscript is clicked, a side note will open below the content, which can then be closed with a similar click. Here is the markup for the sidenote at the beginning of this paragraph:
Enclose the code block in three backticks, followed by a space and then the language name, like this:
