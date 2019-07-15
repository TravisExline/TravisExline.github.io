---
layout: post
title:      "Sinatra Project"
date:       2019-07-15 13:05:20 +0000
permalink:  sinatra_project
---


There's only one way to start this blog, and that's "oof."  This project was a really big test for me, and I'm still hesitant to let myself pass.  In this project, I created an MVC using ActiveRecord.  My goal was to create an application in which individuals could store information on their pet reptiles.  Because keeping reptiles can be difficult with all the different types, habits, and husbandry, having an electronic database to store these animals would be extremely helpful.  However, I also wanted to be able to create logs, or posts, about the care users were giving their animals(i.e, when did you last feed them, or change bedding?).

### My Process

This project was particularly difficult for me.  Although I had my framwork laid out, MVCs and Sinatra would continuously throw me for a loop -  it's definitely something I need to revisit and solidify my knowledge on. 

I began with creating my tables and migrations.  I created 3 tables:  Users, Reptiles, and Posts.  Each of these would sever to help easily create these models later on.  Below is my CreateReptiles table to show how I went about that. 

```
class CreateUsers < ActiveRecord::Migration[5.2]
  def change
    create_table :users do |t|
      t.string :username
      t.string :email
      t.string :password_digest

      t.timestamps null: false
    end
  end
end
```

Next, I dove into creating my three models; User, Reptile, and Post.  My relationships here were as follows: A User has many posts, and a User has many Reptiles.  A Reptile belongs to a User, and a Post belongs to a User.

Then came the hasrd parts - piecing together my Controllers.  

#### Application Controller

In my Application Controller, I let me app live and work here. I defined my helper methods for logging in, defining a user, and logging out.  These helper mthods would help to to stick to easy, readable code in my other controllers. 

#### Users Controller

My Users Controller was responsible for making sure users were signed up to the application as well as logged in.  

#### Posts & Reptile Post Controller

These two controllers were those that gave me the most trouble.  Being able to lay these GET and POST methods was the key to being able to create the logs(posts) and reptiles that belong to each user.  The methods in these controllers allowed me to create and edit posts as well as the reptiles for each user. 

### Views

Finally, I connected my controllers to the corresponding views that were needed to get my project online. For each of my three key controllers (Users, Posts, and Reptile_Posts) I created multiple .erb files to edit, create, delete, and allow for the content to be viewable. 

## Conclusion
It wasn't easy, and it still needs work.  I have parts of this application that I'm definitely upset with, but in the end it actually makes my life as a reptile keeper easier, so I guess that it serves its purpose, which is a small win in my book!
