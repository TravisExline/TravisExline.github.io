---
layout: post
title:      "Working with CSS Grid"
date:       2020-04-13 11:13:09 -0400
permalink:  working_with_css_grid
---


Today I wanted to go over the life-saver that's been CSS Grid.  CSS Grid is a simple way to organize difference elements on the dom.  In short, it create, well, a grid for you to place, organize, and move different elements around in an organized and structured way.  Personally, I've used CSS Grid in many of my projects, and find it extrememly useful for elements such as forms. Let's look at a quick example.

## How do I use it?

When using CSS Grid, it turns an HTML element into a grid.  For example, if I had the following code in my stylesheet.css

``` 
.grid-container {
   display: grid;
}
```

This would take my HTML element  ```grid-container``` and turn it into a functional grid comprised of columns and rows.  From here, the possibilities are endless.  From sizing grids, to spacing options and element placement, CSS Grid makes placement and design simple.  We'll go over a few quick examples of how to use CSS Grid more in depth.


## Using the ```grid-template``` Properties

There's a few very useful properties included with CSS Grid, but this is by far my favorite.  Let's look at a quick example:

```
.grid-container {
   display: grid;
 grid-template-columns: 1fr 1fr 1fr 1fr;
}
```

The code above separates out grid into four distinct columns.  Notice the third line of code starting with 
```grid-template-columns```.  The code following dictates how many columns would be included in this particular grid. 
But how do I actually get what I want, where I want? Easy!  Check out the code below:

```
.grid-container-child {
  display: grid;
grid-column: 1 / 2;
}
```

Here, we see the code ``` grid-column: 1 / 2 ```.  This dictates within what column you would like to place certain elements.  The same can be done for rows, by replacing column, with row. 

It's worth mentioning that even though a specific ```grid-template-row``` wasn't defined in this example, rows DO exsist, and thus can be utilized and moved as such:

```
.grid-container-child {
  display: grid;
	grid-column: 1 / 2;
	grid-row: 2 / 3;
}
```

## Wrap Up

All in all, CSS Grid is a useful tool for all skill levels, and especially for beginners.  By utilizing the grid to be able to move elements to where you see fit in an easy way, CSS Grid allows for some pretty simplified yet powerful styling tools to be used.  In a future blog, I'll dive further into CSS Grid and some of the other features it can bring to your repertoire.
	

