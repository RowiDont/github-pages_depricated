---
layout: post
title: Updating my website Part 2
published: true
tags: ['Jekyll', 'HTML/CSS']
---

Working on my site this week has been a really good learning experience. Quite a few little things have been changed on this site since my last post two days ago. While they are hard to spot, a significant amount of code went into them.

### Pagination

If you scroll to the bottom of this page, you'll notice that you can now see the number of pages in this blog. The feature was suggested by a friend, and I think it adds a lot to the functionality of this blog. Through searching around, I found a [post on timble.net](http://www.timble.net/blog/2015/05/07/better-pagination-for-jekyll.html), which actually gave the jekyll code to create this, and is hosted [here on gihub](https://github.com/timble/jekyll-pagination). But there was no guide explaining how to implement it, and at that point, I still had a very poor understanding of Jekyll.

{: .center}
![pagination-error](/images/pagination-error.PNG)

{: .center .caption}
Improper display of the pagination

The first step was getting the numbering to display inline, instead of in a list. I found out I needed to add the <code CSS>@import "jekyll-pagination";</code> to the styles.css sheet in my main directory. That is where all the SCSS files are imported and combined into one massive CSS file.

This is also when I learned about the folder /includes, and how to "include" those pages in my markdown. It turns out that you can essentially place html files inside other pages. _Includes_ pages are exactly that. The pagination file provided by timble.net is implemented in that way.


### Understanding the actual code behind the new pagination

The pagination was working, but one feature just didn't want to work properly. The ellipsis between two non-consecutive numbers was not showing up.

{: .center}
![elipses-error](/images/elipses-error.PNG)

{: .center .caption}
The illusive ellipsis...

My first idea was to look at sites where it was working. I headed over to [http://www.nooku.org/blog/](http://www.nooku.org/blog/), and opened up DevTools. The difference between my site's HTML/CSS and his was immediately clear. In my HTML, the <code>li</code> element for the ellipsis was lacking the class <code>pages-indicator--active</code>, which included the line <code>display: inline-block;</code>.

Great, so I knew the basic issue. It seemed like even though the element was supposed to be active (since two non-consecutive numbers were next to each other), the HTML wasn't being updated to reflect that.

We'll need to dive a bit deeper into the pagination code to see where the problem was occurring. Check out the relevant excerpts below. I apologize for the rather messy looking brackets, I believe they are an unfortunate side effect of running both Jekyll and Kramdown on the same page:

{% highlight ruby %}
\{\% assign limit = 7 \%\}
\{\% if site.paginate_limit \%\}
    \{\% assign limit = site.paginate_limit \%\}
\{\% endif \%\}

\{\% assign totalpages = paginator.total_pages \%\}

\{\% if totalpages > limit \%\}
    \{\% for count in (2..paginator.total_pages) \%\}
        \{\% if count == dots_prev  \%\}
            \{\% assign indicator_first = ' pages-indicator--active' \%\}
        \{\% endif \%\}
        \{\% if count == dots_next and paginator.page < max_next \%\}
            \{\% assign indicator_last = ' pages-indicator--active' \%\}
        \{\% endif \%\}
        \{\% if forloop.first \%\}
            \{\% assign relative_first = paginator.page | minus: forloop.index | divided_by: 1 \%\}
        \{\% endif \%\}
        \{\% if forloop.last \%\}
            \{\% assign relative_last = paginator.page | minus: forloop.index | replace: '-', '' | divided_by: 1 | plus: 1 \%\}
        \{\% endif \%\}
    \{\% endfor \%\}
\{\% endif \%\}

<li class="pages-indicator \{\{ indicator_first \}\} pages-indicator--offset-\{\{ relative_first \}\}"><span aria-hidden="true">...</span><span class="sr-only">Skipped pages indicator</span></li>
{% endhighlight %}

I was initially frightened looking at this code. I don't even know for certain what language this is in (I know jekyll is written in Ruby, and this is nothing like the Ruby I have written), but I knew With enough patience I could solve my issue. I first went through and found the instances of <code>pages-indicator--active</code>. Based on the code it seemed like if a certain condition was met, the class was added to the ellipsis element called <code>pages-indicator</code>, thus making it visible.

So why wasn't this happening? My first guess was that the variable <code>paginator.total_pages</code> was never initiated in the code, and thus breaking the whole <code>for</code> loop. I quickly realized that it wasn't a local variable though. <code>paginator.total_pages</code> was created by jekyll, and it did in fact exist. So what was that number? Well, obviously it was the total number of pages I had: 6.

If you look at the <code>if</code> statement that initiates the `for` loop, you'll see the issue immediately. <code>if totalpages > limit</code> will return ```false``` when the limit is 7, and the number of total pages is 6. It turns out this code wasn't even running at all! So I changed the code to assign `limit` a value of 5. And just like that, the day was saved. This took me a while to work out, but I'm glad I stuck to it, instead of ditching the pagination feature.

### Writing my own jekyll code

My problems weren't over yet. The pagination was showing up on pages where it really shouldn't have. Like my _About_ page, or individual blog post pages. I knew how I wanted to solve this, but wasn't sure how to implement it. I wanted to see what jekyll variables differed between the regular blog pages, and the individual blog pages. With that information, I'd make an `if` statement to only display the pagination content when you were on the blog.

Consulting this [jekyll cheatsheet](http://ricostacruz.com/cheatsheets/jekyll.html) I included `page.url` and `page.date` in my default.html file. When the pages reloaded, I saw that pages like http://localhost:4000/page2 did not have a date, while individual post pages like http://localhost:4000/2015/10/17/Updating-my-website-Part-2/ did. So I decided to try my hand at writing code in a foreign language based on what I had learned from the previous issue. I came up with this:

{% highlight ruby %}
\{\% if page.date == "" or page.date == nil \%\}
  \{\% if page.url != "/about/" \%\}
    \{\% include pagination.html \%\}
  \{\% endif \%\}
\{\% endif \%\}
{% endhighlight %}

It's fairly simple. If the jekyll variable `page.date` is empty, and if `page.url` does not link to the About page, display the pagination.html file from /_includes.

And that's the story of how this site came to exist. Cheers!
