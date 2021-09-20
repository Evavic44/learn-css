<h1 align="center"><b>Introduction to CSS Grid</b></h1>

*This is a reference guide on CSS `grid` With Examples*

## **Why this tutorial**
This is a tutorial in a series I'm working on, which is Building Responsive websites for Junior Frontend Developers *(Though Backend and Fullstack Developers can use this for reference)* I started this project to explain in simple steps how to use grid to build layouts

## **What will you gain from taking this tutorial? 💯**
- A clear understanding of CSS `Grid`
- Ability to recreate layouts with `Grid`

### **Prerequisites**

<ul>
   <li>A basic understanding of HTML and CSS</li>
   <li>A text-editor: <a href="#" alt="VS code website" target="_blank">VS Code</a>, <a href="#" alt="Sublime website" target="_blank">Sublime Text</a> or <a href="#" alt="Atom" target="_blank">Atom</a></li>
   <li>A browser: <a href="#" target="_blank">Firefox</a> or <a href="#" target="_blank">Edge</a> (or anyone you're most comfortable with, except IE)</li>
</ul>

### **Additional Information**
The code files can be found in the grid folder.

_Have the following list down? Let's get started_

<h2 align="center"><b>What Is CSS Grid</b></h2>
Css grid is a layout system use for building two-dimensional layouts by using rows and columns. Grid can be used for building simple interfaces and complex interface like the <a href="#" target="_blank">Periodic Table</a>

<br/><br/>

_This is how grid is different from Flexbox by the ability to create multiple layouts with one grid container_ 
<!-- Image of flexbox vs grid -->
<img src="https://user-images.githubusercontent.com/62628408/126242420-8fc366dc-f511-48a1-b29d-ca5f19f8d64e.png" width="800px">

To create a grid, we can simply do this by setting an element to: `display: grid` or `display: inline-grid` This automatically makes all the direct children of the element a _grid item_ which is kind of similar to flexbox that has it's direct children as _flex items_.

**Example**

This is a div with a class of container and inside the container, we have four child elements. _note: you can call the .container any name you want, common names you'll usually see are .wrapper, .wrap, .grid or .grid-container but in this case, we'll be using the .container_ 

```html
<div class="container">
   <div>Item One</div>
   <div>Item Two</div>
   <div>Item Three</div>
   <div>Item Four</div>
</div>
```

Now let's add a simple styling to this so we can distinguish them.

```css
div {
   background-color: #4c6ca0;
   color: #fff;
   padding: 2rem;
   border: 1px solid #999;
}
```
**Result**

<img src="https://user-images.githubusercontent.com/62628408/126678821-2462c345-feb1-4f37-907c-3478459001eb.png" width="800px">

Now let's set the parent `.container` to a grid container

```css
.container {
   display: grid;
}
```

Doing this alone dosen't change the markup of the boxes because we haven't specified how we want the layout to be. 
<br/>

## **Grid Highlighter**
The Grid Inspector allows you to examine CSS Grid Layouts using the DevTools, discovering grids present on a page, examining and modifying them, debugging layout issues, and more.


**`Firefox`**

On Firefox, open up the developer's tab using **<kbd>Ctrl + Shift + I</kbd>** on windows and **<kbd>CMD + Opt + I</kbd>** on mac. If you're using Firefox, then navigate to the layout section, you'll see the `Grid` menu just above the box-model. Check the grid-container box to enable the grid highlighter. Another way to do this is to check the tiny grid box next to the `display: grid` in the developer tool.
<!-- Image of the grid highlighter on firefox-->
<img src="https://user-images.githubusercontent.com/62628408/126693362-a4710fa7-0381-4813-b59e-ae521d2196c7.png" width="800px">


**`Chrome`**

If you're on Chrome, open up the developer tools and navigate to the layout tab as well, you'll see the grid overlay button which will toggle on the grid highlighter.
<!-- Image of the grid highlighter on chrome-->
<img src="https://user-images.githubusercontent.com/62628408/126695018-600e53de-0ce1-4df4-b654-1ec54d9a0a68.png" width="800px">


As you can see, this displays a colored border around the grid container and between each grid items and numbers going horizontally and vertically _(more details on the numbers later)_. 

Now to see the grid, we'll have to define the rows and columns respectively and to do that we use the property: `grid-template-columns` and `grid-template-rows`.

## **Grid Template Columns**
So let's specify our markup with these properties

```css
.container {
   display: grid;
   grid-template-columns: 200px 200px 200px; 
}
```

<img src="https://user-images.githubusercontent.com/62628408/126916896-5450e1a6-038e-4fe7-a754-30b3890a3c5f.png" width="800px">


As you can see this creates a grid that is `200px wide` each and it spans only to 3 columns and then starts off the other grid items on the next line. That is because we only specified three columns of `200px` width each.

If we add an extra width, this makes it four columns and the last column starts off on the next line. You can keep adding widths to this property to specify how many columns you want.

```css
.container {
   display: grid;
   grid-template-columns: 200px 200px 200px 200px; 
}
```

<img src="https://user-images.githubusercontent.com/62628408/126918232-0ef71f00-66e5-48c5-88ec-e2077b201ca9.png" width="800px">


## **The repeat() notation**
If you find yourself repeating units, you can use the repeat() function to shorten the property.
Let's say you want to create a 10 `200px` column grid, there is a shortcut for doing that without writing 200px 10 times. 

**Example**

```css 
.container {
   display: grid;
   grid-template-columns: 200px 200px 200px 200px 200px 200px 200px 200px 200px 200px;
}
```
Can also be written as:

```css 
.container {
   display: grid;
   grid-template-columns: repeat(10, 200px);
}
```

<img src="https://user-images.githubusercontent.com/62628408/126919264-0c1057d2-f43d-4ee1-a4ad-4f4b5f4ded4d.png" width="800px">

## **Fixed & Flexible Units**
### _**Fixed Unit**_

Fixed units are units that takes the specified width of a given grid cell irrespective of the container width. Example of fixed units are pixels `px`, `rem` etc.

**Example**
```html 
<div class="container">
   <div>Item One</div>
   <div>Item Two</div>
   <div>Item Three</div>
   <div>Item Four</div>
   <div>Item Five</div>
   <div>Item Six<div>
</div>
```

```css
.container {
   display: grid;
   grid-template-columns: repeat(3, 300px);
}
```

**Result**

<img src="https://user-images.githubusercontent.com/62628408/127165873-998474c7-8d00-437d-b833-125b05f0f97f.gif" width="800px">

From this illustration, we can see that the boxes take up only 300px of it's grid cell and doesnt't shrink on smaller widths because the value is fixed and will always remain at 300px no matter the size of the viewport width `vw`.

### _**Flexible Units**_
Flexible units are units that adjust to the container element. Example of flexible units are: `%` and `fr`. The fractional unit `fr` is a new unit of length which represents a fraction of the available space in a grid container. This unit was introduced during the initial stages of CSS grid which is mostly used when working with css grid.  _You can also use the repeat property on the `fr` unit_

**Example**
```html 
<div class="container">
   <div>Item One</div>
   <div>Item Two</div>
   <div>Item Three</div>
   <div>Item Four</div>
   <div>Item Five</div>
   <div>Item Six<div>
</div>
```

```css
.container {
   display: grid;
   grid-template-columns: 1fr 1fr 1fr;
}
```

**Result**

<img src="https://user-images.githubusercontent.com/62628408/127166508-ff229133-91f3-41b8-a2f4-13c1a5f740a0.gif" width="800px">

## **Combining Units**

We can also combine units to get a desired layout. 
In the example below, we'll combine a `2fr` unit with two `1fr` units track. The `2fr` unit takes up double of the space and the `1fr` track takes up single space each. 

**Example**
```html 
<div class="container">
   <div>Item One</div>
   <div>Item Two</div>
   <div>Item Three</div>
   <div>Item Four</div>
   <div>Item Five</div>
</div>
```

```css
.container {
   display: grid;
   grid-template-columns: 1fr 2fr 1fr;
}
```
**Result**
<!-- Image of combining fractions (fr) -->
<img src="https://user-images.githubusercontent.com/62628408/128458909-c7c6c073-b0f8-4851-a260-58c6224f184e.png" width="800px">

This can be applied to other units as well. In this example below, we combine a `500px` track with  a `1fr` and `2fr` track

```html 
<div class="container">
   <div>Item One</div>
   <div>Item Two</div>
   <div>Item Three</div>
   <div>Item Four</div>
   <div>Item Five</div>
</div>
```

```css
.container {
   display: grid;
   grid-template-columns: 500px 2fr 1fr;
}
```
<!-- Picture of combining fractions and pixels (fr) & (px) -->
<img src="https://user-images.githubusercontent.com/62628408/128459620-76af02d6-1f5c-42aa-85be-95e95337659c.png" width="800px">

The repeat notation can also be combined with other track units. In the example below, we have a 200px track combined with 3(1fr) track. 

**Example**

```html
<div claas="container">
   <div>Item One</div>
   <div>Item Two</div>
   <div>Item Three</div>
   <div>Item Four</div>
   <div>Item Five</div>
</div>
```

```css
.container {
   display: grid;
   grid-template-columns: 200px repeat(3, 1fr);
}
```
**Result** 
<!-- Picture of combining repeat() notation and other units -->
<img src="https://user-images.githubusercontent.com/62628408/128460051-1f870fc8-a1c0-49d3-8c95-4d5f59b8efba.png" width="800px">


## **Implicit & Explicit grid**
Previously, we specifically defined our column tracks with the `grid-template-columns` property and the grid also created rows even though we didn't specify the rows with `grid-template-rows`. These rows are what we call the implicit grid(Implied grid though not suggested). Whereas the explicit grid consist of any row and column defined with `grid-template-column` or `grid-template-rows`(Stated clearly). This might be a little bit confusing at first but with some examples, it'll become easier to grasp. 

**Example**
<!-- Image of Implicit grid  -->
<img src="https://user-images.githubusercontent.com/62628408/128460139-b57fdca1-49b4-4bce-b095-8482030dd552.png" width="800px">

For instance in the example below we have 8 grid child elements and we specify 3 grid columns, so the remaining columns not specified is knocked over to create rows and columns in the implicit grid which are automatically sized by default, where the size is determined by the content inside. 

```html 
<div class="container">
   <div>Item One</div>
   <div>Item Two</div>
   <div>Item Three</div>
   <div>Item Four</div>
   <div>Item Five</div>
   <div>Item Six</div>
   <div>Item Seven</div>
   <div>Item Eight</div>
</div>
```

```css
.container {
   display: grid;
   grid-template-columns: repeat(3, 1fr);
}
```

<!-- Image of Implicit grid row and column -->
<img src="https://user-images.githubusercontent.com/62628408/128460233-c53848ab-19f9-40de-9fd1-eeeadf124f35.png" width="800px">

In the diagram above, we have two grid tracks at the bottom that is outside of the defined grid. This is what we call the Implicit grid, but the grid track above that is defined with 3 columns each is the Explicit grid. 

There is a way to control the size of the implicit grid track using: `grid-auto-rows` and `grid-auto-columns` 

```html 
<div class="container">
   <div>Item One</div>
   <div>Item Two</div>
   <div>Item Three</div>
   <div>Item Four</div>
   <div>Item Five</div>
</div>
```

```css
.container {
   display: grid;
   grid-template-columns: repeat(3, 1fr);
   grid-auto-rows: 200px;
}
```

Now this makes every grid item created in the implicit grid to be 200px tall.

## **Track Sizing and Minmax**
When defining the sizing for automatically created rows or columns, you may want to give the tracks a minimum size initially and a maximum size to ensure the track expands to fit the content. This is where the `minmax()` property comes in. `Minmax ` which stands for _minimum_ - _maximum_ is a function used for specifying the minimum and maximum size of a grid track. 

In the example below, we used the `minmax()` property to specify the initial height of a box to be `100px` at minimum and set the maximum to `auto` which will make the grid container to stretch and fit any content if it get's taller than 200px.

**Example**

```html
<div class="container">
   <div>Item One</div>
   <div>Item Two</div>
   <div>
      Lorem ipsum dolor sit amet, consectetur adipisicing elit. Impedit exercitationem aliquam architecto necessitatibus dolor fuga similique qui autem! Similique ducimus hic autem voluptas rerum, soluta nam ab doloremque accusantium ex.
   </div>
   <div>Item One</div>
   <div>Item One</div>
</div>
```

```css 
.container {
   display: grid;
   grid-template-columns: repeat(3, 1fr);
   grid-auto-rows: minmax(100px, auto); 
}
```

**Result**
<!-- Image of grid auto rows: minmax() -->
<img src="https://user-images.githubusercontent.com/62628408/128460361-a5a0de7f-27e4-416c-b359-81b6ce2d4850.png" width="800px">


As you can see from the diagram, we explicitly set the box to have a minimum height of 100px initially, but the one that has content inside stretches out more than 100px in other to fit the content of the grid. 

This is being controlled by the `auto` attribute. Notice that box four and five still remain at 100px height because the content is small enough to fit into the container without stretching the grid track.  

## **Grid Lines**
When we define a grid container, lines are automatically drawn both horizontally and vertically along the grid tracks. _(Though you can't see these lines so you'll have to use the Firefox `grid highlighter`)._ These lines are used to position items within a grid track.

**For example** below is a grid container with 3 columns and 2 rows but have 4 grid lines on the column and 3 grid lines on the row.

**Example**
<!-- Image of grid lines -->

The column lines are the numbers inside the yellow squares, while the row lines are the green circles. Grid lines can also be named which is very helpful when positioning elements. You can <a href="https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout/Layout_using_Named_Grid_Lines#naming_lines_when_defining_a_grid" target="_blank" title="Naming Grid Lines - MDN Docs">Read more</a> here.

## **Position/Span Grid Rows and Columns**
We can span or position grid columns and rows along the lines of the grid container. Spanning grid columns and rows can be very useful when building complex layouts. Spanning grid items consist of the following property: `grid-column-start`, `grid-column-end` and `grid-row-start`, `grid-row-end` properties.

Spanning and positioning grid items is a very important tool you can use in building complex layouts with CSS grid. I'll be sharing an in-depth guide in another article (hopefully). 
<!-- Image of span & position -->

In the image above, we have a grid container with four columns and three rows. Say we want to position `Item one` in the second column, we'll do that by first targeting the `Item one` using <a href="sudo-selectors" target="_blank" title="Sudo selectors - MDN Reference">sudo selectors</a> _(though you can add custom classes to the items if you lke)_ 

```html 
<div class="container">
   <div>Item One</div>
   <div>Item Two</div>
   <div>Item Three</div>
   <div>Item Four</div>
   <div>Item Five</div>
   <div>Item Six</div>
   <div>Item Seven</div>
   <div>Item Eight</div>
   <div>Item Nine</div>
</div>
```

```css
.container {
   display: grid;
   grid-template-columns: repeat(4, 1fr);
}
```

```css
.container div:first-child {
   grid-column-start: 2;
}
```
<!-- Image of Item one position -->
<img src="https://user-images.githubusercontent.com/62628408/128460488-bd5e613a-6f16-4769-81bc-9d95797a3c12.png" width="800px">

From the image we can see that `Item one` is now positioned at 2 and the other items is pushed over which creates empty spaces on the grid.

So we can specify the start position with `grid-column-start`, we can also specify where the grid item ends using the `grid-column-end` property.

```css
.container div:first-child {
   grid-column-start: 1;
   grid-column-end: 4;
}
```

<!-- Image of item one grid column end (4) -->
<img src="https://user-images.githubusercontent.com/62628408/128460619-34246f38-cb23-40ef-9eca-0637732661d7.png" width="800px">

Now you can see that `Item one` starts at 1 (the default position) on the column spans across and ends in line 4. We can also span the rows down unsing the `grid-row-start` and `grid-row-end` property.

```css
.container div:first-child {
   grid-column-start: 1;
   grid-column-end: 4;
   grid-row-start: 1;
   grid-row-end: 4;
}
```

<!-- Image of grid-row-start and grid-row-end -->

Here `Item one` starts at 1 on the rows spans down and ends in line 4. You can span multiple grid items using this property. 

There is a shorter way of spaning grid items by using the property: `grid-column` and `grid-row` which is a combination of `grid-column start`/`grid-column-end` & `grid-row-start`/`grid-row-end`

```css
.container div:first-child {
   grid-column: 1 / 4;
   grid-row: 1 / 4;
}
```

This gives us thesame result as above and is much more shorter to write.

**This** 
```css
.container div:first-child {
   grid-column: 1 / 4;
   grid-row: 1 / 4;
}
```

**Can also be written as:**

```css 
.container div:first-child {
   grid-column: 1 / span 3;
   grid-row: 1 / span 3;
}
```

The `span` property is basically saying start at 1 and span across 3, which gives us thesame result. One of the diffenreces of using span is that you don't need to know what line number you want the grid cell to move to, you can just say span and specify how many lines you want the grid item to move across and the grid item would span across as instructed. This might be a bit tricky to grasp at first and you don't have to use the span if you don't want to but I think it is something you might need to know.

## **Gutters** 
Gutters also known as gaps can be added between grid rows or columns to space them apart. This behaves almost like adding margins in between the grid items but this time we're adding the `gap` property to the grid container and not the individual grid items. To do that with, we use the `grid-column-gap` and `grid-row-gap` property which is short for `row-gap` (Adds spacing between rows), `column-gap` (Adds spacing between columns) and `gap` (Adds spacing between columns and rows). 

**Example**

```css
.container {
   display: grid;
   grid-template-columns: repeat(3, 1fr);
   column-gap: 1rem;
}
```

<!-- Image of column gap -->
<img src="https://user-images.githubusercontent.com/62628408/128460678-1c8e2f05-9d0e-485e-8e31-1467f3b7a206.png" width="800px">

This adds a spacing of `1rem` between every column in the grid container as seen in the image above. 

```css
.container {
   display: grid;
   grid-template-columns: repeat(3, 1fr);
   row-gap: 1rem; 
}
```

**Example 2**

<!-- image of row gap -->
<img src="https://user-images.githubusercontent.com/62628408/128460745-9fc0822e-0cc2-4e97-8eae-3bf62147b9d9.png" width="800px">


This adds a spacing of `1rem` between every row in the grid container as seen in the image above. 

To add a gap between columns and rows we use the `gap`  property, which is a combination of the `grid-column-gap` and `grid-row-gap`. 


<!-- Image of gap  -->
<img src="https://user-images.githubusercontent.com/62628408/128461567-e8bee3ea-9f43-472b-a7b7-3cf75f2ebb87.png" width="800px">

Now you can see this adds a spacing between the columns and the rows. 

## **Nested Grid(Sub Grid)**
A grid item can become a grid container. To do this, we have to set this grid item to display as a grid, which makes it a sub grid of the main grid(kinda like saying a grid within a grid).


**Example**

```html
   <div class="container">
      <div>Grid</div>
      <div>Grid</div>
      <div clas="nested">
         <div>Sub Grid</div>
         <div>Sub Grid</div>
         <div>Sub Grid</div>
      </div>
   </div>
```

```css
   .container {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      grid-auto-rows: 200px;
      grid-gap: 1rem;
   }
```

In the following example, I have a three-column grid that covers the whole width of the contaniner. On the third grid item, there are some sub items.

<!-- Image of three column grid with nested items -->

But let's style the nested grid items so we can clearly see what is going on with it.

```css
.nested div {
   border: 1px solid #999;
   padding: 1rem;
}
```

Now we set the nested container to a grid which makes all the items witihn it grid items. 

```css
   .nested {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
   }
```

<!-- Image of three column grid with nested grid -->
This is how you nest a grid. For this nested grid items, we can also change the width add a height, grid gap, Etc. 

```css
.nested {
   display: grid;
   grid-template-columns: repeat(3, 1fr);
   grid-auto-rows: 70px;
}
```
<!-- Image of nested grid with gap-->

It basically works the same way as a regular grid item.

## **Grid Alignment**
When it comes to aligninig items, grid and flexbox share a lot of similarities, but you might notice a few differences since grid is two dimensional and flexbox one. 

Grid items can be aligned on the X and Y axis in it's container using the properties:

 - `align-items`

- `align-self`

- `justify-items`

- `justify-self`  

**Alignment on the X axis** 

We can align items on the X axis which is also known as the inline axis(horizontal axis) using the `justify-items` and `justify-self` properties. which are positoioned using the follwoing values:

- `auto`
- `normal`
- `start`
- `end`
- `center`
- `stretch`
- `baseline`
- `first baseline`
- `last baseline`

<img src="https://user-images.githubusercontent.com/62628408/133912800-63aedcd7-cdc7-4e47-806b-8fb5ba334ad8.png" width="800px">


For example, we have 3 columns within our grid, we can align this grid items using any of the property above.

```html
<div class="container">
   <div>Item One</div>
   <div>Item Two</div>
   <div>Item Three</div>
</div>
```

```css
.container {
   display: grid;
   grid-template-columns: repeat(3, 1fr);
   grid-gap: 1rem; 
   justify-items: stretch;
   justify-items: center;
   justify-items: end;
   justify-items: start;
}
```

Comment out the property one by one to see the result.
<img src="https://user-images.githubusercontent.com/62628408/133912812-5c56ea5a-bfe8-4622-b65b-9f73c39d6782.gif" width="800px">


On the first value, we can see the grid items were aligned on the X axis to the start(which is the left)

On the second value, the grid items moved to the opposite direction, which is the end of the column.

From this two illustrated, you should get the idea now, the center value, will center the grid items and the stretch, which is the default value will stretcg out the items.

We looked at the most commonly used four, but you can choose to explore other values.

**Alignment on the Y axis** 

Aligning items on the Y axis basically works the same way except we're aliginig on the block axis(vertical axis) by using the `align-items` and `align-self` properties. which are positoioned using the same values.

```html
<div class="container">
   <div>Item One</div>
   <div>Item Two</div>
   <div>Item Three</div>
</div>
```

```css
.container {
   display: grid;
   grid-template-columns: repeat(3, 1fr);
   grid-auto-rows: 200px;
   grid-gap: 1rem; 
   align-items: stretch;
   align-items: center;
   align-items: end;
   align-items: start;
}
```

You can see we are using the same example as used for justify-items, above. This time we are applying the justify-items property. But to see the effect of the properties, we need to add a height to the grid items. 

Comment out the property one by one to see the result.
<img src="https://user-images.githubusercontent.com/62628408/133912825-9ce2d358-b3bd-4030-b461-d455078d3253.gif" width="800px">

**Align-Self / Justify-self**
Now instead of aligning all the items in a grid container, you can align them individually using the align self and justify self property. To do this, let's add  classes to the each grid item so we can target them.

```html
<div class="container">
   <div class="box1">Item One</div>
   <div class="box2">Item Two</div>
   <div class="box3">Item Three</div>
   <div class="box4">Item Four</div>
</div>
```

```css
.container {
   display: grid;
   grid-template-columns: repeat(4, 1fr);
   grid-auto-rows: 200px;
   grid-gap: 1rem; 
}
```

<!-- Image of 3 column grid with gap -->
To demonstrate the different alignment values, each box will be assigned it's own property.
The first item, is showing the default behavior of align-self, which is to `stretch`. The second item, has an align-self value of `start`, the third `end` and the fourth `center`.

```css
   .box1 {
      align-self: stretch;
   }
```

```css
   .box1 {
      align-self: start;
   }
```

```css
   .box1 {
      align-self: end;
   }
```

```css
   .box1 {
      align-self: center;
   }
```

As with align-self and align-items, you can apply justify-items to the grid container, to set the justify-self value for all items.

```css
   .box1 {
      justify-self: stretch;
   }
```

```css
   .box1 {
      justify-self: start;
   }
```

```css
   .box1 {
      justify-self: end;
   }
```

```css
   .box1 {
      justify-self: center;
   }
```

The justify-self and justify-items properties are not implemented in flexbox. This is due to the one-dimensional nature of flexbox, and that there may be multiple items along the axis, making it impossible to justify a single item.

## **How to center a div with grid**
By combining the align and justify property, we can easilt center an item inside a grid area.
