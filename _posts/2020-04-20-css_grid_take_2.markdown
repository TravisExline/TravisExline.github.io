---
layout: post
title:      "CSS Grid Take 2"
date:       2020-04-20 13:49:45 +0000
permalink:  css_grid_take_2
---


Last week, I talked a little bit about CSS Grid and how to move different elements around within CSS Grid.  This week, I wanted to look at how to style the grid a little bit.

### Sizing Your Grid

Recall the `grid-template-column` and `grid-template-row` properties from last week.  We can also use these properties to explicitly declare the size of each "cell" in our grid.  Take a look at the example below:

```
.grid-container {
  display: grid;
	grid-template-column: 100px auto 100px;
	grid-template-row: 50px 50px;
}
```

In the example above, we've set up a grid containing three columns, and two rows. Here, the `grid-template-column` property sets the WIDTH of the specified columns.  In our example above, it sets the width of the first and third columns to 100px, and the middle column to automatically size based on the remaining space.  

Similarly, the `grid-template-row` property sets the HEIGHT of each specified row.  In the example, we set the height of each row to equal 50px.  

### Other Useful Aspects of CSS Grid

There's a few other properties I use as a staple with CSS Grid to make it easy to move, place, and style some elements.  The first one would be `row-gap`.  This property is pretty self explanitory.  Check out the example below!

```
.grid-container {
  display: grid;
	grid-template-columns: 1fr 1fr 1fr 1fr;
	row-gap: 10px;
}
```

Here, we have four equal sized colums from the `grid-template-columns` property, but nothing explicity defining any row in our grid, which means they'll be added as necessary and of equal size.  But what does `row-gap` do?  It simply add some space between our rows, very similar to adding `padding` to an element. 

Another great staple would be the `align-content` property.  This centers the ENTIRE grid VERTICALLY within the container.  There's a number of different options when looking at this property, but the three I want to touch on are 
`start`, `end`, and `center`. `align-content: start;` will place your rows at the start of the container, while
`align-content: end;` will place the grid rows at the end of the container. 
You can only imagine what `align-content; center` does!

## Wrap Up

There's a lot of different tools in CSS Grid;  Even more than I mentioned here.  Keep some of these tools in your back pocket when alternatives such as `flex` just aren't working out in your situation.  CSS Grid provides a lot of versitility in just these few very simple aspects that can be very useful in a pinch. 


