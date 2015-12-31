---
layout: post
title: Becoming a Web Developer (for real)
published: true
tags: ['App Academy', 'Ruby', 'Rails']
---

It's been a while since I posted here, and as much as I'd like to say that will change, I'm not sure it will. I'm now 4 full weeks into the App Academy (aA) curriculum, and it's been an amazing experience.

##Making things, Part 1

During the first two weeks we were brushing up on our ruby skills, making games, for the most part, and learning about different object oriented programming techniques. The day I enjoyed most was data structures. It was a lot of fun to implement the DFS and BFS algorithms in Ruby, and we ended up using these techniques that same day. Our task was to program the logic for moving a Knight in chess. We ended up finding the algorithms useful several times, which is why I'm really glad I learned about them. Another place we sued them was our minesweeper game.

{: .center}
![Minesweeper](/images/minesweeper.png)

####Knight path
Recursion day had been a nightmare, but I was finding that every day following it I was able to implement recursion in simpler problems without giving it a second thought. We were tasked with creating a program that knew how to move a knight from position A to position B, and was able to return that path. We used recursion and nodes to map out the path, using the parent and children references to eventually rebuild the path from A to B. That was a lot of fun to get working.

#####OOP at the next level
Our last big Ruby project was chess. It was a beast of a project. We didn't make an AI, or anything like that. We simply had to create many different classes for the different piece types. It was a great lesson in class inheritance, and the usefulness of modules.

{: .center}
![Chess - using the cursor in a terminal](/images/chess.png)

The reason this project was tough had little to do with the logic we needed to work out, and almost everything to do with the fact that it was massive. Before, we'd been writing programs that were one page long, if that. Now we had 7 or 8 or more classes, all interacting with each other, methods we were referring to from 5 different files. It was our first big project, and I didn't know it at the time, but it was great preparation for Rails, which is far more complex.

##Making things, Part 2

But all those games we were making ran in the command line, and they weren't useful. It was fun, but also frustrating. I was very ready for the big leagues. Day 1 of SQL kicked my ass. It was really taking me forever to make connections. Luckily I had a brilliant partner who was happy to walk through her thought process with me. On Day 2, SQL clicked and we steamrolled into Rails. This powerful duo has given me the ability to make actual web apps. Like real, live, web apps.

At the end of week 3, we made ActiveRecord *Lite* (our personal attempts at replicating the Rails class that abstracts much of the interaction with the database for you. Rails clicked from day 1, I think mainly because of the time I put into the frustrating yet apparently helpful tutorial, [Blogger 2](http://tutorials.jumpstartlab.com/projects/blogger.html).

From then on we've been making Rails apps. One a day, as per doctor's orders. We've learned the basics of Models, Controllers, and Views, of course. We also have User auth under our belt (the upcoming assessment will see just how fast we can implement it).

##Onward and Upward

Even though we can now make Rails apps, they are ugly as hell. We just learned some CSS, and I went ahead and did some extra tutorials on bootstrap, which I have some experience with (this whole website is built with bootstrap and extra CSS3 goodness). And we start Javascript soon. I am literally foaming at the mouth with excitement.
