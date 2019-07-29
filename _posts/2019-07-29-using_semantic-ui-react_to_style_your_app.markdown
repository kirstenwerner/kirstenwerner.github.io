---
layout: post
title:      "Using Semantic-ui-react to style your app"
date:       2019-07-29 22:36:12 +0000
permalink:  using_semantic-ui-react_to_style_your_app
---


Coming into my fifth and final portfolio project for my online software engineering bootcamp, I knew that submitting an app with zero styling would be unacceptable. I looked at some of my options, including styling completely from scratch by writing all of the CSS myself (and quickly decided I do NOT have the CSS expertise nor the stylistic eye for this to be very reasonable), bootstrap, and semantic-ui. I found that semantic-ui had really accessable and thourough and documentation, and some pretty cool features to choose from, so chose that route. 

First things first, to add styling to your react app with semantic-ui, you need to install the package to the app that you want to style. This is incredibly easy - in your terminal, navigate to the file for your project, and enter the line 
```npm install semantic-ui-react```
(alternitively, you could use 'yarn', rather than 'npm', if you are more comfortable with that notation)

The next step *(and this one is important!)*, is to enter a line of code in your index.html file that allows your app to access the semantic-ui CSS styling sheet. I floundered for embarassingly long after adding the necessary tags around my app and not seeing ANY change in the styling of my app in browser, before realizing that I could import and tag all I wanted and never see ANYTHING without access to the packages built in CSS. There are certainly some variations you can make to this line to fit your specific needs, but the simple line I found to allow the access I needed was as such: 
```    <link rel="stylesheet" href="//cdnjs.cloudflare.com/ajax/libs/semantic-ui/2.3.1/semantic.min.css"></link> ```

Once you have semantic-ui installed, and the CSS stylesheet referenced, you are able to start playing around with all sorts of cool style features! You can format buttons, forms, containers, and cards - among many many other things. 

I chose to start my styling by creating a navigation bar that would allow users to navigate around my single page web app by clicking on buttons that would appear at the top of the page no matter what else was rendered on the page.  This task is easily handled by semantic-ui. First, you need to import whichever feature (which has corresponding tags) you are intending to use from the semantic-ui library. For me, this meant at the top of my NavBar.js file, I needed to add this line: 
```import { Button } from 'semantic-ui-react'```
and then incapsulate the code that I want to describe my buttons with the appropriate semantic-ui tags, like so: 
```          <NavLink to='/' exact><Button size='medium' color='olive'>Home</Button></NavLink>
          <NavLink to='/recycle-center-finder' exact><Button size='big' color='green'>Recycle It!</Button></NavLink>
          <NavLink to='/materials' exact><Button size='medium' color='teal'>Materials</Button></NavLink>```
*note, my semantic-ui 'Button's are also encapsulated in NavLink tags in order to use the react-routed-dom to allow my app to use restful routing.






