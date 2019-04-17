---
layout: post
title:      "Writing my first Sinatra web app - SeattleRestaurantRemeberall"
date:       2019-04-17 16:48:26 -0400
permalink:  writing_my_first_sinatra_web_app_-_seattlerestaurantremeberall
---


For our second portfolio project for the Online Software Engineering program at Flatiron, we were asked to create a web application using Sinatra, sql, and ActiveRecord that had secure user logins, used multiple models, had at least one has_many and one belongs_to relationship, and was controlled by a application_controler. After brainstorming for nearly a week and talking to other people about what a simple problem or annoyance that we all face regularly that might be able to be solved with a simple record-keeping web app, I settled on trying to create a program that would let a user save restaurants when they discover them and look back through thier lists and other user's lists when they want to - I mean, who HASN'T had the experience of deciding to go out to eat with friends or family, only to have their minds go completely blank when they're trying to pick a place to go?!

For this app, what I thought would be the most pertinent information to store about a restaurant would be the type of food (cuisine) and the location (neighborhood). Afterall, "What do you want to eat?" is how the picking-a-restaurant conversation always starts, and it doesn't do much good to get your heart set on a restaurant only to remember that its waaaayyyyy on the other side of town! 

To start off my project, the first thing I needed to do was to decide what tables/models I would need to create, and how those would be related to each other. Obviously I would need to create Users, and those users would nead to have a name, a password, and for good measure, an email to make sure that each user was unique. Next I have Restaurants.  Now I knew that I wanted my restaurants to have a name, a cuisine, and a location, as well as be able to be associated with the user that saved it. So my first thought (and attempt) was to have my Restaurant table look like this: 

```def create_table do |t|
     t.string :name
		 t.string :cuisine
		 t.string :neighborhood
		 t.integer :user_id 
end```

Seems alright, no?  But what sort of functionality do I want my app to have? Does it make sense to save a new instance of "pizza" into the database *every time* a user saves a pizza restuarant? Or neighborhood? And what if I want to be able to search the database record for all sushi restaurants? Or all restaurants in West Seattle or Greenwood? 

As I started working through actually coding out the funtionality that I wanted my app to be able to perform, I kept hitting walls. And I started to get very uncomfortable with having the cuisine and neighborhood information repeated over and over and over again in my tables. I realized I needed a little bit more complex relationships. It makes sense that a neighborhood "has_many" restaurants. And it makes sense that a cuisine "has_many" restaurants, as well. What if a user could have_many restaurants, but could also have_many cuisines and have_many neighborhoods through restaurants? Now I'm on to something! 

With these complex relationships in mind, I knew I needed to create tables in my database to store cuisines and neighborhood, each with their own id's. Then I would need to re-work my Restaurant table to hold foriegn keys for its associated attributed like this: 

```
def create_table do |t|
     t.string :name
		 t.integer :cuisine_id
		 t.integer :neighborhood_id
		 t.integer :user_id
end
```

These new tables allowed me to write my associations:

```
class User < ActiveRecord::Base 
       has_many :restaurants
       has_many :cuisines, through: :restaurants
       has_many :neighborhoods, through: :restaurants 
end
```
	
```
class Restaurant < ActiveRecord::Base
       belongs_to :user
       belongs_to :cuisine
       belongs_to :neighborhood
end
```

```
class Cuisine < ActiveRecord::Base
     has_many :restaurants
end
```

```
class Neighborhood < ActiveRecord::Base
     has_many :restaurants
end
```

And viola! All of my tables and models have the associations needed to code out the functionality I envision my app to have, like being about to search for Restaurant.find_by(cuisine_id = ?) or pull up User.neighborhoods. 

My takeaway from this - it is worth the extra time it takes to really map out what you want your web app to be able to do BEFORE jumping in and guessing on what associations you might need to have. By mapping out how your models will interact - i.e., what has_many of what, and what belongs_to who, you will save yourself a lot of time and headache of having to go back and detroy/rebuild tables, breaking your program to the point of unrecognizability along the way!

Happy Coding!


