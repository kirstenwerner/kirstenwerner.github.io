---
layout: post
title:      "Creating my first Ruby CLI Gem"
date:       2019-03-17 22:42:17 +0000
permalink:  creating_my_first_ruby_cli_gem
---


I've just completed my first Ruby Gem, and whoo! that was a doozy.  After spending days thinking about what I wsa going to make, and procrastinating by re-reading EVERY. SINGLE. THING. that I thought might be helpful before starting actual work on it, I finally sat down to begin my project.

What I found, was that none of the re-reading helped at all. I just had to dive in.

The initial set-up was completely unfamiliar to me, as all of our labs up until this point were set up for us, and we only had to fill in the actual coding logic practices. So back I went again to video walk-throughs of builing a CLI gem, and walked through step-by-step to set up my environment and gemspec. What FINALLY sunk in, was that setting up the environment was a simple as 'require'ing any external gems that my gem would depend on (in this case, being gem dependant on scraping, Nokogiri, Open-URI, and for some added pizzaz, Colorize - plus Pry for development), and 'require-relative'ing all of the seperate objects within my gem. 

Once I had the framework set up, I found it surprisingly simple to work through the functionality that I wanted my gem to have. Relatively simple, but by no means what-so-ever fast! 

My workflow generally went something like this:
 - decide what the next step I wanted to make work was
 - write some code that seemed somewhat close to what I was trying to accomplish
 - run my program
 - recieve some massive string of errors show up in my terminal
 - fix the inevitable simple typo or syntax mistake
 - repeat the last two steps over and over and over again
 - finally get to an actual logic error and hone in on that
 - FINALLY get the logic figured out in a way that seems efficient, DRY (and hopefully elegant and readable)
 - repeat.

Throughout the project, I bounced back and forth between thinking my gem was too simple, to way over-complicating things and having to reign myself back in. Overall the part that I found by far the most difficult and time-consuming was the scraping of my selected web-pages to get the content that I wanted available for my gem to use. This is an area that I think might just come with experience, so I know that I need to put some more time into practicing my scraping. 

In the end, I am proud of my finished product, and I think it gives some pretty cool functionality (with a little cheeky humor thrown in). 

If you want to check it out: https://github.com/kirstenwerner/washington_ski_report 
 
