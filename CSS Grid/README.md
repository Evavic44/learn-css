<h1 align="center">Introduction to CSS Grid</h1>

*This is an in-depth guide on CSS `grid` With Examples*

### Why this tutorial 
This is a tutorial in a series I'm working on, which is Building Responsive websites for Junior Frontend Developers *(Though Backend and Fullstack Developers can use this for reference)* I started this project to explain in simple steps how to use grid to build layouts

### What will you gain from taking this tutorial? 💯 
- A clear understanding of CSS `Grid`
- How to build simple responsive layouts with CSS `Grid`
- Ability to recreate layouts with `Grid`

### Prerequisites
- A basic understanding of HTML and CSS
- A text-editor: - <a href="#" alt="VS code website" target="_blank">VS Code</a> or <a href="#" alt="Atom" target="_blank">Atom</a> (Or Notepad++, whatever works for you.) 
- A browser: <a href="#" target="_blank">Firefox</a> _(highly recommended)_ or <a href="#" target="_blank">Chrome</a> (You can as well use any good browser you're comfortable with except IE)

### Additional Information
The code files can be found in the grid folder.

_Have the following list down? Let's get started_

<h2 align="center">What Is CSS Grid</h2>
Css grid is a layout system use for building two-dimensional layouts by using rows and columns. Grid can be used for building simple interfaces and complex interface like the <a href="#" target="_blank">Periodic Table</a>

_This is how grid is different from Flexbox by the ability to create multiple layouts with one grid container_ 

<!-- Image of Flexbox showing one dimension -->
<!-- Image of Grid showing two dimensions -->

<!-- A grid box labelling the following -->
- grid names
- grid lines
- grid rows
- grid columns
- etc

To create a grid, we can simply do this by setting an element to: `display: grid` or `display: inline-grid` This automatically makes all the direct children of the element a _grid item_ which is kind of similar to flexbox that has it's direct children as _flex items_.

##### For example
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
   background-color: grey;
   color: #fff;
   padding: 2rem;
   border: 1px solid #999;
}
```
##### Result
<!-- Image of the box with display set to grid -->

Now let's set the parent `.container` to a grid container

```css
.container {
   display: grid;
}
```

If you notice, this dosen't change the markup of the boxes because we haven't specified how we want the layout to be. To see the grid, we'll be using a Firefox tool called <a href="#">Grid highlighter</a> to see the grid lines. To see the inspector, open up the developer's tab using the **Ctrl + Shift + I** on windows and **CMD + Shift + I** on mac and then navigate to the layout section, you'll see the `Grid` menu just above the box-model. Check the grid-container box to enable the grid highlighter. Another way to do this is to check the tiny grid box next to the `display: grid` in the developer tool. 

<!-- Image of the grid highlighter -->
As you can see, this displays a colored border around the grid container and between each grid items and numbers going horizontally and vertically _(more details on the numbers later)_. 

Which is why I highly recommend you use Firefox for this because it will help you when working with CSS grids.

Now to see the grid, we'll have to define the rows and columns respectively and to do that we use the property: `grid-template-columns` and `grid-template-rows`.

### Grid Template Columns
So let's specify our markup with these properties

```css
.container {
   display: grid;
   grid-template-columns: 200px 200px 200px; 
}
```
<!-- Image of the Three column grid -->

As you can see this creates a grid that is `200px wide` each and it spans only to 3 columns and then starts off the other grid items on the next line. That is because we only specified three columns of `200px` width each.

If we add an extra width, this makes it four columns and the last column starts off on the next line. You can keep adding widths to this property to specify how many columns you want.

```css
.container {
   display: grid;
   grid-template-columns: 200px 200px 200px 200px; 
}
```
<!-- Image of Four column grid -->

### Repeat 
Let's say you want to create a 10 `200px` column grid, there is a shortcut for doing that without writing 200px 10 times which is by using the **repeat** property. 

```css 
.container {
   display: grid;
   grid-template-columns: repeat(200px 200px 200px 200px 200px 200px 200px 200px 200px 200px);
}
```
Can also be written as:

```css 
.container {
   display: grid;
   grid-template-columns: repeat(10, 200px);
}
```

The repeat notation can also be combined with other track units. In the example below, we have a 200px track combined with 6(1fr) track. 

##### Example
```css
.container {
   display: grid;
   grid-template-columns: 200px repeat(6, 1fr);
}
```
##### Result
<!-- Picture of combined track of  -->


<!-- Ten column grid -->
The result shows us a Ten column grid with the eleventh box knocked to the next line and a scroll bar. This is what we call a fixed grid. Now grid also introduced a flexible unit called the fraction `fr` unit as mentioned earlier. This represent a fraction of the available space in a container and you'll mostly be using `fr` units with grid. 

##### Example
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
   grid-template-columns: 1fr 1fr 1fr;
}
```

##### Result 
<!-- Image of Three column grid (fr) -->

This creates a grid column that spans across the full width of the page but still maintains the three column specified and knocks the other two grid items to the next line. This is why `fr` units are cool and it makes building responsive layouts easier. _You can also use the repeat property on the `fr` unit_

```css
.container {
   display: grid;
   grid-template-columns: repeat(3, 1fr);
}
```
This gives the same result as above.

### Combining Units
We can also combine units to get a desired layout. In the example below, we'll combine a `2fr` unit with two `1fr` units track. The `2fr` unit takes up double of the space and the `1fr` track takes up single space each. 

###### Example

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


### Implicit & Explicit grid
Previously, we specifically defined our column tracks with the `grid-template-columns` property and the grid also created rows even though we didn't specify the rows with `grid-template-rows`. These rows are what we call the implicit grid(Implied grid though not suggested). Whereas the explicit grid consist of any row and column defined with `grid-template-column` or `grid-template-rows`(Stated clearly). This might be a little bit confusing at first but with some examples, it'll become easier to grasp. 

##### Example
<!-- Image of Implicit grid  -->

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
   /* grid-template-columns: repeat(3, 1fr); */
   grid-auto-rows: 200px;
   grid-auto-columns: 200px;
}
```

Now this makes every grid item created in the implicit grid to be 200px tall.