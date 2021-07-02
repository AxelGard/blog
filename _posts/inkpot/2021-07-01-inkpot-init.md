---
layout: post
title:  "inkpot auto generate docs "
date:   2021-07-01 20:00:00 +0200
categories: inkpot
---

I was looking to add some documentation to my [cira](https://github.com/AxelGard/cira) project.
I did not feel like writing a bunch of text and going thurhe all of the function.

so I took a look at some of the common solution in particular Sphinx. They seem to be used a lot so way not, I thought.
I started generating files but I ran in to problems and it semd more difficult then it needed to be. I had previously used the wiki page on my GitHub page and it was nice to do it in that way.

But now I needed to generate documentation from my code in a way were it would output the documentation as markdown. I also needed text for the documentation.However I released that my doc string would work as documentation for the project.

Thus I created **[inkpot](https://github.com/AxelGard/inkpot)**.
I wanted to be able to generate documentation from the docstrings in my Python code and then simply add it to my GitHub wiki page.

The first version of inkpot was just a small script taht did not even have a repo. But I released that I might need this in other projects so why not make it in to a proper package.


![inkpot](https://cdn.pixabay.com/photo/2014/04/05/12/20/ink-316909_960_720.jpg)
