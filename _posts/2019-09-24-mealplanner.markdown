---
layout: post
title:      "Mealplanner"
date:       2019-09-24 22:02:18 -0400
permalink:  mealplanner
---


For this project, I created a Mealplanner using a Rails API/Javascript Frontend.  The purpose of this app is to manage a User's meals for the week, supplying the user with pre-loaded recipes to choose from as well as allowing the user to create his/her own recipes from scratch.  Additionally, a User can search by a specific meal that they are looking to add to a meal planner. 

### Adding Recipes to Planners

The main purpose of this application is to be able to add different recipes and meals to a meal planner.  

``` 

function addRecipeToPlanner(event) {
    // debugger
    let plannerId = currentUser.planners[currentUser.planners.length - 1].id
    // debugger
    fetch(plannerRecipesURL, {
        method: "POST",
        headers: {
            "Content-Type": "application/json",
            Accept: "application/json"
        },
        body: JSON.stringify({
            planner_id: plannerId,
            recipe_id: event.target.dataset.recipeId
        }),
    })
    .then(res => res.json())
    .then(res => {
        // debugger
        currentUser = res
        showCurrentUser()
        renderCurrentUser()
        let planner_recipe = currentUser.planners[0].planner_recipes[currentUser.planners[0].planner_recipes.length-1].recipe
        // debugger
        renderUserPlanner(planner_recipe)
    }) 
		
		```
		
		The code above is the bread and butter for adding Recipes to the Planner.  In this function, after clicking on the "Add Recipe Button", we fetch the PlannerRecipesURL.  We assign the key planner_id to get the id of the User's planner via the code below:
		
		` currentUser.planners[currentUser.planners.length - 1].id `
	
	Additionally, when passing the recipes to the function renderUserPlanner(), we have to look deeper into our Planner object.
	
	`currentUser.planners[0].planner_recipes[currentUser.planners[0].planner_recipes.length-1].recipe `
	
Here, we're able to focus down onto the newst recipe that we want to render in our Planner.  By zeroing in via this code, we avoid the trouble of duplicating recipes in a User's planner. 

### A Simple Search

Having a list of recipes is great, but sorting by each specific meal (breakfast, lunch, or dinner) helps with some quality of life benefits and makes this easier of the User.  To do this, I had to add some functions in my backend.

``` 
    def find_breakfast
        breakfast = Recipe.all.select{|recipe| recipe.meal == "Breakfast"}
        render json: breakfast
    end

    def find_lunch
        lunch = Recipe.all.select{|recipe| recipe.meal == "Lunch"}
        render json: lunch
    end

    def find_dinner
        dinner = Recipe.all.select{|recipe| recipe.meal == "Dinner"}
        render json: dinner
    end
		
		```
		
	These methods allow for the selection of specific recipes based on their meal.  However, that doesn't do the trick.  In additon, an Event Listener will need to be added into frontend.
	
	```
	searchOptions.addEventListener('change', function(e){
    fetch(baseURL + `/${e.target.value}`)
    .then(res => res.json())
    .then(recipes => renderRecipes(recipes))
})
```

		
		

		
		
