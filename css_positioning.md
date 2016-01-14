Clone the starter folder *css_positioning* from Github.

#CSS Layouts & Positioning

##CSS Length Units

Since we’re talking about laying out elements onto a page, it’s important to clarify what length values CSS accepts.  

The pixel (​px)​was traditionally the most common length unit. It attempts to represent one pixel on your particular viewing device. Unfortunately, this is very device specific, so your page may look very different depending on, for example, the operating system’s screen­ resolution.  

In the 90s and early 00s we only had to worry about 800x600 and 1024x768. Since the end of the 00s, CSS developers have had to grapple with increasingly dense [screen resolutions](h​ttp://www.w3schools.com/browsers/browsers_display.asp)​.

Modern high ­resolution screens (e.g. Apple Retina displays) and certain printers treat the CSS value ​1px​ as multiple on­screen pixels to compensate for their incredibly small actual pixel sizes and to prevent web sites and applications from shrinking smaller and smaller as density increases.  

As a result, CSS standards are adjusting to use a different measurement of length, the ​em.​ The “M” is still relative, but instead of being device dependent, it’s relative to font size,­ a better measure of human readability.



###Em/Rem

Try this sample code in `style.css`:

```css
p {
padding-left: 5em;
border: 1px solid gray;
}

.one {
  font-size: 0.5em;
￼￼￼￼
}
.two {
  font-size: 1em;
}
.three {
  font-size: 2em;
}
```

Open this is your browser by using `open index.html` from terminal.

In this example, the ​padding­ left ​inherited by every ​`<p>`​element is ​5em,​ but the actual on­screen representation of that padding adjusts according to the element’s ​font­ size.​The em​ unit attempts to represent the width of the capital­ letter ­M character, so five­ Ms are included in each `<p>` as reference.

Indenting the first line of a paragraph is a good sample use case for ​em.​ The size of the indentation *should* depend on the font ­size of the paragraph.

An alternative to ​em, ​the ​rem,​ generates a length *relative to the ​font­ size​ of the entire page* (the ​html​(or r​oot) ​element) rather than the current element. This unit may be more appropriate for placing components relatively onto a page according to the user’s default font preference, as opposed to the declared font­size on some particular portion of the page.

Note the difference with this small CSS change:

```css
p {
  padding-left: 5rem;
}

```

###Other Length Values

There are several other ways to set size although we won't get into them all here.

Notably, you may also use percentage values for lengths. This is most commonly used for CSS ​widths​, as in “this element should only take up 50% of the width of its container”. But it may also be used elsewhere, such as ​font­-size ​and ​margin.​  

#####Deletion  

Let's get rid of the styling for paragraph's two and three as well as the padding in the `p` elements.  

******************************************

Now we'll set paragraph one to have a width of 50%.  

```css
.one {
  font-size: 0.5em;
  width: 50%;
￼￼￼￼
}
```

We can also utilize `vh` or `vw` units. `Vh`s are for viewport height and `vw`s are for viewport width. These are an alternative to using percentages in certain situations. A width set to `50vw` will take of 50 percent of the viewing width. It's important to note that percentages take up the specified percentage based on the parent container while viewport sizes take up their percentages based on the entire viewport screen.

Let's take a look by setting a border around the div surrounding paragraph two.

```css
#paragraph-two {
  border: 2px solid red;
}
```

Now we'll change paragraph one to have a width of 50vw instead of 50%.

```css
.one {
  font-size: 0.5em;
  width: 50vw;
}
```

And we'll set paragraph two to have a width of 50%.
```css
.two {
  font-size: 0.5em;
  width: 50%;
}

```
Notice the small difference in widths? The first paragraph is taking up half of the viewport screen and the second paragraph is taking up half of the width of the parent div. To make this more evident, we can resize the div using a fixed amount of pixels. Add the below to the existing styling in `#paragraph-two`
```css
#paragraph-two {
  ...
  width: 600px;
}
```

###Display/Hiding Elements

#####Deletion  

Let's delete all of that styling so we can move on to the next topic. The only thing remaining in the stylesheet should be:  

```css
p {
border: 1px solid gray;
}
```
******************************************

We're not going to be using the first paragraph for the next example so let's take a moment to explore visibility settings.

```css
.one {
  display:none;
}
```

The `display: none;` property sets the element to hidden as if the item never existed. It can be brought back by changing the display again.

This is very different from another property which hides the element but it still takes up the same space.

Try the following:
```css
.one {
  visibility: hidden;
}
```

Notice that the whitespace the paragraph would have occupied is still there.  Let's go back to `display: none;` and move on.

##Box Model

###Margins

Let's make a box!

```css
#paragraph-two {
  border: 2px solid red;
  width: 16em;
  height: 16em;
  background-color: lightgray;
}
```

Let's play with the CSS margin property.

Add `margin: 1em;`

The ​margin ​property adds some space around the ​`div`.​The area inside the ​`div`​ doesn’t shrink, but the total area taken up by the element increases. The margin is transparent; it doesn’t inherit the background color.
The ​margin​ property is a shorthand for “margin all around”. You can also specify each margin separately, either as:  

margin: [top] [right] [bottom] [left];  
margin: 0em 10em 0em 10em;  
margin: [top&bottom] [right&left];  
margin: 0em 10em;  

Or as:

margin-­top: 0em;  
margin­-right: 10em;  
margin-­bottom: 0em;    
margin-­left: 10em;  

Let's style the `#paragraph-three` div to have the same size as the other square but different colors so we can see the differences better.

```css
#paragraph-three {
  border: 2px solid green;
  width: 16em;
  height: 16em;
  background-color: lightblue;
  margin: 1em;
}
```

Let's change the margin's on each to be `0em` and take a look...

When two adjacent elements share a margin, the margins will overlap. So if ​margin­-bottom is changed to ​1em​ and ​margin­-top ​is changed to ​1em,​ the total margin between the elements is the overlap (​1em)​, not the sum (​2em)​.

Similarly, if ​margin­-bottom​ is ​1em​ and ​margin­-top ​is ​2em, ​the total margin between the elements is the max (​2em)​, not the sum (​3em)​. The smaller margin is swallowed up within the larger one.  

We can show this by setting two different margins for each box.

```css
#paragraph-two {
  ...
  margin-bottom: 1em;
}

#paragraph-three {
  ...
  margin-top: 2em;
}
```

###Auto Margins

Our square ​`div` ​element has a defined ​width, ​so it doesn’t take up the full­ width of the page. But it does sit along the left side of the page. To horizontally center it, we can play with the left and right margins, but whatever value we pick will break as soon as we resize the browser window.  

The appropriate way to horizontally center a block­ level element is to let the browser automatically calculate the left and right margins. That’s where the ​`auto​` property value comes in.


Let's edit the margin to include the auto setting:

```css

#paragraph-two {
  ...
  margin: 0rem auto;
}
#paragraph-three {
  ...
  margin: 0rem auto;
}
```

When the left and right margins are set to ​auto, ​the browser will automatically calculate it to keep the element centered.

* What happens when only one side (left or right) is set to ​auto?​  
* Can you tell the difference between ​`margin: 0 auto;`​and `​text­align:
center;`?​  

###Padding

Now let’s try padding instead. Leave paragraph-three as is but add padding for paragraph-two to 2em;

```css
#paragraph-two {
  ...
  padding: 2em;
}

```
The CSS ​padding​ property adds space around the text, but within the ​`div` ​border. As before, the ​`div​` grows larger, but the text pushes away the edges.  

Just like ​margin,​​ padding​ is shorthand for “padding all around”. You can also specify each side individually.  

padding: [top] [right] [bottom] [left];  
padding: 0em 10em 0em 10em;  
padding: [top&bottom] [right&left];  
padding: 0em 10em;  

Or as:  

padding­-top: 0em;  
padding­-right: 10em;     
padding-­bottom: 0em;   
padding­-left: 10em;    


Unlike ​margin,​​ padding​ does not “collapse”. If two elements are adjacent and padded, the space between them will be the s​um​ of their respective paddings. This effect tends to be easier to understand, so ​padding​ is more popular than ​margin​ for positioning between elements.

Let's set the padding to `1em` for both boxes:

####Deletion
Now lets take away the margin...
******************************************

Notice that each box still has its own padding. `1em` of padding on the top and bottom of each box create a total of `2em`s of padding.

###Border

You've already seen the border property used. It sets the border between the ​margin​ and the ​padding.​ The shorthand syntax for the ​border​ property is: 

￼`border: style (required), color, width;`
`border: solid #1a86a1 5px;`

The additional fields in most CSS shorthands are optional. That means if they are left out, default values are used instead. Therefore this:  

`border: solid;`

will generate a ​solid​ border with a default ​black​ color and ​2px​ width.

Unlike ​margin​ and ​padding,​ the property order can be rearranged. In fact, the standard syntax is actually:  

`border: width, style (required), color;`

As long as the ​border­ style​ is specified, something will appear. That’s the only required property value (because it’s default value is ​none)​.

There are a number of different ways to set each individual property. These an be easily looked up online so we won't get into them all but know that you can set specific sides, for example:

```css
#paragraph-two {
  border-top: 5px solid red;
  ...
}
```

###Element Dimensions

The total size of an element (a​ctual​ height and width) is the sum of the sizes of its constituent parts:
* content: my internal organs  
* padding:​ my fat  
* border:​ my skin  
* margin:​ my personal space  


This can lead to some confusion. For example, even if I specify a ​width ​for my ​div,​ the actual, real­ world, on­ page width of the element will be greater.

...unless you’re using IE6. Then the ​width ​you specify is the actual width of the element. This can cause some huge layout problems on older versions of IE. For some tips, check [this](https://css­tricks.com/ie­css­bugs­thatll­get­you­every­time/) out.

The way IE6 treats the width actually makes a lot of sense, but that’s not how the CSS spec was written. For example, if I want to display a grid of ​divs ​and I want one ​div​ to take up exactly 25% of the page, I can set ​`width:25%;`. ​But, as soon as I add ​padding,​​ margin,​ and/or a ​border, ​the actual element width is 25% plus... some more.  

I have to do math to figure out how to get that element back down to 25% of the page. Sometimes I even need to use JavaScript if I want my layout to be responsive.
There is a better way. The CSS3 ​[box­ sizing​ property](h​ttps://developer.mozilla.org/en­US/docs/Web/CSS/box­sizing)​ will force elements declared to be `width:25%`; to remain 25% of the width. *_That means border and padding will be forced within the element dimensions instead of adding to the outside of the element._*

Here are some additional resources on how to use it:
* https://css­tricks.com/international­box­sizing­awareness­day/.​
* http://learnlayout.com/box­sizing.html

Note that this CSS3 style has not reached recommendation status, so browser support can be patchy. Use this [site](h​ttp://caniuse.com/#search=box­sizing)​ to help.

To illustrate this let's replace all of the existing css for paragraphs two and three with what is below so they have different borders and padding of 1em on all sides.

```css
#paragraph-two {
  border: 2px dashed blue;
  width: 600px;
  padding: 1em;
}


#paragraph-three {
  border: 2px dashed green;
  width: 600px;
  padding: 1em;

}
```

When we go ahead and add one more property `box-sizing: border-box;` to `paragraph-two` you can see that it gets smaller. It is including its margin *inside* the div versus outside.

For consistent sizing it is a good practice to set all of your elements to have this type of sizing as a default. This can be set at the top of your stylesheet as follows:

```css
body {
  box-sizing: border-box;
}
```
Then if you need to override it later on in the CSS its easy to do so.

Ok, we're done with those paragraphs so lets go ahead and delete the css for those and hide the paragraphs and divs.

###Float

The CSS ​float​ property demonstrates the publishing­ domain ­centric nature of CSS. It’s most common use case is to allow an image to “float” within a block of text, typically to the left or right edge, allowing paragraph text to flow around it. The floated element is taken out of the normal flow​ of type.

Let's try an example:

```css
#paragraph-four {
  background: #1a86a1;
}

#floater {
  width: 10em;
  background: #31D3FD;
  float: left;
  margin: 5px;
}
```

Here we can see a block of text floating within another block of text. The outer text wraps around the floater ​div.​The ​float ​value can be changed to ​left​ or ​right ​to change its position.

By adding some padding to `paragraph-four`:

```css
#paragraph-four {
  ...
  padding: 2em;
}
```

... we can see how the square’s padding wraps around the floater, pushing it away from the
edge as if it were part of the text.

The floater can specify it’s own ​margin​ and ​padding.​

By adding `margin: 1em;` to the `floater` we can see that property being applied only to the floater.

This also shows margin transparency. The container’s background color is visible through the margin.

The item being set to float does not have to be a smaller element inside of another. Let's *delete all of the css for the floater* and set the fifth paragraph to float left instead.

```css
.five {
  width: 10em;
  background: #31D3FD;
  float: left;
  margin: 1em;
}
```

And set the sixth to float right...

```css
.six {
  width: 10em;
  background: #31D3FD;
  float: right;
  margin: 1em;
}
```


A float tries to start close to where it is referenced. But a float can end wherever it wants, even if that means overflowing its container.  

Let's edit the size of paragraph `.five` so that the text overflows its container.

```css
.five {
  ...
  height: 30em;
}
```

If you’d like to prevent a float from overflowing its container, you can use the infamous c​learfix hack.

```css
.five {
  ...
overflow: auto;
zoom: 1; /* IE6 */
}
```

Setting `overflow: auto;` (and zoom:1; for IE6) stretches the container to wrap around it's floater. This works in most browsers but the world of clear fixing can be [treacherous](h​ttp://learnlayout.com/clearfix.html)​. There are many variations of this hack, none of them fully satisfying.


Let's delete these last few lines...

```css
height: 30em;
overflow: auto;
zoom: 1; /* IE6 */
```

And let's go ahead and set the last paragraph (nine) like so:

```css
.nine {
  clear:both;
  background: #1a86a1;
  padding: 2em;
}
```

And just like that we have a basic version of the holy grail layout using floats. This layout is something we also design with flexbox. As you continue to use css you'll gain a better understanding of which method works best for you.

###Display

Divs​, by default, are b​lock­ level elements.​They stretch left and right to take up a whole line of your document. ​​`p` and ​`form`​ are also common block­ level elements.

This default can be changed and is often done to display a list horizontally instead of vertically for a navbar.

Let's select our list set them to inline which does exactly what it sounds like.

```css
li {
  display:inline;
}
```

Notice that the first word in the list is still indented. This is a default for unordered list elements.

Simply override it by setting padding to 0.

```css
ul {
  padding: 0;
}
```

###Position

When it comes to laying elements out onto a page, perhaps the most powerful CSS style is position.​ Wrestling control of element positioning from the browser can be tough, but it’s the only way to have full control.  

The default position value of most elements is ​static.  ​An element styled with `​position: static;` ​is said to be n​ot positioned.​  

#####Relative Positioning
Relative positioning gives you the ability to move an item `relative` to its original position.

To see this in action lets modify the title of the page.

```css
.title {
  border: 3px solid red;
  position:relative;
}
```

Notice that the red border allows us to clearly see the existing boundary and the `position:relative` doesn't change anything. Once an element is relatively positioned, the ​top,​​ right,​​ left, ​and ​bottom​ properties let you shove an element wherever you’d like. Use negative values to push elements backwards.

```css
.title {
  ...
  top: 2em;
  left: 2em;
}
```

Now we can see that the title has shifted down `2em` and left `2em` from its original position. Go ahead and delete that CSS to return the title to its original location and styling.



#####Fixed Positioning

Fixed positioning allows you place an element wherever you’d like relative to the viewport - the current portion of a web page visible through a browser window.

Let's set the bottom navigation links to be fixed.

```css
.bottom-links {
  background-color: white;
  width: 100%;
  position:fixed;
  bottom: 0;
}
```
This snippet locks the footer the bottom of the screen. The element is removed entirely from the normal flow of text in the document and remains hovering in the bottom, even as you scroll the window.
This blocks any other element so as you can see our text in the blue box is too close to the fixed element. We'll change paragraph nine to have some margin on the bottom to account for this.

```css
.nine {
  ...
  margin-bottom: 3em;
}
```

##Absolute Positioning

Absolute positioning is tricky. As the name implies, it lets you position an element absolutely anywhere you’d like on a page.  

Unlike fixed positioning, absolute­ positioned elements can scroll away.
And unlike relative positioning, absolute­ positioned elements aren’t n​ecessarily ​positioned relative to their parent container.  

The confusing part is that absolute positioning i​s still relative positioning.​There are just complicated rules about what it is relative to.  

An element which has a position of absolute will be positioned *relative* to the nearest positioned ancestor. If an absolute positioned element has no ancestors that are positioned, it will be set according to the body and will move as the page scrolls.  

Lets set the top paragraph *four* to have a position of relative and move it up a little.  

```css
#paragraph-four {
  ...
  position:relative;
  top: -1em;
}
```

Now lets move the `#floater` element to the top right of the blue background div and change the color so we can see it better.

```css
#floater {
  background-color: white;
  position:absolute;
  top:1em;
  right:1em;
}
```

Now that element is positioned relative to its nearest ancestor element which is paragraph four. It is located 1em from the top and 1 em from the right side of that paragraph.

However, notice what happens if we comment out the positioning of `#paragraph-four`.

Now the `#floater` element is positioned relative to the body element `1em` from the top and `1em` from the right side.

Now that you've learned a little more about CSS you should be able to confidently position elements on the page and build some great things!
