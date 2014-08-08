---
layout: post
title: "Customise HPSTR Jekyll Theme"
description: ""
category: Web
tags: [Jekyll]
comments: true
share: true
---

## About

Based on unchanged `hpstr-jekyll-theme-master.zip` from [GitHub](https://github.com/mmistakes/hpstr-jekyll-theme/archive/master.zip) at `2014-08-07 16:44:14` whose features include animated navigation, images, table rules and buttons. Jekyll use Liquid markup language so you will see many `{{"{% something "}}%}`. Besides, I just discovered MathJax is easy to set up and renders LaTeX nicely. 

## Highlights

- [Disqus](#disqus)
- [With Chinese characteristics](#chinese)
- [I don't like the category in permalinks](#nocateg)
- [I don't like 'Latest Posts' title](#nolate)
- [Reading time in decimals](#decimal)
- [Clean post tails](#whatrelate)
- [Display post tags](#showtag)
- [Display post preview](#postpreview)
- [Sort by months in archives](#monthsort)
- [Correct case for categories](#rightcase)
- [The first paragraph shouldn't have a bigger font size](#nolead)
- [Highlight code in colour](#codecolor)
- [Old: Generate Table of Contents](#autotoc)

## Contents

- [Configuration files](#config)
- [Writing](#writing)
- [Appendix: Highlight Liquid codes](#liquid)

<!--more-->

## Tree

{% highlight bash %}
├── _config.yml
├── _includes
│   ├── head.html
│   ├── navigation.html
│   └── ...
├── _layouts
│   ├── page.html
│   ├── post.html
│   └── ...
├── index.html
├── archives.html
├── categories.html
├── assets
│   ├── less
│   │   ├── variables.less
│   │   └── ...
│   └── ...
└── ...
{% endhighlight %}

### <a name="config"></a> _config.yml

1. **Blog info:** Change `title`, `description`, `owner`'s `name`.

2. <a name="disqus"></a> **Disqus (comment system):** Input your `disqus_shortname` which can be found on <https://disqus.com/>. Input correctly will get you out of some 'troubles' related to Disqus.

3. <a name="chinese"></a>**Chinese SNS links (in navigation):** Input your SNS ID at `twitter`, `github`, etc. I added Chinese SNS: `zhihu`, `v2ex`, `weibo`, `renren`, `douban`. → Don't worry about using URL or ID, because you will set up icons and icon links later.

4. **Google Analytics (count blog view; track readers' locations):** Input your Google Analytics ID at `google_analytics` which can be found at <http://www.google.com/analytics/> > `Admin` tab > `PROPERTY` column > `Tracking Info` > `Tracking Code` > find the alphameric starts that `UA-`. By the way, [Quicklytics](https://itunes.apple.com/cn/app/quicklytics-google-analytics/id354890919?l=en&mt=8) and [Analytiks](https://itunes.apple.com/cn/app/analytiks-google-analytics/id427268553?l=en&mt=8) let you view statistics at iOS. I use Analytiks but don't recommend it, because it is way too basic compared to Quicklytics.

5. **Navigation cleanup:** You can use and customise `links` or delete `links` part.

6. **Misc.:** Change `timezone` to yours which can be found on `http://en.wikipedia.org/wiki/List_of_tz_database_time_zones`.

7. <a name="nocateg"></a>**Post links:** I don't like the `/:categories/:title/` format of permalinks. Categories are susceptible to changes, and post titles are less susceptible to the problem. For now I change `permalink` to `/:title/`. However, one issue can be arisen, if the post title is too long and broken into ugly multiple lines on your blog, and you want to change the post title. As a result, the old link for the post will be broken. But for now, I have no solution to the problem.

8. **Number of posts per page:** You may want to raise `5` `paginate` if you truncate your post list/index page, afterwards, `index.html`, (because you will edit the file instead of others,) that is, display post preview instead of full post content. My current `paginate` is set to `10`.

9. **Remarks:** Note that the markdown engine in use is kramdown, and kramdown use coderay to highlight code blocks, I guess. Given the current code highlighter is pygments, you can ignore coderay settings, I guess. Besides, I have a question. `node_modules` is in `exclude` list, why it's still pushed to GitHub?

### head.html

<a name="nolate"></a>**Home Title:** I don't like `Latest Posts - lsfalimis`, so I change line 2's (L2) `{{"{% if page.title "}}%}` to `{{"{% if page.title and page.title != site.title "}}%}`. Why can't I leave `title` in `index.html` blank? Give it a try. By the way, I know nothing about coding. If there are simpler codes, please leave the comments, thank you!

### navigation.html

**Use SNS icons:** Choose icons at [here](http://fortawesome.github.io/Font-Awesome/icons/). Wish I could make icons of V2EX, Zhihu and Douban...

### page.html

- <a name="decimal"></a>**Reading time in decimals:** The default display of reading time is fraction. It's quite unpleasing. Given the lesser reading times occur more frequently for my blog, I set up conditionals as follows. Messy code...

{% highlight html %}
{{"{% assign readtime = content | number_of_words | divided_by:site.words_per_minute"}}%}
{{"{% if readtime <= 1 "}}%}1 min. read
{{"{% elsif readtime <= 2"}}%}2 min. read
{{"{% elsif readtime <= 3"}}%}3 min. read
{{"{% elsif readtime <= 4"}}%}4 min. read
{{"{% elsif readtime <= 5"}}%}5 min. read
{{"{% elsif readtime <= 6"}}%}6 min. read
{{"{% elsif readtime <= 7"}}%}7 min. read
{{"{% elsif readtime <= 8"}}%}8 min. read
{{"{% elsif readtime <= 9"}}%}9 min. read
{{"{% elsif readtime <= 10"}}%}10 min. read
{{"{% else "}}%}10+ min. read{{"{% endif "}}%}
{% endhighlight %}

- **Misleading Google Plus '+1' sign:** It seems that the post has already gotten a '+1' on Google Plus. No... So I change `+1` to `Share`.

### post.html

<a name="whatrelate"></a>Redo the steps in `page.html` here. Next I will talk about **`Read More`**. I have no idea how `site.related_posts` are chosen, so I replace this part with 'next post' and 'previous post'. From `{{"{% if site.related_posts.size "}}%}` to `</div><!-- /.read-more -->` are replaced by the code as follows:

{% highlight html %}
<div class="read-more">
    <div class="read-more-content">
      {{"{% if page.next.url "}}%}
      <h3><a href="{{"{{ site.url "}}}}{{"{{ page.next.url "}}}}" title="{{"{{ page.next.title "}}}}">&#8592; {{"{{ page.next.title "}}}}</a></h3>
      <span>Published {{"{{ page.next.date | date: "%d %b %Y" "}}}}</span>
      {{"{% endif "}}%}
      {{"{% if page.next.url and page.previous.url"}}%}<hr>{{"{% endif "}}%}
      {{"{% if page.previous.url "}}%}
      <h3><a href="{{"{{ site.url "}}}}{{"{{ page.previous.url "}}}}" title="{{"{{ page.previous.title "}}}}">{{"{{ page.previous.title "}}}} &#8594;</a></h3>
      <span>Published {{"{{ page.previous.date | date: "%d %b %Y" "}}}}</span>
      {{"{% endif "}}%}
    </div><!-- /.read-more-content -->
</div><!-- /.read-more -->
{% endhighlight %}

### index.html

Firstly, redo 'reading time' step.

- **Head image:** Change `image`'s `feature`. The one I use comes from [Unsplash](http://unsplash.com/) at which you can find Public Domain images that possess No Copyright.

- <a name="showtag"></a>**Post tags:** After post date and before comment hyperlink, I'd like to display tags and the code is:

{% highlight html %}
{{"{% for tag in post.tags "}}%}&nbsp; &bull; &nbsp; <a href="{{"{{ site.url "}}}}/tags/#{{"{{ tag "}}}}" title="Pages tagged {{"{{ tag "}}}}">{{"{{ tag "}}}}</a>{{"{% unless forloop.last "}}%}{{"{% endunless "}}%}{{"{% endfor "}}%}
{% endhighlight %}

- <a name="postpreview"></a>**Post preview:** Replace `{{"{{ post.content "}}}}` to the the following code, and when you are writing, if need, add `<!--more-->` in your post markdown file. The part before the tag will be displayed in post preview.

{% highlight html %}
{{"{% if post.content contains '<!--more-->' "}}%}
  {{"{{ post.content | split:'<!--more-->' | first %"}}}}
  <p><a class="btn btn-info" href="{{"{{ post.url "}}}}">Read more</a></p>
{{"{% else "}}%}
  {{"{{ post.content "}}}}
{{"{% endif "}}%}
{% endhighlight %}

### archives.html

I rename posts.html to archives.html.

<a name="monthsort"></a>**Sort by months:** To do it, another loop to repeat month is needed. Firstly, I capture or declare `this_month` and `next_month`; in liquid loop, `this_something` is like x and another variable is declare to compare with x in conditional in order to realise a loop. `forloop.first` denote the first loop, and I put a h3 title of `this_month` here. `forloop.last` denote the loops except the first loop, and I add a conditional here to produce all other h3 month title that doesn't include the month in the first loop. The code is as follows:

{% highlight html %}
{{"{% for post in site.posts "}}%}
    {{"{% capture this_year "}}%}{{"{{ post.date | date: "%Y" "}}}}{{"{% endcapture "}}%}
    {{"{% capture next_year "}}%}{{"{{ post.previous.date | date: "%Y" "}}}}{{"{% endcapture "}}%}
    {{"{% capture this_month "}}%}{{"{{ post.date | date: "%b" "}}}}{{"{% endcapture "}}%}
    {{"{% capture next_month "}}%}{{"{{ post.previous.date | date: "%b" "}}}}{{"{% endcapture "}}%}

    {{"{% if forloop.first "}}%}
    <article>
      <h2 id="{{"{{ this_year "}}}}-ref">{{"{{ this_year "}}}}</h2>
      <h3 id="{{"{{ this_month "}}}}-ref">{{"{{ this_month "}}}}</h3>
    {{"{% endif "}}%}

      <li class="entry-title"><a href="{{"{{ site.url "}}}}{{"{{ post.url "}}}}" title="{{"{{ post.title "}}}}">{{"{{ post.title "}}}}</a></li>
      
    {{"{% if forloop.last "}}%}
    </article>
    {{"{% else "}}%}
        {{"{% if this_month != next_month "}}%}
        <h3 id="{{"{{ next_month "}}}}-ref">{{"{{ next_month "}}}}</h3>
        {{"{% endif "}}%}
        {{"{% if this_year != next_year "}}%}
        </article>
        <article>
          <h2 id="{{"{{ next_year "}}}}-ref">{{"{{next_year"}}}}</h2>
          <h2 id="{{"{{ next_month "}}}}-ref">{{"{{next_month"}}}}</h2>
        {{"{% endif "}}%}
    {{"{% endif "}}%}
{{"{% endfor "}}%}
{% endhighlight %}

