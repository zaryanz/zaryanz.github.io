---
layout: post
title: Compress HTML in your Jekyll site
subtitle:
tags: [jekyll, compress, html]
comments: true
---

Although compressing and minifying CSS and JavaScript is a common practice, doing the same with HTML is usually neglected. I recently discovered <a href="https://github.com/penibelst/jekyll-compress-html" target="_blank">jekyll-compress-html</a>, a Jekyll plugin that helps you do just that!
Moreover, this plugin is written in pure Liquid, so it does not come with any additional dependencies.

Let's see how you can compress HTML in your site in a few simple steps:

- Download the latest release of the plugin's <a href="https://github.com/penibelst/jekyll-compress-html/releasescompress.html" target="_blank">compress.html</a>.

- Place this HTML file in your `_layouts/` directory.

- In your highest level layout, usually `default.html`, add the following front matter:

```md
---
layout: compress
---

<html>
...
</html>
```

Now, all your markup will be processed by the `compress` layout.

For this website, I observed load time improvements and a 10% reduction in HTML file sizes; however, that number can quickly go up to 20% or 30% depending on how big your HTML files are and how much whitespace they contain.

If you would like to fine-tune your compression, configuration options for the library can be directly specified in the `config.yml` file:

```md
compress_html:
  clippings: []
  comments: []
  endings: []
  ignore:
    envs: []
  blanklines: false
  profile: false
  startings: []
```

More information about these settings can be found in the <a href="https://jch.penibelst.de/" target="_blank">documentation</a>.

PS: After introducing HTML compression, some JavaScript functionality broke for me. However, upon digging into the documentation, I found out that jekyll-compress-html doesn't play well with `//` comments, so I replaced those with `/* */` instead, and everything worked perfectly.

Thanks for reading!
