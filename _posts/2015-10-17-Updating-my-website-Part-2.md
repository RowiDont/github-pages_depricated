---
layout: post
title: Updating my website Part 2
published: true
tags: ['Jekyll', 'HTML/CSS']
---

Working on my site this week has been a really good learning experience. Quite a few little things have been changed on this site since my last post two days ago. While they are hard to spot, a significant amount of code went into them.

### Pagination

If you scroll to the bottom of this page, you'll notice that you can now see the number of pages in this blog. The feature was suggested by a friend, and I think it adds a lot to the functionality of this blog. Through searching around, I found a [post on timble.net](http://www.timble.net/blog/2015/05/07/better-pagination-for-jekyll.html), which actually gave the jekyll code to create this, which is hosted [here on gihub](https://github.com/timble/jekyll-pagination). But there was no guide explaining how to implement it. At this point, I still had a very poor understanding of Jekyll.

{: .center}
![pagination-error](/images/pagination-error.PNG)

{: .center .caption}
Improper display of the pagination

The first step was getting the numbering to display inline, instead of in a list. I found out I needed to add the <code CSS>@import "jekyll-pagination";</code> to the styles.css sheet in my main directory. That is where all the SCSS files are imported and combined into one massive CSS file.

This is also when I learned about the folder /includes, and how to "include" those pages in my markdown. It turns out that you can essentially place html files inside other pages. _Includes_ pages are exactly that. The pagination file provided by timble.net is implemented in that way.


### Understanding the actual code behind the new pagination

The pagination was working, but one feature just didn't want to work properly.

{: .center}
![elipses-error](/images/elipses-error.PNG)

{: .center .caption}
The illusive ellipsis...

My first idea was to look at sites where it was working. I headed over to [http://www.nooku.org/blog/](http://www.nooku.org/blog/), and opened up DevTools. The difference between my site's HTML/CSS and his was immediately clear. In my HTML, the <code>li</code> element for the ellipsis was lacking the class <code>pages-indicator--active</code>, which included the line <code>display: inline-block;</code>.

Great, so I knew the basic issue. It seemed like even though the element was active, the HTML wasn't being updated to reflect that.

We'll need to dive a bit deeper into the pagination code to see where the problem was occuring. Check it out below:

{% highlight %}
{% assign limit = 5 %}
{% if site.paginate_limit %}
    {% assign limit = site.paginate_limit %}
{% endif %}
{% assign totalpages = paginator.total_pages %}
{% endhighlight %}
