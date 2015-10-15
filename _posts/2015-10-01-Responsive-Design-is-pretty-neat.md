---
layout: post
title: Responsive Design is pretty neat
published: true
---

#### Responsive Web Design fundamentals are really cool

My first experience making websites was in middle school, in the days before HTML5 and CSS3. Responsive design wasn't a thing because mobile phones didn't exist. I wasn't very good at making websites, but it was still a lot of fun. But there was a lot that was very frustrating. Tables and divs made absolutely no sense to me back then. Luckily things have changed; I'm older, but the world of web development has also grown up. The tools now available continue to surprise me with how seamlessly they work, and how powerful they are.

Since completing the HTML/CSS course, I've taken two classes on Udacity that are focused on optimizing websites for all types of users. The first was mainly about using CSS3 to create a page layout that reacts appropriately with the size of the browser window. I learned how to better implement `flex` elements, calculate width percentages within the CSS, and order changes. I was really interested in the `order` property because during the HTML/CSS class I really wanted to switch the order of my logo and title, but didn't think it was possible.

The second class was about using responisve images. I learned how to drastically reduce bandwidth usage on my sites with media queries, `picture`, and `srcset`. Alongt he way I picked up quite a few really interesting tools that will definitely help me in the future. The first being Grunt. Woah. Automation is awesome! The second is the massive number of unicode characters that I can use instead of images. So cool.

#### Getting my feet wet in javascript

In the [Responsive Web Design Fundamentals](https://www.udacity.com/course/responsive-web-design-fundamentals--ud893) course, the first project had us making a hamburger menu. Interestingly enough, I stumbled on an article that pretty thoroughly convinced me the hamburger menu was junk, and really shouldn't be used the way it currently is. So for projects that I make for myself, I'll be following that advice. But I had a course project to complete, and despite all my googling, couldn't find a simple pure CSS menu that I could get to work on my website. In the end I decided to just make it myself from the ground up. I figured out what I wanted to do, and then perused the jQuery documentation until I found a method that did what I wanted: `.toggleClass()`. I didn't know a thing about JS or jQuery, but the documentation was really thorough, and I only needed to write a very basic script:

{% highlight js lineos%}
<script>
    $("#menu").click(function() {
        $("#drawer2").toggleClass("hidden");
    });
</script>
{% endhighlight %}


I saw a lot of really powerful methods, and can't wait to start learning Javascript. It was going to be my next class, but I've decided to take a quick detour and learn all that I can about git and github before continuing. Version control is very important, and at the moment I don't do any of it, which is a big no no.
