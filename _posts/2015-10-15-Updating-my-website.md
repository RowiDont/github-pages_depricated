---
layout: post
title: Updating my website
published: true
tags: ['Jekyll', 'HTML/CSS']
---

As you may notice (the one person who has seen this blog in the past month), my site design has changed. I was pretty peeved that I was becoming a web developer yet somehow I didn't have my own website, rather relying on Hyde, a Jekyll theme made by [@mdo](https://twitter.com/mdo).

{: .center}
![my-image](/images/hyde.png)

{: .center .caption}
"Hyde is a brazen two-column Jekyll theme"

The journey into customizing Jekyll to fit my tastes was pretty educational. I won't pretend like I fully understand the magic that is Jekyll, BUT I do finally understand most of the pieces. It was nice that I can now add menus to my site relatively quickly, thanks to my HTML/CSS and responsive design classes.

### Community

I relied on quite a few jekyll blog posts to figure out this website, and it's made me reconsider what I want to do on my blog. I think, in addition to keeping up on my progress, I'd like to write tutorials and general help guides for people also starting out with web development.

Every time I struggle with a concept or idea, and finally reach an answer, why not share it? These are some of the resources that helped me out:

+ [Jekyll - Learning Jekyll By Example by Andrew Munsell](https://learn.andrewmunsell.com/learn/jekyll-by-example/tutorial)
+ [Icons - Fontello, an icon font generator](http://fontello.com/)
+ [Git - How to prioritize files in one branch while merging (stackoverflow)](http://stackoverflow.com/a/8014154)
+ [Music - Chinese Football, the music I listened to while coding](https://chinesefootball.bandcamp.com/album/chinese-football)

### Mobile design principles

If you checkout this site on your phone, you'll notice that I opted for an unconventional menu. No hamburgers here. And that's because I have never liked he hamburger. So you can imagine my delight when I found [this](https://lmjabreu.com/post/why-and-how-to-avoid-hamburger-menus/) excellent write-up by Louie A on the numerous issues with the hamburger.

{: .center}
![mobile-menu](/images/mobile-menu.png)

{: .center .caption}
Mobile menu

The making of this menu was a lot simpler than I thought it would be. Here's the CSS (you may have to add <code>!important</code> depending on how you implement it):

{% highlight CSS %}
@media screen and (max-width: 550px) {
  .move-down {
    background: #f6f6f6;
    position: fixed;
    left: 0;
    right: 0;
    bottom: 0;
    height: 50px;
    border-top: 2px;
  }
}
{% endhighlight %}


### First profesh Ruby code

In completely unrelated news, I wrote my first "real" line of ruby code today, while completing the [Binary Converter](http://coderbyte.com/CodingArea/Editor.php?ct=Binary%20Converter&lan=Ruby) challenge on Coderbyte. Wouldn't be possible without the excellent explanations by Ryan Glassett of App Academy, who showed some new Ruby methods during my coding assessment. I also finally learned how binary works after reading [this](http://www.kerryr.net/pioneers/binary.htm) excellent write-up by Kerry Redshaw. Check out my solution:

{% highlight Ruby %}
def binary_convcert(str)
    num = 0
    str = str.split("")
    str.each_with_index{|x, index|
        num = num + x.to_i*(2**(index-str.length+1).abs)
    }
    return num
end
{% endhighlight %}
