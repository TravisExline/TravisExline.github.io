---
layout: post
title:      "Project 3, Errors, and Searching"
date:       2019-08-11 14:59:44 +0000
permalink:  project_3_errors_and_searching
---


In this project, I enhanced my previous app designed for reptile keepers and breeders.  I enhanced the look of my app, as well as implemented a few different features through nesting as well as errors and validations.

Primarily, I want to tlak about a new search feature that was implemented as well as a quick overview of the simple validations and errors that I included in my app.

First, my validations.  Each of my models each had validations that needed to be passed in order to create an instanc of said model. Below is an example of my User model validations:

```
validates :name, presence: true
  validates :name, length: { in: 2..30 }
  validates :email, uniqueness: true
  validates :email, presence: true
  validates :pet_count, presence: true
	```

Here , I ensured that everyone who wanted to sign up for the app entered a name, email and the number of pets that they own.  In addition, they were required to have a unique email address as well as a length requirement via the name. Due to people having the same name, it wouldnt make sense to include a uniqueness validation for individuals's names. 

After including the validations, I also included error messages to show users when additional input was needed, or if input was incorrect. Below is an example for my Reptiles:

 ```
 <div id="error_explanation">
    <h2>
      <%= pluralize(@reptile.errors.count, "error") %>
      prohibited this article from being saved:
    </h2>

    <ul>
    <% @reptile.errors.full_messages.each do |msg| %>
      <%= msg %></br>
    <% end %>
    </ul>
  </div>
	```
	
	Here, I allowed for errors to be show to the user during the creation of each new reptile.  
	
	Finally, I added a new search feature for both the reptiles and posts made by a User.  
	
	  ``` 
		 <div>
     <h4>Filter Posts</h4>
     <%= form_tag("/posts", method: "get") do %>
       <%= select_tag "date", options_for_select(["Today", "Older"]), include_blank: true %>
       <%= submit_tag "Filter" %>
     <% end %>
   </div>
	 ```
	 
This code, which resides in posts/index.html.erb, creates my filter options in for a users posts.  Here, users can filter by current posts, or older posts. Aside form the changes in the views for my search tool, changes were also made in our index method in the PostsController.

```
    if !params[:date].blank?
      if params[:date] == "Today"
        @posts = Post.from_today
      else @posts = Post.older
      end
			```
	
	This code was able to retrieve the dates of our posts, allowing for the code resideing in the view to then filter everything for the user.

