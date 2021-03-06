---
title: Using Pandoc style footnotes in Eleventy
date: 2021-02-28T16:24:00+01:00
description:
  A brief explanation how to enable Pandoc style footnotes in Markdown on a site
  generated with Eleventy (11ty)
keywords:
  - eleventy
  - 11ty
  - footnote
  - pandoc footnote
  - markdown
  - markdown-it
  - markdown-it-footnote
---

Up until recently this blog was generated by [Hugo][1]. A few weeks ago I
decided to jump on the bandwagon and switch to [Eleventy][2]. All posts were
already written in Markdown so the conversion was fairly pain free.

In the process I had missed that footnotes were broken on these [two][3]
[pages][4]. I don't use footnotes very often but thought it would be nice for
them to work again.

I remembered that the version of Hugo I started out with, uses [Blackfriday][5]
to process Markdown[^1]. Blackfriday supports [Pandoc style footnotes][6].

Eleventy uses [markdown-it][7] to process Markdown files. It is possible to
configure markdown-it by using your own instance using Eleventy's configuration
API.

There is a plugin for Markdown-it called [markdown-it-footnote][8] that also
uses Pandoc style footnotes.

Here is the relevant part of the configuration.

```js
// .eleventy.js

const markdownIt = require('markdown-it');
const markdownItFootnote = require('markdown-it-footnote');

module.exports = (eleventyConfig) => {
  eleventyConfig.setLibrary('md', markdownIt().use(markdownItFootnote));
  // more settings
};
```

As can be seen below. Footnotes are working once again :)

Thanks [Michael][10] for proofreading.

[^1]:
    In Hugo [0.60.0][9] the default library used for Markdown was changed from
    Blackfriday to Goldmark.

[1]: https://gohugo.io
[2]: https://www.11ty.dev
[3]: /2018/09/creating-bundles-with-webpack
[4]: /2019/01/css-custom-properties-in-sass
[5]: https://github.com/russross/blackfriday
[6]: https://pandoc.org/MANUAL.html#footnotes
[7]: https://github.com/markdown-it/markdown-it
[8]: https://github.com/markdown-it/markdown-it-footnote
[9]: https://gohugo.io/news/0.60.0-relnotes/
[10]: https://michaelhastrich.nl
