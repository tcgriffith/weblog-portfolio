---
title: Xaringan presentations with blogdown
author: Peter Baumgartner
date: '2018-07-21'
categories:
  - blogdown
  - demo
tags:
  - hugo-academic
  - xaringan
slug: presentations-with-xaringan
authors:
  - Peter Baumgartner
draft: no
header:
  caption: ''
  image: ''
  preview: yes
summary: This post demonstrates how to present slideshows with the `Xaringan` package. I explain how to integrate slideshows with `Xaringan` into blogdown via internal and external links.
---

{{% toc %}}

# How to integrate Xaringan in blogdown?

I am following in this short post the detailed description by [Tim Mastny](https://timmastny.rbind.io/)  in his blog entry [Embed Slides in Your Blog](https://timmastny.rbind.io/blog/embed-slides-knitr-blogdown/). Please read his article --- especially the second half of it, where he is explaining the [installation procedure](https://timmastny.rbind.io/blog/embed-slides-knitr-blogdown/#upload-your-slideshow-to-your-website).

## Refer to an external slideshow



```r
knitr::include_url('https://timmastny.rbind.io/slides/first_presentation')
```

<iframe src="https://timmastny.rbind.io/slides/first_presentation" width="672" height="400px"></iframe>

## Refer to an internal slideshow



```r
knitr::include_url('/slide/xaringan-demo.html', height = "505px")
```

<iframe src="/slide/xaringan-demo.html" width="672" height="505px"></iframe>

## Summary

Both example above are the same as in Tim's article. 

**Two observations:**

1. There is no need to load the Xaringan package with `library(xaringan)`. At the moment I do not understand why this is not necessary. 
2. In the second example the gray left and right margin has disappeared. The parameter `height = "505px"` does this. To tweak this I had to experiment with the optimal pixel value. (Maybe there is a better way to tweak this parameter with the right value, e.g. taking the value from the css.) 

The height paramter solves one of the problem mentioned by Tim:

> I’m also investigating to see if I can trim the iframe so I only see the slides and not the gray bars on the side.


# How to present slides in full screen view?

Here I wanted to address his second issue:

> I’d like to be able to use a relative reference to the slideshow’s HTML file in the static/ directory, but I think knitr::include_url() requires a live URL. I’ll have to do more research.

## My first try: Using Markdown image links 

My first try was: `![](/slide/xaringan-demo.html/#5)`

![](/slide/xaringan-demo.html#5)

It generates a kind of a thumbnail. Maybe this is theme dependent. I once tried it out in another theme and got other sizes, e.g. over the whole widht of the text column.Presumably this has to be done in one of the css files of the corresponding template. 

A kind of a thumbnail was not the result I was looing for, but it could become handy anyway. For instance as a reference in an article. With the slide number behind the URL one can reference easy every slide frame directly.

## My second try: Usind Markdown with absolute links

The second try is a [link in standard markdown](https://portfolio.peter-baumgartner.net/slide/xaringan-demo#1) to the file. It opens up the full screen presentation. The code:

`The second try is a [link in standard markdown](https://portfolio.peter-baumgartner.net/slide/xaringan-demo#1) to the file.`

This is not ideal one needs always an internet connection for the presentation.

## My third try: Using Markdown with relative links

The third try is a  [relative link in Markdown](/slide/xaringan-demo.html) to the file. It opens up the full screen presentation. The code:

`The third try is a  [relative link in Markdown](/slide/xaringan-demo.html) to the file.`

## Summary 
This is the solution Tim was looking for. I myself tried several approaches in vain. Then I rememberd that there is a demo [blogdown-static website](https://github.com/yihui/blogdown-static) by Yihui Xie. There I found the solution!

# Summary and conclusion

This third approach solves the second question mentioned by Tim. And this is an important solution: With a simple relative link in Markdown can everyone present (Xaringan) slideshows without an internet connection in full screen view.

Sure there would have been always the possibility to go via the operation system to the file on the hard disk directly. But this is not very elegant and would complicate to present an integrated presentation via browser with other (multimedia) elements. One reason out of 11 [why Xihui Yui hotly favours remark.js](https://yihui.name/en/2017/08/why-xaringan-remark-js/) is the feature that you can press the back button in the browser and you will go back to the page from which you visited the slides, instead of reading the slides in the reverse order again. 

The next thing on my agenda is to learn how to apply Xaringan for every day use. I have to read and try out 

+ the example slides ([Xaringan](/slide/xaringan-demo.html) and [remark](https://remarkjs.com/#1)), 
+ the [readme file](https://github.com/gnab/remark) at the remark GitHub site and
+ the documentation in the [remark wiki](https://github.com/gnab/remark/wiki). 

Then I will transfer --- as a first real live application --- my slideshows written with [reveal.js](https://revealjs.com/) stored at my abandoned site at https://notes.peter-baumgartner.net/slide/ to this new site here.

***

To inspect the the full code of this post [follow this link to my GitHub repo](https://github.com/petzi53/weblog-portfolio/blob/master/content/post/2018-07-18-presentations-with-xaringan.Rmd).