### categories.html

{% highlight bash %}
cat tags.html > categories.html
{% endhighlight %}

With Sublime Text replacing's case sensitive on, replace `tags` with `categories`, replace `Tags` with `Categories`, then replace `tag` with `category`, and then replace `class="category"` with `class="tag"`.

<a name="rightcase"></a>**Category case:** By default, categories are changed by Jekyll to lowercase for better processing. We can capitalise categories, but some special terms are exceptions, such as, 'iOS' and 'LaTeX'. Therefore, I replace `<h2 id="{{"{{ this_word "}}}}">{{"{{ this_word "}}}}</h2>` with a conditional:

{% highlight html %}
{{"{% if this_word == 'ios' "}}%}<h2 id="{{"{{ this_word "}}}}">iOS</h2>
{{"{% else "}}%}<h2 id="{{"{{ this_word "}}}}">{{"{{ this_word | capitalize "}}}}</h2>{{"{% endif "}}%}
{% endhighlight %}

### variables.less

It's the first time I saw the code of node.js and less, wow! You can have Grunt generate css from less for you. Download node.pkg from [here](http://nodejs.org/download/). Install the pkg and run `sudo npm install -g grunt-cli`. I prefer Menlo among monospace fonts, so I edit the variables.less, and then given package.json is already written by the theme author, run `grunt` at the `lsfalimis.github.io` directory. New CSS files are generated.

## Writing

- <a name="nolead"></a>**Disable lead paragraph effect:** Use Inspect Element and find that the keyword `first-child`, then search it using Finder, and edit `main.css` that is not under `_site`: change `font-size` to `1rem`.

- <a name="codecolor"></a>**Code highlighting:** I don't get how kramdown code highlighting works, and by wrapping the code block with `~~~`, I can't produce coloured highlighting. So I use pygments by the syntax where you can replace bash with languages in the [list](http://pygments.org/languages/). I don't know why LaTeX is actually supported but not in the list.

{% highlight html %}
{{"{% highlight bash "}}%}
code
{{"{% endhighlight "}}%}
{% endhighlight %}

- **LaTeX rendering:** For now, I use the simplest method. Include the code in post markdown file. Example see the [post](http://lsfalimis.github.io/latex-notes/).

{% highlight html %}
<script type="text/javascript"
    src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>
{% endhighlight %}

- **Display images in columns and rows:** You can set the class to `half` if there are two images in a row, or `third` if three; it has feature like hyperlinks and caption.

{% highlight html %}
<figure class="half">
  <a href="bigger_jpg1"><img src="jpg1" alt=""></a>
  <img src="jpg2" alt=""></a>
  <img src="jpg3" alt=""></a>
  <img src="jpg4" alt=""></a>
  <figcaption>This is a caption.</figcaption>
</figure>
{% endhighlight %}

- **Displays rules in tables:** Append `{: rules="groups"}` as a new line to a table.

- **Display buttons, mostly, download buttons**, like &nbsp;&nbsp; <a href="https://github.com/lsfalimis/Qian-KM-Macros" class="btn btn-info">KM Macros</a> &nbsp;&nbsp; using the following code where by default `btn btn-info` class is blue and `btn` class is black. You can change the colours in `variables.less`.

{% highlight html %}
<a href="https://github.com/lsfalimis/Qian-KM-Macros" class="btn btn-info">KM Macros</a>
{% endhighlight %}

- <a name="autotoc"></a>**Generate Table of Contents (ToC):** It's a review about kramdown's feature. Simple include this to let kramdown generate ToC for you:

{% highlight html %}
## Contents
{:.no_toc}

* 
{:toc}
{% endhighlight %}

## <a name="liquid"></a> Appendix: Highlight Liquid codes

We need to look at `{{"{% something "}}%}` (in my markdown, `{{"{{"}}"{{"{%"}} something "}}%}`) and `{{"{{ something "}}}}` (in my markdown, `{{"{{"}}"{{"{{"}} something "}}}}`). Note that if we want to display `{{"{% something "}}%}` and `{{"{{ something "}}}}`, we we don't need to escape `%}` and `}}`. What we need to escape are `{{"{%"}}` and `{{"{{"}}`, because if we put `%}` or `}}` in inline code or in a code block in markdown file, Jekyll will not report error. However, if we replace any of them with `{{"{%"}}` or `{{"{{"}}` in markdown file, Jekyll will report error. Therefore we have to wrap `{{"{%"}}` or `{{"{{"}}` with `{{"{{"}}"` and `}}`. Let `x` denote special symbols to escape in Liquid, then in order to highlight them in html, we have to write `{{"{{"}}"x"}}` in markdown file.

What if I copied and pasted Liquid code from Jekyll configuration files to markdown file? If you haven't wrapped code blocks, use kramdown's `~~~ language` syntax first, and at the end replace `~~~` with `{{"{% highlight language "}}%}` and `{{"{% endhighlight "}}%}`. If you have already wrapped code blocks with `{{"{% highlight language "}}%}` and `{{"{% endhighlight "}}%}`, the case I have today, do these:

1. Replace `{{"{{"}}` with `{{"{{"}}"{{"{{"}}`.
2. Replace `}}` with `"}}}}`.
3. Replace `{{"{%"}}` with `{{"{{"}}"{{"{%"}}`.
4. Replace `%}` with `"}}%}`.
5. Replace `{{"{{"}}"{{"{%"}} endhighlight "}}%}` with `{{"{% endhighlight "}}%}`.
6. Replace `{{"{{"}}"{{"{%"}} highlight language "}}%}` with `{{"{% highlight language "}}%}`. If there are many languages highlighted in your markdown file, do this step for each of them.

